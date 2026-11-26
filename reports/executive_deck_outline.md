# Executive Consulting Deck Outline — 15 Slides

> **Overview:** Complete 15-slide executive consulting outline presenting the *High-Value & Intervenable Churn* PoC business proposal for **Company A**. All metrics and financial impacts match [`notebooks/telecom_churn_roi_analysis.ipynb`](../notebooks/telecom_churn_roi_analysis.ipynb) 100%, and all 300 DPI charts reside in [`reports/figures/`](figures/).

---

## Slide 1 — Title & Executive Value Hook
- **Action Title:** Turning Telecom Retention Losses into Profit Through Value-Weighted AI *(PoC Proposal for Company A)*
- **Executive Key Takeaway:** Focusing retention on the **top 2.0% high-value risk segment** within a **30-day pre-churn window** converts a projected **−\$4.49M/year** mass-retention loss into **+\$40,887/year net profit (+83.1% ROI)** under U.S. wireless market conditions.
- **Slide Content:**
  - **Proposal Title:** Data-Driven PoC Proposal: Predicting & Preventing High-Value, Intervenable Subscriber Churn for Company A.
  - **Three Hero KPI Callouts:**
    1. **Calibrated Predictive Engine:** LightGBM **`ROC-AUC = 0.7029`** & **`ECE = 0.0070`**.
    2. **Precision Value Targeting:** **`2.0%`** optimal cohort (`1,996` subscribers/mo, **`$173.05`** mean ARPU).
    3. **Quantified U.S. Market Impact:** **`+$40,887/year`** net contribution, **`+83.1%` ROI**, **`85%`** sensitivity pass rate.
  - **Prepared by:** Zaki Abdullah Al Muqarabin — Telecom Churn & ROI Analytics PoC.
- **Visual & Table Mapping:**
  - Clean executive navy cover layout + **3 KPI Hero Cards** at bottom (no raw data tables).
- **Slide Footnotes:**
  - *Internal Company A analysis (`n = 100,000` subscribers); U.S. 0.90%/mo churn calibration anchored to [4], [5].*

---

## Slide 2 — Executive Summary & Engagement Roadmap
- **Action Title:** Company A Holds an Actionable 30-Day Window to Retain High-ARPU Subscribers Before Defection
- **Executive Key Takeaway:** By pairing calibrated LightGBM risk scores with revenue-weighted ranking (*Expected Revenue at Risk*) and three operational levers, Company A can deploy proactive retention without internal ML overhead.
- **Slide Content:**
  - **Client Situation:** Company A manages ~100,000 subscribers (`Client.csv` + `Record.csv`) without an in-house ML team.
  - **Why Act Now?** Because `churn` is observed **31–60 days post-snapshot**, Company A gains an operational **~30-day window** to intervene before customers leave.
  - **Proposal Structure (3 Pillars):**
    1. *U.S. Market Reality & Company A Data Audit* (Slides 3–5).
    2. *Zero-Leakage ML Engine & Actionable Drivers* (Slides 6–9).
    3. *30-Day Playbook, ROI Simulation & Governance Roadmap* (Slides 10–14).
- **Visual & Table Mapping:**
  - **30-Day Operational Timeline Diagram:** `Snapshot (Day 0)` → `LightGBM Scoring & Value Ranking (Days 1–3)` → `3-Lever Outreach Execution (Days 4–30)` → `Churn Prevention Window (Days 31–60)`.
- **Slide Footnotes:**
  - *Churn window definition (31–60 days post-observation) per Company A Dataset Overview documentation.*

---

