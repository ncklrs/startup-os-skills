---
title: Virtual Camera Movement and Perspective
impact: MEDIUM
tags: camera, parallax, perspective, depth, zoom
---

## Virtual Camera Movement and Perspective

**Impact: MEDIUM**

In motion graphics, virtual camera movement creates depth, dynamism, and cinematic quality. Even in 2D compositions, camera techniques bring scenes to life.

## Camera Movement Types

### 1. Pan (Horizontal Movement)

**When to Use**: Show wide scenes, reveal content, follow action

**Speed**: Slow to medium for smooth feel

#### Good Example
```typescript
// Smooth pan across landscape
const cameraX = interpolate(
  frame,
  [0, 120],
  [0, -1920],
  {
    easing: Easing.inOut(Easing.quad),
    extrapolateRight: 'clamp'
  }
);

return (
  <div style={{ transform: `translateX(${cameraX}px)` }}>
    {/* Wide content */}
  </div>
);
```

Smooth, controlled horizontal movement.

#### Bad Example
```
Pan speed: 0.1s for 1920px = too fast, jarring
```

### 2. Tilt (Vertical Movement)

**When to Use**: Reveal height, show top-to-bottom, dramatic reveals

#### Good Example
```typescript
// Tilt up building reveal
const cameraY = spring({
  frame,
  fps,
  from: 1080,
  to: 0,
  config: { damping: 200 }
});

<div style={{ transform: `translateY(${cameraY}px)` }} />
```

### 3. Zoom (Scale)

**When to Use**: Emphasize details, create drama, focus shifts

#### Good Example
```typescript
// Zoom in on product detail
const zoom = spring({
  frame: frame - 60,
  fps,
  from: 1,
  to: 2,
  config: { damping: 200 }
});

const offsetX = -480; // Keep centered during zoom
const offsetY = -270;

<div style={{
  transform: `scale(${zoom}) translate(${offsetX}px, ${offsetY}px)`
}} />
```

Zoom while maintaining center point.

#### Bad Example
```
Scale without translate adjustment:
  - Zooms from top-left corner
  - Feels broken
```

### 4. Dolly (Z-Axis Movement)

**When to Use**: Create depth, move through layers

#### Good Example
```typescript
// Dolly through layers (parallax)
const dollyProgress = spring({ frame, fps });

const layer1Z = interpolate(dollyProgress, [0, 1], [0, -200]);
const layer2Z = interpolate(dollyProgress, [0, 1], [0, -100]);
const layer3Z = interpolate(dollyProgress, [0, 1], [0, 0]);

<>
  <Layer style={{ transform: `translateZ(${layer1Z}px)` }} />
  <Layer style={{ transform: `translateZ(${layer2Z}px)` }} />
  <Layer style={{ transform: `translateZ(${layer3Z}px)` }} />
</>
```

Creates depth perception through differential movement.

### 5. Orbit (Rotate Around)

**When to Use**: Show object from multiple angles, dynamic product shots

#### Good Example
```typescript
// Orbit around product
const angle = interpolate(
  frame,
  [0, 120],
  [0, 360]
);

<div style={{
  transform: `rotate(${angle}deg)`
}} />
```

## Parallax Effect (Multi-Layer Movement)

Create depth with differential layer speeds:

### The Parallax Ratio

- **Foreground**: 1.5x speed (fastest)
- **Midground**: 1.0x speed (normal)
- **Background**: 0.5x speed (slowest)

### Good Example
```typescript
const { fps } = useVideoConfig();
const frame = useCurrentFrame();

const baseMovement = interpolate(
  frame,
  [0, 90],
  [0, -500]
);

const foregroundX = baseMovement * 1.5;  // Fastest
const midgroundX = baseMovement * 1.0;   // Normal
const backgroundX = baseMovement * 0.5;  // Slowest

return (
  <>
    <Background style={{ transform: `translateX(${backgroundX}px)` }} />
    <Midground style={{ transform: `translateX(${midgroundX}px)` }} />
    <Foreground style={{ transform: `translateX(${foregroundX}px)` }} />
  </>
);
```

Creates convincing depth perception.

### Bad Example
```
All layers move at same speed:
  - No depth
  - Feels flat
```

## Camera Easing and Feel

Different movements need different easing:

### Smooth and Cinematic
```typescript
spring({ config: { damping: 200 } })
// Gentle, elegant camera moves
```

### Quick and Snappy
```typescript
spring({ config: { damping: 20, stiffness: 200 } })
// Fast camera whips, energetic
```

### Mechanical and Precise
```typescript
interpolate(frame, [0, 60], [0, 100], {
  easing: Easing.inOut(Easing.quad)
})
// Controlled, predictable
```

## Camera Movement Timing

| Movement | Min Duration | Optimal | Max Duration |
|----------|--------------|---------|--------------|
| Quick pan | 0.5s | 1s | 2s |
| Smooth pan | 2s | 4s | 6s |
| Zoom in | 0.8s | 1.5s | 3s |
| Zoom out | 0.5s | 1s | 2s |
| Orbit | 3s | 5s | 8s |
| Parallax drift | 5s+ | Continuous | — |

## The Ken Burns Effect

