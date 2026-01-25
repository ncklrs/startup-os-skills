---
title: Transitions and Scene Flow
impact: HIGH
tags: transitions, scene-change, flow, continuity
---

## Transitions and Scene Flow

**Impact: HIGH**

Transitions connect scenes and maintain visual flow. Well-designed transitions feel invisible; poor transitions break immersion and feel jarring.

## The Golden Rule of Transitions

**The best transition is often no transition at all.** Use transitions to serve the story, not to show off effects.

## Transition Categories

### 1. Cut (Instant)

**When to Use**: Related scenes, fast pacing, energetic content

**Character**: Immediate, no overlap

#### Good Example
```
Scene 1: Product closeup (ends frame 90)
Scene 2: Product in context (starts frame 90)

Instant cut works because:
- Same subject matter
- Visual continuity
- Fast-paced energy
```

#### Bad Example
```
Scene 1: Dark, moody
Scene 2: Bright, playful

Instant cut creates jarring contrast.
```

### 2. Crossfade (Dissolve)

**When to Use**: Gentle transitions, time passing, mood shifts

**Duration**: 0.3-1s (9-30 frames at 30fps)

#### Good Example
```typescript
// Scene 1 fades out
const scene1Opacity = interpolate(
  frame,
  [60, 75],
  [1, 0],
  { extrapolateRight: 'clamp' }
);

// Scene 2 fades in (overlap)
const scene2Opacity = interpolate(
  frame,
  [68, 83],
  [0, 1],
  { extrapolateRight: 'clamp' }
);

// 8-frame overlap creates smooth blend
```

Overlap creates seamless transition.

#### Bad Example
```
Scene 1 fades out: frames 60-75
Scene 2 fades in: frames 75-90

No overlap = visible gap.
```

### 3. Slide/Push

**When to Use**: Directional flow, revealing new content, UI-style videos

**Duration**: 0.5-1s (15-30 frames)

#### Good Example
```typescript
// Scene 1 slides left, exits
const scene1X = interpolate(
  frame,
  [90, 105],
  [0, -1920],
  { extrapolateRight: 'clamp' }
);

// Scene 2 slides in from right
const scene2X = interpolate(
  frame,
  [90, 105],
  [1920, 0],
  { extrapolateRight: 'clamp' }
);

// Both move in sync, same timing
```

Creates cohesive directional movement.

### 4. Scale Transition

**When to Use**: Zooming focus, hierarchical relationships, dramatic reveals

**Duration**: 0.5-1.5s (15-45 frames)

#### Good Example
```typescript
// Scene 1 scales down and fades
const scene1Scale = spring({
  frame: frame - 90,
  fps,
  from: 1,
  to: 0.8,
  config: { damping: 200 }
});

const scene1Opacity = interpolate(
  frame,
  [90, 105],
  [1, 0]
);

// Scene 2 scales up from small
const scene2Scale = spring({
  frame: frame - 95,
  fps,
  from: 0.8,
  to: 1,
  config: { damping: 200 }
});
```

Creates zoom hierarchy.

### 5. Wipe

**When to Use**: Clean segmentation, chapter changes, directional narrative

**Duration**: 0.4-0.8s (12-24 frames)

#### Good Example
```
Wipe Transition (left to right):

Wipe element:
  - Width animates: 0 → 1920px over 20 frames
  - Color: Brand color or white
  - Covers scene 1, reveals scene 2

Timing:
  Frame 90-100: Wipe covers scene 1
  Frame 100-110: Wipe reveals scene 2
```

Clean, directional scene change.

### 6. Morphing Elements

**When to Use**: Showing transformation, connecting related concepts

**Duration**: 0.8-1.5s (24-45 frames)

#### Good Example
```
Icon Morph Transition:

Scene 1: Ends with icon A (centered)
Transition: Icon A morphs to icon B (0.8s)
Scene 2: Starts with icon B (centered)

Visual continuity through shared element.
```

## Transition Timing Guidelines

| Transition Type | Min Duration | Optimal | Max Duration |
|----------------|--------------|---------|--------------|
| Cut | 0s | 0s | 0s |
| Fast crossfade | 0.2s | 0.3s | 0.5s |
| Standard crossfade | 0.5s | 0.8s | 1.2s |
| Slide | 0.4s | 0.6s | 1s |
| Scale | 0.5s | 1s | 1.5s |
| Wipe | 0.3s | 0.5s | 0.8s |
| Morph | 0.8s | 1.2s | 2s |

## Directional Consistency

Maintain logical directional flow across transitions.

### Good Example
```
Video Navigation Flow:

Scene 1 → Scene 2: Slide left (forward)
Scene 2 → Scene 3: Slide left (forward)
Scene 3 → Scene 2: Slide right (back)

Direction indicates forward/backward navigation.
```

