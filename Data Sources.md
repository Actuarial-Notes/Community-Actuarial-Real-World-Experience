# Data Sources — CARE 2027 Flood Risk Assessment, Hamilton, Ontario

This document catalogues and evaluates data sources relevant to all three parts of the CARE 2027 Hamilton flood case study:

- **Part 1 — Topology and Physics of Flooding:** elevation, precipitation, hydrology, land/soil, and water-level data to model flood extent, depth, and flow.
- **Part 2 — Damage to Buildings and Infrastructure:** building inventories, vulnerability (depth-damage) functions, critical-infrastructure data, and claims history.
- **Part 3 — Financial Impact and Insurance Coverage:** loss/exposure data, solvency/regulatory data, affordability data, climate scenarios, and catastrophe-model platforms.

Each entry is evaluated on **access/cost**, **coverage**, **relevance**, **strengths**, and **limitations**. The catalogue goes beyond the sources named in the Case Study Instructions to reflect the broader landscape a real interdisciplinary team would use.

> **Guiding principle for a student competition:** Build on **free and open sources first** (government, regulator, academic, open-source). Treat **paid** commercial data (MPAC bulk data, CatIQ, MSA, vendor catastrophe models) as benchmarks that practitioners rely on but that students usually cannot license — and use their free public reports where available.

---

# Part 1: Topology and Physics of Flooding

## Summary

| # | Source | Sub-category | Cost | Priority |
|---|--------|--------------|------|----------|
| 1.1 | NRCan CanElevation (HRDEM / MRDEM) | Elevation / terrain | Free / open | **High** |
| 1.2 | OpenTopography | Elevation / terrain | Free | Medium |
| 1.3 | USGS Earth Explorer | Elevation / imagery | Free | Medium |
| 1.4 | Copernicus (Sentinel) / ERA5 | Imagery / reanalysis | Free | Medium |
| 1.5 | ECCC Historical Climate Data | Precipitation / weather | Free | **High** |
| 1.6 | ECCC Engineering Climate Datasets (IDF) | Rainfall extremes | Free | **High** |
| 1.7 | ClimateData.ca + IDF_CC Tool | Climate-adjusted rainfall | Free | **High** |
| 1.8 | Hamilton Conservation Authority Open Data Hub | Watershed / floodplain | Free / open | **High** |
| 1.9 | Lake Ontario water levels (IJC / DFO-CHS / NOAA) | Lake levels | Free | **High** |
| 1.10 | City of Hamilton Open Data | Stormwater / zoning | Free / open | **High** |
| 1.11 | Ontario GeoHub (LIO / GEO) | Provincial GIS | Free / open | **High** |
| 1.12 | CanSIS — Soil Landscapes of Canada | Soil / permeability | Free | Medium |

### 1.1 NRCan CanElevation Series — HRDEM & MRDEM — *(CDEM named in instructions)*
- **Access / Cost:** **Free / open data** (Open Government Licence). Via the Open Government Portal and FTP (GeoTIFF).
- **Coverage:** The **High-Resolution DEM (HRDEM)**, ~1 m, LiDAR-derived, includes Digital Terrain Model (DTM) and Digital Surface Model (DSM); ~500,000 km² across eight provinces incl. southern Ontario (Hamilton area covered). The **Medium-Resolution DEM (MRDEM)**, 30 m nationwide, has **replaced the older CDEM** named in the instructions.
- **Relevance:** The foundational terrain input for flood simulation — drainage, watershed delineation, flow paths, and the Niagara Escarpment's effect on flow.
- **Strengths:** Free, high resolution where LiDAR exists, authoritative, DTM+DSM split.
- **Limitations:** LiDAR coverage/vintage varies; large files need GIS skill.
- **Link:** https://open.canada.ca/data/en/dataset/957782bf-847c-4644-a757-e383c0057995

### 1.2 OpenTopography
- **Access / Cost:** **Free** (academic, NSF-funded).
- **Coverage:** Hosts the 1 m HRDEM mosaic of southern Canada (DTM/DSM) plus global topography, with on-the-fly processing and derived products (slope, hillshade).
- **Relevance:** Convenient access/clipping of Canadian LiDAR DEMs and easy derivative generation for hydraulic modeling.
- **Strengths:** Free, easy subsetting, web-processing tools, good for teaching.
- **Limitations:** Mirrors NRCan data; no Hamilton-specific value beyond convenience.
- **Link:** https://portal.opentopography.org

