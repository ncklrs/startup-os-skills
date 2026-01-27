---
title: Audio Design and Music Strategy
impact: HIGH
tags: audio, music, soundtrack, mood, energy
---

## Audio Design and Music Strategy

**Impact: HIGH**

Audio is 50% of the viewing experience. The right music creates mood, guides pacing, and reinforces the emotional arc of your video.

## Audio Layer Architecture

Professional videos use 3-4 distinct audio layers:

### Layer 1: Background Music (Foundation)
- **Volume**: 40-60% (allows other elements to shine)
- **Purpose**: Sets overall mood and energy
- **Character**: Continuous throughout video or scene

### Layer 2: Sound Effects (Punctuation)
- **Volume**: 60-80% (emphasizes actions)
- **Purpose**: Reinforces visual actions and transitions
- **Character**: Brief, specific, timed precisely

### Layer 3: Ambient Texture (Depth)
- **Volume**: 20-30% (subtle presence)
- **Purpose**: Adds richness and dimension
- **Character**: Continuous, atmospheric, non-intrusive

### Layer 4: Voiceover/Dialog (Optional)
- **Volume**: 80-100% (when present)
- **Purpose**: Narration or spoken content
- **Character**: Clear, prioritized over all other audio

### Good Example
```
30-second Product Video:

Background Music:
  - Upbeat electronic (120 BPM)
  - Volume: 50%
  - Duration: 0-30s (full video)
  - Duck to 30% when SFX play

Sound Effects:
  - Whoosh at 0s (logo entrance): 70%
  - Pop at 5s (feature reveal): 65%
  - Swoosh at 10s (transition): 60%
  - Ding at 25s (CTA): 75%

Ambient Texture:
  - Subtle tech hum
  - Volume: 25%
  - Duration: 0-30s
```

Layered audio creates depth and professional polish.

### Bad Example
```
Just Background Music:
  - One music track at 80%
  - No sound effects
  - No layering
  - Feels flat and amateur
```

## Music Mood and Energy Matrix

Choose music based on desired emotional response:

| Mood | Low Energy | Medium Energy | High Energy |
|------|------------|---------------|-------------|
| **Happy** | Acoustic guitar | Indie pop | Dance electronic |
| **Serious** | Ambient drone | Minimal piano | Orchestral |
| **Inspiring** | Soft strings | Building rhythm | Epic anthem |
| **Playful** | Ukulele | Quirky synth | Upbeat funk |
| **Dramatic** | Dark ambient | Tension strings | Action cinematic |

### Good Example
```
Video: SaaS Product Launch (Inspiring + Medium Energy)

Music Selection:
  - Style: Building rhythm with piano and strings
  - BPM: 100-120
  - Mood: Optimistic, professional
  - Character: Starts simple, builds to fuller arrangement
  - Energy arc: Medium (intro) → High (middle) → Medium (outro)

Rationale: Inspires confidence while maintaining professionalism.
```

### Bad Example
```
Video: Professional SaaS Product

Music Selection:
  - Style: Heavy metal
  - BPM: 180
  - Mood: Aggressive
  - Character: Intense throughout

Mismatched tone for target audience.
```

## Music Energy Arc

Music energy should follow the video's emotional arc:

### Standard Arc (Most common)
```
Hook (0-5s):     Medium-High (grab attention)
Build (5-20s):   Medium → High (building interest)
Peak (20-35s):   High (maximum impact)
Resolve (35-45s): High → Medium (satisfying close)
```

### Dramatic Arc
```
Intro (0-10s):   Low (mysterious)
Build (10-30s):  Low → High (tension building)
Peak (30-50s):   High (dramatic reveal)
Resolve (50-60s): Medium (settle)
```

### Energetic Arc
```
Start (0s):      High immediately (burst of energy)
Sustain (0-40s): High throughout (maintain excitement)
End (40-45s):    High (energetic finish)
```

### Good Example
```
60s Explainer Video:

Music Energy Curve:
  0-10s:  60% energy (hook with moderate excitement)
  10-30s: 60% → 85% (build as features revealed)
  30-45s: 85% (peak during main message)
  45-55s: 85% → 70% (wind down)
  55-60s: 70% → 50% (resolve to calm CTA)

Gradual changes feel natural.
```

### Bad Example
```
Music Energy: Flat 70% throughout

No arc = no emotional journey.
```

## Tempo and BPM Sync

Sync visual beats to music tempo:

