---
title: Sound Effects Selection and Placement
impact: MEDIUM-HIGH
tags: sfx, sound-effects, audio, foley
---

## Sound Effects Selection and Placement

**Impact: MEDIUM-HIGH**

Sound effects (SFX) bring motion graphics to life. They emphasize actions, smooth transitions, and create satisfying feedback. Well-placed SFX make the difference between amateur and professional work.

## The Role of Sound Effects

SFX serve three primary purposes:

1. **Emphasis** — Draw attention to important moments
2. **Transition** — Smooth scene changes
3. **Feedback** — Confirm actions and create satisfaction

## Sound Effect Categories

### UI/Interaction Sounds

**Purpose**: Feedback for user actions and interface elements

| Sound | When to Use | Character | Duration |
|-------|-------------|-----------|----------|
| **Click** | Buttons, selections | Sharp, short | 0.05-0.1s |
| **Pop** | Checkmarks, success states | Bright, snappy | 0.1-0.2s |
| **Toggle** | Switches, toggles | Two-tone (on/off) | 0.15-0.25s |
| **Tap** | Light interactions | Soft, brief | 0.05-0.1s |

### Transition Sounds

**Purpose**: Connect scenes and smooth visual changes

| Sound | When to Use | Character | Duration |
|-------|-------------|-----------|----------|
| **Whoosh** | Fast movements, reveals | Airy, directional | 0.3-0.6s |
| **Swoosh** | Scene transitions | Smooth, flowing | 0.4-0.8s |
| **Swipe** | Slide transitions | Fast, cutting air | 0.2-0.4s |
| **Whomp** | Heavy transitions | Deep, substantial | 0.5-1s |

### Emphasis Sounds

**Purpose**: Highlight important moments

| Sound | When to Use | Character | Duration |
|-------|-------------|-----------|----------|
| **Impact** | Big reveals | Powerful, attention-grabbing | 0.3-0.5s |
| **Boom** | Dramatic moments | Deep, resonant | 0.5-1s |
| **Ding** | Achievements, completions | Bright, musical | 0.3-0.5s |
| **Chime** | Notifications, alerts | Clear, pleasant | 0.4-0.6s |

### Texture Sounds

**Purpose**: Add richness and depth

| Sound | When to Use | Character | Duration |
|-------|-------------|-----------|----------|
| **Riser** | Build anticipation | Ascending, tense | 1-3s |
| **Reverb tail** | After impacts | Spacious, echoing | 1-2s |
| **Glitch** | Tech/digital themes | Broken, stuttered | 0.1-0.3s |
| **Shimmer** | Magical moments | Sparkly, bright | 0.5-1s |

## SFX Placement Strategy

### Rule of Action Reinforcement

Place SFX at the moment of action, not before or after.

#### Good Example
```
Animation: Button Scaling

Frame 0-15: Button scales from 1.0 to 1.1
Frame 15: SFX "pop" plays (at peak of scale)
Frame 15-30: Button returns to 1.0

SFX plays at the moment of maximum action.
```

#### Bad Example
```
Frame 0: SFX plays
Frame 0-15: Button scales
Frame 15-30: Button returns

SFX too early, disconnected from visual.
```

### Anticipation and Release

For dramatic moments, use a riser before the reveal.

#### Good Example
```
Dramatic Reveal:

Frames 0-60: Riser SFX builds (2s)
Frame 60: Impact SFX (coincides with reveal)
Frames 60-90: Reverb tail fades out

Creates anticipation → release pattern.
```

### Layering Sound Effects

Combine 2-3 SFX for rich, full sound.

#### Good Example
```
Logo Impact Moment:

SFX Layer 1: Impact (low frequency, 0.5s)
  - Volume: 70%
  - Provides weight

SFX Layer 2: Whoosh (mid frequency, 0.4s)
  - Volume: 50%
  - Provides movement

SFX Layer 3: Shimmer (high frequency, 0.8s)
  - Volume: 40%
  - Provides sparkle

All start at same frame, different durations.
```

Creates complex, professional sound.

#### Bad Example
```
Single SFX: Generic "swoosh"
  - Feels thin and cheap
```

## Volume and Ducking

### Relative Volume Guidelines

| SFX Type | Volume Range | Purpose |
|----------|--------------|---------|
| **Subtle** | 30-40% | Background texture |
| **Normal** | 50-70% | Standard emphasis |
| **Prominent** | 70-85% | Key moments |
| **Impact** | 80-95% | Major reveals |

### Duck Background Music

When SFX play, reduce background music:

#### Good Example
```typescript
// Background music with ducking
const frame = useCurrentFrame();
const { fps } = useVideoConfig();

// SFX plays at frame 90-120
const isDucking = frame >= 90 && frame <= 120;

<Audio
  src={staticFile("background.mp3")}
  volume={isDucking ? 0.25 : 0.5}
/>

<Sequence from={90}>
  <Audio
    src={staticFile("impact.mp3")}
    volume={0.75}
  />
</Sequence>
```

