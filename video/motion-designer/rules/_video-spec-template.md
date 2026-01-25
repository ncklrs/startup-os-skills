---
title: Video Specification Output Template
impact: CRITICAL
tags: template, specification, output, format
---

## Video Specification Output Template

**Impact: CRITICAL**

This is the format motion-designer should output when creating video specifications. This template ensures all necessary details are included for implementation with `/remotion-best-practices`.

---

# [Video Title]

## Overview

- **Duration**: [X] seconds
- **Dimensions**: 1920x1080 (or specify)
- **Frame Rate**: 30 fps
- **Style**: [Brief description of visual aesthetic]
- **Mood**: [Emotional tone: energetic, calm, professional, playful, etc.]
- **Target Audience**: [Who this is for]

## Color Palette

```
Primary: #HEX - [Color name/purpose]
Secondary: #HEX - [Color name/purpose]
Accent: #HEX - [Color name/purpose]
Background: #HEX - [Color name/purpose]
Text: #HEX - [Color name/purpose]
```

## Typography

- **Headline**: [Font family], [Size]px, [Weight]
- **Subheadline**: [Font family], [Size]px, [Weight]
- **Body**: [Font family], [Size]px, [Weight]

## Audio Strategy

### Background Music
- **Style/Genre**: [Electronic, acoustic, orchestral, etc.]
- **BPM**: [Beats per minute]
- **Mood**: [Upbeat, dramatic, calm, etc.]
- **Energy Level**: [Low/Medium/High]
- **Volume**: 50% base (duck to 25-30% when SFX play)
- **Key Sync Points**:
  - 0s: Music starts
  - [X]s: Beat aligns with [visual event]
  - [Y]s: Energy builds
  - [Z]s: Fade out begins

### Sound Effects

| Time | SFX Type | Description | Volume | Purpose |
|------|----------|-------------|--------|---------|
| 0s | Whoosh | Entrance sweep | 70% | Logo entrance |
| 5s | Pop | Bright snap | 65% | Element reveal |
| 10s | Swoosh | Transition | 60% | Scene change |
| 25s | Ding | Success chime | 75% | CTA emphasis |

### Ambient Texture (Optional)
- **Type**: [Tech hum, nature ambience, etc.]
- **Volume**: 25%
- **Duration**: [Full video or specific scenes]

---

## Scene Breakdown

### Scene 1: [Scene Name] (0s - [X]s, Duration: [X]s)

**Purpose**: [What this scene achieves in the narrative]

**Visual Description**:
- Background: [Full description - color, gradient, pattern, etc.]
- Primary element: [Description - what it is, size, position, color]
- Secondary elements: [Description]
- Typography: [Any text with exact copy, size, position]

