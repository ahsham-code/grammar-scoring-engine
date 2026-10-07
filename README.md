# Grammar Scoring Engine

## Overview

This project predicts continuous grammar scores for spoken English audio.

The task is formulated as a supervised regression problem, where each audio sample is assigned a grammar score between 1 and 5.

## Dataset

- Training samples: 769
- Test samples: 216
- Audio format: WAV
- Sampling rate: 16 kHz
- Audio channels: Mono

## Feature Engineering

The final feature representation contains 119 acoustic and prosodic features, including:

- MFCC
- Delta MFCC
- Spectral features
- Zero-crossing rate
- RMS energy
- Pitch statistics
- Spectral contrast
- Chroma
- Energy dynamics
- Spectral flux

## Model

An ExtraTrees Regressor was selected after comparing multiple regression models.

Final configuration:

- Estimators: 1000
- max_features: 1.0
- min_samples_leaf: 1
- random_state: 42

## Results

| Metric | Score |
|---|---:|
| Training RMSE | 0.2194 |
| Training Pearson | 0.9883 |
| OOF RMSE | 0.7459 |
| OOF Pearson | 0.8009 |
| Kaggle Public Score | 0.7034 |

The out-of-fold metrics provide a more reliable estimate of generalization performance than the training metrics.

## Limitations

The model primarily uses acoustic and prosodic information and does not directly analyze the linguistic content of the speech.

Future improvements could include speech transcription, linguistic features, grammar-error detection, and pretrained speech representations.

## Files

- `grammar_scoring_engine.ipynb` — Complete documented notebook
- `submission_v3.csv` — Final Kaggle submissions.