Music drops 50% when SFX plays, prevents mud.

## SFX Timing Patterns

### Staggered SFX for Lists

When multiple items appear, stagger SFX:

#### Good Example
```
5 Items Entering:

Item 1 entrance: Frame 0, SFX "pop" at 70%
Item 2 entrance: Frame 6, SFX "pop" at 65%
Item 3 entrance: Frame 12, SFX "pop" at 60%
Item 4 entrance: Frame 18, SFX "pop" at 55%
Item 5 entrance: Frame 24, SFX "pop" at 50%

Stagger: 6 frames (0.2s) apart
Volume decreases to prevent overwhelming
```

Creates rhythmic cascade.

#### Bad Example
```
All items: Same frame, same SFX, same volume
= Wall of sound, muddy
```

### Transition SFX Overlap

Overlap transition SFX slightly with next scene:

#### Good Example
```
Scene Transition:

Scene 1 ends: Frame 90
Whoosh SFX starts: Frame 85 (5 frames before)
Scene 2 starts: Frame 90
Whoosh SFX ends: Frame 105 (15 frames after)

Whoosh bridges scenes smoothly.
```

## SFX Frequency Balance

Use different frequencies for layered effects:

- **Low (< 250 Hz)**: Weight, impact, power
- **Mid (250-2000 Hz)**: Body, presence
- **High (> 2000 Hz)**: Sparkle, air, detail

#### Good Example
```
Logo Reveal SFX Stack:

Low: Deep impact "boom" (80 Hz fundamental)
Mid: Whoosh movement (600-1200 Hz)
High: Shimmer sparkle (4000-8000 Hz)

Full frequency spectrum covered.
```

## Silence Between SFX

Allow space between sound effects:

#### Good Example
```
SFX Timing:

0s: Whoosh (0.4s duration)
0.6s: Next SFX (0.2s gap after whoosh)
1.2s: Next SFX (0.6s gap)

Minimum 0.2s between SFX for clarity.
```

#### Bad Example
```
0s: Whoosh
0.3s: Pop (overlaps whoosh)
0.5s: Impact (overlaps pop)

Too dense, chaotic.
```

## SFX for Different Video Types

| Video Type | Primary SFX | Secondary SFX | Density |
|------------|-------------|---------------|---------|
| **UI Demo** | Clicks, pops | Whooshes | High (every action) |
| **Brand Story** | Whooshes, impacts | Ambient textures | Low (key moments) |
| **Product Launch** | Booms, risers | Chimes, shimmers | Medium (punctuation) |
| **Tutorial** | Subtle pops | Light whooshes | Low (minimal distraction) |
| **Explainer** | Pops, dings | Swooshes | Medium (supportive) |

## Common SFX Mistakes

### Mistake 1: Too Many SFX
```
Bad: SFX every 0.5s throughout video
= Overwhelming, amateur

Good: SFX at key moments (every 3-5s)
= Professional restraint
```

### Mistake 2: Stock Overuse
```
Bad: Same "whoosh.mp3" for every transition
= Repetitive, boring

Good: Variety of 3-5 different whooshes
= Dynamic, professional
```

### Mistake 3: Volume Too High
```
Bad: All SFX at 90%+ volume
= Overpowering, harsh

Good: SFX 50-75%, peaks at 85%
= Balanced, pleasant
```

### Mistake 4: Poor Timing
```
Bad: SFX before or after visual action
= Disconnected

Good: SFX synchronized to peak of action
= Cohesive
```

## SFX Selection Checklist

When choosing sound effects:

- [ ] Matches visual action (whoosh for movement, pop for appear)
- [ ] Appropriate duration (not too long)
- [ ] Clean recording (no background noise)
- [ ] Proper frequency range for layering
- [ ] Consistent quality across all SFX
- [ ] Legally licensed for commercial use

## SFX Placement Checklist

For each sound effect:

- [ ] Timed to exact moment of visual action
- [ ] Volume appropriate for emphasis level (30-85%)
- [ ] Doesn't overlap competing SFX (0.2s minimum gap)
- [ ] Background music ducks when SFX plays
- [ ] Layered with complementary frequencies if needed
- [ ] Adds value (doesn't feel gratuitous)
- [ ] Consistent style with other SFX in video
- [ ] Total audio mix doesn't exceed 100%

## Quick Reference: SFX by Moment

| Visual Moment | Recommended SFX | Volume | Duration |
|---------------|-----------------|--------|----------|
| Logo appears | Whoosh + shimmer | 70% | 0.5s |
| Button click | Pop or click | 65% | 0.1s |
| Checkmark | Bright pop | 70% | 0.2s |
| Scene transition | Swoosh | 60% | 0.4s |
| Big reveal | Impact + reverb | 80% | 0.8s |
| Counter counting | Subtle tick | 40% | 0.05s |
| Success state | Ding or chime | 75% | 0.4s |
| Error state | Low buzz | 60% | 0.3s |
| Panel slide in | Whoosh | 55% | 0.3s |
| Text appear | Soft pop | 50% | 0.15s |