### 1.3 USGS Earth Explorer — *named in instructions*
- **Access / Cost:** **Free** (requires free EROS account).
- **Coverage:** Landsat, Sentinel-2, MODIS, ASTER, **SRTM 1-arcsec DEM**, NAIP aerial photos, radar.
- **Relevance:** Satellite imagery for land-use/impervious-surface mapping and SRTM as a fallback DEM; imagery for historical flood-extent validation.
- **Strengths:** Free, deep archive, multi-sensor.
- **Limitations:** SRTM (~30 m) is coarse vs. Canadian LiDAR; US-centric portal.
- **Link:** https://earthexplorer.usgs.gov

### 1.4 Copernicus (Sentinel) / ERA5 Reanalysis
- **Access / Cost:** **Free** (Copernicus Data Space Ecosystem; Climate Data Store for ERA5).
- **Coverage:** Sentinel-1 radar (flood-extent mapping through cloud), Sentinel-2 optical; **ERA5** global reanalysis (precipitation, wind, pressure) hourly back to 1940.
- **Relevance:** Sentinel-1 is excellent for observed flood-extent calibration; ERA5 fills gaps in station precipitation and supports event reconstruction.
- **Strengths:** Free, frequent revisits, all-weather radar, long reanalysis record.
- **Limitations:** ERA5 coarse (~31 km) for urban flooding; processing pipeline required.
- **Link:** https://dataspace.copernicus.eu · https://cds.climate.copernicus.eu

### 1.5 Environment and Climate Change Canada — Historical Climate Data — *named in instructions*
- **Access / Cost:** **Free.**
- **Coverage:** Station-level historical precipitation, temperature, and hourly/daily/monthly records across Canada (climate.weather.gc.ca).
- **Relevance:** Observed precipitation records to define design storms and drive/validate runoff and flood models.
- **Strengths:** Free, authoritative, long records, Hamilton-area stations.
- **Limitations:** Station gaps/discontinuities; point data needs spatial interpolation.
- **Link:** https://climate.weather.gc.ca

### 1.6 ECCC Engineering Climate Datasets — IDF Curves
- **Access / Cost:** **Free.**
- **Coverage:** Short-duration rainfall **Intensity-Duration-Frequency (IDF)** statistics for 549 locations nationwide; downloadable tables/graphs with documentation.
- **Relevance:** IDF curves are the standard input for design-storm return periods feeding stormwater (SWMM) and rational-method runoff calculations.
- **Strengths:** Free, engineering-grade, station-specific.
- **Limitations:** Based on historical stationarity (no climate trend) — pair with 1.7.
- **Link:** https://climate.weather.gc.ca/prods_servs/engineering_e.html

### 1.7 ClimateData.ca + Western University IDF_CC Tool
- **Access / Cost:** **Free.**
- **Coverage:** Downscaled Canadian climate projections; **climate-change-scaled IDF data** on ClimateData.ca; the **IDF_CC** web tool updates local extreme-rainfall stats for climate change (pre-loaded with 898 ECCC stations).
- **Relevance:** Produces **forward-looking design storms** to test future flood scenarios — directly supports the "climate change projections" requirement.
- **Strengths:** Free, Canada-localized, bridges to Part 3 climate scenarios.
- **Limitations:** Scenario/methodology choices require judgement.
- **Links:** https://climatedata.ca · https://www.idf-cc-uwo.ca

### 1.8 Hamilton Conservation Authority — Open Data Hub
- **Access / Cost:** **Free / open** (CSV, KML, GeoJSON, GeoTIFF; WMS/WFS APIs).
- **Coverage:** Watershed boundaries, stream networks, elevation, land cover, and floodplain mapping for **Spencer Creek, Red Hill Creek**, Chedoke, Borer's Creek, etc. — the exact local watersheds the case study highlights.
- **Relevance:** The single most Hamilton-specific hydrology source — regulatory floodplains, subwatershed studies, and stream data for calibrating the physical model.
- **Strengths:** Free, hyper-local, multi-format, API access, authoritative for Hamilton watersheds.
- **Limitations:** Resolution/recency varies by watershed; some studies are PDF-only.
- **Links:** https://conservationhamilton.ca · https://hca-open-data-camaps.hub.arcgis.com

