# AI-Based Rheumatic Heart Disease Detection and Classification

Bachelor's thesis / final-year team project at the Ghulam Ishaq Khan Institute of Engineering Sciences and Technology (GIKI), Pakistan.

The project explores heart-sound classification from phonocardiogram (PCG) recordings using an LSTM baseline and a fine-tuned DistilHuBERT audio transformer. It investigates preprocessing and data augmentation, and includes a Gradio audio-classification prototype.

## Project materials

- [Final thesis report](https://drive.google.com/file/d/1BrRuZqyo3YkyOsw_8qskbOPPVKCMnPXp/view)
- [Project paper](https://drive.google.com/file/d/1rnty9tLLq5t2Q_ZO48VMdIaTzXbQmiQb/view) — publication status not established
- [Demo video](https://drive.google.com/file/d/1nCyEOSsR4w2iWqOVlQEANKVqJ0ka9cX9/view)
- [Project poster](https://drive.google.com/file/d/1_kmUAhUTQj2nlNTFeBOLc1lgz7v97g6Z/view)
- [Original Colab notebook](https://colab.research.google.com/drive/13v7VdgBpLNQ2y3cI8qOpEpgRWamKY-Od)

## Approach

1. Explore recorded heart sounds and class labels.
2. Investigate filtering, normalization, and acoustic features such as MFCCs, spectral centroids, and zero-crossing rate.
3. Expand the training material through augmentation. The report describes time shifts, time stretching, pitch shifts, and volume adjustments using MATLAB.
4. Compare an LSTM approach with fine-tuning of `ntu-spml/distilhubert` using Hugging Face Transformers.
5. Demonstrate audio classification through Gradio.

The recovered notebook includes filtering experiments, normalization, audio export, DistilHuBERT fine-tuning, and a Gradio interface. The LSTM implementation and MATLAB augmentation source were not present in the supplied folder or recovered notebook.

## Reported results and evaluation limits

| Approach | Accuracy reported in the thesis |
| --- | ---: |
| LSTM | 66% |
| Fine-tuned DistilHuBERT | 95% |

These are historical results reported by the team, not independently reproduced results. The report describes expanding approximately 400 recordings to around 1,300 through augmentation.

The recovered notebook loads a folder named `Combined Augmented + Original` and then randomly splits recordings into 90% training and 10% evaluation data (`seed=42`). It does not show grouping original recordings with their augmented versions before splitting, or grouping by patient. Related recordings may therefore occur in both partitions. The evaluation partition is also used to select the best checkpoint. A separate untouched test evaluation is not demonstrated in this notebook.

Heart-sound classification results do not establish clinical RHD diagnostic performance. This is an academic research prototype; the supplied materials do not establish clinical validation.

## Repository contents

- `thesis_original_sanitized.ipynb`: recovered historical Colab notebook, with a credential removed, outputs cleared, and execution metadata removed. Code behavior is otherwise preserved.
- `REPRODUCIBILITY.md`: requirements and known issues in the recovered notebook.

## Team and supervision

- Arham Shahzad
- Faiza Qadir
- Muhammad Hamza Azeem

Advisor: Dr. Shahab Uddin Ansari. Co-advisor: Dr. Khurram Jadoon.

The thesis acknowledges consultation and collaboration with Aga Khan Hospital.

### Arham's contribution

Arham primarily developed the HuBERT-based classification model, including fine-tuning and running successive experiments over several months. His work focused on iteratively testing and refining the main model. The available notebook documents part of this experimentation; a complete experiment-by-experiment record has not been recovered.

## Availability

The dataset and trained weights are not bundled here. The recovered notebook references a Hugging Face model, but its current availability has not been verified. The linked project documents remain on Google Drive and may require access permissions.

No license has been assigned; redistribution rights for team materials and third-party figures require confirmation.
