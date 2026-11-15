# Dataset and model access

## IndoDiscourse source

Use only the canonical JSONL file from the public Hugging Face repository
[Exqrch/IndoDiscourse](https://huggingface.co/datasets/Exqrch/IndoDiscourse):

- Configuration: main
- Revision: 8af8c0f00b05633c05cc41fbd7650178ababc892
- File: indotoxic2024_annotated_data_v2_final.jsonl
- SHA-256: 94bb43546f5040a606a8d842694b7d490df043051377a6580e1e95ad2c7334e7
- Expected source rows: 28,448

Do not load the separate 29-row annotator configuration or demographics. The
notebooks download only this file into /tmp, verify its hash, and record
runtime versions. Public access does not require an HF token. Do not create a
Kaggle Dataset mirror or commit raw or derived data to GitHub.

At the pinned revision, row index 10,295 has null text and label pair (0, 0).
The proposal requires every text value to be a string and malformed data to
halt processing. Notebook 01 reports the anomaly and limits exploratory
analysis to valid rows. Notebook 02 writes a validation report containing only row indices and
column names, plus a blocked manifest without creating a sample. Notebook 03 honors that status
and does not tokenize. Do not coerce, drop, or otherwise resolve this row
without an approved method amendment.

The proposal's sample rules remain authoritative: strict majority per task;
exclude a row if either task is tied; exclude an exact empty string only for
label pair (0, 0); retain whitespace-only text, noise/spam rows, and duplicate
rows. The group key uses NFKC, casefold, trim, and collapsed whitespace.
Keep text_id only as provenance metadata, outside model inputs. Preserve original text as the only classifier input. Do not manually normalize
emoji, slang, punctuation, URLs, profanity, or mixed language.

Review the dataset card, original paper, license, and responsible-use terms
before sharing derived artifacts. The dataset card displays Apache-2.0; the
paper also describes research-use and responsible-use restrictions. Consider
those terms together. Cite the dataset and original paper; see CITATION.cff.

## IndoBERTweet tokenizer

Feature extraction uses only the tokenizer from
[indolem/indobertweet-base-uncased](https://huggingface.co/indolem/indobertweet-base-uncased),
pinned at revision 32e28c05b47e33b6675d2670a1745c50a65e987a. The model
revision and terms are separate from this repository's MIT license. EDA loads
the tokenizer on CPU without model weights.

## Private outputs

Notebook 01 may save aggregate reports and figures only. Notebook 02 may save
a text-bearing processed sample after validation is resolved. Notebook 03 may
save token arrays and split metadata. Keep kernels and outputs private until
rights to share the derived artifacts are confirmed. Kaggle notebook outputs
are the intermediate handoff; do not create a Kaggle Dataset. No notebook
outputs or derived data are committed to GitHub.