### 1.9 Lake Ontario Water Levels — IJC / DFO-CHS / NOAA
- **Access / Cost:** **Free.**
- **Coverage:** **IJC** daily mean Lake Ontario levels (six gauges incl. Toronto/Port Weller); **DFO Canadian Hydrographic Service** (33 Canadian-shore stations); **NOAA GLERL/CO-OPS** records back to 1860 and the Lake Ontario Operational Forecast System (LOOFS).
- **Relevance:** Lake-level boundary conditions are critical given Hamilton's position at the west end of Lake Ontario — needed for coastal/lakeshore flood and backwater scenarios.
- **Strengths:** Free, long high-quality records, real-time + forecast.
- **Limitations:** Multiple agencies/datums to reconcile (CGVD2013 vs. IGLD).
- **Links:** https://ijc.org/en/loslrb/watershed/water-levels · https://www.glerl.noaa.gov/data/wlevels/

### 1.10 City of Hamilton — Open Data — *named in instructions*
- **Access / Cost:** **Free / open** (ArcGIS Open Data / open.hamilton.ca).
- **Coverage:** Stormwater infrastructure ("3 Waters"), zoning, land use, infrastructure, and municipal boundaries.
- **Relevance:** Urban drainage network (storm sewers, culverts, retention ponds) and land use / impervious surfaces for the urban hydrology model.
- **Strengths:** Free, local, downloadable, regularly updated.
- **Limitations:** Some asset detail restricted; completeness varies by layer.
- **Link:** https://open.hamilton.ca

### 1.11 Ontario GeoHub — Land Information Ontario (now Geospatial Ontario / GEO)
- **Access / Cost:** **Free / open** (Open Government Licence – Ontario).
- **Coverage:** Road networks, wetlands, rivers/streams, soils, bedrock, orthophotography, satellite imagery, land cover, municipal boundaries.
- **Relevance:** Provincial-scale watershed, hydrography, and land-cover layers to extend beyond city limits and fill gaps in municipal data.
- **Strengths:** Free, broad provincial coverage, web services.
- **Limitations:** Provincial scale can be coarser than municipal/HCA data.
- **Link:** https://geohub.lio.gov.on.ca

### 1.12 CanSIS — Soil Landscapes of Canada (SLC)
- **Access / Cost:** **Free** (FGDB, GeoJSON, CSV).
- **Coverage:** National soil/landscape attributes (drainage, texture) at ~1:1M scale via the National Soil Database.
- **Relevance:** Soil permeability/infiltration parameters for runoff and the rational method.
- **Strengths:** Free, national, authoritative.
- **Limitations:** Coarse 1:1M scale — supplement with local/urban soil surveys.
- **Link:** https://sis.agr.gc.ca/cansis/

---

# Part 2: Damage to Buildings and Infrastructure

## Summary

| # | Source | Sub-category | Cost | Priority |
|---|--------|--------------|------|----------|
| 2.1 | MPAC | Building inventory / valuation | Free (own/limited); paid (bulk) | **High** |
| 2.2 | StatCan Open Database of Buildings (ODB) | Building footprints | Free / open | **High** |
| 2.3 | Microsoft / OpenStreetMap footprints | Building footprints | Free / open | Medium |
| 2.4 | HAZUS (FEMA) + NRCan Hazus-Canada | Damage / vulnerability functions | Free | **High** |
| 2.5 | FEMA FAST tool | Open-source loss tool | Free / open | Medium |
| 2.6 | Insurance Bureau of Canada — claims | Historical flood claims | Free (aggregate) | **High** |
| 2.7 | Institute for Catastrophic Loss Reduction (ICLR) | Research / vulnerability | Free | **High** |
| 2.8 | Statistics Canada | Building age/type by census | Free | **High** |
| 2.9 | City of Hamilton + Ontario GeoHub | Critical infrastructure | Free / open | **High** |
| 2.10 | Public Safety Canada | Critical infrastructure / hazards | Free | Medium |

### 2.1 MPAC (Municipal Property Assessment Corporation) — *named in instructions*
- **Access / Cost:** **Tiered.** Property owners view their own (and limited other) data **free** via *AboutMyProperty*; municipalities/appellants get reports free in specific contexts; **bulk/third-party assessment data is paid** under MPAC's data-release guidelines.
- **Coverage:** ~5.6 million Ontario properties — assessed values, construction type, age, square footage, occupancy.
- **Relevance:** The authoritative building inventory for classifying Hamilton's stock and estimating replacement/repair costs in depth-damage calculations.
- **Strengths:** Comprehensive, Ontario-authoritative, rich attributes.
- **Limitations:** Bulk data is **paid** and access-restricted (privacy); students likely limited to aggregate/sample use. Combine with free footprints (2.2) and StatCan (2.8).
- **Link:** https://www.mpac.ca

