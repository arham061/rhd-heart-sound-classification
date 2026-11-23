# Reproducing my thesis experiments

This is the Colab notebook I used during my bachelor's thesis. I have kept the experimental code here, including the issues listed below. I have not rerun the training or rebuilt the environment for this repository.

## Environment and data

My notebook expects Google Colab and data folders under `/content/drive/MyDrive/`. Update those paths and supply the corresponding labeled audio data before running it. I have not included the dataset or trained weights.

I used Hugging Face Datasets, Transformers, Accelerate, Evaluate, PyTorch, Librosa, SciPy, NumPy, Matplotlib, SoundFile, IPython, and Gradio. The installation cells do not pin dependency versions, so they may need updating for current releases. The training configuration enables mixed precision and requires suitable GPU support.

## Known issues in my notebook

- My `plot_wave(audio, s, label)` function reads global `y` rather than its `audio` argument. Some plots intended to show filtered or normalized audio may therefore show the unprocessed signal.
- One plotting cell passes 400 Hz while other preprocessing cells use 4,000 Hz.
- One export path says `Highpass`, while the preprocessing loop configures a low-pass filter.
- My normalization code divides by standard deviation without checking for silent audio.
- An early Gradio experiment calls `.shuffle()` on a Python list and cannot run as written.
- The paths refer to my Google Drive folders. This repository does not include dataset creation or MATLAB augmentation scripts.
- My training configuration sets `push_to_hub=True`, which uploads checkpoints to Hugging Face. Disable it if you want to keep training local.

## Evaluation

I split the data after loading the combined original and augmented recordings. That does not explicitly prevent related recordings from appearing in both training and evaluation data.

For a new evaluation, I would group recordings by their original source and by patient where possible, split before augmentation, and keep a separate untouched test set. I also used the evaluation partition to select the best checkpoint, so the reported accuracy is not an independent test result.

## Preparing the notebook for GitHub

I removed the embedded Hugging Face token, saved outputs, execution counters, and user metadata. The experimental code otherwise remains as it was. I have also revoked the old access tokens.
