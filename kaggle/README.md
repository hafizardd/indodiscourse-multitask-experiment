# Kaggle notebooks

The first stage uses three separate private kernels. See
[notebooks/README.md](notebooks/README.md) for run order, upload commands,
private output handoff, and the current validation blocker.

Each notebook folder contains its own notebook and kernel-metadata.json.
Metadata uses a Kaggle username placeholder, private visibility, internet
enabled, GPU disabled, and no dataset sources. Notebook 03 references the
private output of notebook 02. The top-level kernel-metadata.json remains
reserved for the future training notebook.

The notebooks download only the pinned canonical main JSONL into /tmp and
verify its SHA-256. No Kaggle Dataset mirror is used. Outputs are private
notebook artifacts and are not committed to this repository. Kaggle runs have
not been performed yet.
