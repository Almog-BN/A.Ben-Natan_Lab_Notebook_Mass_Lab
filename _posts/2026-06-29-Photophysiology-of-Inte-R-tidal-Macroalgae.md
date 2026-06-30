---
layout: post
title: "Photophysiology of Inte-R-tidal Macroalgae"
author: "Almog Ben Natan"
---

# Photophysiology of Inte-R-tidal Macroalgae

# 1. Introduction:

Photoacclimation is the ability of photosynthetic organisms to adjust the structure and function of their photosynthetic apparatus in response to changes in light availability. Through this process, algae optimize light harvesting and energy utilization under both low- and high-light conditions while minimizing photodamage.

Following a field survey conducted along the Sdot-Yam rocky shore, twelve macroalgal species were collected and examined using pulse-amplitude modulated (PAM) fluorometry under different light conditions. Measurements obtained from both light-acclimated and dark-acclimated samples were used to extract key photophysiological parameters describing photosynthetic performance and photoprotective responses.

The aim of this report is to investigate how changes in light exposure influence the photophysiology of intertidal macroalgae. The extracted parameters were organized into a standardized dataset, analyzed in R, and used to evaluate differences in photosynthetic performance among the sampled algae.

# 2. Methods and materials

## 2.1 Sample collection

Intertidal macroalgae were collected from a rocky shore at Sdot Yam, Israel, on 16 April 2026. A total of thirteen macroalgal samples representing the genera Codium, Colpomenia, Dictyota, Galaxaura, Halimeda, Hypnea, Jania, Laurencia, Nemalion, Padina, Red_UNK, and Ulva were used in this study.

## 2.2 PAM fluorometry

Photophysiological measurements were performed using a Walz Water-PAM II pulse-amplitude modulated (PAM) fluorometer. Measurements followed two protocols: a light-acclimated protocol and a dark-acclimated protocol. The light protocol was used to characterize photosynthetic performance under increasing irradiance, whereas the dark protocol was used to assess the maximum photochemical efficiency of photosystem II following dark adaptation.

Photosynthesis–irradiance (PI) curves were recorded across 17 photosynthetically active radiation (PAR) levels ranging from 0 to 701 µmol photons m⁻² s⁻¹. At each PAR step, steady-state fluorescence (F), maximum fluorescence (Fm′), minimum fluorescence (Fo′), effective quantum yield of PSII (Y(II)), non-photochemical quenching yield (Y(NPQ)), and electron transport rate (ETR) were recorded. These measurements were subsequently used to derive the photophysiological parameters analyzed in this study.

## 2.3 Data organization

