# Raw Data Directory

The original respiratory sound dataset is not included in this repository.

This project uses the ICBHI 2017 Respiratory Sound Database, available from Kaggle:

https://www.kaggle.com/datasets/vbookshelf/respiratory-sound-database

Please download the dataset from Kaggle and extract the raw files under:

```text
data/raw/
```

The code reads the list of selected audio files from:

```text
data/selected_files.csv
```

and recursively searches for the corresponding `.wav` files under `data/raw/`.

## Dataset Description

The ICBHI 2017 Respiratory Sound Database contains respiratory sound recordings with cycle-level annotations. The dataset includes normal and abnormal respiratory sounds, including crackles and wheezes.

In this project, we considered the healthy and pneumonia-related subset used in prior respiratory sound studies. This subset consists of 43 recordings in total:

* 28 healthy recordings
* 15 pneumonia recordings

Among the pneumonia recordings, wheeze and crackle recordings were considered separately.

## Selected Files Used in This Project

For this public demo experiment, we selected one representative recording from each group:

* health: 1 recording
* wheeze: 1 recording
* crackle: 1 recording

Therefore, only three audio files are listed in `data/selected_files.csv`.

Example structure of `selected_files.csv`:

```csv
group,filename
health,217_1b1_Tc_sc_Meditron.wav
wheeze,122_2b3_Al_mc_LittC2SE.wav
crackle,219_2b2_Ar_mc_LittC2SE.wav
```

## Expected Directory Structure

After downloading and extracting the dataset, the directory structure should look like this:

```text
data/
├── README.md
├── selected_files.csv
└── raw/
    ├── ...
    ├── 217_1b1_Tc_sc_Meditron.wav
    ├── 122_2b3_Al_mc_LittC2SE.wav
    ├── 219_2b2_Ar_mc_LittC2SE.wav
    └── ...
```

The raw dataset may contain subdirectories. This is allowed because the code searches for the selected `.wav` files recursively under `data/raw/`.

## Important Note

This repository does not redistribute the original ICBHI audio files.

Users must download the dataset separately from Kaggle and ensure that their use complies with the dataset license and terms of use.
