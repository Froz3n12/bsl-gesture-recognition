# British Sign Language Gesture Recognition

Deep-learning image classification project for recognising **11 static British Sign Language (BSL) alphabet gestures** from hand images. The project compares a convolutional neural network trained from scratch with two MobileNetV2 transfer-learning strategies.

## Project overview

The aim of the project was to investigate how transfer learning affects recognition accuracy when working with a balanced but relatively limited BSL image dataset.

Three models were compared:

| Model | Approach | Validation accuracy reported |
| --- | --- | ---: |
| Baseline CNN | Trained from scratch | ~75% |
| MobileNetV2 | Frozen pretrained backbone | ~89% |
| MobileNetV2 | Fine-tuned upper layers | ~94% |

The fine-tuned MobileNetV2 model produced the strongest validation performance and the most stable learning behaviour. The baseline CNN showed clear overfitting, highlighting the value of pretrained visual features for this task.

## Dataset

The coursework experiment used a balanced dataset containing:

- **11,000 images**
- **11 static BSL alphabet classes**
- **1,000 images per class**
- Images resized to **224 × 224 RGB**
- 80/20 training-validation split in the supplied notebook workflow

The dataset itself is **not included** in this repository. See [`data/README.md`](data/README.md) for the expected directory structure.

## Methodology

1. Load and preprocess the gesture image dataset.
2. Train a baseline CNN using pixel values normalised to `[0, 1]`.
3. Train MobileNetV2 with the ImageNet backbone frozen.
4. Unfreeze the upper MobileNetV2 layers and fine-tune using a lower learning rate.
5. Compare validation learning curves and class-level predictions.
6. Generate a confusion matrix and classification report for the selected model.

## Repository structure

```text
bsl-gesture-recognition/
├── README.md
├── requirements.txt
├── .gitignore
├── data/
│   └── README.md
├── docs/
│   └── project_report.pdf
└── notebooks/
    └── bsl_gesture_recognition.ipynb
```

## Technologies

- Python
- TensorFlow / Keras
- MobileNetV2
- NumPy
- Matplotlib
- scikit-learn
- Google Colab

## Getting started

Clone the repository and install the dependencies:

```bash
git clone https://github.com/Froz3n12/bsl-gesture-recognition.git
cd bsl-gesture-recognition
python -m venv .venv
source .venv/bin/activate   # Linux/macOS
pip install -r requirements.txt
```

On Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

Then open:

```text
notebooks/bsl_gesture_recognition.ipynb
```

Update `ZIP_PATH` or `DATA_DIR` in the notebook to point to your copy of the dataset before running the training cells.

## Notebook cleanup

The original coursework notebook has been reorganised into a clearer, self-contained workflow while preserving the same model architectures and training strategy. The final confusion-matrix section has also been corrected so it computes predictions directly from the validation generator instead of referencing undefined variables.

## Report

The full coursework report is available at [`docs/project_report.pdf`](docs/project_report.pdf). The public repository copy has the student ID removed for privacy; the technical content is unchanged.

## Limitations and future work

The project focuses on static signs and a subset of the BSL alphabet. Future work could include the full alphabet, more varied recording conditions, a dedicated reproducible held-out test split, real-time webcam inference, and temporal models for dynamic gestures.

## Author

**Munib Sarfraz**  
Computer Science with Artificial Intelligence
