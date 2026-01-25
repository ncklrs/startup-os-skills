# Error Handling Rules

## Retry Logic

Each skill invocation should follow this retry pattern:

```bash
invoke_skill() {
  local SKILL_NAME="$1"
  local PROMPT="$2"
  local TOOLS="$3"
  local MAX_RETRIES=2
  local RETRY_COUNT=0
  local SUCCESS=false

  while [ $RETRY_COUNT -lt $MAX_RETRIES ] && [ "$SUCCESS" = false ]; do
    echo "Invoking $SKILL_NAME (attempt $((RETRY_COUNT + 1))/$MAX_RETRIES)..."

    if claude -p "$PROMPT" --allowedTools "$TOOLS" 2>&1; then
      SUCCESS=true
    else
      RETRY_COUNT=$((RETRY_COUNT + 1))
      if [ $RETRY_COUNT -lt $MAX_RETRIES ]; then
        echo "Retry $RETRY_COUNT: $SKILL_NAME failed, retrying..."
        sleep 2
      fi
    fi
  done

  if [ "$SUCCESS" = false ]; then
    echo "ERROR: $SKILL_NAME failed after $MAX_RETRIES attempts"
    return 1
  fi
  return 0
}
```

## Failure Recovery Strategies

### Strategy 1: Partial Output Continuation

If a skill partially succeeds (creates some output but not all), continue with available output:

```bash
# Example: component-gen creates 3 of 4 scenes
if [ $(ls $PIPELINE_DIR/SCENE_*_COMPONENT.md | wc -l) -gt 0 ]; then
  echo "Partial success: $(ls $PIPELINE_DIR/SCENE_*_COMPONENT.md | wc -l) scenes created"
  echo "Missing scenes logged for manual completion"
  # Continue pipeline with partial output
fi
```

### Strategy 2: Fallback to Manual Prompt

If automated invocation fails, provide manual instructions:

```bash
if ! invoke_skill "remotion-animation" "$PROMPT" "$TOOLS"; then
  echo "=== MANUAL FALLBACK REQUIRED ==="
  echo "Run this command manually:"
  echo "claude -p \"$PROMPT\" --allowedTools \"$TOOLS\""
  echo "Then place output at: $PIPELINE_DIR/ANIMATION_CONFIG.md"
  echo "================================"
fi
```

### Strategy 3: Skip Non-Critical Steps

Some steps are optional and can be skipped:

| Step | Critical? | Skip Behavior |
|------|-----------|---------------|
| motion-designer | YES | Cannot skip - required for all downstream |
| remotion-scaffold | YES | Cannot skip - creates project structure |
| remotion-animation | NO | Use default spring configs |
| remotion-composition | YES | Cannot skip - defines scene order |
| remotion-component-gen | YES | Cannot skip - creates actual code |
| remotion-render-config | NO | Use default render settings |
| remotion-asset-coordinator | NO | Skip asset manifest |

```bash
# Skip pattern for non-critical steps
if ! invoke_skill "remotion-render-config" "$PROMPT" "$TOOLS"; then
  echo "WARN: Skipping render-config, using defaults"
  cat > "$PIPELINE_DIR/RENDER_CONFIG.md" << 'EOF'
# Default Render Config
- Codec: h264
- CRF: 18
- Resolution: 1920x1080
- FPS: 30
EOF
fi
```

## Error Logging

All errors should be logged to a pipeline error file:

```bash
LOG_FILE="$PIPELINE_DIR/pipeline.log"
ERROR_FILE="$PIPELINE_DIR/errors.log"

log() {
  echo "[$(date '+%Y-%m-%d %H:%M:%S')] $1" | tee -a "$LOG_FILE"
}

log_error() {
  echo "[$(date '+%Y-%m-%d %H:%M:%S')] ERROR: $1" | tee -a "$ERROR_FILE"
}
```

## Pipeline Status File

Maintain a status file for pipeline progress:

```bash
STATUS_FILE="$PIPELINE_DIR/status.json"

update_status() {
  local STEP="$1"
  local STATUS="$2"  # pending, running, success, failed, skipped

  # Update JSON status file
  jq --arg step "$STEP" --arg status "$STATUS" \
    '.steps[$step] = $status' "$STATUS_FILE" > tmp.json && mv tmp.json "$STATUS_FILE"
}

# Initialize status file
cat > "$STATUS_FILE" << 'EOF'
{
  "started": "$(date -u +%Y-%m-%dT%H:%M:%SZ)",
  "steps": {
    "motion-designer": "pending",
    "remotion-scaffold": "pending",
    "remotion-animation": "pending",
    "remotion-composition": "pending",
    "remotion-component-gen": "pending",
    "remotion-render-config": "pending",
    "remotion-asset-coordinator": "pending"
  }
}
EOF
```

## Cleanup on Failure

If the pipeline fails catastrophically, offer cleanup:

```bash
cleanup_failed_pipeline() {
  echo "Pipeline failed. Clean up artifacts? (y/n)"
  read -r RESPONSE
  if [ "$RESPONSE" = "y" ]; then
    rm -rf "$PIPELINE_DIR"
    echo "Artifacts cleaned up"
  else
    echo "Artifacts preserved at: $PIPELINE_DIR"
  fi
}

trap cleanup_failed_pipeline ERR
```
