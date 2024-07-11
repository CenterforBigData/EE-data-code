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

### Steps and Data Usage Detailed Explanation

- **Step 1: Complete Decomposition Using CEEMDAN**
  - This step employs `Original Data.xlsx` for the initial decomposition of the dataset. The code automates the integration of the decomposed results back into the same `Original Data.xlsx` file. It's important to note that since we do not set a fixed random seed in the decomposition process, the resultant values in `Original Data.xlsx` may not exactly match those in `CEEMDAN Decomposed Data.xlsx`. This file (`CEEMDAN Decomposed Data.xlsx`) contains the decomposed data used in our experiments, reflecting the dataset after the initial CEEMDAN decomposition applied only to the training set.

- **Steps 2 to 4: Extended Window Application, EMNN Training, and Prediction/Decomposition**
  - These steps utilize `CEEMDAN Decomposed Data.xlsx`, which contains the data prepared in Step 1. Here, we perform further decomposition through the extended window application, train the Enhancing Mapping Neural Network (EMNN), and execute the prediction/decomposition processes:
    - **Step 2: Extended Window Application** — Applies further decomposition techniques on the data, preparing it for EMNN training.
    - **Step 3: Training the Enhancing Mapping Neural Network (EMNN)** — This crucial step involves training the EMNN model. Due to the inherent randomness in model training, each trained EMNN model might differ slightly. To ensure that readers can reproduce the exact results from our study, we provide pre-trained EMNN models available at [Google Drive](https://drive.google.com/file/d/1aSySuc8VTQAjtVHrzhjFFm3THMGvIrQL/view?usp=sharing). Readers wishing to replicate the results without retraining can directly use this model and skip to the next step.
    - **Step 4: Prediction/Decomposition** — The final step takes the trained EMNN model and applies it to the dataset for final predictions. Once completed, the newly decomposed subsequences are automatically updated in `CEEMDAN Decomposed Data.xlsx`. Users can compare these updated results with the `EMNN Decomposed Data.xlsx` to verify the consistency and successful replication of the experimental results.

## Section 2: Forecasting Using TFT (Temporal Fusion Transformer) Optimized by TPE (Tree-structured Parzen Estimator)

This section is dedicated to the prediction phase using the TFT model, optimized by the TPE algorithm. We provide separate notebooks for the WTI (`WTI_TFT.ipynb`) and Brent (`Brent_TFT.ipynb`) datasets.

### Model Availability and Training
- **Pre-trained Models:** For users focused on replicating our exact results, we offer pre-trained TFT models located in the `TFT_saved_models` directory, accessible via [Google Drive](https://drive.google.com/file/d/1SSU1ltOUvFuYxi7ro-StC1aIaXzNzkd5/view?usp=sharing).
- **Training Your Own Model:** We've embedded the optimal hyperparameters within the notebooks for ease of use. However, those interested in performing their own hyperparameter optimization can uncomment and execute the TPE code blocks provided.

### Computational Considerations
Due to the computationally intensive nature of the TFT model training (especially considering a 90-day testing period with daily predictions), users might need to adjust the training start date within the code to manage the computational load effectively. This adjustment can help mitigate potential system overloads during extensive training sessions.

---

By following the outlined steps and utilizing the provided resources, users can effectively replicate or extend our forecasting experiments for WTI and Brent crude oils. For any further questions or assistance, please refer to our GitHub issues section or contact the contributors directly.
