# Claude CLI Patterns

## Basic Invocation Pattern

```bash
claude -p "<prompt>" --allowedTools "<tools>"
```

### Parameters

| Flag | Purpose | Example |
|------|---------|---------|
| `-p` | Print mode - non-interactive | Always required |
| `--allowedTools` | Comma-separated tool list | `"Read,Write,Edit,Bash"` |
| `--output-format` | Output format | `json`, `text` |

## Tool Permission Sets by Skill

Each skill requires specific tools:

```bash
# motion-designer: Creates VIDEO_SPEC.md
TOOLS_MOTION="Read,Write,Edit,Bash"

# remotion-scaffold: Creates folder structure
TOOLS_SCAFFOLD="Read,Write,Edit,Bash,Glob"

# remotion-animation: Generates animation configs
TOOLS_ANIMATION="Read,Write,Edit"

# remotion-composition: Creates sequence layout
TOOLS_COMPOSITION="Read,Write,Edit"

# remotion-component-gen: Generates scene components
TOOLS_COMPONENT="Read,Write,Edit,Glob"

# remotion-render-config: Creates render settings
TOOLS_RENDER="Read,Write,Edit"

# remotion-asset-coordinator: Asset manifest
TOOLS_ASSET="Read,Write,Edit,WebSearch"
```

## Prompt Construction Pattern

### Template Structure

```bash
build_prompt() {
  local SKILL="$1"
  local CONTEXT="$2"
  local OUTPUT_PATH="$3"

  cat << EOF
You are using the /$SKILL skill.

$CONTEXT

Output your result to: $OUTPUT_PATH

Follow the skill's output format exactly.
EOF
}
```

### Context Injection

Include relevant outputs from previous steps:

```bash
# Include VIDEO_SPEC in downstream prompts
SPEC_CONTENT=$(cat "$PIPELINE_DIR/VIDEO_SPEC.md")

PROMPT=$(cat << EOF
You are using the /remotion-scaffold skill.

Based on this VIDEO_SPEC.md:
$SPEC_CONTENT

Create the project scaffold...
EOF
)
```

### Multi-Context Injection

When a skill needs multiple inputs:

```bash
# remotion-component-gen needs multiple contexts
SPEC=$(cat "$PIPELINE_DIR/VIDEO_SPEC.md")
ANIMATION=$(cat "$PIPELINE_DIR/ANIMATION_CONFIG.md")
COMPOSITION=$(cat "$PIPELINE_DIR/COMPOSITION_STRUCTURE.md")

PROMPT=$(cat << EOF
You are using the /remotion-component-gen skill.

VIDEO_SPEC.md:
$SPEC

ANIMATION_CONFIG.md:
$ANIMATION

COMPOSITION_STRUCTURE.md:
$COMPOSITION

Generate Scene$SCENE_NUM component...
EOF
)
```

## Output Capture Patterns

### Capture to File

```bash
# Direct file output (skill writes the file)
claude -p "$PROMPT" --allowedTools "$TOOLS"

# Capture stdout to file
claude -p "$PROMPT" --allowedTools "$TOOLS" > "$OUTPUT_FILE"
```

### Capture with Validation

```bash
OUTPUT=$(claude -p "$PROMPT" --allowedTools "$TOOLS" 2>&1)
EXIT_CODE=$?

if [ $EXIT_CODE -eq 0 ]; then
  echo "Skill completed successfully"
else
  echo "Skill failed with exit code: $EXIT_CODE"
  echo "Output: $OUTPUT"
fi
```

## HEREDOC Patterns

### Simple HEREDOC

```bash
claude -p "$(cat << 'EOF'
You are using the /motion-designer skill.

Create a VIDEO_SPEC.md for:
- Product demo video
- 30 seconds
- Modern tech aesthetic

EOF
)" --allowedTools "Read,Write,Edit"
```

### HEREDOC with Variable Interpolation

```bash
# Note: No quotes around EOF allows variable expansion
claude -p "$(cat << EOF
You are using the /remotion-scaffold skill.

Based on this spec:
$VIDEO_SPEC_CONTENT

Create scaffold at: $PROJECT_PATH
EOF
)" --allowedTools "Read,Write,Edit,Bash"
```

### HEREDOC with Preserved Formatting

```bash
# Use 'EOF' (quoted) to prevent variable expansion
claude -p "$(cat << 'EOF'
Generate this exact TypeScript:

```typescript
const springConfig = {
  mass: 1,
  damping: 10,
  stiffness: 100
};
```
EOF
)" --allowedTools "Write"
```

## Parallel Execution

```bash
# Run independent skills in parallel
claude -p "$ANIMATION_PROMPT" --allowedTools "$TOOLS_ANIMATION" &
PID1=$!

claude -p "$COMPOSITION_PROMPT" --allowedTools "$TOOLS_COMPOSITION" &
PID2=$!

# Wait for both to complete
wait $PID1
STATUS1=$?

wait $PID2
STATUS2=$?

if [ $STATUS1 -eq 0 ] && [ $STATUS2 -eq 0 ]; then
  echo "Parallel execution successful"
fi
```

## Loop Patterns

### Scene Generation Loop

```bash
# Extract scene count from VIDEO_SPEC
SCENE_COUNT=$(grep -c "^## Scene" "$PIPELINE_DIR/VIDEO_SPEC.md")

for i in $(seq 1 $SCENE_COUNT); do
  PROMPT=$(build_scene_prompt $i)

  claude -p "$PROMPT" \
    --allowedTools "$TOOLS_COMPONENT"

  # Validate output
  if [ ! -f "$PIPELINE_DIR/SCENE_${i}_COMPONENT.md" ]; then
    echo "ERROR: Scene $i generation failed"
  fi
done
```

## Environment Variables

```bash
# Set environment for all invocations
export ANTHROPIC_API_KEY="${ANTHROPIC_API_KEY}"
export PIPELINE_DIR="$PIPELINE_DIR"

# Pass environment context
claude -p "Working directory: $PIPELINE_DIR
$PROMPT" --allowedTools "$TOOLS"
```