### 2.2 Statistics Canada — Open Database of Buildings (ODB)
- **Access / Cost:** **Free / open** (Open Government Licence; zipped shapefiles).
- **Coverage:** ~4.4 million building footprints aggregated from 107 government open-data sources (incl. Ontario/Hamilton).
- **Relevance:** Free building footprints to define the exposed building set, count structures by flood zone, and join to attributes.
- **Strengths:** Free, national, OSM-compatible licence.
- **Limitations:** Footprints only (limited attributes); coverage/recency varies by municipality.
- **Link:** https://www.statcan.gc.ca/en/lode/databases/odb

### 2.3 Microsoft Building Footprints / OpenStreetMap
- **Access / Cost:** **Free / open** (ODbL for OSM).
- **Coverage:** ML-derived Canadian building footprints (Microsoft) and crowd-sourced OSM buildings, roads, and POIs.
- **Relevance:** Gap-filling/cross-validation of building footprints and quick infrastructure context (roads, bridges, facilities).
- **Strengths:** Free, global, frequently updated.
- **Limitations:** Variable completeness/attribution; OSM quality is uneven locally.
- **Link:** https://www.openstreetmap.org · https://github.com/microsoft/CanadianBuildingFootprints

### 2.4 HAZUS (FEMA) + NRCan Hazus-Canada — *(HAZUS named in instructions)*
- **Access / Cost:** **Free** (HAZUS software + technical manuals; NRCan co-developing a Canadian version under a FEMA agreement).
- **Coverage:** Standardized **depth-damage and fragility functions**, building/infrastructure inventory schema, and multi-hazard loss methodology. Canadian flood applications documented (e.g., Fredericton case studies).
- **Relevance:** The standard, defensible source of depth-damage curves and a full loss-estimation framework for Part 2 — and feeds Part 3's loss modeling.
- **Strengths:** Free, peer-reviewed, North American adaptation underway, transparent methodology.
- **Limitations:** Default curves are US-derived (FIA data through 2001) and need Canadian calibration; software is data-hungry.
- **Links:** https://www.fema.gov/flood-maps/products-tools/hazus · NRCan Hazus-Canada methodology (Tandfonline / NRCan)

### 2.5 FEMA FAST (Flood Assessment Structure Tool)
- **Access / Cost:** **Free / open source.**
- **Coverage:** Lightweight tool combining structure data + flood depths + damage functions — an open alternative to full HAZUS flood modeling.
- **Relevance:** Faster, scriptable damage estimation for a defined Hamilton structure inventory.
- **Strengths:** Free, transparent, easier than full HAZUS.
- **Limitations:** Less comprehensive than HAZUS; requires curated inputs.
- **Link:** https://www.fema.gov/sites/default/files/documents/fema_flood-assessment-structure-tool.pdf

### 2.6 Insurance Bureau of Canada — Historical Flood Claims — *named in instructions*
- **Access / Cost:** **Free** aggregate reports; granular claims data is **members-only**.
- **Coverage:** Industry water-damage/flood claims trends and catastrophic-event loss commentary.
- **Relevance:** Empirical anchor for calibrating/validating depth-damage outputs against real claim severities.
- **Strengths:** Authoritative, Canada-specific, free headline data.
- **Limitations:** Micro-level claims not public; aggregate not Hamilton-specific.
- **Link:** https://www.ibc.ca

### 2.7 Institute for Catastrophic Loss Reduction (ICLR)
- **Access / Cost:** **Free** publications and tools.
- **Coverage:** P&C-industry-founded research institute (Western University). Basement-flooding and urban-flood vulnerability research, mitigation guidance, the **CatView** natural-hazard GIS portal, and the **IDF_CC** tool. Reports such as *Making Flood Insurable for Canadian Homeowners* and *An Assessment of Flood Risk Management in Canada*.
- **Relevance:** Canadian-specific flood vulnerability/mitigation evidence to refine damage functions and connect Part 2 damages to Part 3 insurability/mitigation.
- **Strengths:** Free, Canadian, practitioner-oriented, bridges damage and insurance.
- **Limitations:** Research/guidance rather than raw structured datasets.
- **Link:** https://www.iclr.org/flooding/

### 2.8 Statistics Canada — Building Age & Construction Type — *named in instructions*
- **Access / Cost:** **Free** (Census of Population; most tables).
- **Coverage:** Dwelling age, structural type, and tenure by census tract / dissemination area.
- **Relevance:** Building-stock characterization by neighbourhood to assign vulnerability classes where MPAC bulk data is unavailable.
- **Strengths:** Free, neighbourhood granularity, authoritative.
- **Limitations:** Census categories are coarse vs. engineering classes; periodic updates.
- **Link:** https://www.statcan.gc.ca

