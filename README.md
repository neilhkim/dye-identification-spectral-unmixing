# Dye Identification from Spectral Intensity Data

[Open in Google Colab](https://colab.research.google.com/github/neilhkim/dye-identification-spectral-unmixing/blob/main/notebook.ipynb)

Constrained spectral unmixing of 8-channel fluorescence data to identify whether each PCR compartment contains no dye, one dye, or two dyes.

---

## Files

- `notebook.ipynb` — full analysis and visualizations  
- `requirements.txt` — Python dependencies  
- `data/reference_spectra.csv` — reference dye spectra (8 channels × 8 dyes)  
- `data/intensity_data.csv` — fluorescence measurements for PCR compartments  

---

## Method

The notebook performs a sequential decision pipeline:

1. Detect empty compartments using signal magnitude (\|\|y\|\|).
2. Estimate dye contributions using non-negative least squares (NNLS).
3. Enumerate all valid models (1-dye and 2-dye combinations).
4. Select the best model using Bayesian Information Criterion (BIC).
5. Validate assignments using goodness-of-fit (\(R^2\)).

The signal model is

\[
y = R x + \epsilon
\]

where:

- \(y\) — observed fluorescence vector (8 channels)  
- \(R\) — reference dye spectra matrix  
- \(x\) — dye intensities  
- \(\epsilon\) — measurement noise  

Physical constraints:

- dye intensities must be non-negative  
- each compartment contains **at most two dyes**

---

## Setup

Tested with **Python 3.11**.

### Create and activate a virtual environment

#### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

#### macOS / Linux

```bash
python -m venv venv
source venv/bin/activate
```

---

### Install dependencies

```bash
pip install -r requirements.txt
```

---

## Run

Launch the notebook:

```bash
jupyter notebook notebook.ipynb
```

Then execute cells sequentially.

---

## Output

The notebook generates:

- compartment classifications (empty, 1-dye, 2-dye)
- dye-call summaries across the dataset
- BIC model selection diagnostics
- \(R^2\) goodness-of-fit validation
- plots illustrating signal separation, noise structure, and spectral fits

---

## Reproducibility

To reproduce the analysis:

1. Clone or download the repository.
2. Create a Python virtual environment.
3. Install dependencies from `requirements.txt`.
4. Run `notebook.ipynb` from top to bottom.

All figures and results are generated directly from the notebook.