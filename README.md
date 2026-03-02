# HydroSovereign AI Engine (HSAE) v5.0.0

> **"Satellites can now see what declarations hide."**

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](https://python.org)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.28%2B-red.svg)](https://streamlit.io)
[![ORCID](https://img.shields.io/badge/ORCID-0000--0003--0821--2991-brightgreen.svg)](https://orcid.org/0000-0003-0821-2991)

**Author:** Seifeldin M.G. Alkedir  
**Affiliation:** Independent Researcher (BSc & MSc, University of Khartoum)  
**ORCID:** [0000-0003-0821-2991](https://orcid.org/0000-0003-0821-2991)  
**Version:** 5.0.0 | **Released:** February 2026

---

## What is HSAE?

HSAE is the **first open-source platform** that unifies multi-source satellite remote sensing,
conceptual rainfall-runoff modelling, machine learning, and international water law automation
into a single sovereign intelligence system for transboundary reservoir monitoring.

**Four pillars:**

- 🛰️ **Satellite RS** — Sentinel-1 SAR · Sentinel-2 MSI · GPM IMERG · MODIS MOD16
- 💧 **Hydrology** — HBV rainfall-runoff model · Muskingum routing · MODFLOW groundwater
- 🧠 **AI / ML** — Random Forest 90-day forecast · Monte Carlo uncertainty
- ⚖️ **Water Law** — UN 1997 Watercourses Convention (12 articles) · ICJ evidence chain

Applied to **24 globally contested transboundary basins** across 7 continents.

---

## Original Scientific Contributions

Ten original contributions introduced in HSAE v5.0.0, documented here to record
the original formulation and support proper attribution.

### Group A — Indices and Metrics

| Symbol | Full Name | Formula | Source |
|--------|-----------|---------|--------|
| **ATDI** | Alkedir Transparency Deficit Index | `clip((I_adj − Q_out) / (I_adj + 0.1), 0, 1)` | `hsae_v990.py L146` |
| **AHIFD** | Alkedir Human-Induced Flow Deficit | `(Q_nat − Q_obs) / Q_nat × 100` | `hsae_hbv.py L365` |
| **ASI** | Alkedir Sovereignty Index | `0.35·E + 0.25·ADTS + 0.25·F + 0.15·(1−D/5)` | `hsae_opsroom.py L109` |
| **ADTS** | Alkedir Digital Transparency Score | `max(0, 100 − ATDI)` | `hsae_opsroom.py L95` |
| **α = 0.3** | Alkedir MODIS ET Correction Coefficient | `I_adj = max(0, I_in − 0.3 × natural_loss)` | `hsae_v990.py L145` |

### Group B — Frameworks and Architectures

| Symbol | Full Name | Description | Source |
|--------|-----------|-------------|--------|
| **ALTM** | Alkedir Legal Threshold Mapping | ATDI/AHIFD → UN 1997 Arts. 5 / 7 / 12 | `hsae_hbv.py L366–367` |
| **AFSF** | Alkedir Forensic Scoring Function | `rolling_4_mean(ATDI).max() × 100` | `hsae_v430.py L153` |
| **ASCAF** | Alkedir SAR-NDWI Cloud-Adaptive Fusion | `S1·w + S2·(1−w); optical_ok = NDWI ≥ threshold` | `hsae_v430.py L99–100` |
| **AWSRM** | Alkedir Water Sovereignty Risk Matrix | 2-D: ATDI × Dispute Level → 5 risk tiers | `hsae_opsroom.py` |
| **AHLB** | Alkedir HBV-Legal Bridge | HBV output → AHIFD → ALTM → treaty article flags | `hsae_hbv.py L784` |

### Standard Methods Used

HSAE implements the following established methods, credited to their original authors:
HBV (Bergström, 1992), Penman-Monteith ET₀ (Allen et al., 1998),
SCS-CN (USDA, 1986), Muskingum (McCarthy, 1938),
NSE/KGE/PBIAS (Nash & Sutcliffe, 1970; Gupta et al., 2009),
Random Forest (Breiman, 2001), MODFLOW (McDonald & Harbaugh, 1988).

---

## System Statistics

| Metric | Value |
|--------|-------|
| Python source files | 15 |
| Lines of code | 9,893+ |
| Interactive pages | 13 |
| Global basins | 24 (7 continents) |
| UN 1997 articles automated | 12 |
| Plotly interactive charts | 59 |
| Original documented contributions | 10 |
| Syntax errors | 0 |

---

## Quick Start

```bash
# 1. Clone
git clone https://github.com/seifeldin-alkedir/HSAE.git
cd HSAE

# 2. Install
pip install streamlit pandas numpy plotly scikit-learn \
            pillow folium streamlit-folium requests

# 3. Run
streamlit run app.py          # → http://localhost:8501
```

**Docker (full stack — Streamlit + PostgreSQL + pgAdmin):**
```bash
docker compose up -d
# Streamlit  → http://localhost:8501
# pgAdmin    → http://localhost:5050
```

---

## Module Structure

```
HSAE/
├── app.py                  # 13-page Streamlit router
├── basins_global.py        # 24-basin database — single source of truth
│
├── hsae_v430.py            # Hybrid DSS   — ASCAF · ATDI · AFSF   (10 tabs)
├── hsae_v990.py            # Legal Nexus  — ATDI · α=0.3 · Nexus   (6 tabs)
├── hsae_hbv.py             # HBV model    — AHIFD · ALTM · AHLB
├── hsae_opsroom.py         # Operations   — ASI · ADTS · AWSRM · SITREP
│
├── hsae_alerts.py          # 4-level alerts · Telegram Bot · Art.12 protest
├── hsae_audit.py           # SHA-256 chain · RBAC · ICJ admissibility
├── hsae_legal.py           # ICJ/PCA/ITLOS database · protest generator
├── hsae_science.py         # Penman-Monteith ET₀ · Monte Carlo
├── hsae_validation.py      # NSE/KGE/PBIAS · Taylor diagram · FDC
├── hsae_groundwater.py     # MODFLOW · FAO-56 irrigation · Muskingum
├── hsae_quality.py         # 9 WQ parameters — WHO/FAO — Art.20/21
├── hsae_devops.py          # PostGIS · FastAPI · Docker · CI/CD
└── hsae_intro.py           # Architecture overview · quick start
```

---

## How to Cite

If you use HSAE or any of the Alkedir indices in your work, please cite:

```bibtex
@software{alkedir_hsae_2026,
  author  = {Alkedir, Seifeldin M.G.},
  title   = {HydroSovereign AI Engine (HSAE) v5.0.0},
  year    = {2026},
  version = {5.0.0},
  doi     = {10.5281/zenodo.XXXXXXX},
  url     = {https://github.com/seifeldin-alkedir/HSAE},
  orcid   = {0000-0003-0821-2991}
}
```

> **Note:** Peer-reviewed methodology papers describing the Alkedir indices
> (ATDI, AHIFD, ASI, ALTM, AFSF, ASCAF, AWSRM, AHLB, ADTS, α)
> are in preparation. This repository and Zenodo DOI serve as the
> citable priority record in the interim.

---

## License

[MIT License](LICENSE) — free to use, modify, and distribute with attribution.

The ten original contributions listed above are documented here to record the original
formulation. Any academic use must cite the Zenodo DOI and the author's ORCID.

---

## Contact

**Seifeldin M.G. Alkedir** — Independent Researcher  
BSc & MSc, University of Khartoum, Sudan  
🔗 [orcid.org/0000-0003-0821-2991](https://orcid.org/0000-0003-0821-2991)
