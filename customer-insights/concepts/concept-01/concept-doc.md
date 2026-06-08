# Product Role Column — Feature Concept
**Module:** Customer Insights → Cohort per ASIN tab
**Feature:** Product Role tag column
**Status:** Concept — ready for UX iteration in Cursor

---

## What This Feature Is

Product Role is a computed tag column added to the LTV per ASIN table. Each ASIN receives one tag that describes its commercial behaviour — not based on raw revenue or volume, but on the **relationship between its three LTV components**: 1st Purchase, Entry Repeat, and Cross Repeat.

The goal is to turn a table of numbers into a decision surface. A user scanning the Product Role column should be able to answer in seconds — which ASINs should I invest acquisition spend in, which are retention risks, which are opening my catalog to new buyers — without reading bar proportions or doing mental arithmetic.

The column sits **to the right of the LTV/1st multiplier column** and before the LTV Breakdown bar. It is a non-editable, system-computed field. It does not replace the breakdown bar — it annotates it with a human-readable interpretation.

---

## The Five Tags

### 🚀 Entry Driver
**One-line:** High acquisition volume, low post-purchase engagement.

This ASIN brings in a lot of first-time customers but most of the value stops at the first order. Customers either don't return, or they return to other products rather than this one. High volume without strong retention.

**When to use it:** When an ASIN is above the catalog median in Entry Customers AND the combined Entry Repeat + Cross Repeat makes up less than 25% of total LTV.

**Strategic meaning:** Good for awareness and top-of-funnel acquisition campaigns. Not reliable for loyalty spend. Worth investigating whether the first purchase experience is preventing return.

---

### 🔁 Loyalty Builder
**One-line:** Customers keep buying this product again and again.

Entry Repeat is the dominant component — customers who come in through this ASIN buy it repeatedly. The value is concentrated in the same product re-purchasing rather than spreading across the catalog. Strong for Subscribe & Save candidates.

**When to use it:** When Entry Repeat / Total LTV is above 40% AND Cross Repeat is relatively low (below 20% of total LTV).

**Strategic meaning:** Strong candidate for loyalty campaigns and Subscribe & Save promotion. May not contribute much to catalog expansion but anchors repeat purchase behaviour. Protect and invest in these.

---

### 🌐 Catalog Gateway
**One-line:** Customers enter here and go on to explore the full catalog.

Cross Repeat is the dominant post-first-purchase component. Customers who buy this ASIN first don't necessarily buy it again, but they go on to purchase other products in the catalog. This is the most strategically valuable entry product type for brand health — it acquires and opens.

**When to use it:** When Cross Repeat / Total LTV is above 30% AND Cross Repeat > Entry Repeat.

**Strategic meaning:** The most valuable entry product type for catalog-wide LTV. Acquisition investment here pays off across the entire range, not just this ASIN. Worth prioritising in DSP and prospecting campaigns.

---

### ⚠️ Standalone
**One-line:** Customers buy this once and don't engage further.

Low multiplier and low cross repeat. Customers buy this product once and don't return to it or to anything else in the catalog. Could be a gift product, a seasonal one-time need, a category that doesn't have natural repeat demand, or a product with satisfaction issues.

**When to use it:** When the overall multiplier is below 1.1x AND Cross Repeat / Total LTV is below 15%.

**Strategic meaning:** Investigate before investing. If this is intentional (e.g. a seasonal gift item) the tag is expected. If it's a core product, it signals a retention problem worth diagnosing — check reviews, fulfilment, and whether buyers are returning to competitors.

---

### ⭐ High Value
**One-line:** Strong multiplier, healthy repeat and cross-sell behaviour.

This ASIN does everything well. It acquires customers, retains them, and generates cross-category revenue. Both Entry Repeat and Cross Repeat are above minimum thresholds and the overall multiplier is strong. These are rare and should be protected.

**When to use it:** When the overall multiplier is above the top 25% of catalog AND both Entry Repeat > 15% of total LTV AND Cross Repeat > 15% of total LTV.