### 2.9 City of Hamilton + Ontario GeoHub — Critical Infrastructure — *(City of Hamilton named in instructions)*
- **Access / Cost:** **Free / open.**
- **Coverage:** Municipal infrastructure asset inventories, critical-facility locations (water/wastewater, roads, bridges), plus provincial layers (hospitals, utilities) via GeoHub.
- **Relevance:** Maps critical infrastructure and interdependencies (e.g., power → hospitals) for cascading-failure and network analysis.
- **Strengths:** Free, local + provincial, downloadable.
- **Limitations:** Security-sensitive asset detail may be withheld; completeness varies.
- **Links:** https://open.hamilton.ca · https://geohub.lio.gov.on.ca

### 2.10 Public Safety Canada — Critical Infrastructure & Hazard Data
- **Access / Cost:** **Free.**
- **Coverage:** National critical-infrastructure framework, the National Risk Profile flood backgrounders, and (cross-cutting) the Canadian Disaster Database.
- **Relevance:** Context for critical-infrastructure interdependencies and national flood risk framing.
- **Strengths:** Free, authoritative national perspective.
- **Limitations:** High-level; not asset-level for Hamilton.
- **Link:** https://www.publicsafety.gc.ca

---

# Part 3: Financial Impact and Insurance Coverage

Part 3 asks teams to estimate expected annual losses (EAL), price flood insurance premiums, assess affordability and uptake, model insurer solvency/reinsurance, and evaluate the role of government in catastrophic scenarios.

## Summary

| # | Source | Category | Cost | Priority |
|---|--------|----------|------|----------|
| 3.1 | Insurance Bureau of Canada (IBC) | Industry loss/exposure | Free reports; members-only detail | **High** |
| 3.2 | CatIQ | Industry loss/exposure | Paid subscription | Medium (benchmark) |
| 3.3 | MSA Research | Insurer financials | Paid subscription | Medium (solvency) |
| 3.4 | Swiss Re sigma / Munich Re NatCatSERVICE | Global cat-loss benchmarks | Free reports; paid DB | Medium |
| 3.5 | Public Safety Canada — Canadian Disaster Database | Disaster cost history | Free / open | **High** |
| 3.6 | Parliamentary Budget Officer (PBO) | Fiscal/disaster projections | Free | **High** |
| 3.7 | DFAA / National Flood Insurance Program | Govt. cost-sharing & policy | Free | **High** |
| 3.8 | OSFI (MCT, B-15, SCSE, returns) | Solvency / regulation | Free | **High** |
| 3.9 | Bank of Canada / OSFI climate scenarios | Climate stress testing | Free | Medium-High |
| 3.10 | FSRA (Ontario) | Provincial regulation | Free | Medium |
| 3.11 | Statistics Canada | Affordability / socioeconomic | Free | **High** |
| 3.12 | CMHC — Housing Market Information Portal | Property values / mortgages | Free | **High** |
| 3.13 | IPCC + ClimateData.ca | Climate scenarios | Free | **High** |
| 3.14 | Commercial cat models (RMS, Verisk, JBA, Fathom, KatRisk) | Loss engine | Paid (enterprise) | Low (reference) |
| 3.15 | Oasis Loss Modelling Framework | Open-source cat-model platform | Free / open | **High** |
| 3.16 | NRCan flood mapping / Flood Risk Finder | Hazard exposure | Free / open | **High** |
| 3.17 | CIA / SOA / CAS actuarial research | Methodology | Free | **High** |
| 3.18 | Actuaries Climate Index / ACRI | Climate-loss index | Free | Medium |

## 3A. Insurance Industry Loss & Exposure Data

### 3.1 Insurance Bureau of Canada (IBC) — *named in instructions*
- **Access / Cost:** **Free** public reports/news; granular industry loss/exposure data is **members-only**.
- **Coverage:** Annual catastrophe insured-loss totals, flood commentary, exposure estimates (~1.5M high-risk homes; 80% of cities partly on floodplains), and the influential 2022 *Adapting to Rising Flood Risk* report.
- **Relevance:** Anchors industry loss magnitudes and frames the national flood-program and affordability/uptake debate.
- **Strengths:** Authoritative, Canada-specific, free headlines, flood-policy focus.
- **Limitations:** No public micro-data; aggregate, not Hamilton-specific.
- **Link:** https://www.ibc.ca

