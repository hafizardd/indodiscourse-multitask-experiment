# Reproducibility record

## Source and method

The authoritative sample method is
skripsi-indodiscourse/proposal/chapters/bab3-metodologi.tex. Record the
IndoDiscourse repository, main configuration, pinned revision, canonical
filename, expected and actual row counts, SHA-256, schema audit, and proposal
sample ledger for every run. The expected source is 28,448 rows with SHA-256
94bb43546f5040a606a8d842694b7d490df043051377a6580e1e95ad2c7334e7.

The current snapshot has null text at source row index 10,295. The proposal
requires text to be a string and malformed data to halt. The preprocessing
manifest therefore remains blocked; no sample or token arrays are produced.
Do not change this behavior without a method amendment.

Record the tokenizer repository and revision
(indolem/indobertweet-base-uncased,
32e28c05b47e33b6675d2670a1745c50a65e987a), Python and package versions, and
Kaggle runtime details in notebook reports. The raw JSONL is cached under
/tmp during a run, not /kaggle/working.

## Private artifact handoff

Run the notebooks in order as private Kaggle kernels:

1. EDA writes aggregate reports and figures only.
2. Preprocessing writes a validation report and manifest. It writes a
   text-bearing sample only after the source passes validation.
3. Feature extraction requires a ready upstream manifest and verifies the
   sample hash, row count, and schema before tokenizing. It stores model inputs,
   targets, and split metadata separately and does not create folds.

Kaggle notebook outputs are the only intermediate handoff. Notebook 03 attaches
the private output of notebook 02 through kernel_sources. Keep all kernels and
outputs private until redistribution rights for derived artifacts are
confirmed. Do not create a Kaggle Dataset or commit data and outputs to GitHub.

Kaggle executions have not been performed yet. The saved notebooks contain no
outputs, and no results should be reported until the relevant kernels have run.

## Planned model experiment

The later experiment compares toxicity STL, polarization STL, and shared
encoder MTL using the same five StratifiedGroupKFold splits, stratified by the
joint label pair, with split seed 42. Planned training uses seeds 42, 43, and
44, three epochs, and 45 full-model fine-tuning runs. Report OOF macro-F1 per
task, paired MTL-minus-matching-STL differences, and 10,000 paired
group-bootstrap resamples for 95% intervals. A technical smoke run is excluded
from reported results.

For each completed run, record the complete TOML configuration, condition,
fold, seed, optimizer updates, elapsed time, skipped updates, predictions,
metrics, and output hashes. Record split, training, data-order, and bootstrap
seeds. Resume only from completed run boundaries.