The raw fluorescence measurements were processed to extract the photophysiological parameters used in the subsequent analyses. Original metadata can be found in [Photophysiology metadata](https://github.com/Almog-BN/A.Ben-Natan_Lab_Notebook_Mass_Lab/blob/master/Photophysiology/Photophysiology_Final_csv.csv). Each extracted parameter was assigned to its corresponding sample, taxon, and measurement protocol, and organized into a standardized dataset (Table 1).

**Table 1.** Descriptive statistics of the extracted photophysiological parameters used in the analyses.

| Parameter | Description | Units | n | Mean | SD | Min | Q1 | Median | Q3 | Max |
|-----------|-------------|-------|--:|----:|----:|----:|----:|-------:|----:|----:|
| **ETRmax** | Maximum recorded electron transport rate (light-acclimated samples) | µmol electrons m⁻² s⁻¹ | 13 | 19.169 | 11.193 | 3.900 | 9.500 | 16.800 | 28.700 | 42.400 |
| **Fv/Fm** | Maximum quantum yield of PSII at PAR = 0 | Dimensionless | 8 | 0.589 | 0.140 | 0.345 | 0.535 | 0.636 | 0.696 | 0.712 |
| **NPQ_auc** | Area under the Y(NPQ)–PAR curve | µmol photons m⁻² | 8 | 278.219 | 51.110 | 189.753 | 247.200 | 293.870 | 300.109 | 359.073 |
| **NPQmax** | Peak Y(NPQ) across all PAR steps | Dimensionless | 8 | 0.576 | 0.102 | 0.404 | 0.510 | 0.575 | 0.650 | 0.703 |

## 2.4 PI curve model and parameter extraction

Photosynthesis–irradiance (PI) curves were fitted using non-linear least squares (NLS) in R. The model was fitted to the ETR values measured across increasing PAR levels, separately for the light- and dark-acclimated samples. Prior to model fitting, ETR values equal to zero at PAR values greater than zero were treated as missing values, since these points represented the end of the measurement rather than a valid physiological response. Measurements above PAR 600 µmol photons m⁻² s⁻¹ were excluded from the model fitting.

The fitted model was used to estimate four photophysiological parameters: Am, representing the asymptotic maximum electron transport rate; AQY, representing the initial slope of the curve; Rd, representing the y-intercept of the fitted curve; and Ik, calculated as Am/AQY and representing the irradiance level at which photosynthesis transitions from light-limited to saturation-limited conditions. Two light-acclimated samples, Light_3 (Nemalion) and Light_9 (Halimeda), were excluded from the fitted analysis due to poor curve quality.

## 2.5 Statistical analysis

Differences in the NLS-derived photophysiological parameters (Am, AQY, Rd, and Ik) between light- and dark-acclimated samples were evaluated using paired Wilcoxon signed-rank tests. Only taxa represented in both treatment groups were included in the paired analysis. To account for multiple comparisons, p-values were adjusted using the Benjamini–Hochberg (BH) false discovery rate correction. As a sensitivity analysis, the paired Wilcoxon tests were repeated after excluding Colpomenia to evaluate its influence on the statistical results.

All data processing, statistical analyses, and graphical visualizations were performed in R version 4.3.2 using the packages dplyr, lubridate, hms, tidyr, ggplot2, purrr, broom, and patchwork. Code file available in [Photophysiology R code](https://github.com/Almog-BN/A.Ben-Natan_Lab_Notebook_Mass_Lab/blob/master/Photophysiology/Photophysiology_r_code.txt). 

# 3. Results 

## 3.1 Sample Metadata 

**Table 2.** Macroalgal samples included in the paired statistical analysis. Samples without a matching light or dark pair, or with poor PI curve quality, were excluded.

| Sample ID | Taxon | Group | Used in analysis |
|-----------|-------|-------|------------------|
| Dark_1 | Colpomenia | Dark | ✓ Paired |
| Dark_2 | Dictyota | Dark | ✓ Paired |
| Dark_3 | Sargassum | Dark | ✓ Paired |
| Dark_4 | Padina | Dark | ✓ Paired |
| Dark_5 | Jania | Dark | ✓ Paired |
| Dark_6 | Red_UNK | Dark | Excluded (no light pair) |
| Dark_7 | Ulva | Dark | ✓ Paired |
| Dark_8 | Galaxaura | Dark | Excluded (no light pair) |
| Light_1 | Jania | Light | ✓ Paired |
| Light_2 | Halopteris | Light | Excluded (no dark pair) |
| Light_3 | Nemalion | Light | Excluded (poor curve) |
| Light_4 | Sargassum | Light | ✓ Paired |
| Light_5 | Hypnea | Light | Excluded (no dark pair) |
| Light_6 | Codium | Light | Excluded (no dark pair) |
| Light_7 | Padina | Light | ✓ Paired |
| Light_8 | Cystoseira | Light | Excluded (no dark pair) |
| Light_9 | Ulva | Light | Excluded (poor curve) |
| Light_10 | Galaxaura | Light | Excluded (no dark pair) |
| Light_11 | Dictyota | Light | ✓ Paired |
| Light_12 | Colpomenia | Light | ✓ Paired |
| Light_13 | Ulva | Light | ✓ Paired |

## 3.2 PI curves


![]( https://github.com/Almog-BN/A.Ben-Natan_Lab_Notebook_Mass_Lab/blob/master/Photophysiology/figure_1.png?raw=true )



![]( https://github.com/Almog-BN/A.Ben-Natan_Lab_Notebook_Mass_Lab/blob/master/Photophysiology/figure_2.png?raw=true )



![]( https://github.com/Almog-BN/A.Ben-Natan_Lab_Notebook_Mass_Lab/blob/master/Photophysiology/figure_3.png?raw=true )



![]( https://github.com/Almog-BN/A.Ben-Natan_Lab_Notebook_Mass_Lab/blob/master/Photophysiology/figure_4.png?raw=true )

Light 

Dark

## 3.3 NLS parameters — summary statistics
**Table 3.** Descriptive statistics of the non-linear least squares (NLS)-derived photophysiological parameters for the light- and dark-acclimated macroalgal samples.

| Parameter | Group | n | Mean | SD | Min | Q1 | Median | Q3 | Max |
|-----------|:-----:|--:|-----:|----:|----:|----:|-------:|----:|----:|
| **AQY** | Dark | 8 | 0.190 | 0.073 | 0.068 | 0.142 | 0.205 | 0.222 | 0.308 |
| **AQY** | Light | 11 | 0.137 | 0.024 | 0.099 | 0.123 | 0.139 | 0.148 | 0.184 |
| **Am** | Dark | 8 | 18.079 | 12.651 | 5.982 | 8.605 | 14.834 | 21.690 | 40.569 |
| **Am** | Light | 11 | 21.522 | 12.759 | 6.483 | 11.357 | 17.731 | 30.647 | 47.082 |
| **Ik** | Dark | 8 | 104.384 | 61.385 | 24.821 | 41.221 | 123.494 | 137.909 | 188.649 |
| **Ik** | Light | 11 | 153.421 | 77.377 | 56.989 | 81.305 | 143.221 | 210.516 | 267.871 |
| **Rd** | Dark | 8 | -0.031 | 0.253 | -0.428 | -0.194 | 0.047 | 0.124 | 0.252 |
| **Rd** | Light | 11 | -0.165 | 0.261 | -0.670 | -0.264 | -0.085 | 0.012 | 0.136 |

## 3.4 Distribution of parameters

![]( https://github.com/Almog-BN/A.Ben-Natan_Lab_Notebook_Mass_Lab/blob/master/Photophysiology/figure_5.png?raw=true )


![]( https://github.com/Almog-BN/A.Ben-Natan_Lab_Notebook_Mass_Lab/blob/master/Photophysiology/figure_6.png?raw=true )

![]( https://github.com/Almog-BN/A.Ben-Natan_Lab_Notebook_Mass_Lab/blob/master/Photophysiology/figure_7.png?raw=true )

## 3.5 Light vs Dark taxon comparison 

![]( https://github.com/Almog-BN/A.Ben-Natan_Lab_Notebook_Mass_Lab/blob/master/Photophysiology/figure_8.png?raw=true )

![]( https://github.com/Almog-BN/A.Ben-Natan_Lab_Notebook_Mass_Lab/blob/master/Photophysiology/figure_9.png?raw=true )


## 3.6 Paired comparison of photophysiological parameters

Paired Wilcoxon signed-rank tests comparing the light- and dark-acclimated samples revealed no statistically significant differences in any of the four NLS-derived photophysiological parameters after Benjamini–Hochberg correction (all adjusted p = 0.156). A sensitivity analysis excluding Colpomenia produced similar results, with no parameter remaining significant after multiple-testing correction (all adjusted p ≥ 0.0833).

# 4. Interpretation

The paired comparisons between light- and dark-acclimated macroalgae did not reveal statistically significant differences in any of the four NLS-derived photophysiological parameters (Am, AQY, Rd, and Ik) after Benjamini–Hochberg correction. Although Ik and Rd showed the lowest unadjusted p-values, neither remained significant following correction for multiple comparisons. Repeating the analysis after excluding Colpomenia produced similar results, indicating that this species had only a limited influence on the overall conclusions.

Despite the absence of statistically significant differences, the observed trends are consistent with the expected physiological responses of photoacclimation. Light-acclimated algae generally exhibited higher Ik values, indicating an increased irradiance requirement to reach photosynthetic saturation, whereas dark-acclimated algae tended to display higher AQY values, reflecting greater photosynthetic efficiency under low-light conditions. These patterns agree with the established understanding that algae adjust their photosynthetic apparatus according to the prevailing light environment.

The lack of statistical significance is likely attributable to the limited number of paired samples and the considerable physiological variation among the different macroalgal taxa included in the study. Future studies incorporating a larger number of biological replicates within individual species would improve statistical power and provide a more robust assessment of photoacclimation responses.