## Slide 3 — U.S. Mature Wireless Market Context & Retention Economics
- **Action Title:** In a Saturated Market With Falling Unit Prices, a 5% Retention Lift Outperforms Costly Acquisition
- **Executive Key Takeaway:** With U.S. wireless connections exceeding 600M and real unlimited prices declining, protecting high-ARPU customers yields exponential margin gains over new subscriber acquisition.
- **Slide Content:**
  - **Market Saturation & CapEx Pressure:** U.S. wireless connections grew from **579M** (2024) to **>600M** (2025; ~1.8 per capita), data traffic surged to **159.3 trillion MB**, and industry CapEx approached **\$30B/year**—while real unlimited plan prices fell **>10%** and cost/GB fell **>21%** [1], [2].
  - **ARPU & Overage Compression:** FCC reporting links flat-to-declining ARPU to aggressive promotions, legacy overage fee elimination, and trade-in/bundle competition [3].
  - **Low Natural Churn Benchmarks:** Leading U.S. carriers post **0.76%–0.90%/mo** (**AT&T**) [4] and **0.86%–0.93%/mo** (**T-Mobile**) [5] postpaid phone churn—demanding surgical targeting.
  - **Retention Multiplier:** Acquiring a customer costs **5×–25× more** than retaining one [6], while lifting retention **5%** increases profits **25%–95%** [7].
- **Visual & Table Mapping:**
  - **Industry Benchmark Summary Table (4 rows × 3 columns):** *Saturation & CapEx* [1], [2]; *ARPU Compression* [3]; *U.S. Churn Benchmarks* [4], [5]; *Retention Economics* [6], [7].
- **Slide Footnotes:**
  - `[1]` CTIA (2025); `[2]` CTIA (2026); `[3]` FCC (2024); `[4]` AT&T IR (2024–2025); `[5]` T-Mobile IR (2024–2025); `[6]` Gallo, HBR (2014); `[7]` Reichheld, Bain & Company.

---

## Slide 4 — Company A Data Audit & Pareto Value Concentration
- **Action Title:** Top-Quartile Subscribers (Q4) Generate 48.55% of Revenue Yet Endure 31× Higher Overage Fees
- **Executive Key Takeaway:** Uniform retention campaigns waste budget on low-ARPU accounts; nearly half of Company A's revenue sits in Q4, where billing shock and network friction are most severe.
- **Slide Content:**
  - **Data Hygiene & Governance Audit:** 1:1 merge of `Client.csv` + `Record.csv` (`100,000 × 100`). Removed `Customer_ID` (chronological leakage, `r = −0.75` vs. `months`), `ethnic` (fairness/ethics), `recv_sms_Mean` (`99.13%` zero), and 14 collinear columns (`|r| >= 0.95`).
  - **Pareto Revenue Concentration (`rev_Mean`):**
    - **Q4 (`>= \$70.75`, `n=24,910`):** generates **`48.55%`** of monthly revenue (`$114.03/mo` ARPU; `$1.39M/mo` at risk in sample).
    - **Top 20% (`>= \$78.83`):** generates **`42.17%`** of revenue (`$1.21M/mo` at risk).
  - **Operational Friction (Q4 vs. Q1):** **`31.2×`** overage fees (`$40.87` vs. `$1.31`), **`5.6×`** dropped/blocked calls (`19.41` vs. `3.48`), **`5.5×`** customer care calls (`3.18` vs. `0.58`).
  - **Calibration Flag:** The dataset's `49.56%` churn rate is a *balanced case-control sample*, requiring Stage 5 recalibration to U.S. market norms (`~0.90%/mo`).
- **Visual & Table Mapping:**
  - **Value Quartile Summary Table (Q1–Q4)** showing Revenue Share %, Mean ARPU, Overage $, and Drop/Block Calls.
- **Slide Footnotes:**
  - *Source: Internal EDA of Company A (`n = 100,000`). U.S. carrier churn norms per [4], [5].*

---

## Slide 5 — Key EDA Insights: Actionable Churn Drivers Inside High-Value Q4
- **Action Title:** Aging Handsets, Missing Spend Limits, and Silent Usage Drops Drive Q4 Churn up to 59.5%
- **Executive Key Takeaway:** Within High-Value Q4, four business-modifiable levers separate high-risk accounts from stable ones—including *silent churners* who stop using minutes without ever calling customer care.
- **Slide Content:**
  - **1. Handset Aging (`eqpdays`):** Q4 churn climbs **`+16.33 pp`** from **`43.17%`** (`<=180d`) to **`54.43%`** (`366–730d`) and **`59.50%`** (`>730d`); legacy/undocumented web capability (`WC/MISSING`) reaches **`55.46%–58.13%`** vs. `47.33%` (`WCMB`).
  - **2. Account Spend Protection (`asl_flag`):** Q4 accounts with an active spending limit (`Y`) exhibit **8.82 pp lower churn** (`41.44%` vs. `50.26%`).
  - **3. Silent Usage Drop (`silent_churn_risk`):** Q4 subscribers with sharp traffic drops (`change_mou < -50`) and **zero support calls (`custcare_Mean == 0`)** churn at **`55.58%`** vs. `47.33%`.
  - **4. Normalized Network Failure Rate (`drop_blk_rate`):** Resolving call-volume confounding shows failure rates above P75 (`> 0.083`) lift Q4 churn from **`47.41%`** to **`52.20%`**.
