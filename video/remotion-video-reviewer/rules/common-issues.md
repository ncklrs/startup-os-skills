---
title: Common Issues Checklist
impact: HIGH
tags: issues, checklist, quality, review
---

## Common Issues Checklist

**Impact: HIGH**

Quick reference checklist of frequent Remotion implementation issues.

### Timing Issues

**Issue 1: Seconds not converted to frames**
```typescript
// ❌ WRONG
durationInFrames: 5  // This is 5 frames, not 5 seconds!

// ✓ CORRECT
durationInFrames: 5 * 30  // 150 frames = 5 seconds at 30fps
```

**Issue 2: Missing frame offset for delays**
```typescript
// ❌ WRONG - All elements appear simultaneously
elements.map((el, i) => {
  const progress = spring({ frame, fps, config: SMOOTH });
  // ...
});

// ✓ CORRECT - Staggered appearance
elements.map((el, i) => {
  const progress = spring({
    frame: frame - (i * STAGGER_DELAY),
    fps,
    config: SMOOTH,
  });
  // ...
});
```

**Issue 3: Scene timing doesn't account for overlap**
```typescript
// ❌ WRONG - Hard cut between scenes
scene1: { start: 0, duration: 150 },
scene2: { start: 150, duration: 300 },

// ✓ CORRECT - Crossfade overlap
const TRANSITION = 15;
scene1: { start: 0, duration: 150 + TRANSITION },
scene2: { start: 150 - TRANSITION, duration: 300 + TRANSITION },
```

### Animation Issues

**Issue 4: Inline spring configs instead of constants**
```typescript
// ❌ WRONG
const progress = spring({ frame, fps, config: { damping: 200 } });

// ✓ CORRECT
const progress = spring({ frame, fps, config: SPRING_CONFIGS.smooth });
```

**Issue 5: Repeated spring calculations**
```typescript
// ❌ WRONG - Calculates spring 3 times
<div style={{
  opacity: spring({ frame, fps, config: SMOOTH }),
  scale: spring({ frame, fps, config: SMOOTH }),
  y: interpolate(spring({ frame, fps, config: SMOOTH }), [0,1], [0,100]),
}} />

// ✓ CORRECT - Calculate once, reuse
const progress = spring({ frame, fps, config: SMOOTH });
<div style={{
  opacity: progress,
  scale: progress,
  y: interpolate(progress, [0, 1], [0, 100]),
}} />
```

**Issue 6: Wrong interpolate range**
```typescript
// Spec says: Scale from 0.8 to 1.0

// ❌ WRONG
const scale = interpolate(progress, [0, 1], [0, 1]);

// ✓ CORRECT
const scale = interpolate(progress, [0, 1], [0.8, 1]);
```

### Visual Issues

**Issue 7: Hardcoded colors**
```typescript
// ❌ WRONG
backgroundColor: '#FF6B35'
color: '#FFFFFF'

// ✓ CORRECT
backgroundColor: COLORS.primary
color: COLORS.white
```

**Issue 8: Non-responsive positioning**
```typescript
// ❌ WRONG
left: 960  // Only works at 1920 width

// ✓ CORRECT
left: width / 2
transform: 'translateX(-50%)'
```

**Issue 9: Missing AbsoluteFill**
```typescript
// ❌ WRONG
function Scene1() {
  return <div>Content</div>;
}

// ✓ CORRECT
function Scene1() {
  return (
    <AbsoluteFill style={{ backgroundColor: COLORS.background }}>
      Content
    </AbsoluteFill>
  );
}
```

### Asset Issues

**Issue 10: Direct import instead of staticFile**
```typescript
// ❌ WRONG
import logo from './logo.png';
<img src={logo} />

// ✓ CORRECT
import { staticFile } from 'remotion';
<Img src={staticFile('logo.png')} />
```

**Issue 11: Wrong Audio import**
```typescript
// ❌ WRONG
import music from './music.mp3';
<Audio src={music} />

// ✓ CORRECT
import { staticFile } from 'remotion';
<Audio src={staticFile('music.mp3')} />
```

