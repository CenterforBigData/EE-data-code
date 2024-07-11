# Reproducible Results for WTI and Brent Price Predictions

## Overview
This repository contains all necessary data and code to reproduce the results of our paper on predicting WTI and Brent prices using a two-step approach. First, we apply the Enhanced Mapping Neural Network (EMNN) model for rolling decomposition of the datasets. Subsequently, we train and predict using the Temporal Fusion Transformer (TFT) model, optimized by the Tree-structured Parzen Estimator (TPE), on the decomposed data. The predictions from these sub-series are then aggregated to obtain the final forecast values.

## Section 1: Rolling Decomposition Using EMNN (Enhanced Mapping Neural Network)

This section includes detailed Jupyter notebooks for both WTI and Brent datasets, named `WTI_EMNN.ipynb` and `Brent_EMNN.ipynb`, respectively. These notebooks correspond to the four steps outlined in our paper:
  - **Step 1:** Complete Decomposition Using CEEMDAN
  - **Step 2:** Extended Window Application
  - **Step 3:** Training the Enhancing Mapping Neural Network (EMNN)
  - **Step 4:** Prediction/Decomposition

### Datasets
The data files required for these steps are located in the `Datasets` directory at the root of this repository, consisting of three Excel files:
  - `Original Data.xlsx` – the raw dataset without any processing.
  - `CEEMDAN Decomposed Data.xlsx` – dataset post-initial CEEMDAN decomposition (applied only to the training set).
  - `EMNN Decomposed Data.xlsx` – the final version of our dataset after rolling decomposition through EMNN, used in our experiments.

### Steps and Data Usage
- **Step 1:** Utilizes `Original Data.xlsx`. The decomposed results are automatically integrated into this file post-execution. Note that due to non-fixed random seeds, results may vary and not align perfectly with `CEEMDAN Decomposed Data.xlsx`.
- **Steps 2 to 4:** Employ `CEEMDAN Decomposed Data.xlsx` for extended window applications, EMNN training, and subsequent decomposition. Specifically, `Step 3` involves training the EMNN model. To ensure reproducibility without re-training, we provide a pre-trained EMNN model available at [Google Drive](https://drive.google.com/file/d/1aSySuc8VTQAjtVHrzhjFFm3THMGvIrQL/view?usp=sharing). Users can bypass training by using this model and proceed directly to `Step 4`.

## Section 2: Forecasting Using TFT (Temporal Fusion Transformer) Optimized by TPE (Tree-structured Parzen Estimator)

This section is dedicated to the prediction phase using the TFT model, optimized by the TPE algorithm. We provide separate notebooks for the WTI (`WTI_TFT.ipynb`) and Brent (`Brent_TFT.ipynb`) datasets.

### Model Availability and Training
- **Pre-trained Models:** For users focused on replicating our exact results, we offer pre-trained TFT models located in the `TFT_saved_models` directory, accessible via [Google Drive](https://drive.google.com/file/d/1SSU1ltOUvFuYxi7ro-StC1aIaXzNzkd5/view?usp=sharing).
- **Training Your Own Model:** We've embedded the optimal hyperparameters within the notebooks for ease of use. However, those interested in performing their own hyperparameter optimization can uncomment and execute the TPE code blocks provided.

### Computational Considerations
Due to the computationally intensive nature of the TFT model training (especially considering a 90-day testing period with daily predictions), users might need to adjust the training start date within the code to manage the computational load effectively. This adjustment can help mitigate potential system overloads during extensive training sessions.

---

By following the outlined steps and utilizing the provided resources, users can effectively replicate or extend our forecasting experiments for WTI and Brent crude oils. For any further questions or assistance, please refer to our GitHub issues section or contact the contributors directly.