- **Visual & Table Mapping:**
  - **4-Lever Q4 Diagnostic Table** (`Lever` | `High-Risk Segment` | `Churn Rate` | `Spread` | `Operational Action`).
- **Slide Footnotes:**
  - *Source: High-Value Q4 segmentation on Company A (`n = 24,913`, Q4 baseline = `48.61%`).*

---

## Slide 6 — Problem Definition, Zero-Leakage Architecture & Ablation Proof
- **Action Title:** A Zero-Leakage (70/15/15) Pipeline Delivers Clean Signal After Purging Billing-Artifact Indicators
- **Executive Key Takeaway:** Strict train-only preprocessing and an empirical ablation study confirm our predictive signal comes from genuine behavioral and device drivers rather than pre-closure billing gaps.
- **Slide Content:**
  - **Executive Question:** *Which high-value subscribers face churn risk 31–60 days ahead, and which 30-day intervention maximizes net financial return?*
  - **Zero-Leakage Design (`random_state=42`):** Stratified `70% Train (70K) / 15% Val (15K) / 15% Test (15K)` split; all imputation, `RobustScaler`, `OneHotEncoder`, and Q4/overage cutoffs fit **only on Train**; `107` clean final features (including 25 domain-engineered features).
  - **Decisive Ablation Study Outcome:** Dropping `miss_billing_flag` & `miss_change_flag` **improved** LightGBM Validation ROC-AUC (`0.7052 → 0.7060`) and Brier (`0.2172 → 0.2170`), while a sanity check on the `99.1%` non-missing Test subset (`n=14,859`) retained **`ROC-AUC = 0.6998`**.
- **Visual & Table Mapping:**
  - **Conceptual Pipeline Diagram** (`100K Raw` → `Drop 17 Leak/Collinear + Add 25 Ratios` → `70/15/15 Split` → `Ablation Audit` → `Calibrated Risk Engine`).
  - **Compact Ablation Summary Table (4 Models on Validation)**.
- **Slide Footnotes:**
  - *All preprocessing, splits, and models enforced with `RANDOM_STATE = 42` for 100% reproducibility.*

---

## Slide 7 — Model Comparison, Explicit Metrics & Probability Calibration
- **Action Title:** LightGBM Outperforms All Benchmarks (`ROC-AUC 0.7029`, `ECE 0.0070`) With Directly Usable Probabilities
- **Executive Key Takeaway:** Across four distinct model families, LightGBM achieves the highest ranking accuracy and near-perfect probability calibration, making its outputs reliable inputs for financial threshold decisions.
- **Hold-Out Test Model Comparison Scorecard (`n=15,000`):**
  - **Selected Best Model — `LightGBM` (`931 trees`):** **`ROC-AUC = 0.7029`** | **`PR-AUC = 0.6922`** | **`F1-Score = 0.6422`** | **`Accuracy = 0.6420`** (beating a raw uncleaned baseline `0.6368` without leaked IDs/artifacts) | **`Brier Score = 0.2179`** | **`ECE = 0.0070`**.
  - **Benchmark Models on Hold-Out Test Set:**
    - **`CatBoost`:** `ROC-AUC = 0.6982` | `PR-AUC = 0.6886` | `F1 = 0.6368` | `Accuracy = 0.6399` | `Brier = 0.2194`.
    - **`Random Forest`:** `ROC-AUC = 0.6807` | `PR-AUC = 0.6693` | `F1 = 0.6299` | `Accuracy = 0.6255` | `Brier = 0.2260`.
    - **`Logistic Regression`:** `ROC-AUC = 0.6404` | `PR-AUC = 0.6199` | `F1 = 0.5987` | `Accuracy = 0.6024` | `Brier = 0.2349`.
  - **Executive Translation:** `ROC-AUC 0.7029` means the model ranks true churners above stayers >70% of the time, while `ECE 0.0070` (beating Platt `0.0133` and Isotonic `0.0182`) means predicted probabilities match observed churn rates within `0.7%`.
