# PINN-based Respiratory Sound Analysis

This repository provides a public demo implementation of a physics-informed
neural network (PINN)-based respiratory sound analysis framework.

The model represents short respiratory sound segments as trajectories of a
driven Duffing oscillator and estimates interpretable oscillator parameters
from respiratory audio signals.

## Overview

The purpose of this project is not to build a black-box respiratory disease
classifier, but to investigate whether physically interpretable oscillator
parameters recovered from short respiratory sound segments can show
class-dependent patterns across different respiratory sound groups.

The public demo uses selected recordings from the ICBHI 2017 Respiratory Sound
Database and analyzes three respiratory sound groups:

- health
- wheeze
- crackle

## Repository Structure

```text
pinn-respiratory-sound/
├── README.md
├── data/
│   ├── README.md
│   └── selected_files.csv
├── notebooks/
│   └── pinn_public_demo.ipynb
└── results/
```

## Main Files

- `notebooks/pinn_public_demo.ipynb`  
  Main notebook for preprocessing respiratory sound signals, training the PINN
  model, estimating Duffing oscillator parameters, and generating analysis
  outputs.

- `data/README.md`  
  Instructions for downloading and preparing the respiratory sound dataset,
  including the dataset-selection background.

- `data/selected_files.csv`  
  List of selected `.wav` files used in the public demo experiment.

- `results/`  
  Directory for generated outputs such as figures, parameter tables, and
  analysis results.

## Data

The original respiratory sound dataset is not included in this repository.

This project uses the ICBHI 2017 Respiratory Sound Database, available from
Kaggle:

https://www.kaggle.com/datasets/vbookshelf/respiratory-sound-database

After downloading and extracting the Kaggle archive, copy the original
`audio_and_txt_files/` directory into:

```text
data/raw/audio_and_txt_files/
```

The notebook reads the selected file list from:

```text
data/selected_files.csv
```

and loads only the corresponding `.wav` files from:

```text
data/raw/audio_and_txt_files/
```

For detailed data-preparation instructions and the background of the
recording-selection procedure, see:

```text
data/README.md
```

## Selected Demo Files

The public demo uses two recordings from each group, for a total of six audio
files:

```csv
group,filename
health,159_1b1_Ar_sc_Meditron.wav
health,126_1b1_Al_sc_Meditron.wav
wheeze,122_2b3_Ar_mc_LittC2SE.wav
wheeze,122_2b2_Tc_mc_LittC2SE.wav
crackle,140_2b2_Ll_mc_LittC2SE.wav
crackle,219_2b2_Ar_mc_LittC2SE.wav
```

## Method Summary

Each respiratory audio recording is preprocessed and divided into short time
windows. For each selected window, a PINN is trained to fit the waveform while
satisfying the residual of a driven Duffing oscillator model:

```text
u'' + αu' + βu + γu^3 = B cos(ωt + φ)
```

The recovered parameters provide compact, physically interpretable features of
each respiratory sound segment.

## Usage

Clone the repository:

```bash
git clone https://github.com/nama-0/pinn-respiratory-sound.git
cd pinn-respiratory-sound
```

Prepare the dataset by following the instructions in:

```text
data/README.md
```

Then open and run the main notebook:

```bash
jupyter notebook notebooks/pinn_public_demo.ipynb
```

## Notes

- The raw ICBHI audio recordings and annotation files are not redistributed in
  this repository.
- Users must download the dataset separately and comply with the dataset
  license and terms of use.
- Generated outputs such as model checkpoints, raw audio files, and large
  result files should not be committed to the repository.
- This repository is intended as a reproducible public demo of the
  PINN-based respiratory sound analysis workflow.

## License

Please refer to the repository license for the source code. The respiratory
sound dataset is subject to its own license and terms of use.