# QM640 Capstone: Enron Boundary Stress Signal Detection

Detecting organisational risk signals through combined network and
linguistic analysis of the Enron email corpus, focused on the
Executive Leadership–Trading boundary (January 1999 to December 2001).

## Repository Structure

- `01_extraction/` — Boundary-filtered extraction with address-level
  verification of boundary personnel and deduplication
  (`qm640_extraction.ipynb`, Steps 1 to 33)
- `02_aggregation/` — Monthly aggregates (pre- and post-deduplication),
  volume charts, and the data cleaning log
- `03_network_analysis/` — NetworkX centrality measures (pending)
- `04_linguistic_analysis/` — VADER sentiment scoring and BERTopic
  topic modelling (pending)
- `05_changepoint_detection/` — CUSUM changepoint detection via
  statsmodels and ruptures (pending)

## Data Access

This project uses the publicly released Enron email corpus:

- Enron email corpus: https://huggingface.co/datasets/corbt/enron-emails
- Raw corpus mirror (CMU): https://www.cs.cmu.edu/~enron/

The corpus-linked position-classification file referenced in early
Enron research is not publicly available (Diesner & Carley, 2005).
Boundary personnel roles are verified manually against public records
(regulatory reports, court documents, contemporaneous press coverage);
the verification is documented in the extraction notebook.

The raw corpus (517,401 emails) is not stored in this repository due to
size. The extraction notebook fetches it directly. Committed outputs
(monthly aggregates, charts, data cleaning log) are in `02_aggregation/`.

## Reproducing the Extraction

1. Open `01_extraction/qm640_extraction.ipynb` in Google Colab
2. Run the session setup cells (Steps 1 to 2), then Step 7 onward.
   Steps 3 to 6 are one-time repository setup and are marked in the
   notebook as not to be re-run
3. The corpus is fetched fresh each session; outputs are written to
   `02_aggregation/`

## Author

Anthony Mok, Walsh College, QM640 Data Analytics Capstone
Supervised by Sharath Srivatsa; Faculty Mentor Dr. Srabashi Basu