### Bad Example
```
Scene 1 → Scene 2: Slide left
Scene 2 → Scene 3: Slide right
Scene 3 → Scene 4: Slide up

Random directions = confusing.
```

## Easing and Spring Transitions

Different transitions need different timing curves:

### Sharp/Snappy (UI, energetic)
```typescript
spring({
  config: { damping: 20, stiffness: 200 }
})
// Quick, minimal bounce
```

### Smooth/Elegant (brand, professional)
```typescript
spring({
  config: { damping: 200 }
})
// No bounce, smooth
```

### Bouncy/Playful (fun, casual)
```typescript
spring({
  config: { damping: 8 }
})
// Visible bounce
```

## Audio Sync with Transitions

Pair transitions with appropriate sound effects:

| Transition Type | Recommended SFX |
|----------------|-----------------|
| Cut | None (or subtle click) |
| Crossfade | Subtle whoosh |
| Slide | Directional swoosh |
| Scale | Whoosh + impact |
| Wipe | Sharp swoosh |
| Morph | Shimmer or glitch |

#### Good Example
```
Slide Transition:

Visual:
  Frame 90-105: Scenes slide (0.5s)

Audio:
  Frame 90: Swoosh SFX starts (0.4s duration)
  Frame 90-95: Background music ducks to 30%
  Frame 95-105: Background music returns to 50%

Audio emphasizes and smooths transition.
```

## Transition Overuse Prevention

### Good Pattern
```
30-second video:

0-8s: Scene 1 (no transition, video starts)
8s: Crossfade to Scene 2 (0.5s)
8.5-16.5s: Scene 2
16.5s: Slide to Scene 3 (0.5s)
17-25s: Scene 3
25s: Scale to Scene 4 (0.8s)
25.8-30s: Scene 4 (holds for end)

3 transitions for 4 scenes = appropriate.
```

### Bad Pattern
```
Every 2 seconds: Different flashy transition
= Distracting, amateur
```

## Complex Multi-Element Transitions

For smooth scene changes, stagger element timing:

#### Good Example
```
Scene 1 to Scene 2 Transition:

Scene 1 elements exit (staggered):
  Frame 90: Background fades (0.5s)
  Frame 92: Text slides out left (0.4s)
  Frame 94: Icon scales down (0.3s)

Scene 2 elements enter (staggered):
  Frame 96: Background fades in (0.5s)
  Frame 98: Text slides in right (0.4s)
  Frame 100: Icon scales up (0.3s)

Total transition: 10 frames (0.33s)
Elements overlap for smooth flow.
```

### Bad Example
```
All Scene 1 elements exit at once: Frame 90
All Scene 2 elements enter at once: Frame 100

Feels mechanical, not flowing.
```

## Masked Transitions

Use shape masks for creative transitions:

#### Good Example
```
Circle Mask Transition:

Circle mask:
  - Starts: 0px radius at center
  - Ends: 2000px radius (covers frame)
  - Duration: 0.6s (18 frames)
  - Easing: Ease-out

Reveals Scene 2 through expanding circle.
```

## Color-Based Transitions

Use intermediate color frames for smooth color shifts:

#### Good Example
```
Dark to Light Scene Transition:

Frame 90-92: Scene 1 darkens (multiply by 0.7)
Frame 92-94: White flash overlay (0 → 1 → 0 opacity)
Frame 94-96: Scene 2 lightens (multiply by 0.7 → 1)

Total: 6 frames (0.2s)
Color shift feels intentional.
```

## Transition Matching Content

Match transition style to content:

| Content Type | Best Transitions |
|-------------|------------------|
| Professional/Corporate | Crossfade, simple slides |
| Tech/Modern | Wipes, glitch effects |
| Playful/Fun | Bouncy scales, colorful |
| Elegant/Luxury | Slow crossfades, smooth |
| Energetic/Sports | Fast cuts, dynamic slides |
| Educational | Clean wipes, simple fades |

## Checklist

- [ ] Transition serves the story (not gratuitous)
- [ ] Duration appropriate for content (0.3-1s typical)
- [ ] Easing/spring config matches video mood
- [ ] Direction is consistent and logical
- [ ] Audio (SFX) synchronized with transition
- [ ] Background music ducks during transition if SFX present
- [ ] Multi-element transitions use staggering
- [ ] Transition type matches content style
- [ ] Not overused (max 1 transition per 5-10s)
- [ ] Consistent style with other transitions in video
- [ ] Elements don't feel "cut off" mid-animation
- [ ] Total transition count is reasonable (3-6 for 30s video)
