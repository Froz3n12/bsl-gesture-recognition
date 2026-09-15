# Dataset setup

The image dataset is not redistributed in this repository.

The notebook expects a directory containing one subdirectory per BSL class, for example:

```text
data_root/
├── A/
│   ├── image_001.jpg
│   └── ...
├── B/
│   ├── image_001.jpg
│   └── ...
└── ...
```

The original coursework dataset contained **11 classes and 11,000 images**, with **1,000 images per class**.

When running in Google Colab, update these notebook variables to match your storage location:

```python
ZIP_PATH = Path('/content/drive/MyDrive/DNN/2_hand.zip')
EXTRACT_PATH = Path('/content/2_hand')
DATA_DIR = EXTRACT_PATH / '2_hand'
```

If the dataset is already extracted, set `DATA_DIR` directly and skip the archive extraction step.
