# State Checklist

Review every applicable state of the affected surface, not only the happy path.

## States to check

- Initial loading, refresh, partial content, stale content, ready.
- First-use empty, no search results, unavailable data.
- Validation error, recoverable failure, blocking failure.
- Offline, pending synchronization, synchronization conflict.
- Permission not requested, denied, restricted, revoked.
- Action in progress, confirmed success, cancellation, disabled with a reason.

## Rules

- Never render a failed request as an empty dataset. They call for different
  messages and different actions.
- Distinguish a known failure from an unknown outcome before offering retry.
- Preserve user input on validation or recoverable failure.
- Make retry safe: prevent duplicate submissions and state what will happen.
- Label partial or stale data as such instead of presenting it as current.
- A disabled control explains why, or is replaced by a path forward.
- Announce success only when the source confirms it; a pending save is not a
  completed save.
- Reserve space for loading content so the layout does not jump when data
  arrives.
- For long operations, show progress and offer cancellation when the work can
  be safely interrupted.
- Keep error messages next to the element that caused them, with a way to fix
  the problem.
