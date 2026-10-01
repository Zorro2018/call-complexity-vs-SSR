# SSR vs Complexity -- Portable Demo

Standalone, single-file demo report exploring **Self-Serve Rate (SSR) vs
Call Complexity**, by workflow and over time.

## Important: this is inferred, not sourced from the live report

The actual report lives at
on an internal reporting platform and is behind
Walmart SSO -- it wasn't reachable during this build (the automated browser
session had no saved credentials, and typing in real credentials on your
behalf wasn't something I was going to do). So instead of a 1:1 rebuild,
this demo's structure was **inferred** from:

1. The report's own name (SSR = Self-Serve Rate, vs. Complexity)
2. The **Call Complexity Scorecard** model already built in
   `../call-complexity-scorecard-portable/` -- reused verbatim: the same
   Low/Medium/High tiering convention and the same fictional workflow
   taxonomy (Order Status Inquiries, Password Reset, Billing Disputes,
   Fraud & Identity Verification, etc.)
3. The **Sierra Voice AI Self-Serve Rate** metric already documented in the
   portfolio site (`30% -> 70%` self-serve lift)

**If you can get me a screenshot or export of the real page**, send it over
and this gets tightened up to match the actual chart set, tab names, and
KPI cards exactly. Until then, treat this as a plausible placeholder that
tells a coherent, defensible story on the right topic -- not a faithful
copy of the live report.

## What's in it

Single file: **`ssr-vs-complexity-demo.html`** -- open directly via
`file://`, no server, no auth. Only external dependency is Chart.js (CDN).

4 tabs, each with a **Strategic Insights** callout and a **metric readout**
strip:

1. **Overview** -- fleet-wide KPIs (Overall SSR, Avg Complexity of
   agent-handled contacts, High-Complexity volume share, SSR&harr;Complexity
   correlation) + a bubble scatter of every workflow (complexity vs SSR,
   sized by volume, colored by tier).
2. **Trend** -- 26-week dual-axis line: SSR climbing while the average
   complexity of the *residual* (non-deflected) agent-handled mix also
   climbs -- the "self-serve skims the easy calls" story.
3. **By Complexity Tier** -- SSR by Low/Medium/High tier (bar) + volume
   share by tier (doughnut).
4. **By Workflow** -- every workflow ranked by SSR, plus a detail table
   with tier, volume, complexity score, and SSR.

## Data provenance & sanitization

All 13 workflows, their volumes, complexity scores, and SSR values are
synthetic, generated in-browser with a fixed-seed PRNG (`mulberry32`) --
nothing here is a real production number. The correlation coefficient
shown is *computed live* from the generated data (not hardcoded), so it
stays internally consistent with whatever the underlying numbers are.

The qualitative story is intentional and sign-safe: SSR and complexity are
negatively correlated, low-complexity workflows self-serve well but still
have headroom, high-complexity workflows correctly don't self-serve much,
and the residual agent-handled mix gets harder over time even as headline
SSR improves.
