# Reproducibility record

Every run should record:

- The exact Hugging Face dataset and model revisions.
- Dataset file fingerprint, configuration, schema, row count, sample audit, and
  label-pair counts.
- Python, PyTorch, Transformers, Datasets, scikit-learn, CUDA, and GPU versions.
- The complete TOML configuration and run identifier
  (`condition/fold/seed`).
- Split, training-order, training, and bootstrap seeds.
- Optimizer update counts, elapsed time, skipped updates, and output paths.

The experiment configuration is the protocol source of truth. Any change to
label construction, grouping, split generation, model conditions, training
settings, or evaluation must be reviewed in a Pull Request and documented in
the resulting run manifest.

The planned experiment has 45 full training runs. A technical smoke run checks
data loading, one forward/backward update, prediction, and output writing; it is
not included in the reported experiment. Completed runs save OOF predictions
and logs before temporary model weights are deleted. Resume only from completed
run boundaries; a run interrupted before its outputs are committed to the
manifest is repeated from the beginning.
