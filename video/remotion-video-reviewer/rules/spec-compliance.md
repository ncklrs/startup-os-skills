---
title: Spec Compliance Verification
impact: CRITICAL
tags: spec, compliance, verification, accuracy
---

## Spec Compliance Verification

**Impact: CRITICAL**

Ensuring implementation accurately reflects the motion design specification.

### Scene Count and Structure

**Verify:**
```markdown
Spec lists N scenes → Code has N scene components
Each spec scene → Corresponding SceneN function
```

**Check:**
```typescript
// Spec: 3 scenes (Intro, Demo, CTA)
// Code should have:
function Scene1Intro() { }
function Scene2Demo() { }
function Scene3CTA() { }

<Sequence from={...} durationInFrames={...}>
  <Scene1Intro />
</Sequence>
// ... (3 sequences total)
```

### Duration Matching

**Spec:**
```markdown
Scene 1: 5 seconds
Scene 2: 10 seconds
Total: 15 seconds
```

**Code Verification:**
```typescript
// Check SCENE_TIMING matches spec
const SCENE_TIMING = {
  scene1: { duration: 150 },  // 5s * 30fps ✓
  scene2: { duration: 300 },  // 10s * 30fps ✓
};

// Total composition duration
durationInFrames: 450  // 15s * 30fps ✓
```

### Color Palette Accuracy

**Spec:**
```markdown
Primary: #FF6B35
Background: #0A0A0A
```

**Verification:**
```typescript
// ❌ FAIL - Colors don't match
const COLORS = {
  primary: '#FF6C36',     // Off by one digit
  background: '#0B0B0B',  // Wrong shade
};

// ✓ PASS - Exact match
const COLORS = {
  primary: '#FF6B35',
  background: '#0A0A0A',
};
```

**Check Method:**
Compare hex codes character-by-character. Even one digit off is a compliance failure.

### Typography Compliance

**Spec:**
```markdown
Headline: Inter, 64px, Bold (700)
Body: Inter, 18px, Regular (400)
```

**Verification:**
```typescript
// ❌ FAIL - Font sizes wrong
style={{
  fontSize: 60,  // Should be 64
  fontWeight: 700,
}}

// ✓ PASS - Exact match
style={{
  fontSize: 64,
  fontWeight: 700,
  fontFamily: 'Inter, sans-serif',
}}
```

### Animation Description Match

**Spec:**
```markdown
Logo scales from 0.8 to 1.0 with smooth spring (damping: 200)
```

**Verification:**
```typescript
// ❌ FAIL - Wrong values
const scale = interpolate(progress, [0, 1], [0.5, 1.2]);

// ❌ FAIL - Wrong spring config
const progress = spring({
  frame,
  fps,
  config: { damping: 20 },  // Should be 200
});

// ✓ PASS - Matches spec
const progress = spring({
  frame,
  fps,
  config: { damping: 200 },
});
const scale = interpolate(progress, [0, 1], [0.8, 1]);
```

### Audio Timing Compliance

**Spec:**
```markdown
Sound Effects:
- 0s: Whoosh (entrance)
- 5s: Pop (element reveal)
- 10s: Ding (CTA emphasis)
```

**Verification:**
```typescript
// Check Audio components at correct frame positions
<Sequence from={0}>
  <Audio src={staticFile('whoosh.mp3')} />  // 0s ✓
</Sequence>

<Sequence from={150}>  // 5s * 30fps ✓
  <Audio src={staticFile('pop.mp3')} />
</Sequence>

<Sequence from={300}>  // 10s * 30fps ✓
  <Audio src={staticFile('ding.mp3')} />
</Sequence>
```

### Layout and Positioning

**Spec:**
```markdown
Logo: Centered horizontally, 20% from top
Tagline: Centered, below logo with 32px gap
```

**Verification:**
```typescript
// ❌ FAIL - Not responsive
left: 960,  // Hardcoded

// ✓ PASS - Matches spec
left: width / 2,  // Centered
transform: 'translateX(-50%)',  // Account for element width
top: height * 0.2,  // 20% from top

// Tagline
top: height * 0.2 + logoHeight + 32,  // Below logo + 32px gap
```

### Compliance Report Template

```markdown
## Spec Compliance Report

### Scene Structure
✓ All 3 scenes implemented
✓ Scene naming matches spec
✓ Sequence structure correct

### Timing
✓ Scene 1: 150 frames (5s)
✓ Scene 2: 300 frames (10s)
✓ Total duration: 450 frames (15s)

### Visual Accuracy
✓ Color palette matches exactly
❌ Typography: Font size off in Scene 2 (60px vs 64px)
✓ Layout positioning matches spec

### Animations
✓ Spring configs match spec
❌ Logo scale range incorrect (0.5-1.2 vs 0.8-1.0)

### Audio
✓ Background music present
✓ SFX timing matches spec
✓ Volume levels correct

### Overall Compliance: 90%
Deviations: 2 (typography, animation)
Status: NEEDS REVISION
```

### Compliance Checklist

When reviewing against spec:

- [ ] Scene count matches
- [ ] Scene durations exact (frame-accurate)
- [ ] Color hex codes match exactly
- [ ] Font families, sizes, weights match
- [ ] Animation ranges match spec values
- [ ] Spring configs match spec
- [ ] Audio timing frame-accurate
- [ ] Layout percentages/positions correct
- [ ] Total duration matches spec
- [ ] All spec elements implemented
- [ ] No extra elements not in spec
- [ ] Visual hierarchy maintained
