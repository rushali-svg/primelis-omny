# Customer Insights Use Cases and Edge Cases

## Purpose
This document captures the concrete scenarios and failure states that Elodie described for Customer Insights. It sits alongside the feature brief, sitemap, and userflow so later concept and iteration work can refer to specific situations instead of re-reading the transcript.

## Use Cases

### 1. View customer value in LTV
The user opens the LTV tab to understand customer value over the relevant history window. The view should present revenue and margin where they are meaningful and make it clear how the KPI is being computed.

### 2. Inspect customer composition
The user opens the customer breakdown view to understand how the customer base is split across purchase, entry, repeat, and cross-repeat behavior. The surface should help the user see not only totals, but also the mix behind those totals.

### 3. Review LTV per ASIN
The user opens the `LTV per ASIN` tab to compare products and understand which ASINs contribute most to customer value. The view should support product-level interpretation rather than forcing the user to infer it from raw numbers alone.

### 4. Switch between Customer Insights surfaces
The user moves between LTV, customer breakdown, and LTV per ASIN to compare different perspectives on the same account. The experience should keep the account context stable so the user can compare surfaces without re-orienting themselves.

### 5. Read customer value by account type
The user looks at a seller or vendor account and needs the UI to adapt to that account context. The feature should make the account type understandable enough that the user can interpret the numbers correctly.

### 6. Understand the history window behind a KPI
The user wants to know what time range is actually being used for a metric. When the KPI depends on 12 rolling months or another explicit history window, the UI should make that dependency visible.

### 7. Choose the correct metric mode
The user switches between Revenue and Margin to compare the ASIN table in different business contexts. The view should clearly reflect the selected metric mode without changing the meaning of the table structure.

### 8. Choose the correct currency
The user changes currency so that the ASIN table matches the account’s reporting context. The view should present values in the selected currency while preserving the underlying ranking and composition logic.

### 9. Compare products by breakdown
The user reads the stacked `LTV Breakdown` bars to understand whether ASIN value comes mostly from first purchase, entry repeat, or cross repeat. The table should make the comparison easy to scan across many ASINs.

## Edge Cases

### 1. Not enough history for a metric
If an account does not have enough history for a 12-month rolling calculation, the KPI should not be shown as if it were valid. The UI should withhold the metric and explain that the history window is too short.

### 2. Vendor account detection
If the account is a vendor, the feature should detect that from the account name or account metadata and use that context in the explanation. This is important because some data behavior changes based on account type.

### 3. Disconnected or unpurchased data
If the metric is unavailable because the relevant dataset is not connected or has not been purchased, the UI should say so. The user should not have to guess whether the problem is missing history, missing access, or a real zero value.

### 4. Partial coverage window
If data only becomes available from a later date, the view should surface the coverage window so the user understands that the metric is incomplete rather than empty. The UI should make the start date or visible range clear enough to avoid misinterpretation.

### 5. Unresolved KPI naming
If a KPI appears in the transcript but its meaning is still unclear, such as “LTP,” the document should treat it as unresolved. It should be called out as a placeholder or open definition, not silently normalized into a final product term.

### 6. Visible data but not meaningful data
If a value is technically available but does not make sense in the current context, the UI should explain why it is not being emphasized. The goal is to prevent misleading interpretation when the data exists but is not valid for the current view.

### 7. Small or narrow breakdown segments
If one of the stacked breakdown segments is very small, the label may not fit inside the bar. The UI should still preserve the segment and avoid implying that the category is absent.

### 8. Metric mode changes perception
If the user switches from Revenue to Margin, the row order and comparison structure should remain understandable. The UI should not suggest that the same ASIN has become a different product story just because the metric mode changed.

### 9. Currency conversion should not alter structure
If the selected currency changes, the table values should update without changing the table meaning or the breakdown logic. The user should not lose row-to-row comparability when switching currencies.

## Design Rules
- Prefer explanation over silent absence.
- Do not present missing history as a normal empty state.
- Keep account context visible wherever it affects interpretation.
- Reuse the same language for data states across all Customer Insights surfaces.
- Treat `LTV per ASIN` as a stable tab name, not a placeholder.
