# Product Role Column Userflow

## Primary User Flow
1. The user opens `Customer Insights` and navigates to the `Cohort per ASIN` tab.
2. The user scans the table and sees the new `Product Role` column next to `LTV/1st`.
3. If it is the user's first visit, a subtle inline nudge explains that the badges summarize each ASIN's LTV behavior.
4. The user hovers a badge to see why that specific ASIN received its tag.
5. The user opens the column header info popover if they want the full tag legend and threshold explanation.
6. The user compares the role tag with the existing breakdown bar to validate the interpretation.

## Secondary Flow: Understand A Tag
1. The user focuses on a single ASIN row.
2. The badge tooltip explains the actual evidence behind the tag assignment.
3. The user uses that explanation to decide whether the product should be promoted for acquisition, retention, or catalog expansion.

## Secondary Flow: Learn The System
1. The user clicks or hovers the `Product Role` header info icon.
2. The legend panel shows all five tags and their plain-language meanings.
3. The user closes the panel and continues scanning the table without leaving the page flow.

## Future Flow Not In Scope
1. The user filters the table by role.
2. The table narrows to one or more tag groups.
3. This flow is intentionally deferred until after the first concept iteration.

## Flow Rules
- Keep the table usable even if the user never opens the legend.
- Never force a modal onboarding flow for this feature.
- Do not make the user infer the tag meaning only from color.
- Preserve the existing table reading order and row density.
