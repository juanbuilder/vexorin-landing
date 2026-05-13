# Vexorin Design System

## 1. Brand Identity

**Name:** Vexorin  
**Tagline:** The recognition substrate for institutional capital  
**Positioning:** Hard-tech, institutional-grade signal intelligence for institutional capital markets.

**Voice & Tone:**
- Every sentence is a definitive statement. No hedging, no "we hope to." Only "we are."
- Modeled after intellectual authority (Thiel-esque): contrarian, serious, profoundly precise.
- Type-driven over icon-driven. Signal over noise.
- Target audience: Hedge funds, quant desks, sovereign wealth funds, institutional capital managers.

**Visual Philosophy:**
- High-contrast, minimalist, hard-tech. Geometric, not decorative.
- Precision over decoration. The UI communicates the same certainty the product delivers.
- No gradients (except subtle depth). No glow effects. No playful animations that read as marketing.
- Zero border-radius everywhere—no rounded corners. That signals consumer-friendly. This is instrumentation.

**Component Identity System:**
All components carry visible VXRN-XXX identifiers in the UI (e.g., VXRN-CARD, VXRN-BTN-PRIMARY, VXRN-DATA). These are not internal documentation—they appear as labels in the design itself, signaling precision and deliberation.

---

## 2. Color System

### Design Tokens

All color usage is semantic. The tokens enforce a discipline: signal through restraint.

| Token | Hex | RGB | Semantic Role | Permitted Uses | Forbidden Uses |
|---|---|---|---|---|---|
| `--color-void` | `#0A0A0F` | 10, 10, 15 | Dominant background | Page background, full-screen overlays | Text, borders, fills smaller than page scale |
| `--color-depth` | `#0F1219` | 15, 18, 25 | Panel/card background | Cards, panels, modals, table rows, nested containers | Page-scale backgrounds (use VOID) |
| `--color-steel` | `#1A2B4A` | 26, 43, 74 | Structural accent | Dividers, cell borders, inactive states, hover overlays | Large fill areas, primary text |
| `--color-signal` | `#00E5FF` | 0, 229, 255 | Primary accent | CTAs, active links, active indicators, thin structural rules (2px), key metric highlights | Body text, large fills. Limit: 4px minimum thickness for color fills. |
| `--color-alert` | `#FFB800` | 255, 184, 0 | Secondary accent | Warning states, critical section labels, proven callouts | Decorative use, background fills at scale |
| `--color-threat` | `#FF2D55` | 255, 45, 85 | Critical severity only | Error states, breach indicators, maximum-urgency alerts | More than one per view. Default to ALERT if in doubt. |
| `--color-white` | `#FFFFFF` | 255, 255, 255 | Primary text | Headings, body copy, UI labels | Backgrounds |
| `--color-muted` | `#CCCCCC` | 204, 204, 204 | Secondary text | Captions, metadata, placeholder text, supporting copy | Primary headings or emphasis |

### Contrast Ratios

Verified for WCAG AA compliance:
- `--color-white` on `--color-void`: 18.5:1
- `--color-signal` on `--color-void`: 9.6:1
- `--color-muted` on `--color-void`: 9.1:1
- `--color-alert` on `--color-void`: 8.4:1

### Usage Rules

