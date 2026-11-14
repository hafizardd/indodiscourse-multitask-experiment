# Dataset and model access

## IndoDiscourse

The canonical source is
[`Exqrch/IndoDiscourse`](https://huggingface.co/datasets/Exqrch/IndoDiscourse)
on Hugging Face. The experiment uses the dataset's `main` configuration only;
the separate annotator-demographics configuration is not needed by the
proposal's model inputs.

Before a run:

1. Review the dataset card, the original paper, and the license/usage terms.
2. Pin the Hugging Face repository to an immutable commit revision. Do not use
   a moving `main` branch in a reported run.
3. Record the revision, file fingerprint, schema, actual row count, and the
   result of the proposal's sample-construction audit in the run manifest.
4. Keep the dataset files out of GitHub. Do not publish a Kaggle mirror unless
   the dataset authors or maintainer confirm the redistribution rights.

The Hugging Face page currently displays `Apache-2.0`. The paper also states
that the dataset is for research on detecting and moderating toxic and
polarizing content, rules out surveillance and profiling, and asks users to
preserve its ethical guidelines when redistributing or modifying it. The
license and those responsible-use conditions must be considered together.

The proposal snapshot records 28,448 rows, while the paper and dataset card
report 28,477 texts. Do not silently coerce one count to the other. Reconcile
the selected dataset revision and document the observed count before training.

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

## Outputs

Do not copy raw text into GitHub or attach it to a public notebook output. Keep
training logs, predictions, metrics, and checkpoints under the Kaggle working
directory. Review derivative outputs before sharing them publicly.
