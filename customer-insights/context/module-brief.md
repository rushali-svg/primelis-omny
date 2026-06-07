# Customer Insights — Module Overview
**Project:** Omny
**Module:** Customer Insights
**Purpose:** Orientation document — read this before the detailed brief or any feature ticket

---

## Where This Module Lives in Omny

Omny's sidebar is a flat icon-based navigation with labelled items. Customer Insights is a **top-level module** — it is not nested under any parent section and has no sub-items in the sidebar. It sits alongside other top-level modules: Dashboard, Products, Inventory, Advertising, Profit and Loss, and Market Insights.

```
Omny sidebar (top to bottom)
├── Dashboard
├── Products
├── Inventory
├── Advertising
├── Profit and Loss
├── Market Insights
└── Customer Insights  ← this module (no sub-navigation)
```

Clicking Customer Insights in the sidebar takes the user directly into the module. The internal tab navigation (Dashboard, Cohort, Cohort per ASIN) lives inside the module itself — it is not reflected in the sidebar hierarchy.

This placement matters. Most modules in Omny are focused on products, stock, or advertising spend. Customer Insights is the only module focused on the customer as a long-term entity — what happens after the sale, whether they came back, and how much value they generated over time.

---

## What Customer Insights Is For

Most Amazon seller tools track the order. Customer Insights tracks the customer.

It answers a different set of questions than the rest of Omny:

- Are we acquiring new customers at a healthy rate?
- Are existing customers coming back?
- Which customers are the most valuable over time?
- Are we losing customers faster than we're gaining them?

None of these questions can be answered by looking at orders or campaigns alone. You need to follow the same person across multiple purchases, over multiple months. That is what this module does.

---

## Who Uses It

**Brand managers, e-commerce directors, and analytics leads.** These are not the same people doing daily PPC bid management. They are looking at the business one level up — evaluating health, identifying patterns, and informing budget and strategy decisions for the next quarter.

Their sessions in this module are typically weekly or monthly health checks, not daily operational tasks. They need to scan quickly and read trends confidently. They are not exploring data — they are looking for confirmation or warning signals.

---

## Tab Structure

Customer Insights has three tabs inside the module. Two are fully deployed. The third is the next iteration — context and briefs for it exist in the repo as meeting transcripts and supporting docs.

```
Customer Insights
├── Dashboard        ← deployed, live
├── Cohort           ← deployed, live (formerly named "LTV")
└── Cohort per ASIN  ← next to be designed and built; repo docs exist
```

The first two tabs are **complementary, not redundant.** They answer different questions and are typically used in sequence within the same session.

| | Dashboard | Cohort |
|---|---|---|
| **Question it answers** | How is the full customer base doing right now? | How have specific groups of customers behaved over time? |
| **Time orientation** | Present — rolling monthly or weekly view | Longitudinal — tracks groups from their first purchase onwards |
| **Who it pools** | All customers together | Customers grouped by acquisition month/quarter |
| **How it's read** | Row = one time period | Row = one cohort (acquisition month) |
| **Primary use** | Health check, trend monitoring | Retention analysis, LTV comparison across cohorts |

The **Cohort per ASIN** tab will extend the cohort logic down to the product level — allowing users to understand retention and LTV not just by when customers were acquired, but by which product they first bought. Design work for this tab is the active next step. Refer to the meeting transcripts and feature docs in the repo for context before starting iterations.

---

## How a User Moves Through the Module

A typical session flows like this:

1. User lands on **Dashboard** and scans the Evolution table for anything unusual — churn spiking, acquisition slowing, engagement dropping
2. They spot something — say, repurchase rate has been declining for several months
3. They switch to the **Cohort tab** to understand when this started — is it affecting all cohorts equally, or did a specific acquisition period produce weaker customers?
4. The heatmap reveals that cohorts from a promotional campaign period (e.g. June–August 2025) have noticeably lower values at the 6-month offset compared to surrounding cohorts
5. They take this finding into a planning conversation — those customers were acquired cheaply but aren't returning, which changes the economics of running similar promotions

This is the intended flow. **Dashboard surfaces the signal. Cohort tab explains it.** Design and copy decisions in both tabs should support this sequence.

---

## Global UI Elements (Shared Across Tabs)

These elements persist regardless of which tab is active:

- **All Sellers** filter — top left
- **All Marketplaces** filter — top left
- **All Products** filter — top left (Dashboard only; not visible on Cohort)
- **Currency selector** — top right (€ EUR by default)
- **Tab bar** — Dashboard | Cohort | Cohort per ASIN — horizontal, below the module header

Each tab has its own internal toolbar for controls specific to that view (granularity, comparison period, metric selector, etc.). These are tab-level, not global.

---

## What a Cohort Is — Plain Language

A cohort is a group of customers who made their **first-ever purchase in the same month** (or quarter, depending on the selected granularity).

For example:
- The **January 2026 cohort** = every customer who bought for the first time in January 2026
- The **March 2025 cohort** = every customer who bought for the first time in March 2025

In the Cohort tab heatmap, **each row is one cohort.** The columns to the right show what happened to that group over time — at 0, 3, 6, and 12 months after their first purchase. The metric shown in those cells (LTV, Repurchase rate, etc.) is controlled by the metric dropdown in the toolbar.

Reading a row left to right = watching that group of customers evolve from the day they first bought.

Reading a column top to bottom = comparing how different acquisition periods performed at the same point in their lifecycle.

Empty cells in the heatmap are not missing data — they are future months that simply haven't happened yet for that cohort.

---

## The Relationship Between the Two Live Tabs — Explicitly

These tabs are designed to be used together, but they are structurally independent:

- **Dashboard** shows all customers pooled together. You cannot separate by acquisition period here. It is optimised for speed — one glance should tell you if something is wrong.
- **Cohort** shows customers separated by when they first bought. You cannot see aggregate health here. It is optimised for diagnosis — once you know something is wrong, this is where you find out why.

A user who only uses Dashboard knows that churn is up. A user who also uses Cohort knows that churn is up because customers from Q3 2025 never came back after their first purchase. That is a meaningfully different level of understanding, and it changes the decision made.

---

## Key Things to Know Before Designing for This Module

- Customer Insights is a **flat sidebar entry** — no nested sidebar items. The tab navigation exists only inside the module.
- The tab formerly called "LTV" is now called **"Cohort"** — this rename applies everywhere: design files, copy, code, documentation, and any AI prompts referencing the tab.
- The **Cohort per ASIN tab is the active design frontier** — the two deployed tabs are stable; new iteration work should focus here. Repo context docs exist for this tab.
- The **heatmap is the most technically complex component** in the module — inline bar alignment within table cells is expensive to build and has caused implementation issues; avoid adding new inline visuals to table cells unless critical.
- Both tabs share the same design language and tokens as the rest of Omny — no custom visual system.
- The **Cohort tab metric selector** controls what is shown in the heatmap offset columns; its placement relative to the table is an open design question (the current toolbar position creates a perceived disconnect from the columns it controls).
- **Tooltip copy for all five cohort metrics has been confirmed** — treat as final unless explicitly flagged for revision (see the detailed brief for copy).
- The **LTV Averages cards** at the top of the Cohort tab are out of scope for the current iteration — they require predictive model integration and are tracked in a separate ticket.
