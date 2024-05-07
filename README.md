# CS-598 DL4H Reproducibility Project: "Improving Clinical Outcome Predictions Using Convolution Over Medical Entities with Multimodal Learning"

This repository contains the code for the reproducibility of the paper by Bardak et al.

[Link to paper](https://arxiv.org/abs/2011.12349)

Source code of the paper is found in a [Github repo](https://github.com/tanlab/ConvolutionMedicalNer)

## Environment Setup

Python version 3.10.12 is used. Python library dependencies are found in requirements.txt

List of dependent packages needed:
  - numpy
  - pandas
  - tables
  - nltk
  - spacy
  - gensim
  - keras==2.10.0
  - scipy==1.10.1
  - tensorflow
  - scikit-learn
  - (med7 pre-trained model) https://huggingface.co/kormilitzin/en_core_med7_lg/resolve/main/en_core_med7_lg-any-py3-none-any.whl

## Implementation Steps

### Step 1. Create environment in Anaconda
    
1. Clone repo to local environment

```
git clone https://github.com/zhenc5/CS598-Group-Project.git`
cd CS598-Group-Project
```

2. Create and active new conda environment and install packages

```
conda create --name DLH_project python==3.10.12
conda activate DLH_project
pip install -r requirements.txt
```

### Step 2. Download data

1. Request access to [MIMIC-III v1.4](https://physionet.org/content/mimiciii/1.4/) dataset. (May take several days as it involves HIPAA certification)

2. Once access is approved, download these 3 data files from the [MIMIC-III v1.4](https://physionet.org/content/mimiciii/1.4/) dataset and place in the `data` folder.
    - `ADMISSIONS.csv`
    - `NOTEEVENTS.csv`
    - `ICUSTAYS.csv`

3. Download the output file called `all_hourly_data.h5` from [MIMIC-Extract Pipeline](https://github.com/MLforHealth/MIMIC_Extract) and place in the `data` folder

4. Download the pre-trained [Word2Vec](https://github.com/kexinhuang12345/clinicalBERT) and [FastText](https://drive.google.com/drive/folders/1bcR6ThMEPhguU9T4qPcPaZJ3GQzhLKlz?usp=sharing) embeddings and place in the `embeddings` folder

### Step 3. Run Jupyter notebooks

1. Run `01-Extract-Timeseries-Features.ipynb` to extract the first 24 hours of time-series features from the MIMIC-III Extract raw data

2. Run `02+03-Preprocessing-Clinical-Notes.ipynb` to select the clinical notes based on criteria and to preprocess them.

3. Run `04-Apply-med7-on-Clinical-Notes.ipynb` to extract the medical entities from the clinical notes using [med7](https://github.com/kormilitzin/med7)

4. Run `05-Represent-Entities-With-Different-Embeddings.ipynb` to convert medical entities into word representations using different embedding techniques

5. Run `06-Create-Timeseries-Data.ipynb` to create time-series data to feed through a GRU model.

6. Run `07-Timeseries-Baseline.ipynb` to create the GRU time-series baseline model to predict the 4 different clinical tasks

7. Run `08-Multimodal-Baseline.ipynb` to create the multimodal baseline model to predict the 4 different clinical tasks

8. Run `09-Proposed-Model.ipynb` to create the proposed model with CNN architecture to predict the 4 different clinical tasks

9. Run `DL4H_Team_34.ipynb` that summarizes the data, results and performance metrics among the different models (from notebooks 7-9).

## Results

The table below presents our reproducibility findings in a similar format to the paper's results.

![BaselineResults](https://github.com/zhenc5/CS598-Group-Project/blob/main/images/Baseline%20Result.png?raw=true)

![ProposedModelResults](https://github.com/zhenc5/CS598-Group-Project/blob/main/images/Proposed%20Model%20Result.png?raw=true)

## References
- Download the MIMIC-III dataset via https://mimic.physionet.org/
- MIMIC-Extract implementation: https://github.com/MLforHealth/MIMIC_Extract
- med7 implementation: https://github.com/kormilitzin/med7
- Download Pre-trained Word2Vec & FastText embeddings: https://github.com/kexinhuang12345/clinicalBERT
- Preprocessing Script: https://github.com/kaggarwal/ClinicalNotesICU

