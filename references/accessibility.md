# Accessibility Checklist

Apply to every interactive redesign. A screenshot or automated scan alone does
not establish compliance.

## Names and structure

- Every control has an accessible name; icon-only controls have a visible or
  programmatic label.
- Heading levels and reading order match the visual hierarchy.
- Images that carry meaning have alternative text; decorative images are
  ignored by assistive technology.
- Form fields keep visible labels; a placeholder is not a label.
- Errors are associated with their field and announced, not conveyed by color
  alone.

## Keyboard and focus

- Every action is reachable and operable by keyboard.
- Focus is visible and follows a logical order.
- No keyboard trap; dismissible surfaces close with Escape.
- After navigation, modal opening, or modal closing, focus moves to a
  meaningful place.
- Custom widgets expose the expected role, state, and keyboard behavior.

## Perception

- Text and meaningful icons meet contrast requirements.
- Color is not the only carrier of state, selection, or error.
- Text remains readable and reachable when the system text size is enlarged.
- Motion respects the reduced-motion preference; essential information never
  exists only in an animation.
- Touch targets are comfortable and spaced enough to avoid accidental activation.

## Content and timing

- Time limits can be extended or removed when the task allows it.
- Instructions do not rely on shape, position, or color alone.
- Language and abbreviations are understandable to the intended audience.
