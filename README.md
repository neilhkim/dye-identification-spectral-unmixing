# Dye Identification from Spectral Intensity Data

Constrained spectral unmixing of 8-channel fluorescence data to identify whether each PCR compartment contains no dye, one dye, or two dyes.

## Files

- `notebook.ipynb` — full analysis
- `requirements.txt` — Python dependencies
- `data/reference_spectra.csv` — reference dye spectra
- `data/intensity_data.csv` — compartment intensity data

## Method

The notebook:

1. detects empty compartments using signal magnitude
2. fits nonnegative dye intensities with NNLS
3. evaluates all 1-dye and 2-dye models
4. selects the best model with BIC
5. uses \(R^2\) as a quality check

## Setup

Tested with Python 3.11.

### Create and activate a virtual environment

#### Windows

```bash
python -m venv venv
venv\Scripts\activate