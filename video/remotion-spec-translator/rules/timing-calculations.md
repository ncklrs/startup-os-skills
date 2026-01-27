---
title: Frame Timing and Duration Calculations
impact: CRITICAL
tags: timing, frames, fps, duration
---

## Frame Timing and Duration Calculations

**Impact: CRITICAL**

Accurate conversion of seconds to frames and proper timing calculations for Remotion.

### Basic Conversion Formula

```typescript
// Seconds to frames: seconds * fps
const durationInFrames = seconds * 30; // assuming 30 fps

// Example: 5 seconds = 150 frames
const fiveSeconds = 5 * 30; // 150 frames
```

### Scene Timing Constant Pattern

**Spec:**
```markdown
Scene 1: Logo (0s - 5s, Duration: 5s)
Scene 2: Product (5s - 15s, Duration: 10s)
Scene 3: CTA (15s - 20s, Duration: 5s)
```

**Code:**
```typescript
const SCENE_TIMING = {
  scene1: { start: 0, end: 150, duration: 150 },       // 0-5s
  scene2: { start: 150, end: 450, duration: 300 },     // 5-15s
  scene3: { start: 450, end: 600, duration: 150 },     // 15-20s
} as const;

// Usage in Sequence
<Sequence
  from={SCENE_TIMING.scene1.start}
  durationInFrames={SCENE_TIMING.scene1.duration}
>
  <Scene1 />
</Sequence>
```

### Calculating Scene Timing

Pattern for generating timing constants:

```typescript
// Given: Scene starts at X seconds, duration Y seconds, fps 30
const fps = 30;

const sceneStart = startSeconds * fps;
const sceneDuration = durationSeconds * fps;
const sceneEnd = sceneStart + sceneDuration;

// Example: Scene starts at 5s, lasts 10s
const scene2 = {
  start: 5 * 30,    // 150
  duration: 10 * 30, // 300
  end: 150 + 300,    // 450
};
```

### Sub-Scene Timing

For animations within scenes:

**Spec:**
```markdown
Scene 1 (0-5s):
- Title enters: 0-1s
- Subtitle enters: 1-2s
- Logo enters: 2-3s
- Hold: 3-5s
```

**Code:**
```typescript
function Scene1() {
  const frame = useCurrentFrame();
  const { fps } = useVideoConfig();

  // Scene-relative timing (frame 0 is scene start)
  const titleEnterEnd = 1 * fps;      // 30 frames
  const subtitleEnterEnd = 2 * fps;   // 60 frames
  const logoEnterEnd = 3 * fps;       // 90 frames

  // Title animation (0-30 frames)
  const titleProgress = spring({
    frame: Math.min(frame, titleEnterEnd),
    fps,
    config: SPRING_CONFIGS.smooth,
  });

  // Subtitle animation (30-60 frames)
  const subtitleProgress = spring({
    frame: frame - titleEnterEnd,
    fps,
    config: SPRING_CONFIGS.smooth,
  });

  // Logo animation (60-90 frames)
  const logoProgress = spring({
    frame: frame - subtitleEnterEnd,
    fps,
    config: SPRING_CONFIGS.smooth,
  });

  return (
    <AbsoluteFill>
      {/* Elements with calculated timing */}
    </AbsoluteFill>
  );
}
```

### Transition Overlap Timing

**Spec:**
```markdown
Scene 1 fades out while Scene 2 fades in
Overlap duration: 0.5s (15 frames)
```

**Code:**
```typescript
const TRANSITION_DURATION = 0.5 * 30; // 15 frames

const SCENE_TIMING = {
  scene1: {
    start: 0,
    duration: 150 + TRANSITION_DURATION,  // Extend for fade out
  },
  scene2: {
    start: 150 - TRANSITION_DURATION,     // Start early for fade in
    duration: 300 + TRANSITION_DURATION,
  },
};

// In Scene1
const fadeOut = spring({
  frame: frame - (150 - TRANSITION_DURATION),
  fps,
  config: SPRING_CONFIGS.smooth,
});
const opacity = 1 - fadeOut;

// In Scene2
const fadeIn = spring({
  frame,
  fps,
  config: SPRING_CONFIGS.smooth,
});
const opacity = fadeIn;
```

### Delay Calculations

**Spec:**
```markdown
Elements appear with 0.5s stagger delay
```

**Code:**
```typescript
const STAGGER_DELAY = 0.5 * fps; // 15 frames

elements.map((el, index) => {
  const delay = index * STAGGER_DELAY;

  const progress = spring({
    frame: frame - delay,
    fps,
    config: SPRING_CONFIGS.smooth,
  });

  // Element renders
});
```

### Hold Pattern

**Spec:**
```markdown
Element holds for 3 seconds after entrance
```

**Code:**
```typescript
const ENTRANCE_DURATION = 1 * fps;    // 30 frames
const HOLD_DURATION = 3 * fps;        // 90 frames
const HOLD_END = ENTRANCE_DURATION + HOLD_DURATION; // 120 frames

const enterProgress = spring({
  frame: Math.min(frame, ENTRANCE_DURATION),
  fps,
  config: SPRING_CONFIGS.smooth,
});

// Element visible from frame 0 to HOLD_END
const isVisible = frame <= HOLD_END;
```

### BPM to Frame Timing

**Spec:**
```markdown
Background music: 120 BPM
Sync animations to beats
```

**Code:**
```typescript
const BPM = 120;
const fps = 30;

// Frames per beat
const framesPerBeat = (60 / BPM) * fps;
// 120 BPM = 2 beats/sec = 0.5 sec/beat = 15 frames/beat

// Animation on every beat
const beatNumber = Math.floor(frame / framesPerBeat);
const beatProgress = (frame % framesPerBeat) / framesPerBeat;

// Pulse on each beat
const pulse = beatProgress < 0.3
  ? interpolate(beatProgress, [0, 0.3], [1, 1.2])
  : interpolate(beatProgress, [0.3, 1], [1.2, 1]);
```

### Duration from Spec

Extract total duration:

**Spec:**
```markdown
## Overview
- Duration: 30 seconds
- Frame Rate: 30 fps
```

**Code:**
```typescript
// In composition registry
{
  id: 'video-name',
  component: VideoName,
  durationInFrames: 30 * 30, // 900 frames
  fps: 30,
  width: 1920,
  height: 1080,
}
```

### Timing Checklist

When converting time specs to code:

- [ ] All durations in seconds converted to frames (seconds * fps)
- [ ] Scene timing constants use start/duration/end pattern
- [ ] Delays calculated as frame offsets
- [ ] Transitions account for overlap
- [ ] BPM converted to frames per beat if audio synced
- [ ] Hold durations properly calculated
- [ ] Frame 0 handled correctly (animations start from 0)
- [ ] Total composition duration matches spec
- [ ] Comments show both seconds and frames
- [ ] Constants use const fps = 30 for clarity