Static image with slow zoom/pan (documentary style):

### Good Example
```typescript
// Slow zoom and pan on photo
const progress = frame / (durationInFrames - 1);

const scale = interpolate(progress, [0, 1], [1, 1.2]);
const x = interpolate(progress, [0, 1], [0, -100]);
const y = interpolate(progress, [0, 1], [0, -50]);

<img
  src="photo.jpg"
  style={{
    transform: `scale(${scale}) translate(${x}px, ${y}px)`
  }}
/>
```

Creates life in static images.

## Camera Shake

Add energy or tension with subtle shake:

### Good Example
```typescript
// Subtle camera shake on impact
const shakeIntensity = spring({
  frame: frame - impactFrame,
  fps,
  from: 10,
  to: 0,
  config: { damping: 15 }
});

const shakeX = Math.sin(frame * 0.5) * shakeIntensity;
const shakeY = Math.cos(frame * 0.7) * shakeIntensity;

<div style={{
  transform: `translate(${shakeX}px, ${shakeY}px)`
}} />
```

Controlled shake that settles quickly.

### Bad Example
```
Random large movements:
  - Nauseating
  - Unprofessional
```

## Focus Shifts (Simulated Depth of Field)

Blur background/foreground to direct attention:

### Good Example
```typescript
// Shift focus from background to foreground
const blurBg = interpolate(
  frame,
  [60, 90],
  [0, 10],
  { extrapolateRight: 'clamp' }
);

const blurFg = interpolate(
  frame,
  [60, 90],
  [10, 0],
  { extrapolateRight: 'clamp' }
);

<>
  <Background style={{ filter: `blur(${blurBg}px)` }} />
  <Foreground style={{ filter: `blur(${blurFg}px)` }} />
</>
```

Mimics camera focus shift.

## The 180-Degree Rule

Maintain consistent spatial relationships:

### Good Example
```
Scene 1: Camera shows object from left
Scene 2: Camera moves right but stays on same side of object
Scene 3: Camera continues right, same side

Viewer maintains spatial awareness.
```

### Bad Example
```
Scene 1: View from left
Scene 2: Jump to opposite side

Disorients viewer.
```

## Dutch Angle (Tilted Frame)

Rotated camera for tension or dynamism:

### Good Example
```typescript
// Subtle tilt for energy (5-15 degrees)
const tilt = 8;

<div style={{ transform: `rotate(${tilt}deg)` }} />
```

Use sparingly for emphasis.

### Bad Example
```
45-degree tilt:
  - Extreme, nauseating
  - Use only for intentional disorientation
```

## Camera Path Planning

Plan camera movements on paper first:

### Good Example
```
Shot List:

Shot 1 (0-3s): Wide establishing shot, static
Shot 2 (3-8s): Slow zoom in, 1.0 → 1.5 scale
Shot 3 (8-12s): Pan right while zoomed, reveal detail
Shot 4 (12-15s): Zoom out, return to wide

Intentional, storyboarded camera plan.
```

### Bad Example
```
Random camera movements:
  - No plan
  - Feels arbitrary
```

## Combining Camera Movements

Layer movements for complexity:

### Good Example
```typescript
// Pan + zoom simultaneously
const pan = interpolate(frame, [0, 120], [0, -500]);
const zoom = interpolate(frame, [0, 120], [1, 1.3]);

<div style={{
  transform: `translateX(${pan}px) scale(${zoom})`
}} />
```

Cinematic, dynamic movement.

### Bad Example
```
Pan, then zoom (sequential):
  - Feels mechanical
  - Less engaging
```

## Virtual Camera Limits

Respect physical camera constraints for realism:

### Good Limits
- Max zoom: 3x (feels realistic)
- Max rotation: 15° for energy, 45° for extreme
- Pan speed: Not faster than viewer can track
- Movement smoothness: No instant stops/starts

### Bad Limits
```
10x zoom, instant movements, 90° rotations:
  - Feels fake, videogame-like
```

## Handheld Simulation

Subtle, irregular movement for documentary feel:

### Good Example
```typescript
// Subtle handheld wobble
const wobbleX = Math.sin(frame * 0.1) * 2 + Math.cos(frame * 0.15) * 1;
const wobbleY = Math.cos(frame * 0.12) * 2 + Math.sin(frame * 0.08) * 1;

<div style={{
  transform: `translate(${wobbleX}px, ${wobbleY}px)`
}} />
```

Subtle, organic motion.

## Checklist

- [ ] Camera movement serves story purpose
- [ ] Movement speed is comfortable (not too fast)
- [ ] Easing applied (no linear movements)
- [ ] Parallax uses proper layer speed ratios (0.5x, 1x, 1.5x)
- [ ] Zoom maintains proper center point
- [ ] Camera shake is controlled and brief
- [ ] Movement duration appropriate (1-4s typical)
- [ ] 180-degree rule maintained
- [ ] Combined movements feel intentional
- [ ] Maximum zoom limited to 3x for realism
- [ ] No instant starts or stops
- [ ] Focus shifts direct attention effectively
- [ ] Camera plan supports narrative
- [ ] Handheld effect is subtle if used
- [ ] Movement doesn't cause motion sickness
