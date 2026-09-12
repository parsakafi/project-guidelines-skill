# Web Accessibility Guidelines

Apply these rules when changing browser-facing UI.

## Semantic HTML

Prefer native semantic elements:

```html
<header>
<nav>
<main>
<section>
<article>
<footer>
<button>
<a>
<form>
<label>
```

Do not replace semantic controls with generic `<div>` elements when native controls provide the correct behavior.

## Keyboard access

Every interactive feature must be usable without a mouse.

Verify:

- keyboard focus
- visible focus indicator
- logical tab order
- activation using keyboard
- no keyboard traps

Do not remove default focus styles without providing an equivalent accessible focus state.

## Links vs buttons

Use links for navigation:

```html
<a href="/account">Account</a>
```

Use buttons for actions:

```html
<button type="button">Delete</button>
```

Do not use click handlers on generic elements when a native control is appropriate.

## Forms

Every input should have an accessible label.

Prefer:

```html
<label for="email">Email</label>
<input id="email" name="email">
```

Associate validation errors with the relevant field.

Do not communicate important errors only through color.

## Images

Provide meaningful alternative text.

For decorative images, use appropriate empty alt text:

```html
<img src="..." alt="">
```

Do not use filename-based alt text as a substitute for meaningful descriptions.

## Headings

Maintain a logical heading hierarchy.

Do not choose heading elements solely for visual styling.

Use CSS for presentation.

## Color and contrast

Do not communicate information using color alone.

Ensure sufficient contrast for text and meaningful UI states.

Check hover, focus, disabled, error, success, and selected states.

## ARIA

Prefer semantic HTML over ARIA.

Use ARIA when native HTML cannot express the required semantics.

When using ARIA:

- ensure roles/states/properties are valid
- ensure referenced IDs exist
- keep accessible names accurate
- test actual keyboard and screen-reader behavior

Do not add redundant ARIA to native controls without a reason.

## Dynamic content

For dynamically updated content:

- preserve focus appropriately
- announce important state changes when necessary
- avoid unexpected focus movement
- ensure loading/error/success states are perceivable

## Modals and dialogs

Accessible dialogs should:

- have an accessible name
- move focus into the dialog appropriately
- keep focus contained while open when required
- close predictably
- return focus to the triggering element

Use a tested dialog component where possible.

## Motion

Respect reduced-motion preferences when animation could cause discomfort.

For CSS:

```css
@media (prefers-reduced-motion: reduce) {
  /* reduce or remove non-essential motion */
}
```

Do not make essential information depend on animation.

## Automated testing

Use appropriate automated accessibility checks where practical:

- axe
- Lighthouse
- framework-specific accessibility tooling

Automated tools do not replace manual keyboard testing.

For important interfaces, perform manual checks with keyboard navigation and, when practical, a screen reader.

## Review checklist

Before completing UI work:

- semantic elements used
- keyboard navigation works
- focus is visible
- forms have labels
- errors are accessible
- images have appropriate alt text
- headings are logical
- color is not the only information channel
- contrast is adequate
- dynamic updates are perceivable
- reduced motion is considered
