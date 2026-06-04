# Customer Insights Global Brief

## Problem Statement
Customer Insights needs a clear, trustworthy set of views that help Ops and internal users understand customer value, customer mix, and the limits of the underlying data. The transcript shows that the team already has multiple related surfaces in play, but the current challenge is not only visual design: it is making the data meaning legible, especially when data is missing, incomplete, or only partially available.

## Feature Goal
Create a Customer Insights experience that:
- explains customer value with familiar commercial metrics
- makes customer composition visible through breakdowns such as purchase, entry, repeat, and cross-repeat
- distinguishes real zeros from unavailable or insufficient data
- gives users confidence in why a metric is shown, hidden, or flagged

## Intended Surfaces
This brief covers the Customer Insights work referenced by Elodie in the transcript:
- LTV tab
- cohort or customer breakdown view
- LTV per ASIN tab

The transcript also references a previously started table and a seller-based view used by the Ops team. For this setup, those are treated as part of the same Customer Insights family rather than separate features. The screenshot makes the LTV per ASIN tab concrete: it is a seller-scoped, currency-aware comparison table over ASINs with a revenue/margin toggle and a breakdown by customer-value source.

## Core Requirements
- Show revenue and margin where they are meaningful to the view.
- Keep the tab label as `LTV per ASIN`.
- Expose seller, currency, and metric mode controls in the tab header.
- Show the ASIN comparison table with entry customers, total, `LTV / 1st`, and the stacked `LTV Breakdown`.
- Preserve the 12 rolling month logic where it is required for the KPI.
- Hide KPIs when the required history is not available instead of showing misleading placeholders.
- Detect and explain vendor accounts using account-level information.
- Explain missing data when it is caused by a disconnected or unpurchased dataset.
- Show the available coverage window when data starts only after a later date.
- Keep unresolved metric names, such as the transcript’s “LTP” KPI, explicitly unresolved until product meaning is confirmed.

## Data Interpretation Rules
- If there is not enough history, the KPI is not considered available.
- If a value exists but is only valid for a specific period window, the UI should say so.
- If the issue is account type, history coverage, or data access, the UI should explain which one it is.
- If the data is valid but not complete for the current view, the UI should still give the user enough context to understand why.
- Switching between revenue and margin changes the displayed metric mode, but not the underlying ASIN comparison structure.
- Currency affects display and comparison formatting, not whether the row is valid.

## In Scope
- Defining the overall Customer Insights information model
- Establishing the main data states and empty states
- Clarifying the customer breakdown and LTV-related views
- Capturing product rules that later iteration plans must follow

## Out of Scope
- Final visual design decisions
- Detailed interaction patterns for filters and controls
- Implementation specifics for backend data retrieval
- The AI-assisted workflow discussion at the end of the transcript

## Success Criteria
- A new iteration can start from this brief without re-reading the transcript.
- Future plans can refer to explicit rules instead of reinterpreting the raw conversation.
- Data availability states are defined clearly enough to guide consistent UI behavior.
- The main Customer Insights surfaces are framed as one connected feature family.

## Open Questions
- What exactly does the KPI labeled “LTP” mean?
- Should the user-facing language be optimized primarily for Ops, or for a broader internal audience?
- What should the final naming be for the “cohort” or “customer breakdown” surface if product terminology changes later?