- **Visual & Table Mapping:**
  - **300 DPI Chart:** [01_model_comparison_roc_pr_calibration.png](figures/01_model_comparison_roc_pr_calibration.png) *(ROC, Precision-Recall & Reliability Curves)*.
- **Slide Footnotes:**
  - *Evaluated strictly on Hold-Out Test Set (`n = 15,000`, `RANDOM_STATE = 42`); raw uncleaned baseline accuracy (`0.6368`).*

---

## Slide 8 — Value-Weighted Targeting (*Risk × Revenue*) in High-Value Q4
- **Action Title:** Prioritizing Q4 by `Risk × Revenue` Captures 38.68% of At-Risk Revenue in the Top 20% (+10.24 pp)
- **Executive Key Takeaway:** Weighting churn probability by subscriber revenue (`p_i × rev_Mean`) captures dramatically more revenue at risk per retention dollar than sorting by churn probability alone.
- **Slide Content:**
  - **High-Value Q4 Hold-Out Test Results (`n=3,725`, total churned revenue `$214,121/mo`):**
    - **Top 10% Q4 (`n=372`):** *Risk × Revenue* captures **`24.42%`** of churned revenue vs. `15.14%` (*Risk Only*, **`+9.28 pp`**; Precision `65.6%`).
    - **Top 20% Q4 (`n=745`):** Captures **`38.68%`** vs. `28.44%` (*Risk Only*, **`+10.24 pp`**; Precision `63.1%`).
    - **Top 30% Q4 (`n=1,117`):** Captures **`50.51%`** vs. `39.74%` (*Risk Only*, **`+10.78 pp`**; Precision `62.3%`).
  - **Business Implication:** Over half of Q4's monthly churned revenue is concentrated within the top 30% value-weighted priority queue.
- **Visual & Table Mapping:**
  - **300 DPI Chart:** [02_cumulative_gains_revenue_capture.png](figures/02_cumulative_gains_revenue_capture.png) *(Cumulative Gains & Revenue Capture @ Top-K%)*.
- **Slide Footnotes:**
  - *Computed on Hold-Out Test High-Value Q4 segment (`rev_Mean >= $70.74` Train threshold).*

---