**Strategic meaning:** These are the crown jewels of the catalog. Investment here generates compounding returns. They should be the first priority for both acquisition and loyalty spend.

---

## Computation Logic

All thresholds are **relative to the seller's own catalog**, not hardcoded absolutes. This ensures tags are meaningful whether a catalog has 8 ASINs or 800.

```
For each ASIN, compute:

  entry_share     = Entry Customers / median(all ASINs Entry Customers)
  repeat_share    = Entry Repeat / Total LTV
  cross_share     = Cross Repeat / Total LTV
  multiplier      = Total LTV / 1st Purchase LTV

Tag assignment (in priority order):

  HIGH VALUE      → multiplier in top 25th percentile
                    AND repeat_share > 0.15
                    AND cross_share > 0.15

  CATALOG GATEWAY → cross_share > 0.30
                    AND cross_share > repeat_share

  LOYALTY BUILDER → repeat_share > 0.40
                    AND cross_share < 0.20

  ENTRY DRIVER    → entry_share above catalog median
                    AND (repeat_share + cross_share) < 0.25

  STANDALONE      → multiplier < 1.1
                    AND cross_share < 0.15

  NO TAG          → insufficient data history
                    (do not show tag, show tooltip explaining why)
```

Priority order matters — an ASIN that qualifies for both High Value and Catalog Gateway should receive High Value. Tags are mutually exclusive; each ASIN receives exactly one.

---

## Visual Representation

### Badge design

Badges should feel like status tags, not decorative labels. The reference is Linear's issue labels and ClickUp's priority tags — small, dense, pill-shaped chips with a left-side icon and short text. They should be **immediately scannable** and **differentiable by color** without reading the text.

Each badge uses a distinct color with a tinted background (low saturation fill, higher saturation border and text) so they read clearly on a white table row without being visually loud. The icon sits to the left of the label text inside the pill.

| Tag | Icon | Color | Background | Rationale |
|-----|------|-------|------------|-----------|
| Entry Driver | 🚀 | Indigo | Indigo-50 | Indigo signals momentum and acquisition — forward-moving, top-of-funnel energy |
| Loyalty Builder | 🔁 | Teal | Teal-50 | Teal signals retention and continuity — calm, steady, reliable |
| Catalog Gateway | 🌐 | Violet | Violet-50 | Violet signals breadth and connection — opens outward to the full catalog |
| Standalone | ⚠️ | Amber | Amber-50 | Amber signals caution without alarm — worth attention, not a hard error |
| High Value | ⭐ | Gold / Warm Yellow | Yellow-50 | Gold signals premium status — highest tier, visually distinct from all others |

The badge height should match the table row density — at 36px row height, badges should be approximately 20px tall with 6px horizontal padding. Font size 11px, medium weight. All caps label text is acceptable for scannability but sentence case is preferred for readability.

**Why color-coded and not just text labels?**
Users scanning a long ASIN table will not read every badge word by word. Color allows pattern recognition — a user can glance at the Product Role column and instantly see "mostly teal with a few amber rows" and understand the catalog health without reading. This is the same principle as traffic lights or Linear's priority colors. The icon reinforces the color for accessibility and for users who have learned the system.

---

## Education Layer

### 1. Column header legend (reusing the Signal sponsored ads tooltip pattern)

The column header "Product Role" has a small **(i)** icon to its right. Clicking or hovering the (i) opens a **popover legend panel** — not a simple tooltip but a small structured card, reusing the same pattern as the Signal Sponsored Ads page legend.

The panel shows:

```
┌─────────────────────────────────────────────────────┐
│  Product Role                                        │
│  Tags are computed from each ASIN's LTV composition  │
│                                                       │
│  🚀 Entry Driver      High volume, low repeat         │
│  🔁 Loyalty Builder   Strong same-product return      │
│  🌐 Catalog Gateway   Drives cross-catalog buying     │
│  ⚠️  Standalone        Low repeat, low cross-sell     │
│  ⭐ High Value        Strong multiplier + both types  │
│                                                       │
│  Thresholds are relative to your catalog.             │
└─────────────────────────────────────────────────────┘
```

