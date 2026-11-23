# Recovered notebook: status and reproduction notes

This package preserves a historical research notebook. It has been inspected, but has not been executed or converted into a verified training pipeline.

## Environment and data assumptions

The notebook expects Google Colab and data folders under `/content/drive/MyDrive/`. Update the local data paths and provide the corresponding labeled audio data before use. Data and weights are not included.

The code uses Hugging Face Datasets, Transformers, Accelerate, Evaluate, PyTorch, Librosa, SciPy, NumPy, Matplotlib, SoundFile, IPython, and Gradio. Installation cells are historical and unpinned; a supported dependency set still needs to be established. Mixed-precision training is enabled and requires suitable GPU support.

## Known issues from inspection

- `plot_wave(audio, s, label)` reads global `y` rather than its `audio` argument, so displayed filtered or normalized waveforms may actually show the unprocessed signal.
- A plotting cell passes 400 Hz while other preprocessing cells use 4,000 Hz.
- An export path says `Highpass`, while the dataset preprocessing loop configures a low-pass filter.
- Normalization divides by standard deviation without guarding against silent audio.
- The early Gradio example calls `.shuffle()` on a Python list and cannot run as written.
- Data folders are tied to the author's Google Drive. The notebook does not include dataset creation or MATLAB augmentation scripts.
- Training sets `push_to_hub=True`; running it can upload model checkpoints. Review and disable this setting for local experimentation. The login cell is retained, with the embedded token removed.
- The random split occurs after loading combined augmented and original data. Reproduction should split by original recording (and patient where available) before augmentation, and retain a separate test set.

## Changes made for this archive

- Removed one hard-coded Hugging Face credential from a code comment.
- Cleared all cell outputs and execution counters.
- Removed cell execution and user metadata.
- Preserved the remaining source code, including the issues above, so the archive does not imply a newly validated implementation.

The original credential should be revoked by its owner, because removing it from this copy does not invalidate it or remove it from the source notebook.
