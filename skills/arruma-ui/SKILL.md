---
name: arruma-ui
description: "Use when the user asks to arrumar, redesenhar, polir, normalizar ou auditar uma interface existente ('arruma a UI', 'melhora a interface', 'tirar cara de IA', 'deixar premium', 'normalizar botões', 'UI review', 'redesign'). Audits first, preserves product truth, and applies one restrained system: hierarchy, spacing, controls, states, motion, accessibility, anti-slop, and browser verification."
metadata:
  version: 1.0.0
---

# Arruma UI

One pass for improving an interface that already exists. It combines the useful parts of redesign, design-system normalization, anti-slop critique, craft floor, motion, and accessibility skills. The default is normalize, not replace.

## Stance

- The product exists. Improve it; do not reinvent it.
- Functionality, content, flows, data, and brand stay. Changing them needs explicit permission.
- Restraint reads as premium. One accent, two typefaces, one radius scale, four shadows.
- Audit before editing. Every finding cites a screen, component, or line.
- Deliver working code and rendered evidence, not a plan.

## Modes

- `audit`: report findings only.
- `normalize`: keep the visual world and fix the system. Default.
- `redesign`: replace the visual world. Only when the user asks for a redesign.

For a single screen or a quick job, keep steps 0 to 2, fix the five highest-impact findings, then verify. Do not turn a small job into a full redesign.

## Step 0. Read the room

Read, in this order:

1. Tokens, theme, CSS variables, and the design-system file (`DESIGN.md`, `PRODUCT.md`, `AGENTS.md`, visual guide).
2. The component inventory and the screens in scope.
3. The rendered interface at 390, 768, and 1440, light and dark.

If the app runs, inspect it in the browser. If it does not, use committed screenshots. Never invent screens, data, metrics, or brand.

Completion: one short brief naming the visual world, the three worst problems, and what must stay.

## Step 1. Audit

Score each dimension from 0 to 10. Fix anything under 7. Cite evidence for every finding.

1. Hierarchy. One entry point per screen. The primary action is obvious. The squint test holds.
2. Layout. Grid, container width, spacing rhythm, alignment, density.
3. Type. Scale, measure (45 to 75ch), weights, wrapping, tabular numbers.
4. Color. One accent, one neutral family, contrast, tinted blacks and whites.
5. Surfaces. One elevation language. Border or shadow, not both. Radii from one scale.
6. Controls. Buttons, inputs, tabs, chips, cards. One height per size. Targets at least 44px.
7. Motion. One authored moment. 120 to 240ms. Transform and opacity only. Reduced motion respected.
8. States. Hover, focus, active, disabled, loading, empty, error, success.
9. Responsive. 320, 390, 768, 1024, 1440. No horizontal scroll, clipping, or overlap.
10. Accessibility. Contrast, keyboard, labels, alt text, semantics, visible focus.
11. Copy. Product nouns. Controls name the action. Errors name the problem and the recovery.
12. Performance. No layout shift, sized media, transform-only animation, no unnecessary dependency.
13. Slop. Remove decoration before adding anything.

Common tells to catch while scoring:

- Type: only 400 and 700, body over 75ch, no tabular numbers, orphan words, display tracking past -0.04em.
- Color: mixed warm and cool grays, pure black, more than one accent, untinted shadows, accent over 8%.
- Layout: everything centered, three equal cards, no max-width, 100vh hero, one radius on everything, same gap everywhere.
- Controls: mixed heights, no hover or pressed feedback, missing focus ring, dead links, icon and text misaligned, targets under 44px.
- States: no empty, loading, error, or disabled state. Success shown without a request.
- Content: placeholder names, fake round numbers, AI clichés, identical dates, lorem ipsum, title case everywhere.
- Surfaces: border plus wide shadow on one card, card inside card, glass on everything, gradient text, colored side stripes.
- Motion: `transition: all`, width or height animation, one identical entrance on every section, motion with no state meaning.

