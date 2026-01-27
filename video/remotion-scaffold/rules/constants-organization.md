---
title: Constants Organization
impact: HIGH
tags: constants, colors, springs, timing
---

## Constants Organization

**Impact: HIGH**

Well-organized constants make videos easy to customize and maintain.

### Constants File Structure

```typescript
// constants.ts

// =============================================================================
// COLORS
// =============================================================================

export const COLORS = {
  // Brand colors
  primary: "#FF6B35",      // Ember Orange
  secondary: "#4ECDC4",    // Teal
  accent: "#FFE66D",       // Yellow

  // Backgrounds
  background: "#0A0A0A",   // Near black
  surface: "#171717",      // Card background
  overlay: "rgba(0, 0, 0, 0.5)",

  // Text
  text: "#FFFFFF",
  textMuted: "#A3A3A3",
  textSubtle: "#525252",

  // Semantic
  success: "#10B981",
  warning: "#F59E0B",
  error: "#EF4444",
} as const;

// =============================================================================
// SPRING CONFIGURATIONS
// =============================================================================

export const SPRING_CONFIGS = {
  // Standard animations
  smooth: { damping: 200 },
  snappy: { damping: 20, stiffness: 200 },
  bouncy: { damping: 8 },

  // Specialized
  gentle: { damping: 30, stiffness: 80 },
  elastic: { damping: 12, stiffness: 150 },
  heavy: { damping: 40, stiffness: 60 },
} as const;

// =============================================================================
// TIMING
// =============================================================================

const FPS = 30;

export const SCENE_TIMING = {
  intro: {
    start: 0,
    end: 5 * FPS,
    duration: 5 * FPS,
  },
  content: {
    start: 5 * FPS,
    end: 20 * FPS,
    duration: 15 * FPS,
  },
  outro: {
    start: 20 * FPS,
    end: 25 * FPS,
    duration: 5 * FPS,
  },
} as const;

// Animation micro-timing
export const ANIMATION = {
  staggerDelay: 5,        // Frames between staggered elements
  fadeInDuration: 15,     // Standard fade duration
  holdDuration: 60,       // How long to hold before transition
  exitBuffer: 10,         // Frames before scene end to start exit
} as const;

// =============================================================================
// LAYOUT
// =============================================================================

export const LAYOUT = {
  padding: 80,
  gutter: 40,
  maxContentWidth: 1600,
} as const;

// =============================================================================
// TYPOGRAPHY
// =============================================================================

export const TYPOGRAPHY = {
  fontFamily: "Inter, -apple-system, system-ui, sans-serif",
  sizes: {
    headline: 72,
    title: 56,
    subtitle: 36,
    body: 24,
    caption: 18,
  },
  weights: {
    regular: 400,
    medium: 500,
    semibold: 600,
    bold: 700,
  },
} as const;
```

### Good Example

```typescript
// Using constants throughout composition
import { COLORS, SPRING_CONFIGS, TYPOGRAPHY } from "./constants";

<div
  style={{
    backgroundColor: COLORS.background,
    color: COLORS.text,
    fontFamily: TYPOGRAPHY.fontFamily,
    fontSize: TYPOGRAPHY.sizes.headline,
    fontWeight: TYPOGRAPHY.weights.bold,
  }}
>
```

### Bad Example

```typescript
// Hardcoded values
<div
  style={{
    backgroundColor: "#0A0A0A",  // Magic string
    color: "#FFFFFF",            // Magic string
    fontFamily: "Inter",         // Not standardized
    fontSize: 72,                // Magic number
    fontWeight: 700,             // Magic number
  }}
>
```

### Type Safety with `as const`

Always use `as const` for constants:

```typescript
// With as const - TypeScript knows exact values
export const COLORS = {
  primary: "#FF6B35",
} as const;

// Type is: { readonly primary: "#FF6B35" }
// Can use COLORS.primary safely

// Without as const - TypeScript only knows it's a string
export const COLORS = {
  primary: "#FF6B35",
};

// Type is: { primary: string }
// Loses specific value information
```

### Checklist

- [ ] Colors grouped and commented
- [ ] Spring configs named descriptively
- [ ] Timing uses FPS multiplier (not hardcoded frames)
- [ ] All values use `as const`
- [ ] No magic numbers in component code
- [ ] Section separators for organization
