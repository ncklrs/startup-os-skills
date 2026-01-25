# VSL Storyboard Writer Skill

Expert VSL (Video Sales Letter) and product marketing video storyboard writer skill for Claude Code.

## Purpose

Creates production-ready storyboard scripts for video sales letters, product demos, explainer videos, and social media video content. Bridges the gap between marketing copywriting and video production, outputting scripts optimized for handoff to the motion-designer skill.

## Integration

This skill works in a pipeline:

```
VSL Storyboard Writer → Motion Designer → Remotion Implementation
```

**vsl-storyboard-writer** produces:
- Complete storyboard scripts
- Scene-by-scene breakdowns
- Copy, messaging, and conversion strategy
- Visual direction and psychology
- Production requirements

**motion-designer** consumes the storyboard and produces:
- Technical video specifications
- Frame-by-frame animation details
- Remotion implementation guidance

## When to Use

Invoke this skill when:
- "Write a video script"
- "Create a VSL"
- "Storyboard a sales video"
- "Script a product demo"
- Creating marketing video content
- Planning social media video ads

## Structure

```
vsl-storyboard-writer/
├── SKILL.md                           # Main skill overview
├── README.md                          # This file
└── rules/
    ├── _storyboard-template.md        # Complete template for all scripts
    ├── vsl-hooks.md                   # Hook formulas and attention-grabbing
    ├── vsl-frameworks.md              # AIDA, PAS, and other VSL structures
    ├── cta-optimization.md            # Call-to-action best practices
    ├── script-pacing.md               # Timing and rhythm
    ├── social-proof-strategy.md       # Testimonials and credibility
    ├── objection-handling.md          # Addressing buyer concerns
    ├── visual-storytelling.md         # Show don't tell principles
    └── motion-designer-handoff.md     # Production-ready formatting
```

## Key Frameworks Included

### Hook Types
- Question hooks
- Problem hooks
- Curiosity hooks
- Social proof hooks
- Demonstration hooks
- Pattern interrupt hooks

### VSL Formulas
- **Hook-CTA**: 15-30s social ads
- **PAS**: Problem → Agitate → Solution (30-90s)
- **AIDA**: Attention → Interest → Desire → Action (60-120s)
- **The Explainer**: Context → Mechanism → Benefits (60-180s)
- **VSL Classic**: Full sales video structure (3-10min)

### Conversion Elements
- Strategic social proof placement
- Objection handling sequence
- CTA optimization
- Friction removal
- Urgency and scarcity (authentic only)

## Output Format

Produces comprehensive storyboard scripts with:

1. **Executive Summary**: Goals, audience, framework
2. **Story Arc Overview**: Emotional journey and narrative flow
3. **Scene-by-Scene Breakdown**:
   - Narrative purpose
   - Viewer psychology
   - On-screen copy
   - Visual description
   - Sales elements
   - Motion designer notes
   - Transitions
4. **Asset Requirements**: Copy, visuals, brand elements
5. **Production Specifications**: Platform, format, constraints

## Example Use Cases

### B2B SaaS Product Demo (90s)
Framework: AIDA
Focus: Demo + Social proof + Trial CTA

### Social Media Ad (30s)
Framework: Hook-CTA
Focus: Fast hook + Quick demo + Clear action

### Product Launch Video (3-5min)
Framework: VSL Classic
Focus: Story + Problem + Solution + Proof + Offer

### Explainer Video (60-120s)
Framework: The Explainer
Focus: Education + Benefits + Credibility

## Integration with Remotion

This skill creates scripts specifically designed for Remotion video production:
- Scene structure maps to `<Sequence>` components
- Timing specified in seconds (converted to frames by motion designer)
- Animation guidance compatible with `spring()` and `interpolate()`
- Asset requirements list what's needed for implementation

## Quality Standards

All storyboards include:
- ✅ Attention-grabbing hook (first 3-5 seconds)
- ✅ Clear value proposition
- ✅ Specific, measurable claims
- ✅ Strategic social proof placement
- ✅ Objection handling woven throughout
- ✅ Strong, clear CTA
- ✅ Production-ready specifications
- ✅ Motion designer handoff format

## Best Practices

1. **Start with the CTA, work backwards**: Know where viewers should end up
2. **Show, don't tell**: Use visuals to demonstrate, copy to reinforce
3. **One message per scene**: Don't try to communicate everything everywhere
4. **Address objections implicitly**: Show solutions, don't name fears
5. **Test the hook independently**: First 5 seconds should work as standalone ad
6. **Leave room for creativity**: Provide direction, not dictation
7. **Be production-ready**: Motion designer shouldn't need to guess

## Related Skills

- **motion-designer**: Takes storyboard scripts and creates technical video specs
- **gtm-copywriter**: For email/content that supports video campaigns
- **senior-product-marketer**: For positioning and messaging strategy
- **remotion-best-practices**: For technical implementation guidance

## Created

January 22, 2026

## Version

1.0.0
