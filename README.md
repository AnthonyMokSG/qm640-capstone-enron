# QM640 Capstone: Enron Boundary Stress Signal Detection

Detecting organisational risk signals through combined network and
linguistic analysis of the Enron email corpus, focused on the
Executive Leadership–Trading boundary (January 1999 to December 2001).

## Repository Structure

All analysis is conducted in a single notebook
(`01_extraction/qm640_extraction.ipynb`), which runs through the
project's four analysis stages; each stage writes its outputs to its
own folder below.

- `01_extraction/` — The project notebook: boundary-filtered extraction
  with address-level verification of boundary personnel, deduplication,
  effective-N and power verification (Steps 1 to 34), and the Stage 1
  to 4 analysis pipeline (Steps 35 to 54)
- `02_aggregation/` — Monthly aggregates (pre- and post-deduplication),
  volume charts, and the data cleaning log
- `03_network_analysis/` — Stage 1 outputs (complete): monthly NetworkX
  degree centrality series and chart
- `04_linguistic_analysis/` — Stage 2 outputs (sentiment component
  complete): VADER monthly sentiment series with dispersion and tail
  measures, and chart; BERTopic topic component scheduled
- `05_changepoint_detection/` — Stage 3 and 4 outputs (complete):
  pre-registered ground-truth labels, composite index, precision
  evaluation under the pre-registered and sensitivity specifications,
  bootstrap inference, and CUSUM changepoint detection with a
  disclosed restart sensitivity

## Data Access

This project uses the publicly released Enron email corpus:

- Enron email corpus: https://huggingface.co/datasets/corbt/enron-emails
- Raw corpus mirror (CMU): https://www.cs.cmu.edu/~enron/

The corpus-linked position-classification file referenced in early
Enron research is not publicly available (Diesner & Carley, 2005).
Boundary personnel roles are verified manually against public records
(regulatory reports, court documents, contemporaneous press coverage);
the verification is documented in the notebook.

The raw corpus (517,401 emails) is not stored in this repository due to
size. The notebook fetches it directly. Committed outputs are in the
stage folders listed above.

## Reproducing the Analysis

1. Open `01_extraction/qm640_extraction.ipynb` in Google Colab
2. Run the session setup cells (Steps 1 to 2), then Step 7 onward.
   Steps 3 to 6 are one-time repository setup and are marked in the
   notebook as not to be re-run
3. The corpus is fetched fresh each session for the extraction and
   Stage 1 to 2 steps; Stages 3 and 4 (Steps 45 onward) read only the
   committed CSVs in the stage folders, so they are reproducible
   without the corpus fetch
4. Outputs are written to the relevant stage folder (`02_aggregation/`
   for extraction and aggregation, `03_network_analysis/` onward for
   the analysis stages)

## Author

Anthony Mok, Walsh College, QM640 Data Analytics Capstone;
Mentored by Mr Sharath Srivatsa;
Faculty Supervisors: Dr. Javad Katibai & Dr. Srabashi Basu
