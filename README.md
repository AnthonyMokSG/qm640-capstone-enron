# QM640 Capstone: Enron Boundary Stress Signal Detection

Detecting organisational risk signals through combined network and
linguistic analysis of the Enron email corpus, focused on the
Executive Leadership–Trading boundary (January 1999 to December 2001).

## Repository Structure

All analysis is conducted in a single notebook
(`01_extraction/qm640_extraction.ipynb`). A second-pass deduplication
correction (see below) means the notebook contains two vintages of the
analysis pipeline: the superseded run (Steps 35 to 54, computed on the
287-event set, preserved unaltered as the audit record) and the
corrected run (Steps 58 to 65, computed on the 250-event set), which is
authoritative. Corrected outputs carry a `_corrected` suffix alongside
their superseded counterparts.

- `01_extraction/` — The project notebook: extraction with
  address-level verification, first-pass deduplication, effective-N and
  power verification (Steps 1 to 34); the superseded analysis run
  (Steps 35 to 54); the June 2001 content examination, second-pass
  deduplication discovery and correction (Steps 58 to 60); and the
  corrected analysis pipeline with deferred inference and the topic
  component (Steps 55 to 56, 61 to 65)
- `02_aggregation/` — Monthly aggregates, volume charts, the 20-entry
  cleaning log, and the second-pass duplicate audit
  (second_pass_duplicate_audit.csv, second_pass_dropped_records.csv)
- `03_network_analysis/` — Stage 1 outputs: monthly degree centrality,
  superseded and corrected series and charts
- `04_linguistic_analysis/` — Stage 2 outputs: monthly VADER sentiment,
  superseded and corrected series and charts, and the BERTopic topic
  overview (topic component declared infeasible at this document count;
  see Step 56)
- `05_changepoint_detection/` — Stage 3 and 4 outputs: pre-registered
  ground-truth labels, composite index, precision evaluations,
  bootstrap inference, CUSUM runs (superseded and corrected), and the
  deferred inferential test results

## Data Correction Note

A second-pass deduplication (Steps 58 to 60) identified 37 records
across 33 groups of byte-identical messages that the first-pass rule
(exact timestamp match) structurally could not catch, correcting the
event total from 287 to 250. The full analysis pipeline was recomputed
on the corrected set (Steps 61 to 65); every principal finding
reproduced. Both vintages are committed; the corrected figures are
authoritative.

## Data Access

This project uses the publicly released Enron email corpus:

- Enron email corpus: https://huggingface.co/datasets/corbt/enron-emails
- Raw corpus mirror (CMU): https://www.cs.cmu.edu/~enron/

The corpus-linked position-classification file referenced in early
Enron research is not publicly available (Diesner & Carley, 2005).
Boundary personnel roles are verified manually against public records;
the verification is documented in the notebook.

The raw corpus (517,401 emails) is not stored in this repository due to
size. The notebook fetches it directly.

## Reproducing the Analysis

1. Open `01_extraction/qm640_extraction.ipynb` in Google Colab
2. Run the session setup cells (Steps 1 to 2), then the extraction
   pipeline (Steps 7 to 34), then the correction steps (59 to 60),
   which re-derive the corrected 250-event set. Steps 3 to 6 are
   one-time repository setup; Steps 35 to 54 are the superseded run —
   both are marked in the notebook as not to be re-run
3. The corrected pipeline (Steps 61 to 65) reads only the committed
   CSVs in the stage folders, so it is reproducible without the corpus
   fetch. Step 62 applies VADER scoring internally, so no superseded
   step is a dependency
4. Expected checkpoints are stated in the notebook's run-sequence
   guidance (33/37/250 at Step 59; 37 and 73/177 at Step 60)

## Author

Anthony Mok, Walsh College, QM640 Data Analytics Capstone;
Mentored by Mr Sharath Srivatsa;
Faculty Supervisors: Dr. Javad Katibai & Dr. Srabashi Basu
