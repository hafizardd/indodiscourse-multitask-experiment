# Kaggle notebook workflow

These three notebooks are the first-stage workflow. They are separate Kaggle
kernels so that each stage has its own private output and metadata.

| Order | Folder | Purpose |
|---|---|---|
| 1 | 01-eda | Aggregate-only EDA and method checks; independent of other kernels |
| 2 | 02-preprocessing | Validate the pinned source and create the proposed sample if valid |
| 3 | 03-feature-extraction | Validate the private output of notebook 02 and prepare model inputs |

## Upload and run

1. Replace YOUR_KAGGLE_USERNAME in each folder's kernel-metadata.json.
2. Keep each kernel private, internet enabled, and GPU disabled.
3. Upload each folder from the repository root:

   - kaggle kernels push -p kaggle/notebooks/01-eda
   - kaggle kernels push -p kaggle/notebooks/02-preprocessing
   - kaggle kernels push -p kaggle/notebooks/03-feature-extraction

4. Run 01 and 02 on Kaggle. Notebook 03 is connected to the private output of
   02 through kernel_sources. Kaggle notebook outputs can be attached as inputs
   to later notebooks; no Kaggle Dataset mirror is created.
5. Review each run's manifest and output before continuing. The current pinned
   source has null text at row index 10295. Notebook 02 therefore writes a
   blocked validation report and manifest without a sample. Notebook 03 detects
   that status and stops before tokenization.

## Privacy and handoff

Notebook 01 writes aggregate reports and figures only. Notebook 02 may write a
text-bearing sample, and notebook 03 may write token arrays and split metadata.
Keep all three kernels and their outputs private. Do not publish outputs or
create a Kaggle Dataset until redistribution rights for derived artifacts are
confirmed. No dataset, processed sample, token array, or notebook output belongs
in GitHub.

The raw file is downloaded from the pinned public Hugging Face revision into
/tmp and checked against the configured SHA-256. No HF token is required.
Notebook explanations are written in Indonesian. Kaggle executions have not
been performed yet.