**Element Positions**:
- [Element name]: (x: [#]px, y: [#]px), size: [#]x[#]px
- [Element name]: (x: [#]px, y: [#]px), size: [#]x[#]px

**Animation Details**:

*Element 1 - [Name]*:
- Frames 0-15: Spring entrance from scale 0.8 to 1.0
  - Spring config: `{ damping: 200 }`
  - Opacity: 0 → 1
- Frames 15-90: Hold at scale 1.0
- Frames 90-105: Fade out, opacity 1 → 0

*Element 2 - [Name]*:
- Frames 20-35: Slide in from right (x: 1920 → 960)
  - Easing: `Easing.inOut(Easing.quad)`
- Frames 35-95: Subtle float (±5px Y-axis)
- Frames 95-110: Exit left

**Timing Breakdown**:
- Frame 0-15 (0-0.5s): Background fades in, primary element enters
- Frame 15-30 (0.5-1s): Secondary elements stagger in (6 frame delays)
- Frame 30-90 (1-3s): Hold composition, text is readable
- Frame 90-105 (3-3.5s): Elements exit for transition

**Audio**:
- Background music: 50% volume, [mood description]
- 0s: Whoosh SFX (70%), [purpose]
- 1.5s: Pop SFX (65%), [purpose]

**Visual Hierarchy**:
1. Primary: [What viewers see first]
2. Secondary: [Supporting elements]
3. Tertiary: [Background/atmosphere]

**Transitions Out**:
[How this scene transitions to next - crossfade, slide, scale, etc.]
[Duration and timing details]

---

### Scene 2: [Scene Name] ([X]s - [Y]s, Duration: [Z]s)

[Repeat full structure above for each scene]

---

## Technical Specifications for Remotion

### Composition Setup
```typescript
{
  id: 'video-name',
  component: VideoComponent,
  durationInFrames: [total frames = seconds * 30],
  fps: 30,
  width: 1920,
  height: 1080,
}
```

### Color Constants
```typescript
const COLORS = {
  primary: '#HEX',
  secondary: '#HEX',
  accent: '#HEX',
  background: '#HEX',
  text: '#HEX',
};
```

### Spring Configurations
```typescript
// Smooth, no bounce - use for elegant transitions
const smooth = { damping: 200 };

// Snappy, minimal bounce - use for UI elements
const snappy = { damping: 20, stiffness: 200 };

// Bouncy entrance - use for playful animations
const bouncy = { damping: 8 };

// Heavy, slow - use for dramatic moments
const heavy = { damping: 15, stiffness: 80, mass: 2 };
```

### Animation Timing Constants
```typescript
const { fps } = useVideoConfig();

const SCENE_1_DURATION = 3 * fps;  // 90 frames
const SCENE_2_DURATION = 5 * fps;  // 150 frames
const TRANSITION_TIME = 0.5 * fps; // 15 frames
```

### Asset Requirements
- [ ] Logo file: [format, dimensions]
- [ ] Product images: [list with specs]
- [ ] Icons: [list]
- [ ] Background music: [style, duration, BPM]
- [ ] Sound effects: [list]
- [ ] Fonts: [Google Fonts or local]

---

## Implementation Notes

### Scene Sequence Structure
```typescript
<AbsoluteFill>
  <Sequence from={0} durationInFrames={90}>
    <Scene1 />
  </Sequence>

  <Sequence from={90} durationInFrames={150}>
    <Scene2 />
  </Sequence>

  <Sequence from={240} durationInFrames={120}>
    <Scene3 />
  </Sequence>
</AbsoluteFill>
```

### Audio Implementation
```typescript
// Background music with fade in/out
<Audio
  src={staticFile('background-music.mp3')}
  volume={(f) => {
    // Fade in
    const fadeIn = interpolate(f, [0, 30], [0, 0.5], {
      extrapolateRight: 'clamp'
    });

    // Fade out
    const fadeOut = interpolate(
      f,
      [durationInFrames - 30, durationInFrames],
      [0.5, 0],
      { extrapolateLeft: 'clamp', extrapolateRight: 'clamp' }
    );

    return Math.min(fadeIn, fadeOut);
  }}
/>

// Sound effects
<Sequence from={0}>
  <Audio src={staticFile('whoosh.mp3')} volume={0.7} />
</Sequence>
```

### Parallax Implementation
```typescript
const baseMovement = interpolate(frame, [0, 120], [0, -500]);

<Background style={{ transform: `translateX(${baseMovement * 0.5}px)` }} />
<Midground style={{ transform: `translateX(${baseMovement * 1.0}px)` }} />
<Foreground style={{ transform: `translateX(${baseMovement * 1.5}px)` }} />
```

---

## Quality Checklist

Before implementation:

**Narrative**:
- [ ] Clear hook within first 3 seconds
- [ ] Follows story arc (hook → build → peak → resolve)
- [ ] Maximum of 3 main points
- [ ] Satisfying conclusion with CTA

**Visual Design**:
- [ ] Clear visual hierarchy in every scene
- [ ] Sufficient negative space (30%+ per scene)
- [ ] Color contrast meets readability standards
- [ ] Typography hierarchy clear

**Timing**:
- [ ] All timings in seconds, converted to frames
- [ ] Minimum perception times respected (0.3s for text)
- [ ] Major actions sync with music beats
- [ ] Pacing varies (mix of fast and slow)

**Audio**:
- [ ] Music mood matches video tone
- [ ] Background music 40-60% volume
- [ ] Music ducks when SFX play
- [ ] Fade in/out, no hard cuts
- [ ] SFX placed at moment of action

**Transitions**:
- [ ] Transitions serve story (not gratuitous)
- [ ] Duration appropriate (0.3-1s typical)
- [ ] Audio synchronized
- [ ] Not overused (max 1 per 5-10s)

**Technical**:
- [ ] All required assets listed
- [ ] Spring configs specified
- [ ] Color values provided
- [ ] Implementation notes clear
- [ ] Works with remotion-best-practices patterns

---

## Example Minimal Spec

For reference, here's a minimal 10-second spec:

```markdown
# Quick Product Teaser

## Overview
- Duration: 10 seconds
- Style: Modern, minimal
- Mood: Exciting

## Audio
- Music: Upbeat electronic (120 BPM), 50% volume
- SFX: Whoosh at 0s, pop at 5s, ding at 9s

## Scene 1: Logo Reveal (0-5s)
- Logo scales in (0.8 → 1.0) with spring
- Background: Dark gradient (#0A0A0A → #171717)
- Whoosh SFX at entrance

## Scene 2: Product Shot (5-10s)
- Product image slides in from right
- Tagline appears below
- Pop at 5s, ding at 9s
- Crossfade transition (0.5s)

## Implementation
- Total frames: 300
- Spring config: { damping: 200 }
- Assets: logo.png, product.jpg
```

---

This template ensures comprehensive, implementable video specifications that work seamlessly with Remotion and `/remotion-best-practices`.
