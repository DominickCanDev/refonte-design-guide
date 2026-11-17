---
name: refonte-design-guide
description: A method for analyzing, designing, and implementing UX/UI redesigns for web and mobile pages, components, widgets, and modals. Clarifies information hierarchy, actions, states, accessibility, and visual coherence without losing product meaning or identity.
---

# UX/UI Redesign Method

An autonomous guide for redesigning any web or mobile page, component, widget,
or modal. It provides a method, decision criteria, and generic examples. The
target project's code, data, and instructions are still required to understand
its domain.

## Operating contract

- Read the target code and project instructions before proposing changes.
- Preserve existing functions, destinations, permissions, data, and business
  rules unless explicitly asked to change them.
- Distinguish observations made in the code or interface from design
  recommendations and behavior that was actually verified.
- Do not invent metrics, user feedback, data, or test results.
- Scale effort to risk: a local adjustment needs focused checks; a journey
  redesign needs state and recovery verification.
- Ask for clarification only when a choice changes a business rule, destination,
  important data, or user intent.

## Workflow

Given this guide and the surface to redesign:

1. Read the page, its components, data sources, actions, and destinations.
   Consult the repository instructions.
2. Establish the user's intent on entry and the expected outcome on exit from
   the actually implemented journey.
3. Inventory all information and actions, including loading, error, empty, and
   unavailable states.
4. Define the hierarchy and treatment of each element using the criteria below.
   Also review the whole composition: repetition between components, visual
   weight, styles, spacing, text, and image framing.
5. Implement in the components that are actually used and verify the complete
   affected journey, not just an isolated component's appearance.
6. Deliver a short explanation of the problem fixed, checks performed, and
   remaining limitations.

## Objective

Make the essential information and next useful action immediately
understandable. A redesign should solve a reading, decision, or journey
problem. Changing colors or rounding cards is not enough.

Simplifying means reducing repetition and visual competition while preserving
useful information, functionality, and accessibility. Existing identity is
the starting point.

## Scope the work

Identify the mode before editing. The mode determines the deliverable and how
far the work may go.

| Mode | When it applies | Deliverable |
| --- | --- | --- |
| Audit | The request is to review, or the cause is not yet known | Ranked findings with evidence; no edits unless implementation was requested |
| Focused fix | One screen or component with an identified problem | Targeted change plus checks on the affected states |
| Journey redesign | The problem spans steps, decisions, or recovery | Revised flow, content, actions, and states |
| Shared pattern change | The same defect repeats across surfaces | Variant or token change with every consumer reviewed |

Do not expand beyond the affected journey. Note adjacent problems instead of
fixing them silently. A visual preference alone is not a defect: tie each
finding to an observable element and a concrete consequence.

## 1. Understand the real problem first

Read the component, its data, and its actual actions in addition to any visual
reference. State briefly:

- What the user just did and what they are looking for now.
- What they need to understand first.
- The most useful action at this moment and the other required destinations.
- What currently gets in the way: repetition, inverted priority, competing
  buttons, ambiguous labels, scattered information, unnecessary steps, or
  overflow.

Example: after completing an activity, the saved-status message and a prominent
ornament took first place, while the actual result and the option to continue
deserved priority.

Do not ask the product owner to redefine every margin, title, or button. Infer
ordinary choices from the journey and code. Clarification is useful when a
choice changes a business rule or when incompatible intents remain possible.

### Expected diagnosis

> The user comes here to **[goal]**. They must first understand
> **[information]**, then be able to **[expected action or consultation]**.
> Today, **[concrete element]** gets in the way because **[consequence]**.
> The redesign will **[hierarchy or journey change]**, while preserving
> **[data, destinations, and constraints to keep]**.

Base the diagnosis on observations: two buttons trigger the same action, a
large heading repeats the content, an amount is separated from its condition,
or an essential action is out of reach. Avoid vague justifications such as
"more modern" or "cleaner." Do not present an unmeasured improvement as
measured.

## 2. Give every piece of information a clear role

Organize reading by importance to the task:

1. **Essential**: the result, content, or decision that justifies the screen.
2. **Useful context**: details needed to interpret the essential information.
3. **Supplement**: comparison, history, or secondary destination.

Use order, size, weight, proximity, and space first. Group related information;
avoid a card, icon, or heading for every value. The same information should not
be announced multiple times without a reason.

