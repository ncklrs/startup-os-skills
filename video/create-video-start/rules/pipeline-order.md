# Pipeline Order Rules

## Execution Order and Dependencies

The pipeline MUST execute in this exact order due to data dependencies:

```
motion-designer (1)
       ↓
       VIDEO_SPEC.md
       ↓
remotion-scaffold (2)
       ↓
       SCAFFOLD_MANIFEST.md
       ↓
remotion-animation (3) ←──┐
       ↓                  │
       ANIMATION_CONFIG.md│
       ↓                  │
remotion-composition (4)  │
       ↓                  │
       COMPOSITION_STRUCTURE.md
       ↓                  │
remotion-component-gen (5)┘ (uses both ANIMATION_CONFIG + COMPOSITION_STRUCTURE)
       ↓
       SCENE_*_COMPONENT.md
       ↓
remotion-render-config (6)
       ↓
       RENDER_CONFIG.md
       ↓
remotion-asset-coordinator (7)
       ↓
       ASSET_MANIFEST.md
```

## Dependency Matrix

| Step | Skill | Requires | Produces |
|------|-------|----------|----------|
| 1 | motion-designer | Creative brief | VIDEO_SPEC.md |
| 2 | remotion-scaffold | VIDEO_SPEC.md | SCAFFOLD_MANIFEST.md + files |
| 3 | remotion-animation | VIDEO_SPEC.md | ANIMATION_CONFIG.md |
| 4 | remotion-composition | VIDEO_SPEC.md | COMPOSITION_STRUCTURE.md |
| 5 | remotion-component-gen | VIDEO_SPEC + ANIMATION_CONFIG | SCENE_*_COMPONENT.md + files |
| 6 | remotion-render-config | VIDEO_SPEC.md | RENDER_CONFIG.md |
| 7 | remotion-asset-coordinator | VIDEO_SPEC + SCAFFOLD_MANIFEST | ASSET_MANIFEST.md |

## Parallel Execution Opportunities

Steps 3 and 4 (animation + composition) can run in parallel since they both only depend on VIDEO_SPEC.md:

```bash
# Parallel execution pattern
claude -p "remotion-animation..." &
PID_ANIMATION=$!

claude -p "remotion-composition..." &
PID_COMPOSITION=$!

wait $PID_ANIMATION $PID_COMPOSITION
```

## Validation Gates

Before proceeding to the next step, validate:

1. **After motion-designer**: VIDEO_SPEC.md exists and contains:
   - Overview section with duration, fps, dimensions
   - Color palette with hex codes
   - At least one scene definition
   - Audio specifications

2. **After remotion-scaffold**:
   - Composition directory exists
   - index.tsx created
   - constants.ts created
   - scenes/ directory exists

3. **After remotion-animation**:
   - ANIMATION_CONFIG.md contains spring configs
   - At least one spring configuration defined
   - Interpolation patterns documented

4. **After remotion-composition**:
   - COMPOSITION_STRUCTURE.md contains Sequence definitions
   - Total duration calculated
   - Scene timing breakdown present

5. **After remotion-component-gen**:
   - One SCENE_*_COMPONENT.md per scene in spec
   - Corresponding .tsx file in scenes/ folder
   - Imports reference constants.ts

6. **After remotion-render-config**:
   - RENDER_CONFIG.md contains codec settings
   - Platform-specific commands included

7. **After remotion-asset-coordinator**:
   - ASSET_MANIFEST.md lists all required assets
   - Source recommendations provided