This panel is **dismissible by clicking anywhere outside** it. It is not a modal — it floats above the table. It should feel like a reference card, not an interruption.

**Why this pattern and not inline help text?**
The Signal legend pattern works because it is opt-in — users who already know the system never see it unless they choose to. It collapses all five definitions into one scannable panel rather than scattering explanations across the UI. It also normalises the interaction: users who have seen it on the Signal tab will already know how to use it here.

---

### 2. Per-badge hover tooltip (contextual, data-driven)

Each badge in the table cells gets a hover tooltip. The tooltip does **not** repeat the generic tag definition — it explains why *this specific ASIN* received this tag, using its actual numbers.

Format:

```
┌──────────────────────────────────────────────────────┐
│  🌐 Catalog Gateway                                   │
│  Cross Repeat makes up 34% of this ASIN's total LTV,  │
│  which is the dominant value driver after first        │
│  purchase. Cross Repeat (34%) > Entry Repeat (12%).   │
└──────────────────────────────────────────────────────┘
```

Another example:

```
┌──────────────────────────────────────────────────────┐
│  ⚠️  Standalone                                       │
│  LTV multiplier is 1.08x — below the catalog          │
│  threshold. Cross Repeat accounts for only 9%         │
│  of total LTV.                                        │
└──────────────────────────────────────────────────────┘
```

**Why data-specific and not generic?**
A generic tooltip ("Catalog Gateway: customers go on to buy other products") tells the user what the tag means in theory but doesn't connect it to this ASIN's evidence. Showing the actual numbers closes that gap — the user sees the tag and immediately sees why it was assigned, without having to look left at the breakdown bar. It also builds trust in the system: the tag doesn't feel like a black box.

**Tooltip specs:**
- Trigger: hover on the badge
- Delay: 200ms (avoids accidental triggers while scanning)
- Max width: 280px
- Position: above the badge, centered, with a small arrow pointing down
- Dismisses on mouse-out

---

### 3. First-visit inline nudge (progressive disclosure)

On first visit to the Cohort per ASIN tab, a single dismissible inline banner appears **just above the table**, below the toolbar:

> "Product Role tags summarise each ASIN's LTV behaviour. Hover any tag or click (i) in the column header to learn more."

- One line, light grey background, small close icon on the right
- Dismissed permanently once closed (stored in user preferences)
- Does not reappear on subsequent visits
- Not a modal, not an overlay — stays in the page flow

**Why not a full onboarding flow?**
The tags are not complex enough to warrant a tutorial. The nudge just tells the user the system exists and points to where the explanation lives. Users who are curious will find the legend; users who aren't won't be blocked.

---

## What This Enables Beyond Reading

Once the Product Role column exists, it unlocks a second-order interaction: **filtering the table by role**.

A filter chip above the table — "Show: All · Entry Driver · Loyalty Builder · Catalog Gateway · Standalone · High Value" — lets users reduce the table to only the ASINs that are relevant to a specific decision. A user planning a loyalty campaign can filter to Loyalty Builder and Catalog Gateway only. A user doing a retention audit can filter to Standalone.

This is not in scope for the first iteration but should be designed with this future state in mind. The badge component and the column structure should be built to support filtering without structural changes.

---

## Open Questions Before Iteration

- Are the five tags the right set, or should Standalone be split into "Low Demand" (structural) and "At Risk" (behavioural) to help users act differently on each?
- What happens to an ASIN that is borderline between two tags — is there a confidence indicator, or is the tag always shown as definitive?
- Should the tag be shown on ASINs with very low entry customer counts (e.g. below 50) where the percentages may not be statistically meaningful?
- What is the minimum data history required before a tag is computed — is 3 months of data sufficient or does it require the full 12-month rolling window?