- **60-80 BPM**: Slow, contemplative (2s per beat at 30fps = 60 frames)
- **80-100 BPM**: Moderate, steady (0.75s = 22-23 frames)
- **100-120 BPM**: Upbeat, energetic (0.5s = 15 frames)
- **120-140 BPM**: Fast, exciting (0.43s = 13 frames)
- **140+ BPM**: Very fast, intense (0.35s = 10-11 frames)

### Good Example
```
Music: 120 BPM (beat every 0.5s = 15 frames at 30fps)

Animation Timing:
  Frame 0: Scene 1 starts (beat 1)
  Frame 15: Element enters (beat 2)
  Frame 30: Transition starts (beat 3)
  Frame 45: Scene 2 starts (beat 4)
  Frame 60: Next element (beat 5)

Major visual events land on beats.
```

Creates rhythmic coherence between audio and visual.

## Ducking and Dynamic Volume

Duck (reduce) background music when other audio plays:

### Good Example
```
Scene with Sound Effect:

Frame 0-90:
  - Background music: 50% volume

Frame 90-120: (SFX plays)
  - Background music: 25% volume (ducked -50%)
  - Sound effect: 70% volume
  - Transition: 5 frame fade down/up

Frame 120-onward:
  - Background music: 50% volume (restored)
```

Prevents audio clash, maintains clarity.

### Bad Example
```
Background music: 60% constant
Sound effect: 70% on top

= 130% total volume, muddy mix.
```

## Fade In/Out Technique

Never hard-cut music. Always fade.

### Good Example
```typescript
// Fade in music over 1 second
<Audio
  src={staticFile("background.mp3")}
  volume={(f) =>
    interpolate(f, [0, 30], [0, 0.5], {
      extrapolateRight: 'clamp'
    })
  }
/>

// Fade out at end
volume={(f) => {
  const { durationInFrames } = useVideoConfig();
  return interpolate(
    f,
    [durationInFrames - 30, durationInFrames],
    [0.5, 0],
    { extrapolateLeft: 'clamp', extrapolateRight: 'clamp' }
  );
}}
```

Smooth, professional audio transitions.

### Bad Example
```typescript
// Music just starts/stops
<Audio src={staticFile("background.mp3")} volume={0.5} />
// Hard cuts feel jarring
```

## Music Selection Criteria

When choosing background music:

### Must Have
- [ ] Matches emotional tone of video
- [ ] Appropriate energy level for content
- [ ] BPM allows visual sync (ideally 100-120)
- [ ] No sudden loud moments or drops
- [ ] Consistent quality throughout
- [ ] Legally licensed for use

### Should Have
- [ ] Builds/evolves over time (not repetitive)
- [ ] Clear beats for synchronization
- [ ] Room for sound effects (not too dense)
- [ ] Ending that works with fade-out

### Nice to Have
- [ ] Loops seamlessly if needed
- [ ] Multiple intensity versions (stems)
- [ ] Hit points that align with video beats

## Common Music Styles for Different Videos

| Video Type | Music Style | BPM Range | Key Characteristics |
|------------|-------------|-----------|---------------------|
| SaaS Product | Electronic/Corporate | 100-120 | Clean, modern, optimistic |
| Explainer | Acoustic/Indie | 90-110 | Friendly, approachable |
| Brand Story | Cinematic/Orchestral | 70-100 | Emotional, sweeping |
| Tech Demo | Electronic/Minimal | 110-130 | Futuristic, precise |
| Tutorial | Light Ambient | 80-100 | Unobtrusive, calm |
| Launch Video | Epic/Anthemic | 120-140 | Exciting, building |

## Silence as an Audio Element

Strategic silence is powerful:

### Good Example
```
Scene: Dramatic Reveal

Frames 0-120: Music at 50%
Frames 120-135: Complete silence (0.5s)
  - All audio cuts
  - Creates anticipation
Frames 135-onward: Music returns at 70% with impact SFX
```

Silence makes the following sound more impactful.

## Checklist

- [ ] Music mood matches video tone
- [ ] Energy level appropriate for content
- [ ] Music follows emotional arc (not flat)
- [ ] BPM allows beat synchronization
- [ ] Background music volume: 40-60%
- [ ] Music ducks when SFX play (-6 to -12dB)
- [ ] Fade in over 0.5-1s at start
- [ ] Fade out over 0.5-1s at end
- [ ] No hard cuts or jarring transitions
- [ ] Audio layers create depth (music + SFX + ambient)
- [ ] Total mix doesn't exceed 100% volume
- [ ] Music supports but doesn't overpower visuals
