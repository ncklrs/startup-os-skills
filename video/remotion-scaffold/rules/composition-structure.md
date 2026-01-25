---
title: Composition Structure
impact: HIGH
tags: structure, organization, files
---

## Composition Structure

**Impact: HIGH**

Proper file organization makes compositions maintainable and scalable.

### Folder Structure Pattern

```
src/remotion/compositions/
└── VideoName/
    ├── index.tsx           # Main composition (entry point)
    ├── constants.ts        # Colors, springs, timing
    ├── types.ts            # TypeScript interfaces
    ├── audio.ts            # Audio configuration (if needed)
    └── scenes/             # Scene components (for multi-scene)
        ├── Scene1Name.tsx
        ├── Scene2Name.tsx
        └── ...
```

### When to Use Each Pattern

**Single file (simple videos):**
- Duration < 15 seconds
- 1-2 scenes
- Minimal animations

**Multi-file with scenes/ folder:**
- Duration > 15 seconds
- 3+ distinct scenes
- Complex animations
- Team collaboration

### Good Example

```typescript
// index.tsx - Clean entry point
import { AbsoluteFill, Sequence } from "remotion";
import { COLORS, SCENE_TIMING } from "./constants";
import { IntroScene } from "./scenes/IntroScene";
import { ContentScene } from "./scenes/ContentScene";
import { OutroScene } from "./scenes/OutroScene";

export function ProductDemo() {
  return (
    <AbsoluteFill style={{ backgroundColor: COLORS.background }}>
      <Sequence from={SCENE_TIMING.intro.start} durationInFrames={SCENE_TIMING.intro.duration}>
        <IntroScene />
      </Sequence>
      <Sequence from={SCENE_TIMING.content.start} durationInFrames={SCENE_TIMING.content.duration}>
        <ContentScene />
      </Sequence>
      <Sequence from={SCENE_TIMING.outro.start} durationInFrames={SCENE_TIMING.outro.duration}>
        <OutroScene />
      </Sequence>
    </AbsoluteFill>
  );
}
```

### Bad Example

```typescript
// Everything in one massive file
export function ProductDemo() {
  // 500+ lines of code
  // All scenes inline
  // Hardcoded colors and timing
  // No separation of concerns
}
```

### Naming Conventions

| Type | Convention | Example |
|------|------------|---------|
| Composition folder | PascalCase | `ProductDemo/` |
| Main file | `index.tsx` | Always `index.tsx` |
| Scene files | `Scene{N}{Name}.tsx` | `Scene1Intro.tsx` |
| Constants | `constants.ts` | Always `constants.ts` |
| Types | `types.ts` | Always `types.ts` |

### Checklist

- [ ] Composition has its own folder
- [ ] Entry point is `index.tsx`
- [ ] Constants extracted to `constants.ts`
- [ ] Types defined in `types.ts`
- [ ] Scenes in `scenes/` folder if 3+ scenes
- [ ] Scene files follow naming convention