### 3.2 CatIQ (Catastrophe Indices and Quantification Inc.)
- **Access / Cost:** **Paid subscription** (PERILS AG subsidiary). Public blog/press releases free.
- **Coverage:** Per-event insured-loss indices; annual Industry Exposure Database (2026: ~CAD 23T property sums insured); insured-vs-societal loss splits (CAD 2.4B / 3.4B in 2025).
- **Relevance:** Gold-standard benchmark for event losses and the insured-vs-economic "protection gap."
- **Strengths:** Granular, per-event, Canada-specific.
- **Limitations:** Subscription cost; full data out of reach for students (use free press releases).
- **Link:** https://public.catiq.com

### 3.3 MSA Research
- **Access / Cost:** **Paid** (*MSA Researcher* platform; ~90% of industry).
- **Coverage:** Insurer-level financials, capital, premiums, loss ratios, benchmarking.
- **Relevance:** Supports insurer **solvency/reinsurance** modeling (capital adequacy, PML coverage).
- **Strengths:** Most comprehensive Canadian insurer financial database.
- **Limitations:** Paid; OSFI public returns (3.8) are the free substitute.
- **Link:** https://www.msaresearch.com

### 3.4 Swiss Re *sigma* / Munich Re *NatCatSERVICE*
- **Access / Cost:** **Free** report PDFs; underlying databases paid/restricted.
- **Coverage:** Global/regional natural-catastrophe insured and economic losses, long series, peril breakdowns.
- **Relevance:** Benchmarks for loss trends, the global protection gap, and reinsurance context.
- **Strengths:** Long consistent series; respected methodology; free reports.
- **Limitations:** Global focus; little Hamilton/Canada granularity.
- **Links:** https://www.swissre.com/institute · https://www.munichre.com/en/solutions/reinsurance-property-casualty/natcatservice.html

## 3B. Government Disaster Cost & Policy Data

### 3.5 Public Safety Canada — Canadian Disaster Database (CDD)
- **Access / Cost:** **Free / open** (full spreadsheet via Open Government Portal; geospatial viewer).
- **Coverage:** 1,000+ disasters since 1900 — fatalities, evacuations, and **estimated total costs**, with a built-in CPI normalization tool.
- **Relevance:** Historical Canadian flood frequency/severity for fitting loss distributions and exceedance-probability curves.
- **Strengths:** Free, long history, normalizable, machine-readable.
- **Limitations:** Coarse cost estimates; finalized only post-event; not building-level.
- **Link:** https://www.publicsafety.gc.ca/cnt/rsrcs/cndn-dsstr-dtbs/index-en.aspx

### 3.6 Parliamentary Budget Officer (PBO)
- **Access / Cost:** **Free** independent fiscal analysis.
- **Coverage:** **DFAA** cost projections — floods the costliest disaster type (~$1.2B/yr DFAA support); total disaster costs rising from ~$881M/yr (2010–24) to ~$1.8B/yr (2025–34).
- **Relevance:** Quantifies government fiscal exposure — central to the "role of government" question.
- **Strengths:** Independent, transparent, forward-looking.
- **Limitations:** National aggregates, not Hamilton-specific.
- **Link:** https://www.pbo-dpb.ca

### 3.7 DFAA & the National Flood Insurance Program (program design)
- **Access / Cost:** **Free** federal policy documents.
- **Coverage:** DFAA cost-sharing formula; design of Canada's forthcoming low-cost **National Flood Insurance Program** (Crown reinsurance + high-risk subsidy, premium caps, ~$31.7M + $15M seed funding, targeted launch ~2026).
- **Relevance:** Reference design for the policy options teams must evaluate (mandatory coverage, subsidies, reinsurance backstops).
- **Strengths:** Directly on-topic; defines real Canadian policy framework.
- **Limitations:** Still evolving; final parameters not fully public.
- **Link:** https://www.ibc.ca/issues-and-advocacy/climate/canadians-need-flood-protection

## 3C. Regulatory & Solvency Data

### 3.8 OSFI — *named in instructions*
- **Access / Cost:** **Free.**
- **Coverage:** **MCT (Minimum Capital Test)** for P&C insurers; **Guideline B-15** (Climate Risk Management, updated March 2025); **Standardized Climate Scenario Exercise (SCSE)** incl. flood-exposed regions; public insurer financial returns.
- **Relevance:** Backbone for solvency, capital modeling (TVaR/PML), and reinsurance need — and a free substitute for MSA at the regulatory-return level.
- **Strengths:** Authoritative, free, defines capital requirements.
- **Limitations:** Dense documents; returns require parsing.
- **Link:** https://www.osfi-bsif.gc.ca

