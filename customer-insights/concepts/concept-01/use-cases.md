# Product Role Column Use Cases

## 1. Scan the catalog for strategy
The user wants a fast read on which ASINs are acquisition drivers, retention anchors, or low-value standalone items. The `Product Role` column should turn the table into a decision surface rather than a purely numerical report.

## 2. Understand why a tag was assigned
The user hovers a badge on a specific row and wants to know why the system assigned that tag. The tooltip should cite the ASIN's actual evidence so the user can trust the classification.

## 3. Learn the tag system without interruption
The user is unfamiliar with the tag vocabulary and needs a quick explanation without leaving the table. The header legend should provide the full system in a compact, opt-in popover.

## 4. Confirm the table still makes sense
The user compares the tag with the existing `LTV Breakdown` bar to make sure the new label matches the visual composition. The concept should annotate the row, not compete with it.

## 5. Handle first-time exposure
The user visits the tab for the first time and needs a light explanation of what the badges mean. A dismissible inline nudge should point them to hover and legend help without adding a tutorial flow.

## 6. Review low-data or borderline cases
The user encounters ASINs with too little history or unclear classification. The system should either withhold the tag or explain the limitation rather than presenting a misleading guess.

## 7. Prepare for future filtering
The user may later want to isolate only `Loyalty Builder` or `Standalone` ASINs. That future action should be anticipated in the structure, even if it is not shipped in this concept.

## Edge Cases
- If the ASIN does not have enough history, do not show a confident tag.
- If two rules could apply, use the priority order from the concept doc.
- If the badge color is visible but the user does not know the meaning, the legend must remain available.
- If the row is very small or visually dense, the badge should still remain legible and scannable.
