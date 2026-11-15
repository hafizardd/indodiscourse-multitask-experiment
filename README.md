# IndoDiscourse Multi-Task Experiment

Reproducible Kaggle experiment comparing single-task and multi-task
IndoBERTweet models for toxicity and polarization detection on IndoDiscourse.

**Status:** the first stage is split into three private Kaggle notebooks for
EDA, preprocessing, and feature extraction. The pinned source currently blocks
preprocessing because one row has null text and the proposal requires a string.
Training and evaluation remain planned. This repository contains no dataset,
model weights, or run outputs.

## Research question

Does a shared IndoBERTweet encoder trained jointly for toxicity and polarization
produce different macro-F1 performance from separate single-task models when
all conditions use the same examples and grouped five-fold splits?

The proposal compares three conditions:

1. Single-task toxicity classifier (STL).
2. Single-task polarization classifier (STL).
3. Multi-task classifier (MTL) with one shared encoder and separate output
   heads.

This is full-model fine-tuning, not adapter or PEFT training.

## Experiment outline

- Source data: `Exqrch/IndoDiscourse` on Hugging Face, `main` configuration.
- Sample preparation: strict-majority labels for both tasks; exclude unresolved
  ties; exclude an empty text only when its label pair is `(0, 0)`.
- Grouping: NFKC, case-fold, trim, and collapse whitespace to create the group
  key; preserve the original text for model input.
- Split: five-fold `StratifiedGroupKFold`, stratified on the joint label pair,
  split seed `42`.
- Training: three conditions × five folds × three seeds (`42`, `43`, `44`) =
  45 full training runs, three epochs per run.
- Evaluation: out-of-fold predictions, macro-F1 per task, paired MTL–STL
  differences, and 10,000 paired group-bootstrap resamples for 95% intervals.
- Execution: Kaggle GPU, with a technical smoke run followed by resumable
  batches. The smoke run is excluded from reported results.

The full configuration is in
[`kaggle/config/experiment.toml`](kaggle/config/experiment.toml). It records
the pinned dataset revision and planned experiment settings.

## Dataset access and citation

The dataset is not included in this repository. Use the upstream Hugging Face
repository as the canonical source; the first stage pins its immutable revision.
A public Kaggle mirror is out of scope unless the right to redistribute is
confirmed. See [`docs/DATA.md`](docs/DATA.md) before obtaining
or sharing data.

The current `main` configuration has 28,448 rows; the separate annotator
configuration has 29, and the dataset-level aggregate is 28,477. The meaning
of the historical paper/card count remains uncertain.

Please cite both the original IndoDiscourse paper and the dataset page. See
[`CITATION.cff`](CITATION.cff) and the citation guidance in `docs/DATA.md`.

## Kaggle notebook workflow

Run the notebooks in order on Kaggle. Per-notebook metadata, upload commands,
private output handoff, and the current preprocessing blocker are documented in
[kaggle/notebooks/README.md](kaggle/notebooks/README.md). Notebook cells are
saved without outputs. Kaggle runs have not been performed yet.

The existing [kaggle/kernel-metadata.json](kaggle/kernel-metadata.json) remains
reserved for the later training notebook.

## Development

Use GitHub Flow: create a short branch, commit a focused change, and open a Pull
Request to `main`. Commit messages follow Conventional Commits in English. See
[`CONTRIBUTING.md`](CONTRIBUTING.md) for branch, commit, and PR guidance.

The MIT license applies to original code in this repository only. It does not
change the terms for IndoDiscourse, IndoBERTweet, or other upstream assets.
