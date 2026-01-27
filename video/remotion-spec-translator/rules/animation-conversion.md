---
title: Animation Spec to Code Conversion
impact: CRITICAL
tags: animations, spring, interpolate, timing
---

## Animation Spec to Code Conversion

**Impact: CRITICAL**

Converting motion design animation descriptions into working spring and interpolate code.

### Spring Animation Pattern

**Spec Description:**
```markdown
Element scales from 0.8 to 1.0 with smooth spring
Spring config: { damping: 200 }
```

**Code Translation:**
```typescript
const elementProgress = spring({
  frame,
  fps,
  config: { damping: 200 },
});

const scale = interpolate(elementProgress, [0, 1], [0.8, 1]);

<div style={{
  transform: `scale(${scale})`,
}} />
```

### Multi-Property Animations

**Spec:**
```markdown
Logo entrance:
- Scale: 0.8 → 1.0
- Opacity: 0 → 1
- Y position: 50px → 0px
Timing: 0-30 frames
Spring: { damping: 200 }
```

**Code:**
```typescript
const logoProgress = spring({
  frame,
  fps,
  config: { damping: 200 },
});

const scale = interpolate(logoProgress, [0, 1], [0.8, 1]);
const opacity = logoProgress; // 0 to 1 naturally
const y = interpolate(logoProgress, [0, 1], [50, 0]);

<div style={{
  transform: `scale(${scale}) translateY(${y}px)`,
  opacity,
}} />
```

### Delayed Animations

**Spec:**
```markdown
Title appears after 30 frame delay
```

**Code:**
```typescript
const titleProgress = spring({
  frame: frame - 30,
  fps,
  config: SPRING_CONFIGS.smooth,
});

// Progress will be 0 until frame 30, then animate
```

### Hold and Exit Pattern

**Spec:**
```markdown
Element behavior:
- Frames 0-30: Enter
- Frames 30-120: Hold
- Frames 120-135: Exit
```

**Code:**
```typescript
// Entrance
const enterProgress = spring({
  frame,
  fps,
  config: SPRING_CONFIGS.smooth,
});

// Exit
const exitProgress = spring({
  frame: frame - 120,
  fps,
  config: SPRING_CONFIGS.smooth,
});

// Combine: fade in, hold, fade out
const opacity = frame < 120
  ? enterProgress
  : 1 - exitProgress;
```

### Easing vs Spring

**When spec says "smooth ease":**
```typescript
// Use interpolate with easing
const progress = frame / totalFrames;
const eased = Easing.inOut(Easing.cubic)(progress);
const x = interpolate(eased, [0, 1], [0, 1000]);
```

**When spec says "spring" or "bounce":**
```typescript
// Use spring
const progress = spring({
  frame,
  fps,
  config: { damping: 20, stiffness: 200 }, // bouncy
});
```

### Continuous Animations

**Spec:**
```markdown
Element rotates continuously
```

**Code:**
```typescript
// Linear rotation, no spring
const rotation = (frame * 2) % 360; // 2 degrees per frame

<div style={{
  transform: `rotate(${rotation}deg)`,
}} />
```

### Oscillating Animations

**Spec:**
```markdown
Element pulses between 0.9 and 1.1 scale
```

**Code:**
```typescript
const pulse = Math.sin(frame * 0.1) * 0.1 + 1;
// Oscillates: 0.9 → 1.0 → 1.1 → 1.0 → 0.9

<div style={{
  transform: `scale(${pulse})`,
}} />
```

### Sequence Timing

**Spec:**
```markdown
Three elements stagger in:
- Element 1 at frame 0
- Element 2 at frame 15
- Element 3 at frame 30
```

**Code:**
```typescript
const elements = [
  { text: 'First', delay: 0 },
  { text: 'Second', delay: 15 },
  { text: 'Third', delay: 30 },
];

{elements.map((el, i) => {
  const progress = spring({
    frame: frame - el.delay,
    fps,
    config: SPRING_CONFIGS.smooth,
  });

  return (
    <div key={i} style={{ opacity: progress }}>
      {el.text}
    </div>
  );
})}
```

### Path Animations

**Spec:**
```markdown
Element follows arc from (0, 0) to (500, 300)
```

**Code:**
```typescript
const progress = spring({
  frame,
  fps,
  config: SPRING_CONFIGS.smooth,
});

// Arc calculation
const x = interpolate(progress, [0, 1], [0, 500]);
const y = interpolate(progress, [0, 1], [0, 300]) +
  Math.sin(progress * Math.PI) * 100; // Arc height

<div style={{
  transform: `translate(${x}px, ${y}px)`,
}} />
```

### Common Spring Configs

Map spec descriptions to configs:

| Spec Description | Spring Config | Use Case |
|-----------------|---------------|----------|
| "smooth", "elegant" | `{ damping: 200 }` | Refined animations |
| "snappy", "quick" | `{ damping: 20, stiffness: 200 }` | UI interactions |
| "bouncy", "playful" | `{ damping: 8 }` | Energetic entrances |
| "heavy", "dramatic" | `{ damping: 15, stiffness: 80, mass: 2 }` | Big reveals |
| "subtle", "gentle" | `{ damping: 300 }` | Background elements |

### Animation Checklist

When converting animation specs:

- [ ] Identify animation type (spring vs easing vs continuous)
- [ ] Extract timing values to frame calculations
- [ ] Create progress variable with spring/interpolate
- [ ] Apply progress to correct CSS properties
- [ ] Handle delays with frame offsets
- [ ] Use appropriate spring config from constants
- [ ] Combine multiple properties on same progress
- [ ] Add comments referencing spec timing
- [ ] Test edge cases (frame 0, last frame)