For each existing element, decide whether to keep, group, reword, move to an
accessible detail view, or remove as redundant. Information needed for a
decision must remain visible when the decision is made. Do not hide an error,
cost, important condition, or frequent action in a menu just to make the
screen look lighter.

| Question | Possible decision | Condition |
| --- | --- | --- |
| Can the result be understood or a decision made without this element? | Keep it at the first level | Include essential unit, context, and condition |
| Do several elements answer the same question? | Group them | Do not merge distinct concepts |
| Is the same information repeated with the same meaning? | Remove one occurrence | Equal values alone do not prove redundancy |
| Is the detail only consulted occasionally? | Move it to an explicit secondary access point | Its destination and label must make it findable |
| Does the text describe an action that is already clear in context? | Shorten it | Preserve meaning, destination, and necessary distinctions |
| Is the element decorative and distracting? | Reduce its weight or remove it | Preserve useful landmarks and product identity |

For every removal or relocation, explain where the information or function
remains available, or why it was genuinely duplicated. When its domain role is
unclear, keep it until clarified.

## 3. Establish action hierarchy

- When the journey has an obvious next step, give it the primary emphasis.
  Secondary actions remain visible with less visual weight.
- Use short, precise labels such as "Continue," "Edit," "Details," or "Back"
  when the context is sufficient.
- Keep touch targets comfortable even for visually quiet buttons.
- Preserve confirmations and safeguards required for sensitive actions.
- Choose icons for their perceived meaning and provide accessible labels for
  icon-only controls.

A single primary button may suit a confirmation screen, but it is not a
mechanical rule. A browsing page, form, or comparison should follow its own
usage.

## 4. Preserve meaning, identity, and behavior

Keep the relevant colors, type, and conventions of the page or product. A
shared structure can support multiple identities without making every screen
look identical.

Verify the meaning of data before presenting it. A current result, best result,
and ranking are different pieces of information. Do not copy a unit from one
domain to another. Do not invent values to fill a composition or announce
success before confirmation.

Preserve destinations, permissions, business rules, and independent settings.
Wire buttons to real behavior and check loading, error, empty, success,
unavailable, and retry states.

### Reuse existing patterns deliberately

- Prefer the existing component, token, and convention over a new one. Check
  available variants before creating a local override.
- Distinguish a local variant from a global change. Changing a shared component
  requires reviewing every consumer, not only the screen in front of you.
- Do not add a dependency, font, or icon set for a single screen when the
  project already provides an equivalent.
- Keep shared semantics stable: the same role should not look different on
  adjacent screens without a reason.

## 5. Compose a coherent page

Components that are readable in isolation do not guarantee a good page.
Evaluate what their combination produces across content states, not only the
quality of each component.

**Clean does not mean neutral.** Removing noise and repetition does not require
removing colors, illustrations, textures, gradients, or ornaments that give the
interface its identity. Keep what serves context and hierarchy, adjusting
intensity rather than deleting it by default.

**Clarifying hierarchy should not erase visual character.** When the UX
structure works, refine its expression through surfaces, color, typography,
illustration, and context-appropriate details. Reduce excessive effects without
removing all decoration by default.

Keep two complementary questions separate:

- **UX**: Can users understand the information, choices, and consequences?
- **UI**: Do composition, styles, and proportions make that hierarchy visible
  and coherent at screen scale?

| Dimension | Concrete question | Possible adjustment |
| --- | --- | --- |
| Visual weight | What attracts attention, and does its importance justify it? | Reduce competing accents before enlarging the primary action |
| Styles | Do surfaces, buttons, and icons feel like the same interface? | Harmonize borders, shadows, radii, and roles without erasing useful differences |
| Typography | Do headings, values, and explanations have distinct roles? | Establish stable type sizes and weights |
| Spacing | Are related elements closer than unrelated groups? | Adjust internal and section spacing |
| Secondary actions | Does their treatment give them too much presence? | Lighten their appearance while keeping a comfortable target |
| Images | Is the subject recognizable in the actual frame? | Choose ratio, position, and crop for the image |

Coherence does not require a uniform or minimalist style. An illustration or
reward can be expressive; check whether the combined effects fit its role on
the page. A reusable component may need a quieter variant here while retaining
its richer presentation elsewhere.

### Honest self-review

