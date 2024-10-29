# EmoDSc-SER: Speech Emotion Recognition using CNNs

This repository contains the implementation of a **Speech Emotion Recognition (SER)** system using a neural network architecture that combines 1D and 2D CNNs with an MLP (DNN) for classification. Below is a detailed explanation of the project structure, the steps involved, and how to reproduce the experiments.

## Project Structure

The project consists of the following key parts:

### 1. Data Preparation (`1_PreparacionDatos_EmoDSc.ipynb`)
In this first notebook, the raw datasets are processed and prepared for the training pipeline.

- **Datasets folder**: This folder should contain all the raw datasets, such as **RAVDESS**, **CREMA-D**, or others. Make sure the datasets are in their original structure without modifications.
- **CSV generation**: A CSV file is created, which maps each emotion to its corresponding audio file path (with `emotion` and `path` columns).
- **Balancing the dataset**: We perform a random balancing of the dataset so that each emotion has the same number of audio samples. This ensures balanced training data.
- **Silence removal**: Silence segments are removed from the audio files to focus on the actual speech content.
- **Data augmentation**: Techniques such as noise addition or pitch shifting are applied to augment the data for better training.
- **Dataset partitioning**: The data is split into three sets: **training**, **validation**, and **testing** sets.

### 2. Feature Extraction (`2_SeleccionCaracteristicas_EmoDSc.ipynb`)
In this notebook, we extract features from the processed audio files.

- **Audio features**: Using **librosa**, we extract different features from the audio files, such as MFCCs, chroma, spectral contrast, etc. These features are stored in `.npy` format.
- **Spectrogram image generation**: We also generate spectrogram images from the audio, which are saved in a folder. These images are used as input for the 2D CNN model.
- **CSV generation**: CSV files are created for each dataset with the corresponding features extracted from the audio files.

### 3. Model Training (`3_Clasificacion_EmoDSc.ipynb`)
The final notebook involves constructing and training the neural network.

- **Neural network architecture**: The architecture consists of both **1D CNN** and **2D CNN** layers for audio and image-based feature inputs, followed by a fully connected **MLP** (DNN) layer for classification.
- **Model training**: The training process is carried out using the training and validation sets. 
- **Results**: The results, including loss and accuracy curves, are saved and visualized.
- **Model saving**: The trained model is saved in `.h5` format.

## Folder Descriptions

- **`CSVs/`**: This folder contains the CSV files generated during the data preparation and feature extraction stages. These CSVs store the file paths and corresponding emotions or features for each dataset.
  
- **`Figuras/`**: Contains figures generated during the training process, such as accuracy and loss curves.

- **`Modelo/`**: Stores the training results, including graphs of the training process and the final trained model (`.h5` file).

- **`datasets/`**: This folder should contain the raw datasets (e.g., **RAVDESS**, **CREMA-D**) downloaded in their original structure. No changes are made to the dataset folder structures. Simply download the datasets and place them here.

- **`EmoDSc_Aumentado/`**: Contains the augmented audio files after the data augmentation step.

- **`EmoDSc_Silenciados/`**: Contains the processed audio files with silences removed.

## Important Note: Large Files
All the feature files and models (in `.npy` and `.h5` formats) used for training are not included in this repository due to GitHub file size limits. However, you can download these files from our **Google Drive** link below:

- **[Download Features and Model from Google Drive](https://your-google-drive-link)**

After downloading, please place the files in the appropriate directories:

