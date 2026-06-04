# Customer Insights Sitemap

## Feature Structure
Customer Insights is a family of related internal analytics views centered on customer value, customer mix, and data reliability. The feature should be organized as a small set of tightly related surfaces rather than a single overloaded dashboard.

## Main Surfaces
- LTV tab
- Customer breakdown / cohort tab
- LTV per ASIN tab

## LTV per ASIN Tab Structure
- Header controls
  - Seller selector
  - Currency selector
  - Metric toggle: Revenue / Margin
- Table summary
  - Result count, such as `16 ASINs`
- Table columns
  - ASIN
  - Product Name
  - Entry Customers
  - Total
  - LTV / 1st
  - LTV Breakdown
- Breakdown legend
  - 1st Purchase
  - Entry Repeat
  - Cross Repeat
- Row rendering
  - Stacked bar visualizes the breakdown composition
  - Currency values are shown inside the bar segments where space allows
  - Rows are ordered as a comparison list across ASINs

## Shared Supporting States
- Account selector / seller context
- Data availability state
- Insufficient history state
- Vendor detection state
- Missing connection or unpurchased data state
- Coverage-window explanation state

## Information Hierarchy
1. Primary metric or summary for the selected view
2. Breakdown of customer composition or value drivers
3. Context explaining whether the metric is complete, partial, or unavailable
4. Supporting detail for the data window or account type

## Navigation Model
- Users enter Customer Insights through the feature entry point.
- Users choose the relevant surface from the feature tabs.
- Each surface presents a related view of the same underlying account context.
- When the data cannot be shown normally, the view should stay navigable and explain the reason.

## Visibility Rules
- The UI should not depend on file movement or hidden states to explain data conditions.
- Missing or incomplete data should be visible in the view itself.
- Repeated explanations should be consistent across all Customer Insights surfaces.
- Currency and metric mode changes should update the table display without changing the feature structure.

## Related Concept Boundaries
- The feature is not a general reporting dashboard.
- The feature is not a backend data exploration tool.
- The feature is focused on interpretation, not raw data inspection.
