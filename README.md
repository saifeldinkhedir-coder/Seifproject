<div align="center">

# 🌊 HydroSovereign AI Engine — HSAE v6.0.0

[![ORCID](https://img.shields.io/badge/ORCID-0000--0003--0821--2991-a6ce39?style=flat&logo=orcid&logoColor=white)](https://orcid.org/0000-0003-0821-2991)
[![Email](https://img.shields.io/badge/Email-saifeldinkhedir%40gmail.com-D14836?style=flat&logo=gmail&logoColor=white)](mailto:saifeldinkhedir@gmail.com)
[![License](https://img.shields.io/badge/License-MIT-yellow?style=flat)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.12-3776AB?style=flat&logo=python&logoColor=white)](https://python.org)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.38-FF4B4B?style=flat&logo=streamlit&logoColor=white)](https://streamlit.io)
[![GEE](https://img.shields.io/badge/Google%20Earth%20Engine-ready-4285F4?style=flat&logo=google&logoColor=white)](https://earthengine.google.com)

**26 basins · 7 continents · 15,023 lines · 23 Python modules · Zero syntax errors**

*"Satellites can now see what declarations hide — and climate change will make the gap worse."*

</div>

---

## 👤 Author

**Seifeldin M.G. Alkedir** — سيف الدين محمد قسم الله الخضر

| | |
|--|--|
| 🎓 **Education** | M.Sc. Environmental Science · B.Sc. Chemistry — University of Khartoum |
| 💼 **Role** | Independent Researcher · Environmental Manager & Consulting Project Manager (10+ years) |
| 🏗️ **Projects** | NEOM · Saudi Aramco · Rua Al Madinah · Municipal Mega-Projects |
| 📜 **Certifications** | ISO 14001 · PMP · IOSH |
| 🛠️ **Technical** | CESMP · EIA/ESIA · Air & Noise Modelling (AERMOD, SoundPLAN) · GIS & Remote Sensing |
| 📍 **Location** | Madinah, Saudi Arabia |
| 📞 **Phone** | +966 0500896171 |
| 📧 **Email** | saifeldinkhedir@gmail.com |
| 🔬 **ORCID** | [0000-0003-0821-2991](https://orcid.org/0000-0003-0821-2991) |

---

## 🌊 What is HSAE?

**HSAE** is the first open-source platform that unifies **multi-source satellite remote sensing**, **conceptual rainfall-runoff modelling**, **machine learning**, and **international water law automation** into a single sovereign intelligence system for transboundary reservoir monitoring.

Four pillars:

| Pillar | Components |
|--------|-----------|
| 🛰️ **Satellite RS** | Sentinel-1 SAR · Sentinel-2 NDWI · GPM IMERG · MODIS ET/NDVI/LST · VIIRS NTL · Landsat WQ |
| 💧 **Hydrology** | HBV rainfall-runoff · Muskingum routing · MODFLOW groundwater · Penman-Monteith ET₀ |
| 🧠 **AI / ML** | RF + MLP + GBM Ensemble · Isolation Forest · Multi-step Forecast · Monte Carlo |
| ⚖️ **Water Law** | UN 1997 Convention (17 articles) · ICJ/PCA/ITLOS · Auto-protest · IPCC AR6 SSP scenarios |

Applied to **26 globally contested transboundary basins** across **7 continents**.

---

## 🔬 Original Scientific Contributions

Ten original indices and frameworks introduced in HSAE, documented here to establish priority of authorship.

### Group A — Indices & Metrics

| Symbol | Full Name | Formula | Module |
|--------|-----------|---------|--------|
| **ATDI** | Alkedir Transparency Deficit Index | `clip((I_adj − Q_out) / (I_adj + 0.001), 0, 1)` | hsae_tdi.py |
| **AHIFD** | Alkedir Human-Induced Flow Deficit | `(Q_nat − Q_obs) / Q_nat × 100` | hsae_hbv.py |
| **ASI** | Alkedir Sovereignty Index | `0.35·E + 0.25·ADTS + 0.25·F + 0.15·(1−D/5)` | hsae_opsroom.py |
| **ADTS** | Alkedir Digital Transparency Score | `max(0, 100 − ATDI)` | hsae_opsroom.py |
| **α = 0.30** | Alkedir MODIS ET Correction Coefficient | `I_adj = max(0, I_in − 0.30 × (ET_PM + ET_MODIS))` | hsae_tdi.py |

### Group B — Frameworks & Architectures

| Symbol | Full Name | Description | Module |
|--------|-----------|-------------|--------|
| **ALTM** | Alkedir Legal Threshold Mapping | ATDI/AHIFD → UN 1997 Arts. 5 / 7 / 9 / 12 | hsae_hbv.py |
| **AFSF** | Alkedir Forensic Scoring Function | `rolling_30(TDI).max() × 100` | hsae_v430.py |
| **ASCAF** | Alkedir SAR-NDWI Cloud-Adaptive Fusion | `S1·w + S2·(1−w)` ; w driven by cloud cover | gee_engine.py |
| **AWSRM** | Alkedir Water Sovereignty Risk Matrix | 2-D: ATDI × Dispute Level → 5 risk tiers | hsae_opsroom.py |
| **AHLB** | Alkedir HBV-Legal Bridge | HBV → AHIFD → ALTM → treaty article flags | hsae_hbv.py |

### Canonical TDI Formula (hsae_tdi.py — single source of truth)

```
I_adj  = max(0, I_in − 0.30 × (ET_PM + ET_MODIS))   [BCM/day]
TDI    = max(0, (I_adj − Q_out) / (I_adj + 0.001))    [0–1]
ATDI   = mean(TDI) × 100                               [%]
AFSF   = max(rolling_30(TDI)) × 100                   [%]
```

**Legal trigger thresholds (UN 1997):**

| TDI | Article | Violation |
|-----|---------|-----------|
| ≥ 0.25 | Art. 5 | Equitable & Reasonable Use |
| ≥ 0.40 | Art. 7 | No Significant Harm |
| ≥ 0.55 | Art. 9 | Regular Exchange of Data |

### Standard Methods (credited to original authors)

HBV (Bergström, 1992) · Penman-Monteith ET₀ (Allen et al., 1998) · SCS-CN (USDA, 1986) · Muskingum (McCarthy, 1938) · NSE/KGE (Nash & Sutcliffe, 1970; Gupta et al., 2009) · Random Forest (Breiman, 2001) · MODFLOW (McDonald & Harbaugh, 1988)

---

## 📊 System Statistics

| Metric | v5.0.0 | v6.0.0 |
|--------|--------|--------|
| Python source files | 15 | **23** |
| Lines of code | 9,893 | **15,023** |
| Global basins | 24 | **26** |
| Satellite sensors | 3 | **8** |
| UN 1997 articles automated | 12 | **17** |
| GEE Python API (live fetch) | ❌ | **✅** |
| AI models | RF only | **RF + MLP + GBM + IsolationForest** |
| Climate scenarios (SSP) | ❌ | **SSP1/2/3/5 to 2100** |
| SQLite persistence | ❌ | **✅** |
| Syntax errors | 0 | **0** |

---

## 🚀 Quick Start

```bash
# 1. Clone
git clone https://github.com/alkedir/hsae.git
cd hsae

# 2. Install dependencies
pip install streamlit pandas numpy scipy plotly folium streamlit-folium \
            scikit-learn requests openpyxl schedule python-telegram-bot \
            earthengine-api

# 3. (Optional) Activate GEE Live Engine — one-time browser login
earthengine authenticate

# 4. Run
streamlit run app.py
```

Opens at: **http://localhost:8501**

---

## 🏗️ Architecture

```
HydroSovereign_HSAE/
├── app.py                  Main router + simulation engine
├── basins_global.py        26-basin registry (single source of truth)
├── hsae_tdi.py             ★ Canonical TDI (ε = 0.001 · α = 0.30)
│
├── Satellite Data
│   ├── gee_engine.py       GEE Python API — live fetch (8 sensors)
│   ├── hsae_gee_data.py    GEE JS scripts + 5 live APIs + parsers + UI
│   └── ground_data.py      Compatibility shim
│
├── Scientific Core
│   ├── hsae_science.py     Water balance · Penman-Monteith ET₀ · Monte Carlo
│   ├── hsae_hbv.py         HBV + AHIFD + ALTM + AHLB
│   ├── hsae_validation.py  NSE / KGE / RMSE / Taylor Diagram + GRDC
│   ├── hsae_v430.py        Hybrid DSS + ASCAF + AFSF
│   └── hsae_v990.py        Legal Nexus + ATDI + α=0.30
│
├── AI & Climate
│   ├── hsae_ai.py          RF+MLP+GBM + Isolation Forest + forecast
│   └── hsae_climate.py     SSP1-2.6/2-4.5/3-7.0/5-8.5 to 2100
│
├── Legal & Governance
│   ├── hsae_legal.py       UN 1997 Arts 5–21 + ICJ/PCA/ITLOS
│   └── hsae_audit.py       RBAC + SHA-256 audit trail
│
├── Operations
│   ├── hsae_opsroom.py     ASI + ADTS + AWSRM + SITREP dashboard
│   ├── hsae_alerts.py      4-level alerts + Telegram + Art.12 protest
│   ├── hsae_devops.py      CI/CD + monitoring
│   └── hsae_db.py          SQLite: run history + anomaly events
│
├── Domain Modules
│   ├── hsae_quality.py     WQI — WHO/FAO — Arts. 20/21
│   ├── hsae_groundwater.py MODFLOW + FAO-56 irrigation + Muskingum
│   ├── hsae_export.py      HTML/Excel/JSON/GeoJSON export
│   └── hsae_intro.py       Welcome + basin explorer
│
└── Configuration
    ├── requirements.txt
    └── .streamlit/config.toml
```

---

## 🛰️ GEE Workflow

**Option A — Python API (live):**
```bash
earthengine authenticate   # one-time
# Then use ⚡ GEE Live Engine tab in the app
```

**Option B — Manual export:**
1. **📡 Real Data · APIs** → **GEE Scripts** tab
2. Select sensor → copy JavaScript
3. Paste into [code.earthengine.google.com](https://code.earthengine.google.com) → Run → Export to Drive
4. Download CSV → upload in **GEE Uploads** tab → **🔗 Merge All Sources**

---

## 📖 Citation

```bibtex
@software{alkedir2026hsae,
  author  = {Alkedir, Seifeldin M.G.},
  title   = {HydroSovereign AI Engine (HSAE) v6.0.0},
  year    = {2026},
  version = {6.0.0},
  doi     = {10.5281/zenodo.XXXXXXX},
  url     = {https://github.com/alkedir/hsae},
  orcid   = {0000-0003-0821-2991}
}
```

> **Note:** Peer-reviewed methodology papers describing the Alkedir indices (ATDI, AHIFD, ASI, ALTM, AFSF, ASCAF, AWSRM, AHLB, ADTS, α) are in preparation. This repository and Zenodo DOI serve as the citable priority record in the interim.

---

## 📄 License

**MIT License** — free to use, modify, and distribute with attribution.

The ten original contributions listed above are documented here to record the original formulation. Any academic use must cite the Zenodo DOI and the author's ORCID.

---

<div align="center">
<i>Combining 10 years of field environmental practice with satellite science and AI<br>
to address the water sovereignty challenges of transboundary river basins.</i>
</div>
