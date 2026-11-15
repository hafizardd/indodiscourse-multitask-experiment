# Dataset and model access

## IndoDiscourse

The canonical source is
[`Exqrch/IndoDiscourse`](https://huggingface.co/datasets/Exqrch/IndoDiscourse)
on Hugging Face. The experiment uses the dataset's `main` configuration only;
the separate annotator-demographics configuration is not needed by the
proposal's model inputs.

Before a run:

1. Review the dataset card, the original paper, and the license/usage terms.
2. Use the pinned dataset revision `8af8c0f00b05633c05cc41fbd7650178ababc892`
   and record it for reported runs; do not use a moving branch.
   The main JSONL SHA-256 is also pinned in `kaggle/config/experiment.toml`
   and checked by the local first-stage notebook.
3. Record the revision, file fingerprint, schema, actual row count, and the
   result of the proposal's sample-construction audit in the run manifest.
4. Keep the dataset files out of GitHub. Do not publish a Kaggle mirror unless
   the dataset authors or maintainer confirm the redistribution rights.

The Hugging Face page currently displays `Apache-2.0`. The paper also states
that the dataset is for research on detecting and moderating toxic and
polarizing content, rules out surveillance and profiling, and asks users to
preserve its ethical guidelines when redistributing or modifying it. The
license and those responsible-use conditions must be considered together.

At the pinned revision, the current dataset-server configuration sizes are
28,448 rows for `main/main` and 29 for the separate `annotator/annotator`
configuration, totaling 28,477 at dataset level. Only `main` is loaded. This
observation does not establish what the historical paper or card meant by
28,477 texts. Record actual counts and compare them with the proposal without
forcing a match.

The local validation found one method blocker in the pinned `main` file: row
index 10,295 has a null `text` value and the label pair `(0, 0)`. The proposal
requires every text value to be a string and says malformed rows halt
processing. The notebook therefore stops at validation and does not coerce this
value to an empty string or drop the row. Resume preprocessing only after the
method specifies how to handle it.

## IndoBERTweet

The planned model source is
[`indolem/indobertweet-base-uncased`](https://huggingface.co/indolem/indobertweet-base-uncased).
Pin its revision independently from the dataset. Its license and terms remain
separate from this repository's MIT license.

## Citation

Please cite the dataset repository and the original paper:

> Susanto, L., Wijanarko, M. I., Pratama, P. A., Tang, Z., Akyas, F., Hong, T.,
> Idris, I. K., Aji, A. F., & Wijaya, D. T. (2025). A multi-labeled dataset for
> Indonesian discourse: Examining toxicity, polarization, and demographics
> information. *Findings of the Association for Computational Linguistics: ACL
> 2025*, 18863–18890. https://doi.org/10.18653/v1/2025.findings-acl.966

## Local cache and outputs

The local first-stage notebook caches the pinned main JSONL in `data/raw`
and writes a derived JSONL and provenance manifest in `data/processed`.
The source file SHA-256 is pinned in the experiment config and checked against
the cache.
Both locations are Git-ignored. The derived file retains original text, labels,
group metadata and diagnostics, but no annotator IDs or demographics. Treat it
as dataset content and do not publish it before redistribution rights are clear.

## Outputs

Do not copy raw text into GitHub or attach it to a public notebook output. Keep
training logs, predictions, metrics, and checkpoints under the Kaggle working
directory. Review derivative outputs before sharing them publicly.