For every critique, identify the observable element, explain its possible
effect, and propose a proportionate adjustment. Distinguish observation,
visual judgment, and behavior that was actually verified. Also name what works
and should be preserved.

Empty space is not automatically wasteful; a cropped image is not automatically
badly framed; a style difference may be intentional. A screenshot permits
reviewing visible composition, not concluding about every state or interaction.

## 6. Generic example: a result screen

Situation: an activity has just ended. The user wants to know the result of this
attempt, compare it with their best result, then try again or view details. A
general ranking does not mean that the current attempt is a new record.

The old presentation emphasized a large trophy, a status message, and a
position, with the result shown only afterward. Statistics were secondary and
several actions competed with one another. The problem was visual priority
given to status and rank instead of the immediate result and next step.

Example presentation using illustrative values:

```text
                    ACTIVITY COMPLETE       <- quiet status
                           333               <- dominant information
                          points              <- unit beside the result

             158 units · 7 steps · 11.57 s   <- attempt measurements

             Overall rank · #1   Best: 3379 points

                    [ Try again ]            <- only filled button
                 Details          Home       <- secondary actions
```

The result and its unit form the first group. Attempt measurements form the
second. Rank and best result form a less prominent comparison group. Lines can
wrap on a narrow screen; reading order must not depend on a fixed width.

The numbers are presentation examples, not hard-coded data. Metrics and units
must come from the real domain. A repeated number may be omitted from a compact
summary, but a useful distinction must remain visible when it matters to the
journey. A tie is not a new record. A completion status must not claim that
data was saved successfully while saving is still pending or has failed.

Actions must trigger their actual destinations: restart the activity, open
details, and return home. The work includes wiring these actions and their
states.

### Applying the method to other pages

These hypothetical situations illustrate the reasoning:

| Situation | Problem to solve | Application |
| --- | --- | --- |
| Order confirmation | Amount, fees, and conditions are scattered | Group what supports the decision and show the total before confirmation |
| Profile form | Repeated headings and a hard-to-find save action | Group related fields, prioritize saving, and keep errors beside their fields |
| Event list | Dominant badges, hard-to-compare dates, ambiguous sorting | Prioritize information used to choose and make sort and filters understandable |
| Audio settings | One global toggle hides independent settings | Group controls without merging them and state precisely what each one enables |

A reading page may have no dominant button. A comparison page may give equal
importance to several options. Do not turn every screen into a central result
followed by a large button.

## 7. Verify and deliver

Check real actions and changed states, small screens, enlarged text, long
labels, and large values. Prefer wrapping or controlled scrolling to shrinking
text excessively. Keep actions reachable, labels accessible, and contrast
readable.

Run the static analysis and focused functional checks appropriate to the work.
Follow the target project's instructions and test tools; do not recreate a
removed legacy test suite without an explicit request.

Match checks to the change:

| Change | Checks |
| --- | --- |
| Element removed or moved | Information and function remain reachable; decision data is still visible when needed |
| Action relabeled or rewired | Destination and side effects are correct; guards and confirmations still apply |
| Layout recomposed | Narrow screen, long labels, large values, enlarged text |
| State touched | Loading, error, empty, partial, retry, success |
| Shared component or token changed | Every consumer reviewed in its own content states |

At delivery, briefly explain the fixed problem, the new reading and action
priority, the checks performed, and their limitations.

## Reference checklists

Load only the files relevant to the task:

| File | Use it when |
| --- | --- |
| `references/states.md` | The surface loads data, performs actions, or can fail |
| `references/accessibility.md` | Any interactive redesign |
| `references/copy.md` | Labels, errors, values, or units are edited |
| `references/anti-patterns.md` | Auditing, or reviewing your own proposal |

## Completion criteria

- The first level answers the user's intent and is distinct from supplements
  without making them unreadable.
- Every removed or moved piece of information is justified, and decision-critical
  data remains available at the right time.
- Actions have understandable labels and trigger the expected destinations or
  operations, with their real safeguards and states.
- The solution remains usable with relevant formats and text sizes; it does not
  depend on tiny text or hidden actions.
- The result respects screen identity and domain constraints.
- Combined components maintain coherent visual hierarchy, and repetition between
  components has been reviewed across content states.
- The delivery note distinguishes completed checks from unverified points.

A redesign limited to a new palette, rounded corners, or unjustified removal of
information does not satisfy this method.
