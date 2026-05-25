# Economic and Ecological Losses from Wildfires using Machine Learning

**Master's Thesis** – HSE University, Data Science Programme  
**Author:** Muhammad Suliman  
**Supervisor:** Dr. Ramon Antonio Rodriges Zalipynis  
**Year:** 2026  

## 📄 Thesis PDF

The final version of the thesis is available as [`main.pdf`](./main.pdf).

## Repository Structure

```text
.
├── main.pdf
├── Chapters/
│   ├── chapter1_introduction.tex
│   ├── chapter2_literature_review.tex
│   ├── chapter3_methodology.tex
│   ├── chapter4_results.tex
│   ├── chapter5_discussion.tex
│   ├── chapter6_conclusion.tex
│   ├── main.tex
│   └── references.bib
├── Code files/
│   ├── 1_target_construction.ipynb
│   ├── 2_baseline_modeling.ipynb
│   ├── 3_environmental_augmentation.ipynb
│   ├── 4_ablation_analysis.ipynb
│   ├── 5_grouped_validation.ipynb
│   ├── 6_vietnam_supporting_study.ipynb
│   ├── 7_ecological_risk_proxy.ipynb
│   └── 8_economic_ecological_overlap.ipynb
└── README.md
```

## 🎯 Overview

This thesis develops a **county‑level wildfire risk prediction and assessment pipeline** using publicly accessible datasets. The main target is wildfire **Expected Annual Loss (EAL)** from the FEMA National Risk Index. Baseline predictors (population, building value, social vulnerability, resilience) are combined with environmental variables derived from topography (SRTM), land cover (NLCD), and warm‑season climate (gridMET).

Key results:
- **Random Forest** with combined features achieves test R² = **0.829** and cross‑validation R² = **0.795**.
- **State‑wise grouped validation** shows a more realistic geographic transferability (R² = **0.603** for the combined model).
- Environmental predictors (precipitation, VPD, shrub fraction, elevation) dominate feature importance.
- An **exploratory ecological risk proxy** identifies counties where high monetary risk overlaps with natural vegetation exposure.

## 📊 Data Sources

| Source | Data | Resolution |
|--------|------|------------|
| FEMA National Risk Index | Wildfire Expected Annual Loss, exposure, vulnerability, resilience | County |
| LANDFIRE | Existing Vegetation Type (EVT), Canopy Height | 30 m |
| SRTM | Elevation, slope, aspect | 30 m |
| NLCD 2019 | Forest, shrub, grass, developed fractions | 30 m |
| gridMET | Warm‑season Tmax, precipitation, wind speed, VPD | ~4 km |

## 🛠️ Reproducibility – Notebooks Description

The notebooks in the `Code files/` folder are ordered to reproduce the full analysis:

| Notebook | Description |
|----------|-------------|
| **1_target_construction** | Clean and log‑transform FEMA NRI wildfire EAL; prepare county‑level target. |
| **2_baseline_modeling** | County‑only exposure/value/vulnerability/resilience models (Linear, Ridge, RF, GBM). |
| **3_environmental_augmentation** | Add topography, land cover, and climate predictors; compare performance. |
| **4_ablation_analysis** | Test removal of county‑level predictors (area, vulnerability, resilience). |
| **5_grouped_validation** | State‑wise grouped cross‑validation for geographic transferability. |
| **6_vietnam_supporting_study** | Supporting fine‑scale deep learning classification (An Giang, Vietnam). |
| **7_ecological_risk_proxy** | Construct ecological risk proxy: `Predicted risk percentile × Natural vegetation fraction`. |
| **8_economic_ecological_overlap** | Quadrant analysis (high/low economic risk × high/low ecological exposure). |

**Requirements:**  
- Python 3.9+ with packages: `pandas`, `numpy`, `scikit‑learn`, `matplotlib`, `seaborn`, `geopandas`, `rasterio`, `jupyter`.
- Earth Engine scripts (used to extract the point‑day dataset) are available upon request.

## 📚 Citation

If you use any part of this work, please cite:

```bibtex
@mastersthesis{Suliman2026Wildfire,
  author = {Muhammad Suliman},
  title = {Economic and Ecological Losses from Wildfires using Machine Learning},
  school = {HSE University},
  year = {2026}
}
