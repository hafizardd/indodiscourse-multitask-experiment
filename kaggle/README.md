# Kaggle kernel scaffold

The Kaggle kernel metadata is prepared, but the notebook has intentionally not
been created yet. The Kaggle API is not authenticated in this environment, so
no Kaggle kernel has been published.

Before uploading:

1. Add `indodiscourse_mtl.ipynb` and the experiment modules in this folder.
2. Replace `YOUR_KAGGLE_USERNAME` in `kernel-metadata.json` with the actual
   Kaggle username. The GitHub owner `hafizardd` does not imply the Kaggle
   username.
3. Pin dataset and model revisions in `config/experiment.toml`.
4. Confirm authorized access to the data and set Kaggle Internet or an approved
   input source.
5. Push from this folder with `kaggle kernels push -p kaggle/`.

The kernel is marked private until code, data access, and outputs are ready for
public release.
