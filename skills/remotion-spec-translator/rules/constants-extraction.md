---
title: Constants Organization and Extraction
impact: HIGH
tags: constants, colors, spring, timing, organization
---

## Constants Organization and Extraction

**Impact: HIGH**

Proper organization of colors, spring configurations, and timing values in dedicated constants sections.

### Color Palette Constants

**Spec:**
```markdown
## Color Palette
Primary: #FF6B35 - Ember Orange
Secondary: #A855F7 - Purple
Background: #0A0A0A - Black
Text: #FFFFFF - White
Accent: #22C55E - Emerald
```

**Code:**
```typescript
// ============================================
// COLOR PALETTE
// ============================================

const COLORS = {
  primary: '#FF6B35',      // Ember Orange
  secondary: '#A855F7',    // Purple
  background: '#0A0A0A',   // Black
  text: '#FFFFFF',         // White
  accent: '#22C55E',       // Emerald
} as const;
```

### Extended Color Palette

For complex palettes with shades:

```typescript
const COLORS = {
  // Base colors
  background: '#0a0a0a',
  charcoal: '#171717',
  slate: '#262626',
  silver: '#a3a3a3',
  white: '#ffffff',

  // Brand colors
  emberOrange: '#ff6b35',
  flameOrange: '#ff8c42',
  goldenOrange: '#ffb347',

  // Accent colors
  purple: '#a855f7',
  emerald: '#22c55e',
  recordRed: '#ef4444',
} as const;
```

### Spring Configuration Constants

**Spec:**
```markdown
## Spring Configurations
Smooth: { damping: 200 } - elegant transitions
Snappy: { damping: 20, stiffness: 200 } - UI elements
Bouncy: { damping: 8 } - playful animations
```

**Code:**
```typescript
// ============================================
// SPRING CONFIGURATIONS
// ============================================

const SPRING_CONFIGS = {
  smooth: { damping: 200 },
  snappy: { damping: 20, stiffness: 200 },
  bouncy: { damping: 8 },
} as const;

// OR with descriptive names
const SMOOTH_SPRING = { damping: 200 };
const SNAPPY_SPRING = { damping: 20, stiffness: 200 };
const BOUNCY_SPRING = { damping: 8 };
```

### Scene Timing Constants

**Spec:**
```markdown
Scene 1: Intro (0s - 5s)
Scene 2: Demo (5s - 15s)
Scene 3: CTA (15s - 20s)
```

**Code:**
```typescript
// ============================================
// SCENE TIMING CONSTANTS
// ============================================

const SCENE_TIMING = {
  scene1: { start: 0, end: 150, duration: 150 },       // 0-5s
  scene2: { start: 150, end: 450, duration: 300 },     // 5-15s
  scene3: { start: 450, end: 600, duration: 150 },     // 15-20s
} as const;
```

### Animation Duration Constants

Extract common durations:

```typescript
// ============================================
// ANIMATION CONSTANTS
// ============================================

const ANIMATION = {
  transitionDuration: 15,      // 0.5s
  staggerDelay: 10,            // 0.33s
  holdDuration: 90,            // 3s
  fadeInDuration: 30,          // 1s
} as const;
```

### Typography Constants

**Spec:**
```markdown
## Typography
Headline: Inter, 64px, Bold
Subheadline: Inter, 32px, SemiBold
Body: Inter, 18px, Regular
```

**Code:**
```typescript
// ============================================
// TYPOGRAPHY CONSTANTS
// ============================================

const TYPOGRAPHY = {
  headline: {
    fontSize: 64,
    fontWeight: 700,
    fontFamily: 'Inter, sans-serif',
  },
  subheadline: {
    fontSize: 32,
    fontWeight: 600,
    fontFamily: 'Inter, sans-serif',
  },
  body: {
    fontSize: 18,
    fontWeight: 400,
    fontFamily: 'Inter, sans-serif',
  },
} as const;
```

### Layout Constants

For positioning and sizing:

```typescript
// ============================================
// LAYOUT CONSTANTS
// ============================================

const LAYOUT = {
  padding: {
    small: 16,
    medium: 32,
    large: 64,
  },
  spacing: {
    tight: 8,
    normal: 16,
    relaxed: 24,
  },
  borderRadius: {
    small: 4,
    medium: 8,
    large: 12,
  },
} as const;
```

### Asset Path Constants

```typescript
// ============================================
// ASSET PATHS
// ============================================

const ASSETS = {
  logo: 'logo.svg',
  backgroundMusic: 'background-music.mp3',
  whooshSfx: 'whoosh.mp3',
  productImage: 'product.jpg',
} as const;
```

### Placement in File

Organize constants at the top of the file:

```typescript
import {
  AbsoluteFill,
  spring,
  useCurrentFrame,
  useVideoConfig,
  Sequence,
} from "remotion";

// ============================================
// TYPE DEFINITIONS
// ============================================

export interface VideoNameProps {}

// ============================================
// COLOR PALETTE
// ============================================

const COLORS = { ... } as const;

// ============================================
// SPRING CONFIGURATIONS
// ============================================

const SPRING_CONFIGS = { ... } as const;

// ============================================
// SCENE TIMING CONSTANTS
// ============================================

const SCENE_TIMING = { ... } as const;

// ============================================
// UTILITY FUNCTIONS
// ============================================

const seededRandom = (seed: number) => { ... };

// ============================================
// REUSABLE COMPONENTS
// ============================================

function ParticleSystem() { ... }

// ============================================
// SCENE COMPONENTS
// ============================================

function Scene1() { ... }

// ============================================
// MAIN COMPOSITION
// ============================================

export function VideoName() { ... }
```

### Using Constants

Reference constants consistently:

```typescript
// Good - using constants
<AbsoluteFill style={{ backgroundColor: COLORS.background }}>
  <div
    style={{
      fontSize: TYPOGRAPHY.headline.fontSize,
      color: COLORS.primary,
    }}
  >
    {/* Content */}
  </div>
</AbsoluteFill>

const progress = spring({
  frame,
  fps,
  config: SPRING_CONFIGS.smooth,
});

// Bad - hardcoded values
<AbsoluteFill style={{ backgroundColor: '#0A0A0A' }}>
  <div
    style={{
      fontSize: 64,
      color: '#FF6B35',
    }}
  >
    {/* Content */}
  </div>
</AbsoluteFill>

const progress = spring({
  frame,
  fps,
  config: { damping: 200 },
});
```

### Constants Checklist

When extracting constants from spec:

- [ ] All colors in COLORS constant with descriptive names
- [ ] Spring configs in SPRING_CONFIGS or individual constants
- [ ] Scene timing in SCENE_TIMING with start/duration/end
- [ ] Common animation durations extracted
- [ ] Typography styles in TYPOGRAPHY constant
- [ ] Asset paths in ASSETS constant
- [ ] Constants placed before components
- [ ] All constants use `as const` for type safety
- [ ] Constants have inline comments matching spec
- [ ] Sections separated with comment dividers
