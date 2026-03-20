# 1095-B Tax Form — Product Outline

*Last updated: March 2026 | Team: Core Veteran Experiences (CVE) | Department of Veterans Affairs*

---

## Overview

The 1095-B Tax Form product on VA.gov enables Veterans and dependents enrolled in VA healthcare to securely sign in and download their IRS Form 1095-B — proof of minimum essential health coverage — as a PDF or plain-text file, eliminating the need to call the VA or wait for a mailed replacement copy.

---

## Problem Statement

Veterans and dependents enrolled in VA healthcare are required by law to receive IRS Form 1095-B, which proves they had qualifying health coverage for the tax year. Prior to this product, the VA had no digital channel for delivering this form: it was printed and mailed at a cost of approximately **$4 million per year**. When Veterans lost their form or needed a copy for a state with an individual coverage mandate, they had to call the VA, wait for a representative, and then wait again for a physical reprint to arrive by mail — a multi-day delay during an already time-sensitive tax filing season.

This experience is inconsistent with federal mandates for digital government services and with the expectations Veterans have from modern consumer experiences.

**How might we** make the 1095-B tax form instantly and reliably accessible to Veterans through a secure digital experience on VA.gov — without requiring them to call or wait?

---

## Desired User Outcomes

- Veterans and dependents can sign in to VA.gov, navigate to the Records hub, and immediately download their current and prior-year 1095-B forms as a PDF or plain-text file.
- Veterans who call the VA seeking a replacement form are directed by call center representatives to self-serve on VA.gov, resolving their need without a reprint.
- Veterans with disabilities or limited digital literacy can access the form through an accessible, plain-language experience that meets WCAG 2.1 AA standards.
- Veterans know exactly why they do or do not have a 1095-B available (e.g., CHAMPVA status, not enrolled) without needing to call.

---

## Undesired User Outcomes

- More than 10% of Veterans enrolled in VA healthcare for a given tax year are unable to view or download their form on VA.gov.
- Veterans encounter confusing or contradictory error messages that lead them to call the VA unnecessarily.
- Veterans with accessibility needs (screen readers, low vision, cognitive disabilities) cannot successfully complete the download task.
- Veterans who are not LOA3-verified are blocked without clear direction on how to verify their identity.

---

## Desired Business Outcomes

- A measurable reduction in reprints and resends each tax season compared to prior years.
- Reduced cost burden on the Health Eligibility Center (HEC) call center during peak tax season (January–April).
- VA.gov's delivery of the 1095-B is compliant with IRS requirements and the 21st Century IDEA Act mandate for digital government services.
- A reliable, low-maintenance product that can be updated annually with minimal engineering effort.
- All VES products have a published, current product brief — satisfying OCTO OKR 1.1.

---

## Undesired Business Outcomes

- An increase in call volume or reprints during the tax season following digital launch, indicating Veterans cannot find or trust the digital experience.
- A product that requires significant engineering resources each year simply to update the tax year template.
- Backend data inaccuracies that cause Veterans to receive incorrect coverage information, creating compliance or legal risk.

---

## Measuring Success

### Key Performance Indicators (KPIs)

