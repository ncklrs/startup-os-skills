---
title: Timing and Pacing
impact: CRITICAL
tags: timing, pacing, rhythm, tempo, frames
---

## Timing and Pacing

**Impact: CRITICAL**

Timing is the soul of motion design. The same visual elements with different timing create entirely different emotional experiences.

## Frame Rate Foundation

Working at 30 fps (frames per second):
- 1 second = 30 frames
- 0.1 second = 3 frames
- 0.5 second = 15 frames

Always think in seconds first, then multiply by fps for frame precision.

### Good Example
```typescript
const { fps } = useVideoConfig();

// Define in seconds, convert to frames
const INTRO_DURATION = 2 * fps;        // 60 frames
const TRANSITION_TIME = 0.5 * fps;     // 15 frames
const HOLD_TIME = 1.5 * fps;           // 45 frames
```

Readable and maintainable timing.

### Bad Example
```typescript
// Magic numbers with no context
const intro = spring({ frame: frame - 60 });
const transition = spring({ frame: frame - 15 });
```

Unclear what the timings represent.

## Minimum Perception Times

Human perception has physical limits:

- **2 frames (0.07s)** — Absolute minimum to register something happened
- **6 frames (0.2s)** — Minimum for recognizing what happened
- **9 frames (0.3s)** — Comfortable minimum for reading short text
- **15 frames (0.5s)** — Standard UI micro-interaction
- **30 frames (1s)** — Comfortable for reading a sentence

### Good Example
```
Scene: Success Notification

Frame 0-9: Checkmark appears (0.3s - recognizable)
Frame 9-69: "Success!" message holds (2s - readable)
Frame 69-84: Fade out (0.5s - smooth exit)

Total: 2.8 seconds
```

Every element has sufficient time to register.

### Bad Example
```
Scene: Rushed Notification

Frame 0-3: Checkmark flashes (0.1s - too fast)
Frame 3-18: Message appears (0.5s - can't read)
Frame 18-21: Fade out (0.1s - jarring)

Total: 0.7 seconds
```

Too fast to comprehend.

## The Golden Ratio of Motion

Entrances and exits should follow asymmetric timing:

- **Entrance: 1.0x** — Normal speed, builds anticipation
- **Hold: 2-3x** — Longer duration, allows comprehension
- **Exit: 0.5-0.7x** — Faster than entrance, maintains energy

### Good Example
```
Element Animation Arc:

Entrance: 0-45 frames (1.5s)
  - Spring animation with anticipation

Hold: 45-135 frames (3s)
  - Static or subtle animation
  - Time to read/understand

Exit: 135-165 frames (1s)
  - Faster spring or fade
  - Move to next element

Ratio: 1.5s : 3s : 1s  (1 : 2 : 0.67)
```

Creates natural rhythm with emphasis on content.

### Bad Example
```
Symmetric Timing:

Entrance: 1s
Hold: 1s
Exit: 1s

Ratio: 1 : 1 : 1
```

Feels mechanical and boring.

## Staggered Timing

When animating multiple elements, stagger by 3-10 frames for flow.

### Good Example
```
List of 5 Items Entering:

Item 1: frame 0
Item 2: frame 6   (0.2s delay)
Item 3: frame 12  (0.4s delay)
Item 4: frame 18  (0.6s delay)
Item 5: frame 24  (0.8s delay)

Each item 6 frames (0.2s) after previous.
Total cascade: 24 frames (0.8s)
```

Creates smooth, flowing cascade effect.

### Bad Example
```
All Items Simultaneous:

All items: frame 0

OR

All items: random delays
```

Simultaneous feels chaotic. Random delays feel unintentional.

## Easing and Spring Timing

Different animations need different timing curves:

### Fast and Snappy (UI elements)
```typescript
spring({
  config: { damping: 20, stiffness: 200 }
  // Quick, minimal bounce
  // Duration: ~20-30 frames (0.7-1s)
})
```