### 3.9 Bank of Canada / OSFI Climate Scenario Analysis
- **Access / Cost:** **Free** reports.
- **Coverage:** 2022 BoC-OSFI Climate Scenario Analysis Pilot and a follow-on flood project on residential real-estate lending exposure (basis for SCSE region selection).
- **Relevance:** Methodology for flood-driven financial stress testing.
- **Strengths:** Canadian, flood-specific, rigorous.
- **Limitations:** Focused on lender/insurer exposure, not premium pricing.
- **Link:** https://www.bankofcanada.ca/2022/01/bank-canada-osfi-pilot-helps-canadian-financial-sector-assess-climate-change-risks/

### 3.10 FSRA (Financial Services Regulatory Authority of Ontario)
- **Access / Cost:** **Free.**
- **Coverage:** Ontario market conduct, property/auto insurance regulation, consumer protection.
- **Relevance:** Provincial regulatory backdrop for a Hamilton-focused product.
- **Strengths:** Ontario-specific, free.
- **Limitations:** Less tied to flood capital/pricing than OSFI.
- **Link:** https://www.fsrao.ca

## 3D. Socioeconomic & Affordability Data

### 3.11 Statistics Canada — *named in instructions*
- **Access / Cost:** **Free** (most tables; some custom tabulations paid).
- **Coverage:** Household income (Census, Canadian Income Survey), the **Canadian Index of Multiple Deprivation (CIMD)**, and research on flooding–deprivation intersections.
- **Relevance:** Core inputs for affordability (premium-to-income ratios by Hamilton neighbourhood) and equity/uptake.
- **Strengths:** Authoritative, neighbourhood-level, free, existing flood-deprivation research.
- **Limitations:** Income data lags; not flood-specific alone.
- **Link:** https://www.statcan.gc.ca

### 3.12 CMHC — Housing Market Information Portal (HMIP) — *named in instructions*
- **Access / Cost:** **Free** portal.
- **Coverage:** Property/housing values, income ranges, mortgage and debt indicators to census-tract level.
- **Relevance:** Property values feed ground-up loss and insured-value (TIV) estimates; mortgage data inform affordability and lender exposure.
- **Strengths:** Free, fine geography, authoritative.
- **Limitations:** Market-level values, not individual replacement costs (pair with MPAC).
- **Link:** https://www03.cmhc-schl.gc.ca/hmip-pimh

## 3E. Climate Scenario Data

### 3.13 IPCC + Canadian Climate Projections — *named in instructions*
- **Access / Cost:** **Free** (IPCC AR6; ClimateData.ca; ECCC).
- **Coverage:** Precipitation-intensity projections, RCP/SSP scenarios, climate-adjusted IDF curves.
- **Relevance:** Drives forward-looking loss adjustment — shifting EAL and EP curves under climate change.
- **Strengths:** Free, authoritative, Canadian-localized options.
- **Limitations:** Translating projections into loss multipliers needs hydrological modeling (links to Part 1).
- **Links:** https://www.ipcc.ch · https://climatedata.ca

## 3F. Catastrophe Modeling Platforms

