# British Sign Language Gesture Recognition

**Computer vision · Transfer learning · Model evaluation**

An image classification project comparing a CNN trained from scratch with two MobileNetV2 approaches to recognise **11 static British Sign Language alphabet gestures**.

The fine-tuned model achieved approximately **94% validation accuracy**, compared with approximately 75% for the baseline CNN.

[Explore the notebook](notebooks/bsl_gesture_recognition.ipynb) · [Read the report summary](docs/project_report_summary.md) · [Dataset setup](data/README.md)

## The problem

Recognising hand gestures requires a model to distinguish small differences in finger position and orientation. This project investigates whether pretrained visual features improve performance on a balanced but limited BSL image dataset.

## Results

| Model | Training approach | Reported validation accuracy |
| --- | --- | ---: |
| Baseline CNN | Trained from scratch | ~75% |
| MobileNetV2 | Frozen ImageNet backbone | ~89% |
| MobileNetV2 | Fine-tuned upper layers | **~94%** |

Fine-tuning improved reported validation accuracy by approximately **19 percentage points** over the baseline. The baseline showed clear overfitting, while the fine-tuned model had the strongest validation performance.

These are approximate results from the coursework experiment, measured on its validation split. They do not represent performance on a separate held-out test set or live webcam input.

## What I built

- A notebook workflow covering image loading, preprocessing, training and evaluation.
- A baseline CNN and two transfer learning experiments using TensorFlow and Keras.
- Learning-curve comparisons to examine convergence and overfitting.
- A confusion matrix and classification report for class-level error analysis.

## Dataset and method

| Component | Configuration |
| --- | --- |
| Dataset | 11,000 images; 1,000 per class |
| Task | Single-label classification across 11 static alphabet gestures |
| Input | 224 × 224 RGB images |
| Split | 80% training, 20% validation |
| Baseline preprocessing | Pixel values scaled to `[0, 1]` |
| Transfer learning preprocessing | MobileNetV2 preprocessing |
| Fine-tuning | Upper backbone layers trained at a lower learning rate |

The dataset is not distributed in this repository. Follow the [dataset instructions](data/README.md) to supply your own copy. Augmentation must preserve sign meaning; transformations such as horizontal flipping can change a gesture.

## Run the notebook

Clone the repository and create an environment:

```bash
git clone https://github.com/Froz3n12/bsl-gesture-recognition.git
cd bsl-gesture-recognition
python -m venv .venv
```

Activate it on Linux or macOS:

```bash
source .venv/bin/activate
```

Or on Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

Install dependencies and launch Jupyter:

```bash
python -m pip install -r requirements.txt
jupyter notebook notebooks/bsl_gesture_recognition.ipynb
```

Set `ZIP_PATH` or `DATA_DIR` in the notebook to your dataset location before running the cells in order. The notebook can also be used in Google Colab with the dataset paths adjusted.

## Repository guide

| Path | Contents |
| --- | --- |
| [notebooks/bsl_gesture_recognition.ipynb](notebooks/bsl_gesture_recognition.ipynb) | Training and evaluation workflow |
| [docs/project_report_summary.md](docs/project_report_summary.md) | Methodology, findings and error analysis |
| [data/README.md](data/README.md) | Expected dataset layout |
| [requirements.txt](requirements.txt) | Python dependencies |

**Tools:** Python, TensorFlow, Keras, MobileNetV2, NumPy, Matplotlib, scikit-learn, Jupyter and Google Colab.

## Scope and next steps

This is a static image classifier for a subset of the BSL alphabet. It does not translate full BSL conversations or recognise movement over time.

Further work would add a dedicated held-out test set, more varied lighting and viewpoints, webcam evaluation and temporal models for dynamic gestures. Dependencies specify minimum versions rather than a fully locked environment, so fresh training runs may produce different results.

## Author

**Munib Sarfraz**  
First Class Computer Science with Artificial Intelligence graduate, Birmingham City University.

[LinkedIn](https://www.linkedin.com/in/munib-sarfraz/) · [GitHub](https://github.com/Froz3n12)