**Issue 12: Large unoptimized assets**
```typescript
// ❌ PROBLEM
// Using 4000x3000 PNG for 400x300 element

// ✓ SOLUTION
// Resize to 800x600 (2x for retina), convert to JPEG if no transparency
```

### Code Organization Issues

**Issue 13: No constants extraction**
```typescript
// ❌ WRONG
<div style={{ backgroundColor: '#FF6B35' }} />
const p = spring({ frame, fps, config: { damping: 200 } });

// ✓ CORRECT
const COLORS = { primary: '#FF6B35' } as const;
const SMOOTH = { damping: 200 };

<div style={{ backgroundColor: COLORS.primary }} />
const p = spring({ frame, fps, config: SMOOTH });
```

**Issue 14: Missing scene timing constants**
```typescript
// ❌ WRONG
<Sequence from={0} durationInFrames={150}>
<Sequence from={150} durationInFrames={300}>

// ✓ CORRECT
const SCENE_TIMING = {
  scene1: { start: 0, duration: 150 },
  scene2: { start: 150, duration: 300 },
} as const;

<Sequence from={SCENE_TIMING.scene1.start} durationInFrames={SCENE_TIMING.scene1.duration}>
```

**Issue 15: No TypeScript types**
```typescript
// ❌ WRONG
export function MyVideo(props) {

// ✓ CORRECT
export interface MyVideoProps {
  title?: string;
}

export function MyVideo({}: MyVideoProps) {
```

### Performance Issues

**Issue 16: Expensive calculations in render**
```typescript
// ❌ WRONG - Recalculated every frame
const particles = Array.from({ length: 1000 }, () => ({
  x: Math.random() * width,
  y: Math.random() * height,
}));

// ✓ CORRECT - Deterministic, seeded
const seededRandom = (seed: number) => {
  const x = Math.sin(seed) * 10000;
  return x - Math.floor(x);
};

const particles = Array.from({ length: 1000 }, (_, i) => ({
  x: seededRandom(i * 123) * width,
  y: seededRandom(i * 456) * height,
}));
```

**Issue 17: Missing memoization for heavy calculations**
```typescript
// ❌ WRONG
const complexCalculation = /* expensive operation */;

// ✓ CORRECT
const complexCalculation = useMemo(
  () => /* expensive operation */,
  [dependency]
);
```

### Integration Issues

**Issue 18: Wrong hook usage**
```typescript
// ❌ WRONG
const frame = useCurrentFrame();
// ... but never use useVideoConfig

// ✓ CORRECT
const frame = useCurrentFrame();
const { fps, width, height } = useVideoConfig();
```

**Issue 19: Incorrect Sequence nesting**
```typescript
// ❌ WRONG
<Sequence from={0} durationInFrames={150}>
  <Sequence from={150} durationInFrames={300}>  // Nested!
    <Scene2 />
  </Sequence>
</Sequence>

// ✓ CORRECT
<Sequence from={0} durationInFrames={150}>
  <Scene1 />
</Sequence>
<Sequence from={150} durationInFrames={300}>  // Sibling
  <Scene2 />
</Sequence>
```

### Quick Review Checklist

Print this for fast reviews:

**Timing**
- [ ] Seconds → frames conversion (× fps)
- [ ] Delays use frame offsets
- [ ] Scene timing adds up to total

**Animations**
- [ ] Spring configs in constants
- [ ] Progress variables extracted
- [ ] Interpolate ranges match spec

**Visuals**
- [ ] Colors use COLORS constant
- [ ] Responsive positioning (width/height)
- [ ] AbsoluteFill on all scenes

**Assets**
- [ ] staticFile() for all assets
- [ ] Appropriate formats
- [ ] Optimized sizes

**Code Quality**
- [ ] Constants extracted
- [ ] TypeScript types defined
- [ ] Scene timing constants

**Performance**
- [ ] No random() in render
- [ ] Heavy calculations memoized
- [ ] Progress variables reused
