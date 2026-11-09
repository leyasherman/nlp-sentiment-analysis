# Cross-Domain Sentiment and Emotion Analysis

UCL NLP group coursework investigating whether a model trained on Reddit emotions can identify fine-grained emotions in Twitter customer support messages. The business question is whether an emotion classifier transfers reliably enough to support customer service analytics.

## Contribution

Leya Sherman contributed data preprocessing, BERT fine-tuning and model training, as documented in the supplied project notebook. Baseline modelling, evaluation, analysis and write-up were collaborative group work. This repository preserves the prepared notebooks without claiming sole authorship.

## Technologies and methodology

Python, pandas, NumPy, scikit-learn, PyTorch, Hugging Face datasets/transformers, matplotlib and seaborn. The work compares a TF-IDF/logistic regression baseline with fine-tuned `bert-base-uncased`, uses GoEmotions train/validation/test splits, converts labels for single-label classification and evaluates transfer to customer support tweets. It includes annotation agreement, per-class metrics, confusion analysis and broader sentiment groupings.

## Recorded results

The narrative in [the main notebook](emotion_detection_cross_domain.ipynb) reports:

| Evaluation | Macro F1 |
|---|---|
| Logistic regression, GoEmotions | 0.305 |
| BERT, GoEmotions | 0.430 |
| BERT, annotated Twitter sample | 0.002 |

These are retained coursework findings from notebook text; outputs, model weights and evaluation datasets are absent, and publication did not independently reproduce the numbers. The very low transfer result requires checking label mapping and evaluation consistency before drawing conclusions about model capability. The central practical finding is that in-domain performance alone does not establish suitability for customer support automation.

## Start here

- [Main project notebook](emotion_detection_cross_domain.ipynb): contribution statement, experiment and interpretation.
- [`project_part2.ipynb`](project_part2.ipynb), [`project_part3.ipynb`](project_part3.ipynb) and [`project_part_f.ipynb`](project_part_f.ipynb): additional supplied development versions. These overlap; they are not four independent experiments or a required sequential pipeline.

## How to run

Kaggle or Colab with GPU access is useful for BERT training. For a local environment, install the imported packages:

```bash
python -m venv .venv
# Activate the environment, then:
python -m pip install jupyterlab pandas numpy scikit-learn torch transformers datasets accelerate matplotlib seaborn openpyxl kagglehub
python -m jupyterlab
```

This is a source-level dependency list, not a tested version lock. Review notebook installation cells and training APIs for compatibility with your chosen versions. The main notebook loads `go_emotions` (`simplified`) through Hugging Face and expects the Customer Support on Twitter CSV plus an annotated Excel file at Kaggle-specific paths. Obtain authorised copies from the original providers and update those paths. The annotated evaluation file is not supplied, so the cross-domain metrics cannot be reproduced from public data alone. Keep Kaggle/Hugging Face credentials in platform secrets or local configuration outside Git.

## Limitations

The single-label conversion discards co-occurring emotions. Class imbalance, a small annotated sample, historical support language and domain shift limit transfer. The notebook contains exploratory deployment recommendations; they are proposals, not validated capabilities. Model performance and label alignment require verification before any operational use. No source text, customer identifiers, model weights or restricted coursework briefs are redistributed. Data licences and platform terms apply to any separately obtained datasets.
