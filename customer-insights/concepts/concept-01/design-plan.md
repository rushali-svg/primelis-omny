# Cohort per ASIN - Figma Shell + Prototype Plan

## Summary
Rebuild the Customer Insights `Cohort per ASIN` shell inside the linked Figma file so it matches the existing Omny structure, then add a clickable prototype that incorporates the `Product Role` concept and header tooltip behavior.

## Key Changes
- Rebuild the shell from the linked Figma source instead of using the HTML mockup as the reference.
- Keep the global Omny UI elements in the same layout as the source Figma file.
- Preserve the module-level shell patterns from `module-brief.md`:
  - seller and marketplace controls at top left
  - currency selector at top right
  - tab bar under the module header
- Update the table to include the `Product Role` column and keep the existing `LTV Breakdown` structure intact.
- Preserve the screenshot’s non-negotiable table data and density.
- Move the `Product Role` legend into the column header tooltip pattern.
- Remove the `LTV Breakdown` legend from the visible header and turn it into the same tooltip-style treatment.
- Add prototype interactions so the screen can be reviewed interactively.
- Keep the `Product Role` badge list available as a tooltip, not as a separate visible legend block above the table.

## Assumptions
- The Figma file is the source of truth for shell structure and spacing.
- The screenshot is still the visual source of truth for table hierarchy and row density.
- Figtree is the only brand font required for this pass.
- The brand accent color `#FEC9AA` should shape the shell, callouts, and active states without overriding the role colors.
- The concept docs remain the source of truth for the `Product Role` meanings, badge colors, and tooltip copy.
- A future role filter chip is still out of scope for this iteration unless explicitly added later.

## Review Checks
- The global shell visually matches the linked Figma file more closely than the HTML mockup.
- The `Product Role` tooltip lives in the header, not as a standalone legend block above the table.
- The `LTV Breakdown` header no longer carries the legend block.
- Prototype interactions are present for the header tooltip / review flow.
- The resulting layout still reads like Customer Insights, not a generic dashboard shell.
