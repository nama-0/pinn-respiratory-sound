# PINN-based Respiratory Sound Analysis

This repository provides a public demo implementation of a physics-informed neural network (PINN)-based respiratory sound analysis framework.

The model represents short respiratory sound segments as trajectories of a driven Duffing oscillator and estimates interpretable oscillator parameters from respiratory audio signals.

## Overview

The purpose of this project is not to build a black-box respiratory disease classifier, but to investigate whether physically interpretable oscillator parameters recovered from short respiratory sound segments can show class-dependent patterns across different respiratory sound groups.

The public demo uses selected recordings from the ICBHI 2017 Respiratory Sound Database and analyzes three representative respiratory sound groups:

* healthy
* wheeze
* crackle

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

* `notebooks/pinn_public_demo.ipynb`
  Main notebook for preprocessing respiratory sound signals, training the PINN model, estimating Duffing oscillator parameters, and generating analysis outputs.

* `data/README.md`
  Instructions for downloading and preparing the respiratory sound dataset.

* `data/selected_files.csv`
  List of selected `.wav` files used in the public demo experiment.

* `results/`
  Directory for generated outputs such as figures, parameter tables, and analysis results.

## Data

The original respiratory sound dataset is not included in this repository.

This project uses the ICBHI 2017 Respiratory Sound Database, available from Kaggle:

https://www.kaggle.com/datasets/vbookshelf/respiratory-sound-database

Please download the dataset separately and extract the raw files under:

```text
data/raw/
```

The code reads the selected file list from:

```text
data/selected_files.csv
```

and recursively searches for the corresponding `.wav` files under `data/raw/`.

For more details, see:

```text
data/README.md
```

## Selected Demo Files

The public demo uses one representative recording from each group:

```csv
group,filename
health,217_1b1_Tc_sc_Meditron.wav
wheeze,122_2b3_Al_mc_LittC2SE.wav
crackle,219_2b2_Ar_mc_LittC2SE.wav
```

## Method Summary

Each respiratory audio recording is preprocessed and divided into short time windows.
For each selected window, a PINN is trained to fit the waveform while satisfying the residual of a driven Duffing oscillator model:

```text
u'' + αu' + βu + γu^3 = B cos(ωt + φ)
```

The recovered parameters provide compact, physically interpretable features of the respiratory sound segment.

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

* The raw ICBHI audio files are not redistributed in this repository.
* Users must download the dataset separately and comply with the dataset license and terms of use.
* Generated outputs such as model checkpoints, raw audio files, and large result files should not be committed to the repository.
* This repository is intended as a reproducible public demo of the PINN-based respiratory sound analysis workflow.

## License

Please refer to the repository license for the source code.
The respiratory sound dataset is subject to its own license and terms of use.
