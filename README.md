# Wheat Analysis: Phenology, Risk Modeling, and Spatial Zoning

This repository contains the scripts and input data used for the analysis of wheat phenology, disease risk modeling (Wheat Blast), and spatial-temporal trends presented in my paper.

## Project Structure and Workflow

The analysis follows a logical progression from data pre-processing and model validation to spatial zoning and climate sensitivity analysis.

### 0. Phenological Data Preparation
*   **[`PhenologicalEstimationDataPrep.ipynb`]**: Prepares experimental trial data for model validation.
    *   Imports and reshapes trial records from Embrapa, RECORBE, and Patos de Minas.
    *   Extracts climate-based GDD and temperature data for specific trial environments.
    *   Produces merged datasets used for empirical threshold estimation.

### 1. Phenological Threshold Estimation
*   **[`PhenologicalEstimation.qmd`]**: Validates the GDD-based phenological models using experimental trial data.
    *   Performs Leave-One-Environment-Out Cross-Validation (LOEO-CV).
    *   Generates error analysis plots comparing observed vs. predicted phenology.

### 2. Risk Modeling and Large-Scale Analysis
*   **[`XavierRiskAnalysis.ipynb`]**: The core pipeline for regional analysis.
    *   Calculates GDD and phenological dates across the entire Region of Interest (ROI).
    *   Calculates the epidemic and water deficit risks
    *   Generates spatial datasets used for zonation and temporal trend analysis, and plots.

### 3. Spatial Analysis and Zoning
*   **[`SowingdateZones.qmd`]**: Defines optimal sowing windows based on smoothed risk surfaces.
    *   Fits Generalized Additive Models (GAM) and performs Ordinary Kriging of residuals.
    *   Classifies pixels into temporal bins to define risk-minimizing sowing zones.
    *   Produces high-resolution zonation rasters (TIFF format).

### 4. Climate Sensitivity and Temporal Trends
*   **[`ENSO_Temporal_Trend.qmd`]**: Analyzes El Niño Southern Oscillation (ENSO) influence.
    *   Uses Beta-Mixed Effects models to examine sensitivity to Oceanic Niño Index (ONI) trimesters.
    *   Evaluates risk gradients across different sowing dates and geographical locations.

---

## Directory Organization

### [`InputData/`]
Contains raw and intermediate datasets required for the analysis:
*   **Shapefiles (`.shp`)**: Brazilian state boundaries, municipality centroids, and Region of Interest (ROI) masks (e.g., altitude filter >700m).
*   **Experimental Data (`.xlsx`, `.csv`)**: Phenological trial records from Embrapa and RECORBE.
*   **Climate Indices**: ONI trimesters for ENSO analysis (`ONI_Analysis.xlsx`).
*   **Environmental Data**: Soil datasets (Curve Number - CN) and grid probability data (`PRI_emp.xlsx`).
*   **OBS**: It is necessary to download larger inputdata files from https://drive.google.com/drive/folders/1tSP-ndn-Z5ZEkxB9KFITN3U2lHAGKpiP?usp=drive_link, and move the downloaded file to InputData

### [`OutputData/`]
Directory where generated outputs are stored, needs to be created inside in your folder

---
