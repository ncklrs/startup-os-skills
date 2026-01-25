# Context Passing Rules

## Document Flow

Each skill produces a document that downstream skills consume:

```
Creative Brief (user input)
      │
      ▼
┌─────────────────────────┐
│ VIDEO_SPEC.md           │ ◄── motion-designer output
│ - Overview              │
│ - Color Palette         │
│ - Scene Definitions     │
│ - Audio Specs           │
└─────────────────────────┘
      │
      ├──────────────────┬──────────────────┬──────────────────┐
      ▼                  ▼                  ▼                  ▼
┌─────────────┐   ┌─────────────┐   ┌─────────────┐   ┌─────────────┐
│ SCAFFOLD_   │   │ ANIMATION_  │   │ COMPOSITION_│   │ RENDER_     │
│ MANIFEST.md │   │ CONFIG.md   │   │ STRUCTURE.md│   │ CONFIG.md   │
└─────────────┘   └─────────────┘   └─────────────┘   └─────────────┘
      │                  │                  │
      │                  └────────┬─────────┘
      │                           ▼
      │                  ┌─────────────────────────┐
      │                  │ SCENE_*_COMPONENT.md    │
      │                  │ (one per scene)         │
      │                  └─────────────────────────┘
      │                           │
      └───────────┬───────────────┘
                  ▼
         ┌─────────────────────────┐
         │ ASSET_MANIFEST.md       │
         └─────────────────────────┘
                  │
                  ▼
         ┌─────────────────────────┐
         │ PIPELINE_COMPLETE.md    │
         └─────────────────────────┘
```

## Context Extraction Patterns

### Extract Specific Sections

```bash
# Extract just the color palette from VIDEO_SPEC
extract_palette() {
  sed -n '/## Color Palette/,/^## /p' "$PIPELINE_DIR/VIDEO_SPEC.md" | head -n -1
}

# Extract scene definitions
extract_scenes() {
  sed -n '/## Scenes/,/^## /p' "$PIPELINE_DIR/VIDEO_SPEC.md" | head -n -1
}
```

### Extract Scene-Specific Context

```bash
# Get details for Scene N
extract_scene_details() {
  local SCENE_NUM=$1
  sed -n "/### Scene $SCENE_NUM/,/^### Scene/p" "$PIPELINE_DIR/VIDEO_SPEC.md" | head -n -1
}
```

## Context Size Management

### Truncation for Large Specs

```bash
# If VIDEO_SPEC is too large, extract only relevant parts
MAX_CONTEXT_LINES=200

if [ $(wc -l < "$PIPELINE_DIR/VIDEO_SPEC.md") -gt $MAX_CONTEXT_LINES ]; then
  # Use overview + specific scene only
  CONTEXT=$(cat << EOF
$(head -50 "$PIPELINE_DIR/VIDEO_SPEC.md")

...

$(extract_scene_details $SCENE_NUM)
EOF
  )
else
  CONTEXT=$(cat "$PIPELINE_DIR/VIDEO_SPEC.md")
fi
```

### Summary Context

For downstream skills that need overview only:

```bash
# Create a summary context
create_summary_context() {
  cat << EOF
## Video Overview
$(grep -A5 "## Overview" "$PIPELINE_DIR/VIDEO_SPEC.md")

## Scene Count: $(grep -c "^### Scene" "$PIPELINE_DIR/VIDEO_SPEC.md")

## Duration: $(grep "Duration:" "$PIPELINE_DIR/VIDEO_SPEC.md" | head -1)
EOF
}
```

## Document Format Contracts

### VIDEO_SPEC.md Contract

Skills that consume VIDEO_SPEC.md expect:

```markdown
## Overview
- Duration: X seconds
- FPS: X
- Dimensions: WxH

## Color Palette
- Primary: #XXXXXX
- Secondary: #XXXXXX
- Background: #XXXXXX

## Scenes

### Scene 1: [Name]
- Duration: X seconds
- Start: Xs
- End: Xs
- Elements: [list]
- Animation: [description]

## Audio
- Music: [description]
- SFX: [list]
```

### ANIMATION_CONFIG.md Contract

Skills that consume ANIMATION_CONFIG.md expect:

```markdown
## Spring Configurations

### Default Spring
```typescript
const defaultSpring = {
  mass: 1,
  damping: 10,
  stiffness: 100
};
```

### [Animation Name] Spring
```typescript
const [name]Spring = {...};
```

## Timing Constants
```typescript
const TIMING = {
  FADE_IN: 15,
  FADE_OUT: 15,
  STAGGER_DELAY: 5
};
```
```

### COMPOSITION_STRUCTURE.md Contract

Skills that consume COMPOSITION_STRUCTURE.md expect:

```markdown
## Sequence Layout

```tsx
<Sequence from={0} durationInFrames={X}>
  <Scene1 />
</Sequence>
<Sequence from={X} durationInFrames={Y}>
  <Scene2 />
</Sequence>
```

## Scene Timing

| Scene | Start Frame | End Frame | Duration |
|-------|-------------|-----------|----------|
| 1     | 0           | X         | X frames |
| 2     | X           | Y         | Y frames |

## Total Duration
X frames = Y seconds @ Z fps
```

## Context Validation

Before passing context, validate it contains required data:

```bash
validate_video_spec() {
  local SPEC="$1"
  local ERRORS=""

  if ! grep -q "## Overview" "$SPEC"; then
    ERRORS+="Missing Overview section\n"
  fi

  if ! grep -q "## Color Palette" "$SPEC"; then
    ERRORS+="Missing Color Palette section\n"
  fi

  if ! grep -q "### Scene" "$SPEC"; then
    ERRORS+="Missing Scene definitions\n"
  fi

  if [ -n "$ERRORS" ]; then
    echo "VIDEO_SPEC validation failed:"
    echo -e "$ERRORS"
    return 1
  fi
  return 0
}
```

## Inter-Skill References

When a skill needs to reference output from another skill:

```bash
# In component-gen prompt, reference animation config
PROMPT=$(cat << EOF
Using these spring configurations from ANIMATION_CONFIG.md:
$(grep -A10 "### Default Spring" "$PIPELINE_DIR/ANIMATION_CONFIG.md")

And these timing constants:
$(grep -A10 "## Timing Constants" "$PIPELINE_DIR/ANIMATION_CONFIG.md")

Generate Scene$SCENE_NUM with these animations applied.
EOF
)
```

## Context Caching

For repeated access, cache extracted context:

```bash
# Cache commonly used extracts
CACHE_DIR="$PIPELINE_DIR/.cache"
mkdir -p "$CACHE_DIR"

get_color_palette() {
  if [ ! -f "$CACHE_DIR/palette.txt" ]; then
    extract_palette > "$CACHE_DIR/palette.txt"
  fi
  cat "$CACHE_DIR/palette.txt"
}
```
