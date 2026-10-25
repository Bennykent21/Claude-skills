---
name: neumorphism
description: Use when the user explicitly requests neumorphism, soft UI, embossed surfaces, or inset neumorphic controls. Use the style deliberately, with accessible contrast, visible focus, and restrained dual shadows.
---

# Neumorphism / Soft UI

Use this skill when the requested visual language is **neumorphism**: controls and surfaces emerge from a single softly contrasting background through paired light and dark shadows. Do not apply it just because a generic interface needs polish.

## Design model

1. **Begin with one surface colour.** The page background and raised elements should be close in colour; depth comes mainly from light direction, shadow softness, and inset treatment rather than strong card fills.
2. **Pick one light direction.** Use a light highlight from the upper-left and a darker soft shadow toward the lower-right. Keep that direction consistent across cards, buttons, toggles, and fields.
3. **Use three depth states at most:** background, raised, and inset/pressed. Reserve deep inset shadows for interactive controls or intentional wells; do not put every nested element in a shadow.
4. **Keep the interface sparse.** Neumorphism works best with clear spacing and a restrained set of controls. Dense dashboards need stronger layout, separators, and typographic hierarchy.
5. **Use semantic design tokens.** Define surface, raised-shadow, inset-shadow, text, border, focus, and status roles. Avoid one-off shadow values per component.

## Starting CSS pattern

~~~css
:root {
  color-scheme: light;
  --soft-surface: #e8edf3;
  --soft-text: #253247;
  --soft-text-muted: #566579;
  --soft-highlight: #ffffff;
  --soft-shadow: #c5ccd5;
  --soft-focus: #245fe8;
}
.soft-raised {
  background: var(--soft-surface);
  border: 1px solid rgb(255 255 255 / 28%);
  border-radius: 16px;
  box-shadow:
    7px 7px 16px var(--soft-shadow),
    -7px -7px 16px var(--soft-highlight);
}
.soft-inset {
  background: var(--soft-surface);
  border: 1px solid rgb(0 0 0 / 4%);
  border-radius: 12px;
  box-shadow:
    inset 4px 4px 9px var(--soft-shadow),
    inset -4px -4px 9px var(--soft-highlight);
}
~~~

Treat these values as a starting point, not a preset for every project. Derive hues, contrast, radii, and shadow strength from the actual product palette and target display.

## Accessibility rules — non-negotiable

- **Shadows communicate depth, not meaning.** Never use shadow alone to show selected, disabled, error, success, or focus states. Add a visible border, icon/state label, underline, or other redundant cue.
- **Protect text contrast.** The soft-surface palette can make low-contrast text tempting. Check actual text/background pairs; if the chosen palette fails contrast, change the colours or reduce the neumorphic treatment rather than weakening readability.
- **Keep focus obvious.** Use a high-contrast :focus-visible outline or ring that remains visible against the paired shadows. Do not remove the browser outline without an equivalent replacement.
- **Make controls identifiable.** Buttons need clear affordances and hover, pressed, disabled, and keyboard-focus states. Inputs need persistent labels; placeholders are not labels.
- **Support touch and assistive tech.** Preserve semantic elements, keyboard operation, accessible names, and adequate touch targets. State changes must be exposed programmatically.
- **Design dark mode independently.** Recompute surface and shadow tokens for the dark palette; do not mechanically invert the light shadows or rely on black shadows against near-black backgrounds.

## Component treatment

- **Cards:** use raised treatment sparingly; some content groups should remain flat to preserve hierarchy.
- **Buttons:** raised by default only when it helps recognition; use an inset or slight surface shift for pressed state, while retaining a non-colour/non-shadow cue.
- **Inputs:** inset wells can help suggest entry, but keep labels, borders, validation messages, and focus rings clear.
- **Navigation:** prefer flat active indicators and strong typography over a row of identical raised pills.
- **Dialogs and menus:** prioritize separation and readable text. Use an opaque or near-opaque surface when content behind it would reduce legibility.
- **Charts/status:** use semantic colour and labels; avoid encoding data using subtle shadow variations.

## Build and review workflow

1. Confirm the user requested this style, or present it as one option rather than silently imposing it.
2. Establish the base surface, text, border, accent, focus, light-shadow, and dark-shadow tokens.
3. Implement a small representative set: one card, one button, one field, one selected/focused state.
4. Check typography, contrast, focus visibility, hover/pressed/disabled states, and dark mode before scaling the treatment.
5. Preview at narrow and wide widths. If the UI starts feeling muddy or affordances disappear, reduce shadows and restore explicit boundaries.
6. Verify reduced-motion preferences if transitions are added. Shadows are decoration; controls must remain understandable without animation.

## Avoid

- Applying two-directional shadows to every element on the page.
- Low-contrast body text, invisible borders, and state communicated only through depth.
- A different light direction on each component.
- Using neumorphism for every surface in dense, data-heavy screens.
- Treating a design trend as more important than usability or the product's existing design system.
