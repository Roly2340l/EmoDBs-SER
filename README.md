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
- **Model saving**: The trained model is saved in `.h5` format and is already included in this repository.

## Folder Descriptions

- **`CSVs/`**: This folder contains the CSV files generated during the data preparation and feature extraction stages. These CSVs store the file paths and corresponding emotions or features for each dataset.
  
- **`Figuras/`**: Contains figures generated during the training process, such as accuracy and loss curves.

- **`Modelo/`**: Stores the training results, including graphs of the training process and the final trained model (`.h5` file), which is already included in this repository.

- **`datasets/`**: This folder should contain the raw datasets (e.g., **RAVDESS**, **CREMA-D**) downloaded in their original structure. No changes are made to the dataset folder structures. Simply download the datasets and place them here.

- **`EmoDSc_Aumentado/`**: Contains the augmented audio files after the data augmentation step.

- **`EmoDSc_Silenciados/`**: Contains the processed audio files with silences removed.

### Important Note on Empty Folders
Since GitHub does not upload empty folders, you will need to manually create the following directories before running the notebooks:

- **`Datasets/`**: To store the raw datasets (e.g., RAVDESS, CREMA-D).
- **`EmoDSc_Aumentado/`**: To store the augmented audio files.
- **`EmoDSc_Silenciados/`**: To store the audio files with silences removed.
- **`Caracteristicas/`**: To store the `.npy` feature files that are generated or downloaded (more details below).

Once these folders are created, download or generate the necessary files as described in the following sections.

## Download Links for Datasets

To reproduce the experiments, you will need to download the following datasets:

- **[RAVDESS (Ryerson Audio-Visual Database of Emotional Speech)](https://www.kaggle.com/datasets/uwrfkaggler/ravdess-emotional-speech-audio)**
- **[RAVDESS (Ryerson Audio-Visual Database of Emotional Song)](https://www.kaggle.com/datasets/uwrfkaggler/ravdess-emotional-song-audio)**
- **[ESD (Emotional Speech Dataset)](https://github.com/HLTSingapore/Emotional-Speech-Data)**
- **[JL-Corpus](https://www.kaggle.com/datasets/tli725/jl-corpus)**
- **[SAVEE (Surrey Audio-Visual Expressed Emotion)](https://github.com/CheyneyComputerScience/CREMA-D)**
- **[TESS (Toronto emotional speech set)](https://www.kaggle.com/datasets/ejlok1/toronto-emotional-speech-set-tess)**
- **[ASVP-ESD (Speech & Non-Speech Emotional Sound)](https://www.kaggle.com/datasets/dejolilandry/asvpesdspeech-nonspeech-emotional-utterances)**
- **[CREMA-D (Crowd-sourced Emotional Multimodal Actors Dataset)](https://www.kaggle.com/datasets/ejlok1/cremad)**

Once downloaded, place the datasets in the `Datasets/` folder.

## Important Note: Feature Files (from Google Drive)
The extracted feature files (`.npy`) used for training are too large to upload to GitHub. However, you can download them from the following Google Drive link:

- **[Download Features from Google Drive](https://drive.google.com/drive/folders/1IgC-iU3W-tv1rpYqKNdxAl_v_nwKMQSC?usp=drive_link)**

These `.npy` files contain the extracted features used during training. They must go inside the "Caracteristicas" folder.

## Environment Setup

To replicate the environment in which the experiments were conducted, we recommend using **Miniconda**. The `Environment_backup.yml` file is included to help you recreate the same environment used during the development of this project.

### 1. Install the environment using Miniconda:
```bash
conda env create --file Environment_backup.yml
