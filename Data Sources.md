# Data Sources — Part 3: Financial Impact and Insurance Coverage

This document catalogues and evaluates data sources relevant to **Part 3: Financial Impact and Insurance Coverage** of the CARE 2027 Hamilton flood case study. Part 3 asks teams to estimate expected annual losses (EAL), price flood insurance premiums, assess affordability and uptake, model insurer solvency/reinsurance, and evaluate the role of government in catastrophic scenarios.

The sources below go beyond the five named in the Case Study Instructions (IBC, OSFI, CMHC, Statistics Canada, IPCC) to cover the broader landscape an actuarial team would realistically draw on. Each entry is evaluated on **access/cost**, **coverage**, **relevance to Part 3**, **strengths**, and **limitations**.

> **Note on the case study context:** This is a student competition. The practical recommendation is to **build on free and open sources first** (government, regulator, open-source models) and treat paid commercial data (CatIQ, MSA, vendor cat models) as "good to know exists" benchmarks that real practitioners use but that students generally cannot license. Where a paid source has a free public-facing report, that report is the usable artifact.

---

## Quick-Reference Summary

| # | Source | Category | Cost | Free artifact available? | Priority for Part 3 |
|---|--------|----------|------|--------------------------|---------------------|
| 1 | Insurance Bureau of Canada (IBC) | Industry loss/exposure | Free reports; detailed data members-only | Yes (annual loss stats, advocacy reports) | **High** |
| 2 | CatIQ (Catastrophe Indices & Quantification) | Industry loss/exposure | Paid subscription | Partial (press releases, blog) | Medium (benchmark) |
| 3 | MSA Research | Insurer financials | Paid subscription | Partial (quarterly summaries) | Medium (solvency) |
| 4 | Public Safety Canada — Canadian Disaster Database | Disaster cost history | Free / open data | Yes (full CSV download) | **High** |
| 5 | Parliamentary Budget Officer (PBO) | Fiscal/disaster cost projections | Free | Yes (full reports) | **High** |
| 6 | DFAA / National Flood Insurance Program design | Govt. cost-sharing & policy | Free | Yes (Public Safety, Budget docs) | **High** |
| 7 | OSFI (MCT, B-15, SCSE, financial returns) | Solvency / regulation | Free | Yes (guidelines, returns) | **High** |
| 8 | Bank of Canada / OSFI climate scenario work | Climate stress testing | Free | Yes (pilot + flood project reports) | Medium-High |
| 9 | Statistics Canada | Socioeconomic / affordability | Free (mostly) | Yes (census, CIS, CIMD) | **High** |
| 10 | CMHC — Housing Market Information Portal | Property values / mortgages | Free | Yes (full portal) | **High** |
| 11 | IPCC + Canadian climate projections | Climate scenarios | Free | Yes (AR6, ClimateData.ca) | **High** |
| 12 | Commercial cat models (Moody's RMS, Verisk, JBA, Fathom, KatRisk) | Hazard/vulnerability/loss engine | Paid (enterprise) | Methodology papers only | Low (reference) |
| 13 | Oasis Loss Modelling Framework | Open-source cat model platform | Free / open source | Yes (full software) | **High** |
| 14 | NRCan flood mapping (FHIMP, Flood Risk Finder, CFM Inventory) | Hazard exposure | Free / open data | Yes | **High** |
| 15 | Swiss Re sigma / Munich Re NatCatSERVICE | Global cat loss benchmarks | Free reports; paid DB | Yes (sigma PDFs) | Medium |
| 16 | CIA / SOA / CAS actuarial research | Methodology | Free | Yes (research papers) | **High** |
| 17 | Actuaries Climate Index / ACRI | Climate-loss index | Free | Yes (data downloads) | Medium |

---

## 1. Insurance Industry Loss & Exposure Data

### 1.1 Insurance Bureau of Canada (IBC) — *named in instructions*
- **Type / Access:** National P&C industry association. **Free** public reports, news releases, and advocacy publications; granular industry loss/exposure data is generally **members-only** (insurers).
- **Coverage:** Annual insured-loss totals for catastrophes, flood-specific commentary, exposure estimates (e.g., ~1.5 million high-risk homes, 80% of cities partly on floodplains), and detailed policy analysis such as *Adapting to Rising Flood Risk* (the influential 2022 flood insurance solutions report).
- **Relevance to Part 3:** Anchors industry-level loss magnitudes, supports the case for a national flood program, and frames affordability/uptake arguments.
- **Strengths:** Authoritative, Canada-specific, free headline figures, directly addresses flood insurance design.
- **Limitations:** Detailed claims/exposure micro-data not publicly downloadable; figures are aggregate, not Hamilton-specific.
- **Link:** https://www.ibc.ca

### 1.2 CatIQ (Catastrophe Indices and Quantification Inc.)
- **Type / Access:** Toronto-based subsidiary of PERILS AG. **Paid online subscription.** Widely regarded as the most authoritative source of Canadian catastrophe loss data.
- **Coverage:** Insured-loss indices by event, an annual **Industry Exposure Database** (2026 edition: ~CAD 23 trillion of property sums insured), and societal-vs-insured loss splits (e.g., CAD 2.4 B insured / 3.4 B societal in 2025).
- **Relevance to Part 3:** The gold-standard benchmark for calibrating event losses and the insured-vs-economic loss gap (the "protection gap" central to affordability/uptake analysis).
- **Strengths:** Granular, per-event, Canada-specific, exposure-weighted.
- **Limitations:** **Subscription cost** puts full data out of reach for most student teams. Public CatIQ blog/press releases give usable headline numbers for free.
- **Link:** https://public.catiq.com

### 1.3 MSA Research
- **Type / Access:** Independent Canadian firm; dominant provider of P&C/L&H insurer financial data via the **paid** *MSA Researcher* platform (~90% of the industry).
- **Coverage:** Insurer-level financial statements, capital, premiums, loss ratios, benchmarking.
- **Relevance to Part 3:** Directly supports **insurer solvency and reinsurance** modeling — capital adequacy, PML coverage, and stress testing of a flood-exposed carrier.
- **Strengths:** Most comprehensive Canadian insurer financial database.
- **Limitations:** Paid; aimed at industry. For students, OSFI's public financial returns (below) are a free substitute.
- **Link:** https://www.msaresearch.com

### 1.4 Swiss Re *sigma* / Munich Re *NatCatSERVICE*
- **Type / Access:** Global reinsurer research. Swiss Re **sigma** reports and Munich Re NatCat summaries are **free PDFs**; the underlying databases (sigma explorer, NatCatSERVICE) are paid/restricted.
- **Coverage:** Global and regional natural-catastrophe insured and economic losses, long time series, peril breakdowns (flood, SCS, wildfire).
- **Relevance to Part 3:** Benchmarks for loss trends, the global protection gap, and reinsurance pricing context.
- **Strengths:** Long, consistent series; respected methodology; free headline reports.
- **Limitations:** Global focus; little Hamilton/Canada granularity in free outputs.
- **Links:** https://www.swissre.com/institute · https://www.munichre.com/en/solutions/reinsurance-property-casualty/natcatservice.html

---

## 2. Government Disaster Cost & Policy Data

### 2.1 Public Safety Canada — Canadian Disaster Database (CDD)
- **Type / Access:** **Free / open data.** Full spreadsheet downloadable via the Open Government Portal; geospatial viewer available.
- **Coverage:** 1,000+ disasters since 1900 — location, dates, fatalities, injuries, evacuations, and **estimated total costs**, with a built-in CPI normalization tool.
- **Relevance to Part 3:** Historical Canadian flood frequency/severity for fitting loss distributions and exceedance-probability curves; normalization supports trend analysis.
- **Strengths:** Free, long history, normalizable, machine-readable.
- **Limitations:** Cost estimates are coarse and only finalized after events conclude; not building-level.
- **Link:** https://www.publicsafety.gc.ca/cnt/rsrcs/cndn-dsstr-dtbs/index-en.aspx · Open data: https://open.canada.ca/data/en/dataset/1c3d15f9-9cfa-4010-8462-0d67e493d9b9

### 2.2 Office of the Parliamentary Budget Officer (PBO)
- **Type / Access:** **Free** independent fiscal analysis.
- **Coverage:** Projections of the **Disaster Financial Assistance Arrangements (DFAA)** program — floods projected as the costliest disaster type, DFAA support averaging ~$1.2 B/yr (floods) and total disaster costs rising from ~$881 M/yr (2010–24) to ~$1.8 B/yr (2025–34).
- **Relevance to Part 3:** Quantifies the **government's role and fiscal exposure** in catastrophic scenarios — central to the "role of government" question.
- **Strengths:** Independent, transparent methodology, forward-looking.
- **Limitations:** National aggregates, not Hamilton-specific.
- **Link:** https://www.pbo-dpb.ca

### 2.3 DFAA & the National Flood Insurance Program (program design)
- **Type / Access:** **Free** federal policy documents (Public Safety Canada, federal budgets, SOREM working-group materials).
- **Coverage:** Cost-sharing formula of DFAA; design of Canada's forthcoming low-cost **National Flood Insurance Program** (Crown reinsurance + high-risk subsidy, premium caps, ~$31.7 M + $15 M seed funding, targeted launch ~2026).
- **Relevance to Part 3:** The reference design for **policy options** — mandatory coverage, subsidies, reinsurance backstops, premium caps — that teams are explicitly asked to evaluate.
- **Strengths:** Directly on-topic; defines the real Canadian policy framework.
- **Limitations:** Program still evolving; final parameters not fully public.
- **Links:** https://www.ibc.ca/issues-and-advocacy/climate/canadians-need-flood-protection · https://www.publicsafety.gc.ca

---

## 3. Regulatory & Solvency Data

### 3.1 OSFI — *named in instructions*
- **Type / Access:** **Free.** Federal prudential regulator. Publishes guidelines, capital tests, and **insurer financial/regulatory returns**.
- **Coverage:**
  - **MCT (Minimum Capital Test)** guideline — the capital adequacy framework for P&C insurers (risk margins, capital required for catastrophe risk).
  - **Guideline B-15: Climate Risk Management** (updated March 2025) — expectations for climate scenario analysis, capital/liquidity buffers, ICAAP/ORSA integration.
  - **Standardized Climate Scenario Exercise (SCSE)** — including flood-exposed regions selected from the BoC/OSFI flood project.
  - Public financial returns for federally regulated insurers.
- **Relevance to Part 3:** The backbone for **solvency, capital modeling (TVaR/PML), and reinsurance need** — and a free substitute for MSA at the regulatory-return level.
- **Strengths:** Authoritative, free, directly defines capital requirements teams must respect.
- **Limitations:** Regulatory framework documents are dense; returns require parsing.
- **Link:** https://www.osfi-bsif.gc.ca

### 3.2 Bank of Canada / OSFI Climate Scenario Analysis
- **Type / Access:** **Free** reports.
- **Coverage:** The 2022 BoC-OSFI **Climate Scenario Analysis Pilot** (transition risk) and a follow-on **flood project** assessing residential real-estate lending exposure to flood risk — the basis for SCSE region selection.
- **Relevance to Part 3:** Methodology and scenario design for **flood-driven financial stress testing** of lenders/insurers.
- **Strengths:** Canadian, flood-specific, methodologically rigorous.
- **Limitations:** Focused on financial-sector exposure rather than premium pricing.
- **Link:** https://www.bankofcanada.ca/2022/01/bank-canada-osfi-pilot-helps-canadian-financial-sector-assess-climate-change-risks/

### 3.3 FSRA (Financial Services Regulatory Authority of Ontario)
- **Type / Access:** **Free.** Ontario's provincial insurance regulator.
- **Coverage:** Provincial market conduct, auto/property insurance regulation, and consumer protection context for Ontario.
- **Relevance to Part 3:** Provincial regulatory backdrop for a Hamilton-focused product; complements federal OSFI.
- **Strengths:** Ontario-specific, free.
- **Limitations:** Less directly tied to flood capital/pricing than OSFI.
- **Link:** https://www.fsrao.ca

---

## 4. Socioeconomic & Affordability Data

### 4.1 Statistics Canada — *named in instructions*
- **Type / Access:** **Free** (most tables; some custom tabulations paid).
- **Coverage:** Household income (Census of Population, Canadian Income Survey), dwelling characteristics, and the **Canadian Index of Multiple Deprivation (CIMD)**. StatCan has published research specifically on *the intersection of flooding and deprivation* at the neighbourhood level.
- **Relevance to Part 3:** Core inputs for **affordability analysis** — premium-to-income ratios by Hamilton neighbourhood — and equity/uptake assessment.
- **Strengths:** Authoritative, neighbourhood-level (census tract/dissemination area), free, flood-deprivation research already exists.
- **Limitations:** Income data lags (latest ~2024 reference year); not flood-specific on its own.
- **Link:** https://www.statcan.gc.ca

### 4.2 CMHC — Housing Market Information Portal (HMIP) — *named in instructions*
- **Type / Access:** **Free** portal.
- **Coverage:** Property/housing values, household income ranges, mortgage and debt indicators, down to the **census-tract / neighbourhood** level.
- **Relevance to Part 3:** Property values feed **ground-up loss and insured-value (TIV)** estimates; mortgage/debt data inform affordability and the lender-exposure angle.
- **Strengths:** Free, fine geographic granularity, authoritative housing data.
- **Limitations:** Market-level values, not individual replacement costs; pair with MPAC (Part 2) for building-level valuation.
- **Link:** https://www03.cmhc-schl.gc.ca/hmip-pimh

---

## 5. Climate Scenario Data

### 5.1 IPCC + Canadian Climate Projections — *named in instructions*
- **Type / Access:** **Free.** IPCC AR6 reports and data; Canadian downscaled projections via **ClimateData.ca** and Environment and Climate Change Canada.
- **Coverage:** Precipitation-intensity projections, RCP/SSP scenarios, IDF (intensity-duration-frequency) curve updates for climate-adjusted return periods.
- **Relevance to Part 3:** Drives **forward-looking loss adjustment** — shifting EAL and exceedance-probability curves under climate change, a required dimension of the analysis.
- **Strengths:** Free, authoritative, Canadian-localized options available.
- **Limitations:** Translating climate projections into flood-loss multipliers requires hydrological modeling (links back to Part 1).
- **Links:** https://www.ipcc.ch · https://climatedata.ca

---

## 6. Catastrophe Modeling Platforms (Hazard → Vulnerability → Loss)

### 6.1 Commercial Cat Model Vendors — Moody's RMS, Verisk, JBA Risk Management, Fathom, KatRisk
- **Type / Access:** **Paid / enterprise licensing.** JBA, Fathom, and others are increasingly accessible through open platforms (Moody's Intelligent Risk Platform, Verisk Model Exchange, Oasis). Verisk, KatRisk, and Moody's RMS models underpin the U.S. NFIP "Risk Rating 2.0."
- **Coverage:** Probabilistic flood event sets, depth grids, vulnerability/damage functions, and financial loss modules for insured-loss estimation.
- **Relevance to Part 3:** The industry-standard engines for generating **stochastic event sets, EP curves, and PML/TVaR** — exactly the methodology Part 3 describes.
- **Strengths:** Validated, granular, production-grade.
- **Limitations:** **Prohibitively expensive** for students; pricing not public. Use published methodology papers as a **reference** for how to structure your own model.
- **Links:** https://www.moodys.com/web/en/us/capabilities/catastrophe-modeling.html · https://www.jbarisk.com · https://www.fathom.global

### 6.2 Oasis Loss Modelling Framework (LMF)
- **Type / Access:** **Free / open source** (BSD-3, GitHub). Not-for-profit.
- **Coverage:** Full simulation engine, standardized hazard/vulnerability data formats, financial module, web UI and API — the open analog to commercial platforms. Example: the open Future Danube fluvial/pluvial flood model.
- **Relevance to Part 3:** Lets a team **actually build and run a catastrophe model** end-to-end without licensing fees — generating event sets, applying depth-damage curves (from Part 2), and aggregating insured losses with deductibles/limits.
- **Strengths:** Free, industry-grade architecture, extensible, transparent.
- **Limitations:** Requires technical setup; teams must supply their own Hamilton hazard/vulnerability data.
- **Link:** https://oasislmf.org · https://github.com/oasislmf

### 6.3 NRCan Flood Mapping — FHIMP, Flood Risk Finder, Canada Flood Map Inventory
- **Type / Access:** **Free / open data.** Natural Resources Canada, under the National Adaptation Strategy ($164.2 M, 2024–2028 FHIMP investment).
- **Coverage:** **Canada's Flood Risk Finder** (first national public flood hazard/risk portal, opt-in by province), the **Canada Flood Map Inventory** (searchable by address), and regional flood hazard maps via GEO.CA.
- **Relevance to Part 3:** Defines the **exposed asset footprint** in Hamilton — which properties fall in which flood zones — the spatial basis for assigning losses and risk-based premiums.
- **Strengths:** Free, official, improving coverage, address-searchable.
- **Limitations:** Coverage is still being completed; Ontario/Hamilton availability depends on provincial opt-in. Hamilton Conservation Authority floodplain mapping (see Part 1) is a complementary local source.
- **Links:** https://natural-resources.canada.ca/science-data/science-research/natural-hazards/flood-mapping · https://geo.ca/flood-mapping/

---

## 7. Actuarial Methodology & Climate-Loss Indices

### 7.1 CIA / SOA / CAS Flood & Climate Research
- **Type / Access:** **Free** research publications.
- **Coverage:** Notably the joint 2018 report *Incorporation of Flood and Other Catastrophe Model Results into Pricing and Underwriting*, plus ongoing CIA climate practice-area resources and CAS climate research library.
- **Relevance to Part 3:** Direct **methodological guidance** on premium calculation, loading, and embedding cat-model output into pricing/underwriting — tailored to Canadian P&C actuaries.
- **Strengths:** Free, actuary-focused, Canada-relevant, peer-reviewed.
- **Limitations:** Guidance rather than data; needs to be paired with the loss/exposure sources above.
- **Link:** https://www.cia-ica.ca/actuaries/practice-areas/climate/

### 7.2 Actuaries Climate Index (ACI) & Actuaries Climate Risk Index (ACRI)
- **Type / Access:** **Free** data downloads (monthly/seasonal by region).
- **Coverage:** ACI tracks frequency of climate extremes and sea-level change; ACRI links those extremes to **economic and human losses**. Canada is covered by five regions (Hamilton falls in the **Northeast Forest, NEF** region).
- **Relevance to Part 3:** A free, ready-made index for **climate-loss trend signals** and as an explanatory variable in loss modeling.
- **Strengths:** Free, sponsored by the actuarial profession (incl. CIA), regional.
- **Limitations:** Coarse regional resolution — useful as a trend indicator, not for Hamilton-specific pricing.
- **Link:** https://actuariesclimateindex.org/data/

---

## Recommended Data Stack for Part 3 (free-first)

A student team can build a credible Part 3 analysis almost entirely on **free** sources, using paid sources only as published-report benchmarks:

1. **Loss frequency/severity & history:** Canadian Disaster Database + IBC annual loss reports + Swiss Re *sigma* (benchmark) → fit loss distributions and EP curves.
2. **Exposure & values:** NRCan/Hamilton flood maps (which properties) + CMHC HMIP + MPAC (Part 2) → total insured value at risk.
3. **Loss engine:** Oasis LMF (free) using Part 1 hazard + Part 2 depth-damage curves → ground-up and insured losses, PML/TVaR.
4. **Climate adjustment:** IPCC / ClimateData.ca + Actuaries Climate Index → forward-looking loss multipliers.
5. **Pricing methodology:** CIA/SOA/CAS 2018 flood-pricing report → structure pure premium + loadings.
6. **Affordability & uptake:** Statistics Canada income/CIMD + CMHC mortgage data → premium-to-income ratios by neighbourhood.
7. **Solvency & capital:** OSFI MCT + B-15 + public financial returns (MSA as paid benchmark) → capital adequacy and reinsurance need.
8. **Government role / policy:** PBO DFAA projections + National Flood Insurance Program design + IBC advocacy reports → evaluate subsidies, mandatory coverage, reinsurance backstop.

**CatIQ, MSA Research, and commercial cat models** are the tools real-world practitioners rely on; teams should reference their existence and published outputs even where full licensing is out of reach.

---

*Compiled for CARE 2027 — Flood Risk Assessment in Hamilton, Ontario. Cost/access details reflect publicly available information as of June 2026 and should be reconfirmed directly with each provider.*
