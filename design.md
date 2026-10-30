# Design: Luna Lee

The locked visual system for the personal site. All four routes share the same palette, type, spacing, controls, and footer language; each page keeps its own reading shape.

## System
- Genre: editorial
- Shape of the first page: Index, with a worked example as the signature
- Theme: Broadside, bill colourway
- Axes: buff paper / condensed display / vermilion accent · posture: committed
- Page shapes: Index (home), calculator index, Narrative Workflow (guide), app screen (payoff calculator)

## Tokens
`assets/tokens.css` is the source of truth.

```css
:root {
  --color-paper: oklch(92% 0.028 88); --color-paper-2: oklch(88.5% 0.032 88); --color-paper-3: oklch(85% 0.036 86);
  --color-ink: oklch(18% 0.01 50); --color-ink-2: oklch(30% 0.012 50); --color-muted: oklch(43% 0.02 62); --color-rule: oklch(75% 0.028 82);
  --color-accent: oklch(53% 0.19 33); --color-accent-ink: oklch(95.5% 0.018 88); --color-focus: oklch(53% 0.19 33);
  --font-display: "Six Caps", "Impact", sans-serif; --font-display-2: "Source Serif 4", Georgia, serif;
  --font-body: "Archivo Narrow", "Arial Narrow", ui-sans-serif, sans-serif;
  --radius-card: 0; --radius-pill: 0; --rule-hair: 1px; --rule-bar: 5px; --shadow-card: none;
}
```

The shared spacing, type scale, timing, and container live beside these theme values in `assets/tokens.css`. Base browser and accessibility rules live in `assets/base.css`; page composition lives in `assets/site.css`.

## Controls
- Primary: ink fill, square corners, 48px minimum height
- Secondary: paper fill with ink border, square corners, 44px minimum height

## Motion
Still print. Focus and hover states are immediate; reduced-motion preferences disable transitions.

## Exports
`assets/tokens.css` is the source of truth for this project.
