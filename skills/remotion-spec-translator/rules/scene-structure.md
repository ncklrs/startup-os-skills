---
title: Scene Component Structure
impact: CRITICAL
tags: structure, scenes, components, layout
---

## Scene Component Structure

**Impact: CRITICAL**

Every scene in a motion design spec must translate to a properly structured Remotion scene component.

### Core Pattern

Each scene component follows this structure:

```typescript
function SceneNName() {
  const frame = useCurrentFrame();
  const { fps, width, height } = useVideoConfig();

  // Animation progress calculations
  const progress = spring({
    frame,
    fps,
    config: SPRING_CONFIGS.configName,
  });

  // Element-specific animations
  const element1Progress = spring({
    frame: frame - delayFrames,
    fps,
    config: SPRING_CONFIGS.configName,
  });

  return (
    <AbsoluteFill style={{ backgroundColor: COLORS.background }}>
      {/* Background layer */}
      <div>{/* Background elements */}</div>

      {/* Midground layer */}
      <div>{/* Primary content */}</div>

      {/* Foreground layer */}
      <div>{/* Overlay elements */}</div>
    </AbsoluteFill>
  );
}
```

### Naming Convention

From spec scene name to component name:

**Spec:**
```markdown
## Scene 1: Logo Reveal (0s - 5s)
## Scene 2: Product Showcase (5s - 15s)
```

**Code:**
```typescript
function Scene1LogoReveal() { }
function Scene2ProductShowcase() { }
```

Pattern: `Scene[N][PascalCaseName]`

### Layer Organization

Organize elements by visual depth:

```typescript
<AbsoluteFill style={{ backgroundColor: COLORS.background }}>
  {/* BACKGROUND LAYER - slowest movement, deepest */}
  <div style={{ position: 'absolute', ... }}>
    {/* Gradients, patterns, ambient elements */}
  </div>

  {/* MIDGROUND LAYER - primary content */}
  <div style={{ position: 'absolute', ... }}>
    {/* Main UI, text, key visuals */}
  </div>

  {/* FOREGROUND LAYER - fastest movement, closest */}
  <div style={{ position: 'absolute', ... }}>
    {/* Overlays, particles, focal elements */}
  </div>
</AbsoluteFill>
```

### State Management

Extract animation progress variables:

```typescript
// Good - reusable progress
const titleProgress = spring({
  frame: frame - 30,
  fps,
  config: SPRING_CONFIGS.smooth,
});

const titleOpacity = titleProgress;
const titleY = interpolate(titleProgress, [0, 1], [50, 0]);

<div style={{
  opacity: titleOpacity,
  transform: `translateY(${titleY}px)`,
}}>
  {title}
</div>

// Bad - repeated calculations
<div style={{
  opacity: spring({ frame: frame - 30, fps, config: { damping: 200 } }),
  transform: `translateY(${interpolate(
    spring({ frame: frame - 30, fps, config: { damping: 200 } }),
    [0, 1],
    [50, 0]
  )}px)`,
}}>
  {title}
</div>
```

### Delayed Animations

Handle staggered entrances:

```typescript
// Spec: "Elements stagger in with 10 frame delays"
const elements = ['Item 1', 'Item 2', 'Item 3'];

{elements.map((text, index) => {
  const delay = index * 10;
  const elementProgress = spring({
    frame: frame - delay,
    fps,
    config: SPRING_CONFIGS.smooth,
  });

  return (
    <div
      key={index}
      style={{
        opacity: elementProgress,
        transform: `translateX(${interpolate(
          elementProgress,
          [0, 1],
          [-30, 0]
        )}px)`,
      }}
    >
      {text}
    </div>
  );
})}
```

### Scene Dimensions

Use VideoConfig for responsive positioning:

```typescript
function Scene1() {
  const { width, height } = useVideoConfig();

  return (
    <AbsoluteFill>
      {/* Center element */}
      <div style={{
        position: 'absolute',
        left: width / 2,
        top: height / 2,
        transform: 'translate(-50%, -50%)',
      }}>
        Centered
      </div>

      {/* Percentage-based positioning */}
      <div style={{
        position: 'absolute',
        left: width * 0.2,
        top: height * 0.3,
      }}>
        20% from left, 30% from top
      </div>
    </AbsoluteFill>
  );
}
```

### Checklist

When translating scene specs to components:

- [ ] Component name matches spec scene name
- [ ] Uses AbsoluteFill as root wrapper
- [ ] Destructures frame, fps, width, height from hooks
- [ ] Animation progress variables are extracted
- [ ] Elements organized by visual depth layers
- [ ] Delayed animations use frame offsets
- [ ] Positions use width/height from VideoConfig
- [ ] Background color from COLORS constant
- [ ] Spring configs from SPRING_CONFIGS constant
- [ ] Comments reference spec sections
