# Copy Checklist

## Labels

- One name per concept, used consistently across the journey.
- Action labels describe the outcome: "Save changes," "Delete draft," "Try
  again" instead of "OK," "Submit," or "Validate."
- Avoid repeating context the surrounding screen already establishes.
- Destructive actions name the object affected.
- Avoid internal jargon, implementation terms, and unexplained abbreviations.

## Errors and feedback

- State what happened and what the user can do next.
- Do not blame the user; keep their input intact.
- Empty states state the situation and the next useful action.
- Do not use celebration or exclamation for a non-success state.
- Distinguish "nothing here yet" from "we could not load this."

## Values and units

- Use the unit that matches the domain; never copy a unit from another concept.
- Round and format according to the locale; keep precision meaningful.
- Do not imply that a current result, a best result, and a ranking are the same
  measure.
- A tie is not a new record; state a record only when the domain confirms it.

## Localization and layout

- Assume translated strings can grow substantially longer than the source.
- Allow labels to wrap; do not shrink text to force a single line.
- Avoid concatenating sentences from fragments that may not translate in the
  same order.
