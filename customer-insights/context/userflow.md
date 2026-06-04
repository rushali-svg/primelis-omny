# Customer Insights Userflow

## Primary User Journey
1. The user opens Customer Insights for a specific seller or account.
2. The user lands on a surface such as LTV, customer breakdown, or LTV per ASIN.
3. The user reads the primary KPI or summary for the selected surface.
4. The user checks whether the metric is valid for the current account and history window.
5. The user reviews supporting breakdowns such as purchase, entry, repeat, and cross-repeat.
6. If the data is missing or incomplete, the user reads the explanation instead of assuming the view is broken.
7. The user may switch surfaces to compare different aspects of the same account.

## Secondary User Flow: Insufficient History
1. The user opens a Customer Insights view.
2. The system detects that the account does not have enough history for a 12-month rolling calculation.
3. The KPI is hidden or withheld rather than shown as a misleading placeholder.
4. The user sees a message explaining that the metric requires more history.

## Secondary User Flow: Vendor or Data-Access Case
1. The user opens the view for a vendor account or an account with missing data access.
2. The system identifies the condition using account metadata or data availability checks.
3. The view explains whether the issue is vendor status, missing purchase, or disconnected data.
4. The user can understand whether the issue is fixable by changing account context or by waiting for a data connection.

## Secondary User Flow: Partial Coverage
1. The user opens a surface where data begins only after a later date.
2. The UI surfaces the coverage window so the user understands the visible range.
3. The user can still interpret the available values without assuming the entire history is present.

## Design Behavior Rules
- Do not hide missing-data states behind empty cells with no explanation.
- Do not expose undefined KPI meanings as if they were final product decisions.
- Keep the surface readable even when data conditions differ across accounts.
