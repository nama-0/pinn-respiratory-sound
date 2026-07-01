# Raw Data Directory

The original respiratory sound dataset is not included in this repository.

This project uses the ICBHI 2017 Respiratory Sound Database, available from Kaggle:

https://www.kaggle.com/datasets/vbookshelf/respiratory-sound-database

After downloading and extracting the Kaggle archive, copy the original
`audio_and_txt_files/` directory into:

```text
data/raw/audio_and_txt_files/
```

Keep the full `audio_and_txt_files/` directory downloaded from Kaggle. The
public demo reads the selected file list from:

```text
data/selected_files.csv
```

and loads only the corresponding `.wav` files from:

```text
data/raw/audio_and_txt_files/
```

The annotation `.txt` files may remain in the same directory as provided in
the original dataset, but they are not required to run the public demo.

## Dataset Selection Background

For the broader study, a candidate pool was constructed using patient-level
diagnostic labels and cycle-level respiratory-event annotations from the ICBHI
dataset.

The resulting recording-level event distribution is shown below.

| Diagnosis | both | crackle | no-event | wheeze |
|:--|--:|--:|--:|--:|
| Healthy | 2 | 4 | **28** | 1 |
| Pneumonia | 0 | **7** | 22 | **8** |

Here, `both` denotes recordings containing both wheeze and crackle events,
whereas `no-event` denotes recordings with no annotated wheeze or crackle
events.

The study-level candidate pool was defined using the following three groups:

- **health:** Healthy / no-event recordings (28 recordings)
- **wheeze:** Pneumonia / wheeze recordings (8 recordings)
- **crackle:** Pneumonia / crackle recordings (7 recordings)

Therefore, the candidate pool contained 43 recordings in total. The remaining
categories in the table were not used in this study.

Patient diagnostic labels and annotation `.txt` files were used only to
construct this candidate pool. The public demo does not recreate this
selection procedure and does not require `patient_diagnosis.csv` to be placed
in `data/raw/`.

## Selected Files Used in This Project

For the public demo experiment, two representative recordings were selected
from each candidate group:

- health: 2 recordings
- wheeze: 2 recordings
- crackle: 2 recordings

Therefore, the demo uses six audio files in total. These files are listed in
`data/selected_files.csv`.

```csv
group,filename
health,159_1b1_Ar_sc_Meditron.wav
health,126_1b1_Al_sc_Meditron.wav
wheeze,122_2b3_Ar_mc_LittC2SE.wav
wheeze,122_2b2_Tc_mc_LittC2SE.wav
crackle,140_2b2_Ll_mc_LittC2SE.wav
crackle,219_2b2_Ar_mc_LittC2SE.wav
```

## Expected Directory Structure

After preparing the data, the directory structure should look like this:

```text
data/
├── README.md
├── selected_files.csv
└── raw/
    └── audio_and_txt_files/
        ├── 159_1b1_Ar_sc_Meditron.wav
        ├── 159_1b1_Ar_sc_Meditron.txt
        ├── 126_1b1_Al_sc_Meditron.wav
        ├── 126_1b1_Al_sc_Meditron.txt
        ├── 122_2b3_Ar_mc_LittC2SE.wav
        ├── 122_2b3_Ar_mc_LittC2SE.txt
        ├── 122_2b2_Tc_mc_LittC2SE.wav
        ├── 122_2b2_Tc_mc_LittC2SE.txt
        ├── 140_2b2_Ll_mc_LittC2SE.wav
        ├── 140_2b2_Ll_mc_LittC2SE.txt
        ├── 219_2b2_Ar_mc_LittC2SE.wav
        ├── 219_2b2_Ar_mc_LittC2SE.txt
        └── ...
```

The `audio_and_txt_files/` directory may contain all original ICBHI audio and
annotation files. The demo loads only the six `.wav` files listed in
`selected_files.csv`.

## Important Note

This repository does not redistribute the original ICBHI audio recordings or
annotation files.

Users must download the dataset separately from Kaggle and ensure that their
use complies with the dataset license and terms of use.