### Smooth and Natural (transitions)
```typescript
spring({
  config: { damping: 200 }
  // No bounce, elegant
  // Duration: ~25-40 frames (0.8-1.3s)
})
```

### Bouncy and Playful (announcements)
```typescript
spring({
  config: { damping: 8, stiffness: 100 }
  // Big bounce, energetic
  // Duration: ~40-60 frames (1.3-2s)
})
```

### Heavy and Impactful (dramatic reveals)
```typescript
spring({
  config: { damping: 15, stiffness: 80, mass: 2 }
  // Slow, weighty
  // Duration: ~50-70 frames (1.7-2.3s)
})
```

## Beat-Based Timing

Sync major actions to music beats (typically 120 BPM = 0.5s per beat at 30fps = 15 frames).

### Good Example
```
Background Music: 120 BPM (beat every 15 frames)

Frame 0: First element enters (beat 1)
Frame 15: Second element enters (beat 2)
Frame 30: Transition starts (beat 3)
Frame 45: New scene (beat 4)

All major actions land on beats.
```

Creates rhythmic coherence with audio.

### Bad Example
```
Frame 0: Element enters
Frame 17: Next element (off-beat)
Frame 29: Transition (off-beat)
Frame 51: New scene (off-beat)

Feels disconnected from music.
```

## Scene Duration Guidelines

| Scene Type | Minimum | Optimal | Maximum |
|------------|---------|---------|---------|
| Splash/Logo | 1s | 2s | 3s |
| Title card | 2s | 3s | 5s |
| Simple info | 3s | 5s | 7s |
| Complex info | 5s | 8s | 12s |
| Transition | 0.3s | 0.5s | 1s |

### Good Example
```
Video Structure (30s total):

Scene 1 (Logo): 0-2s
Scene 2 (Hook): 2-7s (5s - optimal for concept)
Scene 3 (Feature 1): 7-14s (7s - complex info)
Scene 4 (Feature 2): 14-21s (7s - complex info)
Scene 5 (CTA): 21-30s (9s - allow action time)
```

Each scene has appropriate duration for complexity.

## Pacing Variation

Vary pacing to maintain engagement. Mix fast and slow moments.

### Good Example (30s video)
```
0-5s: Fast (hook, grab attention)
5-12s: Medium (build, explain)
12-20s: Slow (emphasize key point)
20-25s: Fast (energy, excitement)
25-30s: Slow (resolve, CTA)

Energy Curve: Fast → Medium → Slow → Fast → Slow
```

Creates dynamic, engaging rhythm.

### Bad Example
```
0-30s: Constant medium pace throughout

No variation = monotonous.
```

## Anticipation and Follow-Through

Build anticipation before action, allow follow-through after.

### Good Example
```
Button Click Animation:

Frames 0-6: Anticipation (scale down to 0.95, 0.2s)
Frames 6-12: Action (scale to 1.1, 0.2s)
Frames 12-24: Follow-through (spring back to 1.0, 0.4s)

Total: 24 frames (0.8s)
Ratio: 1:1:2 (anticipation:action:follow-through)
```

Feels natural and satisfying.

### Bad Example
```
Frames 0-6: Instant scale to 1.1
Frames 6-12: Instant back to 1.0

No anticipation or follow-through = mechanical.
```

## Checklist

- [ ] All timings defined in seconds, converted to frames
- [ ] Minimum perception times respected (0.3s for text)
- [ ] Entrance/hold/exit ratio follows 1:2:0.7 guideline
- [ ] Multiple elements use staggered timing (5-10 frame delays)
- [ ] Animation speed matches content importance
- [ ] Major actions sync with music beats
- [ ] Scene durations appropriate for content complexity
- [ ] Pacing varies (mix of fast and slow)
- [ ] Anticipation and follow-through included
- [ ] Total duration supports viewer comprehension
