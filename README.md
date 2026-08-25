# Data Consent & Lineage Dashboard

A working prototype of an internal audit tool for AI platform teams: it tracks every data source feeding an AI feature, whether consent to use that data is still valid, and where the data flows once it's collected.

**[Live demo](#)** — enable GitHub Pages (see below) and drop the link here.

## The problem

AI features quietly accumulate data dependencies: chat transcripts, voice recordings, CRM records, third-party feeds. Consent for each of those sources has its own basis, its own expiry, and its own owner. Without a single register, it's easy for a feature to keep running on a data source whose consent has lapsed, been revoked, or was never recorded in the first place — and nobody notices until an audit.

## What this demonstrates

This is a companion piece to [ai-governance-console](../ai-governance-console), which covers feature-level policy and approval workflows. This one is scoped narrower and deeper: consent status and data lineage specifically, including the workflow gaps that matter for a compliance owner —

- **Status is only useful with an action attached.** Each consent state (granted, expiring, expired, revoked, missing) carries its own next step — send a renewal reminder, request a renewal, archive from the pipeline, send a consent request — rather than just flagging a problem and leaving it there.
- **Bulk triage.** Filtering to a single status surfaces a bar to action every matching entry at once, not one at a time.
- **Sort and filter by urgency, not just status.** Expiry windows (7/14/30/60 days, or already past due) and an urgency-first sort make "what needs attention this week" answerable at a glance.
- **The data-entry path is visible in the UI**, not assumed. Sources can be added manually, imported as a CSV batch, or (once built) synced from a connected pipeline — the entry points are shown, not hidden behind an unexplained dataset.
- **Lineage, not just status.** Every entry traces from source → processing pipeline → the AI feature(s) consuming it, so a compliance review can see the downstream blast radius of a lapsed consent record.

## Try it

Open `index.html` in a browser — no build step, no dependencies. Use the status chips, the expiry-window and sort dropdowns, and the "Add data source" button to add or import entries. Click any row to expand its full lineage trail and take the suggested action.

## Stack

Plain HTML, CSS and JavaScript — no framework, no backend. State lives in memory for the session, which keeps the demo self-contained and easy to fork.

## Enable a live link

Settings → Pages → Deploy from branch → `main` / `root`. GitHub will publish `index.html` at `https://<username>.github.io/data-consent-lineage-tracker/`.

---
Prototype built for portfolio/case-study purposes. Not a substitute for legal or compliance advice.