*Data sources: [Google Analytics](https://analytics.google.com) | [Datadog](https://datadoghq.com) | [Domo](https://va-gov.domo.com) (filter: `/download-your-irs-1095-b`)*

| Category | Ease of Use | Service Completion | Trust / Satisfaction | Health |
|----------|-------------|-------------------|----------------------|--------|
| **KPI** | % of users who successfully see download links (`1095b-available-forms-found`) | # of PDF + TXT downloads per month (clicks on download links) | CSAT score (Domo intercept survey) | Available-forms endpoint error rate |
| **KPI** | Avg session time on page (target: task-focused, not excessive) | % of sessions that result in at least one download | N/A | PDF download endpoint error rate |
| **KPI** | % of users who encounter a system error (red alert — `1095b-available-forms-system-error`) | Reduction in HEC reprints/resends vs. prior year baseline | N/A | PDF/TXT endpoint latency (ms) |

#### Baseline KPI Values (2025 Tax Season / Early 2026 Data)

| Metric | Baseline Value | Source | Target |
|--------|---------------|--------|--------|
| CSAT score | 58.33% (Jan 2026), 68.89% (Feb 2026) | Domo intercept survey | Improve by 5 points over prior period (per OCTO OKR 1.1) |
| Monthly page views (peak tax season) | 43,635 (Jan 2026), 93,951 (Feb 2026) | Google Analytics | Track YoY growth; no target floor set yet |
| PDF download latency | ~1.27–1.29s | Datadog | < 4 seconds (per OCTO OKR 1.2) |
| Available-forms latency | ~406–421ms | Datadog | < 4 seconds (per OCTO OKR 1.2) |
| Available-forms error rate | 0.27% (Jan 2026), 0.38% (Feb 2026) | Datadog | < 1% per endpoint (per OCTO OKR 2.2) |
| PDF download error rate | ~0.03% | Datadog | < 1% per endpoint (per OCTO OKR 2.2) |
| HEC reprints/resends (baseline) | TBD — awaiting data from HEC | HEC / VHA | Reduce year-over-year |

> **Note:** Reprints/resends baseline data is needed from the Health Eligibility Center to fully close OKR 1.1's KPI requirement. This is the most critical missing data point.

### Objectives and Key Results (OKRs)

*Aligned to 2026 OCTO OKRs:*

- **Objective 1: Optimize product delivery for Veteran impact**
  - Key result 1.1: This product outline defines a product vision, explains the problem to be solved, and sets KPIs for measuring impact ✅
  - Key result 1.2: A published product roadmap is maintained and updated at least quarterly
  - Key result 1.3: Each feature on the roadmap is linked to a product brief (initiative brief)

- **Objective 2: Products operate with high reliability and accessibility**
  - Key result 2.1: Latency, error rate, volume, and saturation are monitored and reported via Datadog
  - Key result 2.2: All three endpoints maintain < 1% error rate; product targets 99.8%+ uptime
  - Key result 2.3: Team evaluates feasibility of continuous ATO for 1095-B (status: TBD)

- **Product-level OKR: Increase Veteran self-service adoption for 1095-B**
  - Key result: Reduce HEC reprints/resends by a measurable amount in the 2026 tax season vs. 2025 (baseline TBD from HEC)
  - Key result: Maintain CSAT ≥ 70% during peak tax season (Jan–Apr)
  - Key result: < 1% error rate across all three API endpoints throughout 2026

---

## Assumptions

1. **(Highest risk)** The Enrollment Services (ES) API provides accurate, complete coverage data for all enrolled Veterans. If the data is incomplete or stale, Veterans will see incorrect or missing forms, potentially generating more call volume rather than reducing it.
2. Veterans who need their 1095-B form are motivated enough to sign in with a verified (LOA3) account. Veterans who have not yet identity-verified may not complete the process without additional guidance.
3. Call center representatives at HEC will actively redirect callers to VA.gov once the digital product is live and reliable. Without this coordination, the reduction in reprints/resends will be limited.
4. Annual tax year template updates can be handled with minimal engineering effort by the team responsible for this product.
5. CHAMPVA beneficiaries will continue to be handled separately by VHA/CHAMPVA and are out of scope for this product.

---

## Solution Approach

### What we built (MVP — launched March 31, 2025)

The MVP delivers a single, authenticated page at [va.gov/records/download-your-irs-1095-b](https://www.va.gov/records/download-your-irs-1095-b) where LOA3-verified Veterans and dependents can download their current-year 1095-B as a PDF or plain-text file. No marketing or outreach was done for the MVP; the primary adoption path was call center representatives redirecting Veterans who called about reprints.

We chose a minimal approach — no opt-in flows, no paperless delivery preference, no previous years — to ensure reliability and to get value to Veterans in time for the 2025 tax season. The previous team's work (2022) was not launched; IIR rebuilt a true MVP from scratch prioritizing reliability over features.

### What we're building next

- **Previous years forms** (in progress, 2026): Veterans will be able to access up to three prior years of 1095-B forms from the same page. This eliminates the need to call for older copies and increases the product's year-round utility.
- **New Enrollment System API migration** (complete): The product now connects directly to the Enrollment Services API rather than a legacy S3 batch file, improving data freshness and reliability.
- **Annual tax year template updates**: Adding the 2025 form template for the 2026 tax filing season.
- **Wayfinding / findability** (sitewide team): Cross-links from other VA.gov pages to make the form more discoverable without relying solely on call center referrals.

### What we explicitly decided NOT to include (and why)

- **Opt-in to paperless delivery**: This feature was designed but required cross-team coordination with MyVA, VA Profile, VA Notify, and HEC. Given complexity and risk to the MVP timeline, it was descoped and has not been picked up as of Q1 2026.
- **CHAMPVA users**: CHAMPVA beneficiaries have a separate process through VHA. They are excluded from the product's scope to avoid confusion; the product displays an informational message directing them appropriately.
- **Push notifications or proactive outreach**: The VA sends physical forms anyway, so there is no urgency to add email/SMS notifications for the MVP phase.

### How this solution evolves

The product will require annual maintenance each January to update the tax year template. Beyond maintenance, the team's current focus is extending the product to support previous years' forms. Future iterations may include mobile app integration (VA Health and Benefits app) if the VA.gov Records hub is extended there, but no decision has been made.

**Mobile app:** The current solution does not include the VA Health and Benefits mobile application. Given that the 1095-B download involves a file download action, the mobile experience requires additional UX and technical work. This will be evaluated in a future initiative.

### Supporting Research

This work is supported by user research conducted by the previous team (2022):
- [Discovery research (2022)](https://github.com/department-of-veterans-affairs/va.gov-team/blob/master/products/health-care/1095b-tax-form/design/VA_1095-B%20Initial%20Research%20Discovery_2-4-22.pptx)
- [Round 1 research synthesis](https://github.com/department-of-veterans-affairs/va.gov-team/blob/master/products/health-care/1095b-tax-form/research/round%201%20Research%20Findings%20Report.md)
- [Round 2 research synthesis](https://github.com/department-of-veterans-affairs/va.gov-team/blob/master/products/health-care/1095b-tax-form/research/round2/round2-research-report.md)

UAT was conducted on the MVP prior to launch. No additional user research is currently planned for the previous-years forms feature given the low complexity of the UX change, but the team should consider research if error rates or CSAT indicate confusion.

### Initiatives

- MVP Digital Access | [Product Outline (this document)](#)
- Previous Years Forms | [Initiative Brief — TBD](#)

---

## Launch Strategy

The MVP was launched with no public marketing or communications. The primary awareness channel was HEC call center representatives, who were briefed to redirect Veterans seeking reprints to VA.gov.

Future awareness and adoption strategies should include:
- Coordination with HEC to update call center scripts and measure deflection rates
- Cross-links from VA.gov health care hub pages (handled by the Sitewide team)
- Potential inclusion in VA-wide communications around tax season (January)

[Link to Release Plan](https://github.com/department-of-veterans-affairs/va.gov-team/blob/master/products/health-care/1095b-tax-form/product/1095b-release-plan.md)

## Launch Dates

- **MVP Launch Date:** March 31, 2025
- **Previous Years Forms target:** Q1 2026 (in progress as of March 2026)
- **Impact review:** To be evaluated after the 2026 tax season closes (approximately May 2026); key metrics: downloads, CSAT, and HEC reprint volume compared to 2025 baseline.

---

## Solution Narrative

### Current Status

The product launched March 31, 2025 at [va.gov/records/download-your-irs-1095-b](https://www.va.gov/records/download-your-irs-1095-b). As of February 2026, the product has served nearly **94,000 page views in a single month** during peak tax season with CSAT at 68.89% and error rates well below 1% across all endpoints.

The team (CVE) is currently completing:
1. Migration to the new Enrollment Services API (removing S3 dependency)
2. Adding the 2025 tax year form template
3. Building previous years forms support (up to 3 prior years)
4. Cleanup of legacy S3 architecture

### Key Decisions

| Date | Decision | Rationale |
|------|----------|-----------|
| 2024 | Rebuilt from scratch rather than resuming 2022 work | Previous work was never launched; a true MVP with reliability emphasis was more appropriate than inheriting incomplete code |
| 2024 | Excluded opt-in paperless delivery from MVP | Required complex cross-team coordination (MyVA, VA Profile, VA Notify, HEC); would have delayed launch past tax season |
| 2025 | Migrated from S3 batch files to direct Enrollment Services API | Improves data freshness and eliminates a fragile batch dependency |
| 2025 | Descoped opt-in paperless delivery indefinitely | Cross-team resources not available; feature not picked up by any other team |
| 2026 | Adding previous years support (3 years) | High Veteran value for amended returns and state tax filing requirements |

---

## Screenshots

### Before
N/A — this functionality is net new and did not exist on VA.gov prior to March 2025. Veterans had to call the VA and wait for a physical reprint.

### After

[Figma user flow (Sep 2025)](https://www.figma.com/design/cP7JJ9ExBtn2jNax9cfinA/1095-B?node-id=1036-24356&t=4u2RwT3RjCOwd9gC-1)

[Figma designs (Sep 2025)](https://www.figma.com/design/cP7JJ9ExBtn2jNax9cfinA/1095-B?node-id=1037-32186&t=4u2RwT3RjCOwd9gC-1)

---

#### Communications

<details>

- **Team Name:** Core Veteran Experiences (CVE) — Department of Veterans Affairs
- **GitHub Label:** 1095b-tax-form
- **Slack channel:** #iir-product-teams-public
- **Product POCs:** Megan Commons (megan.commons@oddball.io) | Pete Egan (peter.egan@oddball.io)
- **Stakeholders:** Dave Conlon (VAPO), Health Eligibility Center (HEC), Enrollment Systems Team

</details>

#### Team Members

<details>

- **VAPO / DEPO Lead:** Dave Conlon
- **PM:** Megan Commons (megan.commons@oddball.io)
- **Engineering:** Kris Pethtel (kris.pethtel@adhocteam.us)
- **Research/Design:** Raquel Eisele (raquel.eisele@adhocteam.us)

</details>

#### Stakeholders

<details>

- **Health Eligibility Center (HEC):** Tarsha Tremble (tarsha.tremble@va.gov) | Stacey Echols (stacey.echols@va.gov)
- **Enrollment Services:** Joshua Faulkner (Joshua.Faulkner@va.gov)
- **OCTO / VAPO:** Dave Conlon
- **Sitewide Team:** Randi Hecht (wayfinding / cross-links)

</details>