## Step 2. Plan

Write at most 120 words:

- three to five moves
- what stays
- files and screens touched
- how you will verify

No new sections, palette, or dependency unless the user asks. Do not create a design document unless the user asks.

## Step 3. Normalize

Use the project's tokens. If there are none, create the smallest set:

| Token | Values |
|---|---|
| Space | 4, 8, 12, 16, 24, 32, 48, 64 |
| Radius | 6 small, 10 control, 14 card, 18 shell; pills only for tags and small controls |
| Type | 12, 13, 14, 16, 20, 24, 32, 40, 56; body 14 to 16, line-height 1.5 to 1.65 |
| Control height | 32 compact, 40 default, 48 touch; one height per size |
| Icon | 16, 20, 24; one stroke weight |
| Shadow | four levels max; offset plus soft blur; tint from the background hue |
| Border | 1px hairline; never border plus wide shadow on the same card |
| Focus | 2px ring, 2px offset, always visible |
| Motion | 120 to 240ms, cubic-bezier(0.22, 1, 0.36, 1), stagger 40ms |
| Container | max 1200 to 1440px, centered, fluid gutters |

Rules:

- Buttons and inputs share the same height at the same size.
- Primary, secondary, and ghost differ by fill, not by five radii.
- Cards exist only when elevation communicates hierarchy.
- Spacing above a heading is larger than below it.
- Numerals in data use tabular figures.
- Selection, caret, scrollbar, and focus ring come from the palette, not the browser default.
- The accent covers under 8% of a viewport.
- Headings track at most -0.04em.
- Body text never sits under 12px. Functional text never sits under 11px.

## Step 4. Implement in passes

1. Tokens and global resets.
2. Layout and shell.
3. Components.
4. States and copy.
5. Motion.

Keep the diff readable. No drive-by rewrites. After each pass, run the app and look at the result.

## Step 5. Verify

- 390, 768, and 1440; light and dark.
- Keyboard: Tab, Shift+Tab, Enter, Escape.
- Reduced motion.
- No horizontal scroll, clipping, or overlap.
- No layout shift on load. Animations hold 60fps.
- Contrast 4.5:1 for body, 3:1 for large text.
- Read the screenshots. Capturing is not checking.

Completion: every screen in scope checked at every viewport, with no open finding or an explicitly accepted one.

## Step 6. Report

In the user's language, short:

- what changed, with files and screens
- before and after evidence
- what stayed
- risks and unknowns
- one next move

## Anti-slop floor

Remove before adding. Never ship:

- purple-to-blue gradient or gradient text
- glass and blur as generic decoration
- 3D, particles, or shader effects as default decoration
- a card inside a card
- emoji as an icon
- an eyebrow label above a heading
- three equal icon-heading cards as the page structure
- pure `#000` or `#fff` outside the token block
- Inter, Roboto, Open Sans, Poppins, or Lato as the display face
- everything centered on one axis
- invented metrics, testimonials, logos, or case studies
- `transition: all`, or animation of width, height, top, or left
- essential information only on hover
- invisible focus
- decorative motion with no state meaning
- placeholder names and startup clichés
- a stock secondary action next to the primary

## House taste

These are the skill's opinionated defaults when the brief leaves the axis free.

- Editorial, calm, premium. Space is the main luxury.
- One accent. Warm neutrals or cool neutrals, never mixed.
- Display face with character, body grotesque, one outlier at most.
- Serif display for editorial, legal, and clinical work. Sans for tools.
- Quiet motion with one authored moment. No motion theater.
- Copy in the product's language. For Brazilian products, pt-BR. Plain words, no jargon.
- Vanilla HTML, CSS, and JavaScript first when the stack is free.
- Keep the existing brand. Do not invent a new one.
- Show the result working. A plan is not a deliverable.

## Stop and ask

- changing product logic, content, or data
- adding a dependency or framework
- destructive cleanup
- replacing the brand or the visual world