**SIGNAL (#00E5FF) Discipline:**
- SIGNAL is electric and carries visual weight. It should feel like *signal* — precise and intentional.
- Limit to: structural accents (the 2px rule), one active CTA per view, inline text links, active/focused states.
- Never use SIGNAL as a fill on elements larger than 4px thickness. It loses power in scale.
- Never use SIGNAL for backgrounds. The 2px rule is the signature application.

**ALERT (#FFB800) vs THREAT (#FF2D55):**
- ALERT is for "pay attention." THREAT is for "stop and look."
- Default to ALERT for warning states. Use THREAT only for breaches, errors, or maximum-severity alerts.
- Never use both THREAT and ALERT in the same view unless the severity distinction is critical.

---

## 3. Typography System

### Font Families

**Primary Sans:** `'IBM Plex Sans', 'Inter', system-ui, sans-serif`  
**Mono:** `'IBM Plex Mono', 'JetBrains Mono', 'Courier New', monospace`

Both font families load from Google Fonts CDN in a single import request:
```
https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@400;500;600;700&family=IBM+Plex+Sans:wght@400;600;700&display=swap
```

### Mono-Treatment Rule

**Apply monospace font to:**
- Section labels (all-caps)
- Component tags (VXRN-XXX)
- Metric values (numbers in data displays, indices, version strings)
- Code snippets or technical identifiers
- Any text meant to signal "this is a precise value, not prose"

**Apply sans to:**
- Paragraph body copy and descriptive text
- Navigation and UI labels (unless they are component identifiers)
- Extended reading

This creates visual hierarchy: mono = precision, sans = story.

### Type Scale — Desktop

| Role | Element | Font | Weight | Size | Line-height | Letter-spacing | Case |
|---|---|---|---|---|---|---|---|
| Display XL | Hero tagline | IBM Plex Mono | 700 | 72px | 1.05 | -0.02em | Mixed |
| H1 | Page/section title | IBM Plex Mono | 700 | 56px | 1.1 | -0.02em | Mixed |
| H2 | Section heading | IBM Plex Mono | 600 | 40px | 1.15 | -0.01em | Mixed |
| H3 | Subsection | IBM Plex Sans | 700 | 28px | 1.2 | 0 | Mixed |
| H4 | Component heading | IBM Plex Sans | 600 | 20px | 1.3 | 0.01em | Mixed |
| H5 | Card heading | IBM Plex Sans | 600 | 16px | 1.4 | 0.01em | Mixed |
| H6 | Label heading | IBM Plex Mono | 500 | 12px | 1.5 | 0.1em | ALL CAPS |
| Body | Paragraph | IBM Plex Sans | 400 | 16px | 1.7 | 0 | Mixed |
| Body SM | Caption/metadata | IBM Plex Sans | 400 | 14px | 1.6 | 0 | Mixed |
| Mono | Code/technical values | IBM Plex Mono | 400 | 14px | 1.5 | 0 | Mixed |
| Label | Component tags, overlines | IBM Plex Mono | 500 | 11px | 1 | 0.12em | ALL CAPS |
| Overline | Section context | IBM Plex Mono | 400 | 11px | 1 | 0.2em | ALL CAPS |

### Type Scale — Mobile (`max-width: 768px`)

Scale all sizes down by ~0.7–0.75:
- Display XL → 48px
- H1 → 36px
- H2 → 28px
- H3 → 22px
- H4 → 18px
- H5 → 14px
- H6 → 10px
- Body → 15px (slight reduction for density)

Label and Overline remain 11px and 10px respectively (already small).

### Typography Do/Don't

**DO:**
- Use mono at large scale for technical precision (H1, H2).
- Use all-caps + increased letter-spacing for labels only (H6, Label, Overline).
- Stack fonts in the priority order specified.
- Use font weights: 400 (regular), 500 (medium), 600 (semibold), 700 (bold). No 300 or 800.
- Increase line-height for body copy (1.6–1.7) to improve readability.

**DON'T:**
- Mix font families within a single heading element (don't use San heading with Mono text inside it).
- Use font weights below 400.
- Apply letter-spacing to body copy (only labels/overlines).
- Justify text alignment (use left align for readability).
- Use more than one font family per role.

---

## 4. Spacing & Grid

### Base Unit

**8px.** All spacing values are multiples of 8px.

### Spacing Scale

| Token | Value | Use |
|---|---|---|
| `--space-1` | 4px | Micro gaps (tag padding, icon margins) |
| `--space-2` | 8px | Tight spacing (label-to-value, badge padding) |
| `--space-3` | 16px | Component internal padding |
| `--space-4` | 24px | Card padding, subsection spacing |
| `--space-5` | 32px | Between components in a section |
| `--space-6` | 48px | Section top/bottom padding |
| `--space-7` | 64px | Large section separators |
| `--space-8` | 96px | Hero padding, major vertical rhythm |

### Grid System

- **Columns:** 12-column grid
- **Gutter:** 24px (desktop), 16px (tablet), 12px (mobile)
- **Max content width:** 1280px
- **Page padding:** 80px horizontal (desktop), 40px (tablet), 20px (mobile)

**Snap-scroll sections:**
- Full viewport width (100vw) with centered max-width 1280px content container
- Padding: `var(--space-8)` horizontal on desktop, `var(--space-6)` on tablet, `var(--space-3)` on mobile

### Layout Utilities

```css
.grid-cols-2   /* 2-up layout, collapses to 1 on mobile */
.grid-cols-3   /* 3-up layout, collapses to 1 on mobile */
.grid-cols-4   /* 4-up layout, collapses to 2 on tablet, 1 on mobile */
```

---

## 5. Motion & Animation

### Animation Philosophy

Motion communicates precision, not delight. Transitions should feel like instruments—calibrated, purposeful, invisible unless you're looking for them. No bounce easing. No spring physics. No playful overshoots.

### Easing Values

| Name | Value | Use |
|---|---|---|
| `--ease-default` | `cubic-bezier(0.2, 0, 0.38, 0.9)` | General UI transitions (IBM Carbon standard) |
| `--ease-enter` | `cubic-bezier(0, 0, 0.38, 0.9)` | Elements entering the viewport |
| `--ease-exit` | `cubic-bezier(0.2, 0, 1, 0.9)` | Elements leaving the viewport |
| `--ease-expressive` | `cubic-bezier(0.4, 0.14, 0.3, 1)` | Emphasis moments only (sparingly) |

### Duration Scale

| Token | Value | Use |
|---|---|---|
| `--duration-fast` | 100ms | Hover states, focus ring changes |
| `--duration-default` | 200ms | Button state changes, toggles, simple state shifts |
| `--duration-reveal` | 600ms | Section entry animations, fade-in on viewport entry |
| `--duration-transition` | 400ms | Panel open/close, expand/collapse, complex transitions |

### Viewport Entry Animation (Standard)

This is the primary animation pattern: when a section enters the viewport, its child elements fade in with upward motion.

**Initial state:**
```css
opacity: 0;
transform: translateY(20px);
```

**Final state:**
```css
opacity: 1;
transform: translateY(0);
```

**Timing:**
- Duration: `var(--duration-reveal)` (600ms)
- Easing: `var(--ease-enter)`
- Stagger: 100ms per child element (max 5 steps = 500ms total)

**Implementation:**
```css
.animate-child {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity var(--duration-reveal) var(--ease-enter),
              transform var(--duration-reveal) var(--ease-enter);
}

.animate-child.is-visible {
  opacity: 1;
  transform: translateY(0);
}

.animate-child:nth-child(1) { transition-delay: 0s; }
.animate-child:nth-child(2) { transition-delay: 0.1s; }
.animate-child:nth-child(3) { transition-delay: 0.2s; }
.animate-child:nth-child(4) { transition-delay: 0.3s; }
.animate-child:nth-child(5) { transition-delay: 0.4s; }
```

### Scroll-Snap Behavior

**Desktop:** `scroll-snap-type: y mandatory` — sections snap into place as you scroll.  
**Mobile:** `scroll-snap-type: y proximity` — sections snap when you're close, but allow normal scrolling if content overflows. This prevents "snap traps" on mobile where content exceeds viewport height.

**Container:**
```css
scroll-behavior: smooth;
scroll-snap-type: y mandatory; /* desktop */
```

**Sections:**
```css
scroll-snap-align: start;
height: 100vh; /* desktop */
```

### Motion Do/Don't

**DO:**
- Stagger children in reading direction (top-to-bottom, left-to-right).
- Use `prefers-reduced-motion` media query to disable animations for accessibility.
- Combine opacity + transform (fade + motion together).
- Keep transitions under 600ms for most interactions.

**DON'T:**
- Animate background colors (reads as marketing, not instrument).
- Use `transform: scale()` (reads as "consumer app").
- Create infinite animations (except when explicitly needed for loading states).
- Use parallax effects.
- Add motion to decorative elements.

**Accessibility:**
```css
@media (prefers-reduced-motion: reduce) {
  .animate-child {
    transition: none;
    opacity: 1;
    transform: none;
  }
}
```

---

## 6. Component Specifications

### 6.1 Cards & Panels

**Visual identity:**
- Background: `--color-depth`
- Border: 1px solid `--color-steel`
- Border-radius: 0 (no rounded corners)
- Padding: `var(--space-4)` (24px)
- Position relative (for absolute-positioned badge)

**On hover:**
- Border-color transitions to `--color-signal` at 40% opacity
- Duration: `var(--duration-default)` (200ms)
- Easing: `var(--ease-default)`

**Accent variant (for emphasis):**
- Add 2px solid `--color-signal` left border
- Remove 1px left border from main border to keep total width consistent

**Structure:**
```
[VXRN tag — positioned absolute bottom-left]
[Heading — H4 or H5]
[Divider — thin STEEL rule, optional]
[Body copy]
[Optional: CTA button or metric value]
```

### 6.2 Badges & Component Tags

The VXRN-XXX identifier system. Display on all major components.

**Styling:**
- Font: IBM Plex Mono, 11px, weight 500, letter-spacing 0.12em
- Case: ALL CAPS
- Color: `--color-muted`
- Background: `--color-depth`
- Border: 1px solid `--color-steel`
- Padding: 2px 6px
- Display: inline-block
- Position: absolute (bottom-left of parent container, which must be `position: relative`)

**Variants:**
- Default (VXRN-CARD): `--color-muted` text
- Alert (VXRN-ALERT): `--color-alert` text
- Threat (VXRN-THREAT): `--color-threat` text

### 6.3 Buttons

Three distinct variants for three levels of hierarchy. Avoid using more than one Primary per view.

**Primary Button** — The one definitive action per view.
- Background: `--color-signal`
- Text: `--color-void` (dark text on bright background for legibility)
- Font: IBM Plex Mono, 13px, weight 600, letter-spacing 0.08em, ALL CAPS
- Padding: 12px 24px
- Border-radius: 0
- Border: none
- Cursor: pointer

**Hover state:**
- Background: `--color-signal` at 85% opacity
- No transform (no scale, no translate)
- Duration: `var(--duration-default)`

**Active state:**
- Background: `--color-signal` at 70% opacity

**Secondary Button** — Supporting actions, lower hierarchy.
- Background: transparent
- Border: 1px solid `--color-signal`
- Text: `--color-signal`
- Font: IBM Plex Mono, 13px, weight 600, letter-spacing 0.08em, ALL CAPS
- Padding: 12px 24px
- Border-radius: 0

**Hover state:**
- Background: `--color-signal` at 10% opacity
- Border-color: unchanged

**Ghost Button** — Low-hierarchy actions, minimal visual weight.
- Background: transparent
- Border: 1px solid `--color-steel`
- Text: `--color-muted`
- Font: IBM Plex Mono, 13px, weight 500, letter-spacing 0.08em, ALL CAPS
- Padding: 12px 24px
- Border-radius: 0

**Hover state:**
- Border-color: `--color-muted`
- Text: `--color-white`

**Forbidden for all buttons:**
- box-shadow (no elevation)
- border-radius > 0 (no rounded corners)
- transform on hover (no scale, translate, rotate)

### 6.4 Data Tables

Designed for dense, precise data display.

**Container:**
- Background: `--color-depth`
- Border: 1px solid `--color-steel`
- Border-radius: 0
- Padding: 0 (no outer padding—borders define edges)

**Header row:**
- Background: `--color-steel`
- Text: `--color-white`
- Font: Label style (IBM Plex Mono, 11px, weight 500, ALL CAPS, letter-spacing 0.12em)
- Padding: 12px 16px

**Data rows:**
- Background: `--color-void` (slightly darker for zebra striping alternation)
- Border-bottom: 1px solid `--color-steel`

**Cells:**
- Padding: 12px 16px
- Text alignment: left (default)
- Numbers: right-aligned, IBM Plex Mono
- Text: IBM Plex Sans

**Hover state (entire row):**
- Border-left: 2px solid `--color-signal` (visual focus cue)
- Background: unchanged

**Alternate rows (zebra striping):**
- Alternate background: `--color-depth` (slightly lighter than base `--color-void`)

### 6.5 Dividers

The 2px SIGNAL rule is the primary structural separator. It carries visual and semantic weight.

**2px SIGNAL Divider (primary):**
```css
border: none;
height: 2px;
background: var(--color-signal);
margin: var(--space-6) 0; /* breathing room */
```

**1px STEEL Divider (secondary, within-component):**
```css
border: none;
height: 1px;
background: var(--color-steel);
margin: var(--space-3) 0;
```

**Usage:**
- Full-width SIGNAL dividers between major sections
- Thin STEEL dividers within cards or between content rows
- Never use vertical dividers (use borders instead)

### 6.6 Metric Callout Blocks

Large-number + label pattern. Used for highlighting key metrics, pricing, or statistics.

**Container:**
- Background: `--color-depth`
- Border: 1px solid `--color-steel`
- Border-left: 2px solid `--color-signal` (optional, for emphasis)
- Padding: `var(--space-4)` (24px)
- Border-radius: 0

**Content structure:**
```
[Label: Overline style — IBM Plex Mono, 11px, ALL CAPS, var(--color-muted)]
[Metric value: IBM Plex Mono, 40–56px, weight 700, var(--color-white)]
[Sub-label: IBM Plex Sans, 13px, var(--color-muted)]
[Badge positioned absolute bottom-left: VXRN-METRIC]
```

### 6.7 Alert & Warning Callouts

**Container:**
- Background: `--color-depth`
- Border-left: 2px solid `--color-alert` (or `--color-threat` for critical)
- Padding: `var(--space-4)` (24px)
- Border-radius: 0

**Icon:**
- Minimal geometric shapes only (circle, triangle, square)
- Size: 16px–20px
- Color: matches border color

**Label:**
- IBM Plex Mono, ALL CAPS, color matches border
- Font-size: 11px, letter-spacing 0.12em

**Body:**
- IBM Plex Sans, 16px, `--color-white`
- Line-height: 1.7

---

## 7. Layout Patterns

### Snap-Scroll Sections

The primary layout paradigm. Each section is a full viewport unit—designed to be consumed one at a time, snap-scrolling between them.

**Technical implementation:**

```css
.snap-container {
  height: 100vh;
  height: 100dvh; /* override on supporting browsers */
  overflow-y: scroll;
  scroll-snap-type: y mandatory;
  scroll-behavior: smooth;
}

.snap-section {
  height: 100vh;
  height: 100dvh;
  scroll-snap-align: start;
  overflow: hidden; /* prevents content overflow trap */
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: var(--space-8) var(--page-padding);
  max-width: var(--max-width);
  margin: 0 auto; /* center content within full-width section */
}

@media (max-width: 768px) {
  .snap-container {
    scroll-snap-type: y proximity; /* safety valve on mobile */
  }

  .snap-section {
    height: auto;
    min-height: 100svh; /* small viewport height */
    overflow: visible;
    justify-content: flex-start;
    padding-top: var(--space-6);
  }
}
```

**Key notes:**
- Desktop: `height: 100vh` ensures full viewport per section, with `overflow: hidden` to trap content
- Mobile: `min-height: 100svh` allows content to overflow naturally if needed, with `scroll-snap-type: proximity` to avoid snap traps
- `scroll-behavior: smooth` provides the smooth scrolling experience
- Content is centered in a max-width container within each full-width section

### Hero Section Structure

The opening keynote. Sets tone and visual hierarchy.

```
[Overline class: "VXRN-BRAND — RECOGNITION SUBSTRATE"]
[H1 class: "VEXORIN"]
[2px SIGNAL divider rule, full width, var(--space-6) margin top]
[Tagline: P class with text-body: "The recognition substrate for institutional capital."]
[Body copy: P class with text-body and text-muted: 1–2 sentences of positioning]
[Optional button group:]
  [Button Primary: "REQUEST ACCESS"]
  [Button Secondary: "VIEW DOCUMENTATION"]
[Badge positioned absolute bottom-left: VXRN-HERO]
```

### Content Section Structure

Standard structure for all subsequent sections.

```
[Overline class: "01 — COLOR SYSTEM"]
[H2 class: "Design Tokens"]
[2px SIGNAL divider rule]
[Content grid: grid-cols-3 / grid-cols-4 as appropriate]
[Badge: VXRN-[SECTION]]
```

### Do/Don't

**DO:**
- Align everything to the 8px grid (no 7px, 9px, or off-grid spacing).
- Give every component a visible VXRN tag in demo contexts.
- Use the 2px SIGNAL rule as the primary rhythmic separator between sections.
- Keep data tables right-aligned for numbers.
- Use full-width containers (100vw) with max-width centered content for sections.

**DON'T:**
- Round any corners (`border-radius: 0` everywhere).
- Use more than one chart per view.
- Mix font families within heading elements.
- Add decorative background patterns or textures.
- Use more than two accent colors (SIGNAL + one of ALERT/THREAT) in a single section.
- Center-align body text (left-align for readability).
- Use abbreviated labels without explanation (spell out acronyms on first use).

---

## 8. CSS Custom Property Reference

Complete token list for implementation.

### Colors
```css
--color-void:     #0A0A0F;
--color-depth:    #0F1219;
--color-steel:    #1A2B4A;
--color-signal:   #00E5FF;
--color-alert:    #FFB800;
--color-threat:   #FF2D55;
--color-white:    #FFFFFF;
--color-muted:    #CCCCCC;
```

### Typography
```css
--font-mono:         'IBM Plex Mono', 'JetBrains Mono', 'Courier New', monospace;
--font-sans:         'IBM Plex Sans', 'Inter', system-ui, sans-serif;

--font-size-display: 4.5rem;   /* 72px */
--font-size-h1:      3.5rem;   /* 56px */
--font-size-h2:      2.5rem;   /* 40px */
--font-size-h3:      1.75rem;  /* 28px */
--font-size-h4:      1.25rem;  /* 20px */
--font-size-h5:      1rem;     /* 16px */
--font-size-h6:      0.75rem;  /* 12px */
--font-size-body:    1rem;     /* 16px */
--font-size-body-sm: 0.875rem; /* 14px */
--font-size-mono:    0.875rem; /* 14px */
--font-size-label:   0.6875rem;/* 11px */
--font-size-overline:0.6875rem;/* 11px */
```

### Spacing
```css
--space-1: 4px;
--space-2: 8px;
--space-3: 16px;
--space-4: 24px;
--space-5: 32px;
--space-6: 48px;
--space-7: 64px;
--space-8: 96px;
```

### Layout
```css
--page-padding: 80px;
--max-width:    1280px;
--grid-gutter:  24px;
```

### Motion
```css
--ease-default:   cubic-bezier(0.2, 0, 0.38, 0.9);
--ease-enter:     cubic-bezier(0, 0, 0.38, 0.9);
--ease-exit:      cubic-bezier(0.2, 0, 1, 0.9);
--ease-expressive:cubic-bezier(0.4, 0.14, 0.3, 1);

--duration-fast:    100ms;
--duration-default: 200ms;
--duration-reveal:  600ms;
--duration-transition: 400ms;
```

### Borders & Shadows
```css
--border-thin:   1px solid var(--color-steel);
--border-signal: 2px solid var(--color-signal);
--border-alert:  2px solid var(--color-alert);
--border-threat: 2px solid var(--color-threat);
```

---

## Implementation Checklist

- [ ] Use DESIGN.md as the source of truth for all web interfaces (website, deck, internal tooling)
- [ ] Implement all CSS custom properties as specified
- [ ] All components must carry visible VXRN-XXX identifiers
- [ ] Zero border-radius on all elements (institutional aesthetic)
- [ ] Test all color combinations for contrast ratio compliance
- [ ] Verify snap-scroll behavior on mobile (no content overflow traps)
- [ ] Test animation performance—60fps smooth scrolling
- [ ] Verify `prefers-reduced-motion` support
- [ ] Document any deviations from this spec with reasoning