## Slide 9 — Model Interpretability (Exact TreeSHAP) & Intervenability
- **Action Title:** 38.52% of Model Predictive Power Comes From 35 Directly Actionable Business Levers
- **Executive Key Takeaway:** Far from a black box, LightGBM relies heavily on modifiable device, billing-structure, and call-quality levers—with 8 of the Top 15 features directly controllable by Company A.
- **Slide Content:**
  - **Exact TreeSHAP Breakdown Across All 107 Features (Hold-Out Test):**
    - **(a) Actionable / Intervenable (35 features): `38.52%`** of total `|SHAP|` — led by `eqpdays` (#1, `9.13%`, ↑), `hnd_price` (#5, `3.09%`, ↓), `totmrc_Mean` (#6, `3.04%`, ↓), `rev_per_mou` (#10, `2.44%`, ↑), `ovr_mou_share` (#12, `2.27%`, ↑), `mrc_to_rev_ratio` (#13, `2.17%`, ↓), `eqp_to_tenure_ratio` (#14, `1.98%`, ↑), and `phones_per_year` (#15, `1.92%`, ↑).
    - **(b) Behavioral / Usage Signal (46 features): `38.31%`** — early-warning triggers led by `mou_pct_change_3m` (#2, `7.59%`), `avgqty` (#9, `2.70%`), `avgmou` (#11, `2.31%`).
    - **(c) Static / Demographic (26 features): `23.17%`** — fixed tenure/region context (`months` `6.34%`, `crclscod` `3.38%`, `lor` `2.98%`, `area` `2.93%`).
  - **Engineering Validation:** **6 of the Top 15** predictors are Stage 3 engineered ratios/deltas.
- **Visual & Table Mapping:**
  - **300 DPI Chart:** [03_feature_importance_intervenability.png](figures/03_feature_importance_intervenability.png).
- **Slide Footnotes:**
  - *Exact TreeSHAP (`pred_contrib=True`) computed on `LightGBM` Hold-Out Test predictions (`n = 15,000`).*

---

## Slide 10 — Business Proposal: 30-Day Proactive Retention Playbook
- **Action Title:** A 3-Lever Retention Playbook Matches Each At-Risk Subscriber to Cost-Effective Intervention
- **Executive Key Takeaway:** Targeted subscribers are routed automatically to one of three actions inside the 30-day window, with 80%+ handled via low-cost digital bill-shock protection rather than expensive handset subsidies.
- **Slide Content:**
  - **Decision Formula:** $\text{Expected Net Benefit}_i = (p_i \cdot \text{rev\_Mean}_i) \cdot s_k \cdot H \cdot m - \big[c_{\text{out},k} + (p_i s_k + (1-p_i)u_k)c_{\text{off},k}\big]$.
  - **Three Levers & Mix in Optimal Cohort (Top 2.0% U.S. Market):**
    1. **Bill-Shock Protection (`80.25%` share | `1,602` subs/mo):** Proactive overage alerts & plan right-sizing for `asl_flag=N` (`ovrrev >= $14.44`) — `$1` outreach + `$10` conditional offer, `20%` save rate, `5%` cannibalization.
    2. **Device Upgrade (`19.06%` share | `380` subs/mo):** Trade-in/installment credits for `eqpdays > 365` or `WC/MISSING` webcap — `$2` outreach + `$45` conditional credit, `25%` save rate, `4%` cannibalization.
    3. **Proactive Care (`0.70%` share | `14` subs/mo):** Priority CS outreach for network friction / silent drops — `$5` outreach + `$12` goodwill credit, `15%` save rate, `4%` cannibalization.
  - **Grounded Benchmarks:** `12-month` LTV horizon, `45%` contribution margin (midpoint of AT&T `42.0%` [4] & T-Mobile `49.7%` [5] margins); `15%–25%` save rates conservatively below McKinsey's `15%–30%` AI churn-reduction range [8], [9].
- **Visual & Table Mapping:**
  - **3-Lever Action Matrix Table** (`Trigger` | `Action` | `Cost Structure` | `Save Rate` | `Cohort Share`).
- **Slide Footnotes:**
  - `[4]` AT&T IR (42.0% Mobility EBITDA); `[5]` T-Mobile IR (49.7% Service EBITDA); `[8]` & `[9]` McKinsey & Company (AI retention & network CX).

---

## Slide 11 — Cutoff Optimization & U.S. Market Base-Rate Calibration (`0.90%/mo`)
- **Action Title:** Bayes Recalibration Locks Optimal Targeting at Top 2.0% (`1,996` Subs/Mo), Preventing Over-Targeting Losses
- **Executive Key Takeaway:** Uncalibrated sample probabilities (`49.56%`) severely overstate intervention profitability; recalibrating to the `0.90%/mo` U.S. market rate isolates a profitable peak at **Top 2.0%**.
- **Slide Content:**
  - **Bayes Prior-Odds Calibration:** Scaling odds by $\gamma = 0.00924$ aligns model risk to U.S. postpaid norms (`0.90%/mo` [4], [5]).
  - **Validation-Selected Cutoff → Hold-Out Test Performance:**
    - Validation sweep peaks at **Top 2.0%** (`1,996` subs/mo per `100K` portfolio).
    - Target cohort averages **`$173.05/mo` ARPU** with **`2.36%/mo` calibrated churn risk** (**`~2.6×`** market average), generating **`+$3,407/month`** net benefit on **`$4,098/month`** spend (**`+83.1%` ROI**).
    - Expanding past **Top 7%–10%** erodes net margin as stayer cannibalization outweighs retention gains (`Top 10%`: `−$1,744/mo`).
- **Visual & Table Mapping:**
  - **300 DPI Chart:** [04_net_benefit_roi_cutoff_optimization.png](figures/04_net_benefit_roi_cutoff_optimization.png).
- **Slide Footnotes:**
  - `[4]` AT&T FY 2025 churn `0.90%/mo`; `[5]` T-Mobile FY 2025 churn `0.93%/mo`. Realized Test figures computed via Bayes importance weighting.

---

## Slide 12 — Quantified Financial Impact: Before vs. After (Two-Scale Scorecard)
- **Action Title:** Precision ML Flips Mass Retention's `−$4.49M/Year` Loss Into `+$40,887/Year` Net Profit (`+83.1%` ROI)
- **Executive Key Takeaway:** Under real-world U.S. churn rates (`0.90%/mo`), indiscriminate retention destroys millions in margin, whereas LightGBM precision targeting cuts spend by >99% and generates positive net ROI.
- **Slide Content (CFO *Before vs. After* Scorecard on Hold-Out Test, Extrapolated to 100K):**
  - **Scenario 2 — U.S. Market `0.90%/mo` (100K Annualized ×12 Waves | 12M Rev at Risk: `$7.55M`):**
    - *Without ML (Mass Retention Top 100%):* Spend **`$5,201,997/yr`** → Gross Rev Retained `$1,573,258` → Contrib `$707,966` → **Net Loss `−$4,494,031/yr` (`−86.4%` ROI)**.
    - *With Precision ML (Optimal Top 2.0% = `23,950` sub-months/yr):* Spend **`$49,174/yr`** → Gross Rev Retained **`$200,135`** → Contrib **`$90,061`** → **Net Profit `+$40,887/yr` (`+83.1%` ROI)**.
  - **Scenario 1 — Sample Dataset Scale (`49.56%` churn, 100K | 12M Rev at Risk: `$34.67M`):**
    - *Operational Top 20% (`20,000` subs):* Spend `$135,638` → Gross Rev Retained `$3,419,883` → Contrib `$1,538,948` → **Net Profit `+$1,403,309` (`+1,034.6%` ROI)**.
- **Visual & Table Mapping:**
  - **300 DPI Chart:** [05_before_after_financial_comparison.png](figures/05_before_after_financial_comparison.png).
- **Slide Footnotes:**
  - *Hold-Out Test (`n = 15,000`) extrapolated to 100,000 subscribers assuming `45%` contribution margin & `12-month` LTV horizon.*

---

## Slide 13 — Financial Robustness: 2D Sensitivity Stress-Test
- **Action Title:** Optimal Top 2.0% Targeting Remains Profitable Across 85% (17/20) of Cost, Save-Rate, and LTV Scenarios
- **Executive Key Takeaway:** Business viability is resilient to operational variance: even if save rates fall 40% or costs jump 50%, net ROI remains positive as long as saved customers stay at least 12 months.
- **Slide Content:**
  - **Matrix A (`Save Rate` × `Intervention Cost` — `17/20` positive scenarios):**
    - *Base Case (`100% save × 100% cost`):* **`+83.1%` ROI (`+$40.9K/yr`)**.
    - *Pessimistic Efficacy (`60% save × 100% cost`):* still profitable **`+12.2%` ROI (`+$5.9K/yr`)**.
    - *Cost Overrun (`100% save × 150% cost`):* still profitable **`+22.1%` ROI (`+$16.3K/yr`)**.
    - *Optimistic Case (`140% save × 75% cost`):* **`+234.9%` ROI (`+$88.4K/yr`)**.
  - **Matrix B (`Save Rate` × `Retention LTV Horizon` — `17/20` positive scenarios):**
    - Every horizon `>= 12 months` yields positive ROI (`+12.2%` to `+151.2%` at 12 mo; **`+266.3%` / `+$130.9K/yr`** at 24 mo base; **`+402.3%` / `+$202.0K/yr`** at 24 mo optimistic).
    - *Operational Guardrail:* Losses occur only if saved subscribers churn again within `<= 6 months` (`−8.4%` at base save rate).
- **Visual & Table Mapping:**
  - **300 DPI Chart:** [06_sensitivity_roi_heatmap.png](figures/06_sensitivity_roi_heatmap.png).
- **Slide Footnotes:**
  - *Stress-tested on the fixed Top 2.0% Hold-Out Test cohort under Scenario 2 (`RANDOM_STATE = 42`).*

---

## Slide 14 — 6-Month Implementation Roadmap, Risks & Governance
- **Action Title:** A Phased 6-Month Rollout Validates Real-World Lift via Controlled A/B Pilot Before Full Scale
- **Executive Key Takeaway:** Deployment risks are mitigated from day one through a randomized 90/10 pilot, digital automation for >99% of touches, and strict privacy governance excluding sensitive attributes.
- **Slide Content:**
  - **3-Phase Rollout Roadmap:**
    - *Phase 1 (Months 1–2) — Controlled A/B Pilot:* Monthly scoring on `Top 2.0%` (`~2,000/mo`) split **90% Treatment / 10% Holdout Control**; exit gate `>=15%` incremental save, `<=5%` cannibalization, `<20%` 90-day recidivism.
    - *Phase 2 (Months 3–4) — CRM & Billing Automation:* Automated batch triggers (`<48 hrs`) with `<5-day` execution SLA inside the 30-day window.
    - *Phase 3 (Months 5–6) — Retraining & Uplift Expansion:* Quarterly retraining on pilot outcomes, *Uplift Modeling* (*persuadables* vs. *sure-stays*), and 5G/FWA bundling expansion.
  - **Four Risk Mitigations:** (1) *Drift* → monthly PSI & ECE monitoring + quarterly retraining; (2) *Contact Fatigue* → max 1 offer/6 mo; (3) *Privacy/Fairness* → permanent exclusion of `ethnic` & `Customer_ID` + hashed IDs; (4) *CS Capacity* → digital delivery for `Bill-Shock` (`80.25%`) & `Device Upgrade` (`19.06%`).
- **Visual & Table Mapping:**
  - **3-Phase Roadmap Table** + **4-Pillar Risk & Governance Matrix**.
- **Slide Footnotes:**
  - *AI customer-service governance principles aligned with McKinsey telco best practices [8].*

---

## Slide 15 — References & Sources
- **Action Title:** Complete Primary Reference List
- **Executive Key Takeaway:** All market figures, U.S. carrier benchmarks, margin assumptions, and AI retention findings are backed by verifiable, publicly accessible sources.
- **Slide Content:**
  1. `[1]` CTIA (2025). *2025 Annual Survey Highlights*. https://www.ctia.org/news/2025-annual-survey-highlights
  2. `[2]` CTIA (2026). *2026 Annual Survey Highlights*. https://www.ctia.org/news/2026-annual-survey-highlights
  3. `[3]` Federal Communications Commission / FCC (2024). *2024 Communications Marketplace Report (FCC 24-136)*. https://docs.fcc.gov/public/attachments/FCC-24-136A1.pdf
  4. `[4]` AT&T Inc. *Investor Relations — FY 2024 & FY 2025 Financial Reporting*. https://investors.att.com
  5. `[5]` T-Mobile US, Inc. *Investor Relations — FY 2024 & FY 2025 Financial Reporting & News Releases*. https://investor.t-mobile.com/news-releases
  6. `[6]` Gallo, A. (2014). *The Value of Keeping the Right Customers*. Harvard Business Review. https://hbr.org/2014/10/the-value-of-keeping-the-right-customers
  7. `[7]` Reichheld, F. F. *Prescription for Cutting Costs*. Bain & Company. https://www.bain.com/insights/prescription-for-cutting-costs/
  8. `[8]` McKinsey & Company. *Why AI-Enabled Customer Service Is Key to Scaling Telco Personalization*. https://www.mckinsey.com/industries/technology-media-and-telecommunications/our-insights/why-ai-enabled-customer-service-is-key-to-scaling-telco-personalization
  9. `[9]` McKinsey & Company. *The Network Is the Product: How AI Can Put Telco Customer Experience in Focus*. https://www.mckinsey.com/industries/technology-media-and-telecommunications/our-insights/the-network-is-not-a-black-box-how-ai-can-put-telco-customer-experience-in-focus
- **Visual & Table Mapping:**
  - Clean numbered reference list `[1]`–`[9]` with full accessible URLs.
- **Slide Footnotes:**
  - *All market statistics, U.S. carrier churn benchmarks, margin anchors, and AI retention findings trace directly to public primary sources.*
