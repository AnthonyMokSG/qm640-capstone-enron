# QM640 Capstone: Enron Boundary Stress Signal Detection

Detecting organisational risk signals through combined network and
linguistic analysis of the Enron email corpus, focused on the
Executive Leadership–Trading boundary (January 1999 to December 2001).

## Repository Structure

- `01_extraction/` — CASOS position-file boundary filtering, produces
  sender/recipient-level cross-boundary email counts
- `02_aggregation/` — Monthly aggregation of filtered emails into the
  variables used for centrality and changepoint analysis
- `03_network_analysis/` — NetworkX centrality measures
- `04_linguistic_analysis/` — VADER sentiment scoring and BERTopic
  topic modelling
- `05_changepoint_detection/` — ruptures-based changepoint detection
  and statsmodels analysis

## Data Access

This project uses the CASOS-released Enron email corpus, available at:
- Enron email corpus: https://huggingface.co/datasets/corbt/enron-emails
- CASOS position files (role classification): https://www.cs.cmu.edu/~enron/

The raw corpus (517,401 emails) is not stored in this repository due to
size. Scripts in `01_extraction/` fetch it directly. Only boundary-filtered
outputs and monthly aggregates are committed here.

## Reproducing the Extraction

1. Open `01_extraction/extraction.ipynb` in Google Colab
2. Run all cells in order; the notebook fetches the raw corpus and CASOS
   position files automatically
3. Outputs are written to `01_extraction/` (boundary-filtered counts) and
   `02_aggregation/` (monthly aggregates)

## Author

Anthony Mok, Walsh College, QM640 Data Analytics Capstone
Supervised by Sharath Srivatsa; Faculty Mentor Dr. Srabashi Basu
