# Reproducible Results for WTI and Brent Price Predictions

## Overview
This repository contains all necessary data and code to reproduce the results of our paper on predicting WTI and Brent prices using a two-step approach. First, we apply the Enhanced Mapping Neural Network (EMNN) model for rolling decomposition of the datasets. Subsequently, we train and predict using the Temporal Fusion Transformer (TFT) model, optimized by the Tree-structured Parzen Estimator (TPE), on the decomposed data. The predictions from these sub-series are then aggregated to obtain the final forecast values.

### Part 1: Data Decomposition Using EMNN
The code for this part is provided in two Jupyter notebooks: `WTI_EMNN.ipynb` and `Brent_EMNN.ipynb`, corresponding to the WTI and Brent datasets, respectively. The decomposition process involves the following steps, consistent with those described in our paper:

#### Steps:
1. **Complete Decomposition Using CEEMDAN** (`# step 1`)
   - Initial decomposition of the training set using the CEEMDAN method.
   - Source file: `Original Data.xlsx`
   - Output integrated back into `Original Data.xlsx`
   - Note: Since a random seed is not set, decomposed sequences may not exactly match those in `CEEMDAN Decomposed Data.xlsx`.

2. **Extended Window Application** (`# step 2`)

3. **Training the Enhancing Mapping Neural Network (EMNN)** (`# step 3`)
   - This step involves training the EMNN model.
   - Note: Due to randomness, each trained model may vary. Pre-trained models can be accessed from [Google Drive](https://drive.google.com/file/d/1aSySuc8VTQAjtVHrzhjFFm3THMGvIrQL/view?usp=sharing) for replicating our results directly without retraining.

4. **Prediction/Decomposition** (`# step 4`)
   - The decomposed sequences are added back to the `CEEMDAN Decomposed Data.xlsx`.

### Part 2: Price Forecasting Using Optimized TFT
The forecasting models are detailed in `WTI_TFT.ipynb` and `Brent_TFT.ipynb`. The prediction process is divided into two main sections:

1. **Replicating the Experimental Results**
   - Pre-trained models are available for use from [Google Drive](https://drive.google.com/file/d/1SSU1ltOUvFuYxi7ro-StC1aIaXzNzkd5/view?usp=sharing).
   - Models were trained with optimal hyperparameters derived from TPE.

2. **Training the TFT Models Independently**
   - Optional: Run the commented TPE code sections to derive optimal hyperparameters.
   - Due to the computational intensity, especially with a prediction horizon of 90 days and a step size of 1 day, users are advised to adjust the starting point of predictions to manage computational load.

### Data Files
- `Original Data.xlsx`: Raw dataset.
- `CEEMDAN Decomposed Data.xlsx`: Dataset post-initial CEEMDAN decomposition.
- `EMNN Decomposed Data.xlsx`: Final version used in our experiments after EMNN decomposition.

### Models
- EMNN models are stored in `EMNN_saved_models`.
- Pre-trained TFT models can be downloaded from the provided Google Drive links.

### Instructions for Use
To reproduce the results, simply follow the steps outlined in each notebook. For direct results replication without retraining models, use the pre-trained models linked above. For those interested in training their own models, detailed instructions and necessary code modifications are provided within the notebooks.

Thank you for your interest in our work. We hope this repository helps you understand and replicate our experimental procedures effectively.
