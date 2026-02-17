# MOSDEF-Analysis-Pipeline

Comprehensive Jupyter-based analysis pipeline for the MOSFIRE Deep Evolution Field (MOSDEF) survey public data release — focusing on rest-frame optical emission-line diagnostics, galaxy ISM properties, and redshift evolution at cosmic noon (z ≈ 1.4–3.8).

## Overview

This repository contains a complete, reproducible workflow to:

- Load and merge MOSDEF redshift and emission-line catalogs
- Apply quality filtering (S/N > 3 on key lines)
- Compute standard line ratios and BPT classifications (Kauffmann+2003, Kewley+2001)
- Estimate gas-phase metallicity using the O3N2 strong-line method (PP04 calibration)
- Correct for dust attenuation using the Balmer decrement and Calzetti-like curve
- Calculate Hα-based star formation rates (dust-corrected, cosmological luminosity distance)
- Perform correlation analysis, PCA, KMeans clustering, Random Forest classification, and Gradient Boosting regression
- Generate publication-style diagnostic plots (BPT, MZR evolution, SFR–z, A_V–z, Balmer histogram, etc.)

The pipeline closely follows methods and findings from key MOSDEF papers (Shapley+2015, Sanders+2016/2018/2021, Strom+2018, Runco+2021, Reddy+2015).

## Features

- Robust loading of FITS and text-based MOSDEF catalogs
- Safe handling of fluxes, errors, and log ratios
- Signal-to-noise filtering for reliable diagnostics
- BPT classification with visualization (colored by class and redshift)
- O3N2 metallicity with error propagation
- Balmer decrement → E(B–V) → A_V (clipped version)
- Dust-corrected Hα SFR (Kennicutt 1998 / Chabrier IMF)
- Correlation heatmap of derived properties
- PCA + KMeans clustering in feature space
- Supervised ML: Random Forest (BPT class prediction), Gradient Boosting (metallicity regression)
- Binned median trends with bootstrap uncertainties
- Clean, modular structure suitable for extension

## Requirements

pip install numpy pandas matplotlib seaborn astropy scipy scikit-learn

## Key Scientific Results (from this analysis)

- Clean sample (S/N > 3): ~63% Star-forming, ~25% Composite, ~12% AGN
- Clear high-z BPT offset: higher [O III]/Hβ at fixed [N II]/Hα (~0.2–0.4 dex above local sequence)
- Downward metallicity evolution: median 12+log(O/H) drops from ~8.6 (z<1.8) to ~8.3 (z~2.5) using PP04
- Modest dust attenuation: median A_V ~0.5–1.0 mag, no strong z trend
- SFR(Hα, dust-corrected) typically 10–100 M⊙ yr⁻¹ in the z~2 bin
- Strong correlations: metallicity ↔ line ratios, SFR ↔ A_V (+0.49)
- Clustering reveals two main SF subpopulations (high/low excitation) + rare extreme objects

**Note:** Results use uncorrected fluxes (no slit-loss/aperture correction applied; typical MOSDEF factor ~1.7–2.0× missing). PP04 metallicities likely overestimate true values by ~0.1–0.3 dex at z>2.

## Citation & Acknowledgments
If you use this pipeline or derived results in your work, please cite:

Kriek et al. (2015), ApJ, 807, L22 (MOSDEF survey)
The relevant MOSDEF diagnostic papers (Shapley+2015, Sanders+2016/2021, etc.)
And link back to this repository

Developed with help from Grok (xAI) during interactive refinement.


Feel free to adjust the repository name slightly or add your own GitHub username/branding.

Let me know if you want:
- A more compact README version
- Addition of badges (Python version, license, DOI if you make a Zenodo release)
- A requirements.txt file suggestion
- A suggested folder structure / .gitignore

Good luck with the upload!
