# Hidden Markov Model (HMM)

## Project Overview

This project implements a **Hidden Markov Model (HMM)** to classify human activities using smartphone sensor data from accelerometer and gyroscope. The model distinguishes between motion patterns collected from two participants performing four distinct physical activities.

## Project Structure

```
HMM/
├── data/                          # Raw sensor data organized by participant
│   ├── david/                     # Data from participant David
│   └── queen/                     # Data from participant Queen
├── dataset/                       # Processed CSV files (52 files)
│   ├── jumping_david_01.csv       # 6 jumping sessions (David)
│   ├── jumping_queen_01.csv       # 5 jumping sessions (Queen)
│   ├── standing_david_01.csv      # 7 standing sessions (David)
│   ├── standing_queen_01.csv      # 7 standing sessions (Queen)
│   ├── still_david_01.csv         # 6 still sessions (David)
│   ├── still_queen_01.csv         # 7 still sessions (Queen)
│   ├── walking_david_01.csv       # 6 walking sessions (David)
│   └── walking_queen_01.csv       # 6 walking sessions (Queen)
├── logs/                          # Training and execution logs
├── outputs/                       # Generated outputs and visualizations
└── hmm_pipeline.ipynb             # Main HMM implementation notebook
```

## Model Architecture

* **Type**: Hidden Markov Model (HMM) with Gaussian emissions
* **States**: 4 (Jumping, Standing, Still, Walking)
* **Training Algorithm**: Baum-Welch
* **Decoding Algorithm**: Viterbi
---
## Features Extracted
* **Time-domain**: Mean, Standard Deviation, RMS, SMA, Correlations
* **Frequency-domain**: Dominant frequency components, spectral energy distribution
---
## Technical Implementation
* **Window Size**: 100 samples (1 second at 100 Hz)
* **Overlap**: 50% sliding window
* **Normalization**: Z-score standardization per feature
* **Data Format**: CSV files with timestamp, accelerometer (x,y,z), and gyroscope (x,y,z) values
---
## Usage
```bash
# Clone the repository
git clone https://github.com/dzuokumor/HMM.git
cd HMM

# Run the pipeline notebook
jupyter notebook hmm_pipeline.ipynb
```

---

## Requirements

```
numpy, pandas, matplotlib, seaborn, scipy, scikit-learn, hmmlearn, jupyter
```

Install dependencies:

```bash
pip install numpy pandas matplotlib seaborn scipy scikit-learn hmmlearn jupyter
```

---

## Pipeline Steps

1. **Data Loading** – Raw data is loaded from the `data/` directory
2. **Preprocessing** – Data is cleaned and structured into the `dataset/` directory
3. **Feature Extraction** – Relevant features are extracted for HMM training
4. **Model Training** – HMM is trained using the Baum-Welch algorithm
5. **Decoding** – Viterbi algorithm is applied to infer hidden state sequences
6. **Evaluation** – Performance metrics and results are saved to `outputs/`
7. **Logging** – Execution details and metrics are recorded in `logs/`

---

## Output Files

* `outputs/` – Predicted sequences, evaluation metrics, and visualizations
* `logs/` – Training logs and runtime information