### 3.14 Commercial Cat Model Vendors — Moody's RMS, Verisk, JBA, Fathom, KatRisk
- **Access / Cost:** **Paid / enterprise.** Increasingly accessible via open platforms (Moody's IRP, Verisk Model Exchange, Oasis). Verisk/KatRisk/RMS underpin the US NFIP "Risk Rating 2.0."
- **Coverage:** Probabilistic flood event sets, depth grids, vulnerability functions, financial loss modules.
- **Relevance:** Industry-standard engines for stochastic event sets, EP curves, and PML/TVaR.
- **Strengths:** Validated, granular, production-grade.
- **Limitations:** Prohibitively expensive for students; pricing not public. Use methodology papers as reference.
- **Links:** https://www.moodys.com/web/en/us/capabilities/catastrophe-modeling.html · https://www.jbarisk.com · https://www.fathom.global

### 3.15 Oasis Loss Modelling Framework (LMF)
- **Access / Cost:** **Free / open source** (BSD-3, GitHub).
- **Coverage:** Full simulation engine, standardized hazard/vulnerability formats, financial module, web UI + API (e.g., the open Future Danube flood model).
- **Relevance:** Lets a team **actually build and run** a catastrophe model end-to-end without licensing — event sets, depth-damage curves (Part 2), insured losses with deductibles/limits.
- **Strengths:** Free, industry-grade, transparent, extensible.
- **Limitations:** Technical setup; team supplies Hamilton hazard/vulnerability data.
- **Links:** https://oasislmf.org · https://github.com/oasislmf

### 3.16 NRCan Flood Mapping — FHIMP, Flood Risk Finder, Canada Flood Map Inventory
- **Access / Cost:** **Free / open data** (National Adaptation Strategy; $164.2M FHIMP, 2024–2028).
- **Coverage:** Canada's **Flood Risk Finder** (first national public flood hazard/risk portal, provincial opt-in), the **Canada Flood Map Inventory** (address-searchable), regional maps via GEO.CA.
- **Relevance:** Defines the exposed asset footprint — which Hamilton properties fall in which flood zones — the spatial basis for assigning losses and risk-based premiums.
- **Strengths:** Free, official, improving coverage.
- **Limitations:** Coverage still being completed; Hamilton availability depends on Ontario opt-in (HCA mapping in 1.8 is the local complement).
- **Link:** https://natural-resources.canada.ca/science-data/science-research/natural-hazards/flood-mapping

## 3G. Actuarial Methodology & Climate-Loss Indices

### 3.17 CIA / SOA / CAS Flood & Climate Research
- **Access / Cost:** **Free** publications.
- **Coverage:** The joint 2018 report *Incorporation of Flood and Other Catastrophe Model Results into Pricing and Underwriting*, plus CIA climate practice-area resources and CAS climate research.
- **Relevance:** Direct methodological guidance on premium calculation, loading, and embedding cat-model output into pricing — tailored to Canadian actuaries.
- **Strengths:** Free, actuary-focused, Canada-relevant, peer-reviewed.
- **Limitations:** Guidance, not data; pair with loss/exposure sources.
- **Link:** https://www.cia-ica.ca/actuaries/practice-areas/climate/

### 3.18 Actuaries Climate Index (ACI) & Actuaries Climate Risk Index (ACRI)
- **Access / Cost:** **Free** data downloads.
- **Coverage:** ACI tracks climate-extreme frequency and sea-level change; ACRI links extremes to economic/human losses. Hamilton falls in the **Northeast Forest (NEF)** region.
- **Relevance:** Free index for climate-loss trend signals and as a modeling covariate.
- **Strengths:** Free, profession-sponsored (incl. CIA), regional.
- **Limitations:** Coarse regional resolution — a trend indicator, not Hamilton-specific pricing.
- **Link:** https://actuariesclimateindex.org/data/

---

# Recommended Data Stack (free-first, by part)

**Part 1 — Physical model:** NRCan HRDEM + ECCC IDF/historical precipitation + ClimateData.ca/IDF_CC (future storms) + Hamilton Conservation Authority floodplains + Lake Ontario levels (IJC/DFO) + City of Hamilton stormwater + CanSIS soils → flood extent/depth/flow.

**Part 2 — Damage model:** StatCan Open Database of Buildings + MPAC/StatCan attributes + HAZUS-Canada / FAST depth-damage curves + ICLR vulnerability research + City of Hamilton/Ontario GeoHub critical infrastructure, validated against IBC claims trends → repair/replacement losses and high-risk assets.

**Part 3 — Financial/insurance model:**
1. *Loss history:* Canadian Disaster Database + IBC + Swiss Re sigma (benchmark).
2. *Exposure/values:* NRCan/HCA flood maps + CMHC HMIP + MPAC.
3. *Loss engine:* Oasis LMF (Part 1 hazard + Part 2 curves) → PML/TVaR, EP curves.
4. *Climate adjustment:* IPCC/ClimateData.ca + Actuaries Climate Index.
5. *Pricing:* CIA/SOA/CAS 2018 report → pure premium + loadings.
6. *Affordability/uptake:* StatCan income/CIMD + CMHC mortgage data.
7. *Solvency/capital:* OSFI MCT + B-15 + public returns (MSA as paid benchmark).
8. *Government role:* PBO DFAA projections + National Flood Insurance Program design + IBC advocacy.

**Paid sources to know but not rely on:** MPAC bulk data, CatIQ, MSA Research, and commercial cat models (RMS, Verisk, JBA, Fathom, KatRisk) are the practitioner standard; reference their existence and published outputs even where full licensing is out of reach.

---

*Compiled for CARE 2027 — Flood Risk Assessment in Hamilton, Ontario. Cost/access details reflect publicly available information as of June 2026 and should be reconfirmed directly with each provider.*
