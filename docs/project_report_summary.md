# Project Report Summary

## Automatic Recognition of British Sign Language Alphabet Gestures Using Convolutional Neural Networks

This project investigates convolutional neural networks and transfer learning for recognising static British Sign Language (BSL) alphabet gestures from images.

## Objective

The task is formulated as a single-label, multi-class image classification problem using 11 selected static alphabet gestures. The aim is to compare a CNN trained from scratch against MobileNetV2 transfer-learning approaches and determine which provides the strongest generalisation.

## Dataset and preprocessing

The experiment used a balanced image dataset with 11 classes and 11,000 images in total. Images were resized to 224 x 224 pixels. The baseline CNN used standard pixel rescaling, while the MobileNetV2 models used the preprocessing function associated with the pretrained ImageNet model.

Aggressive augmentation was avoided because transformations such as horizontal flipping can change the semantic meaning of hand gestures.

## Models

### Baseline CNN

A CNN trained from scratch using convolution, max-pooling, dropout, flattening and dense layers. It provided a reference point for comparison but showed substantial overfitting.

### Frozen MobileNetV2

MobileNetV2 pretrained on ImageNet was used as a frozen feature extractor. Only the classification head was trained, reducing the number of trainable parameters and improving generalisation.

### Fine-tuned MobileNetV2

The upper portion of the MobileNetV2 backbone was unfrozen and trained with a reduced learning rate. This allowed pretrained visual features to adapt more closely to the BSL gesture domain.

## Reported validation results

| Model | Validation accuracy | Observation |
| --- | ---: | --- |
| Baseline CNN | ~75% | Clear overfitting and weaker generalisation |
| Frozen MobileNetV2 | ~89% | Strong improvement from transfer learning |
| Fine-tuned MobileNetV2 | ~94% | Best performance and most stable convergence |

The fine-tuned MobileNetV2 model was selected as the strongest approach.

## Error analysis

The remaining errors were concentrated around visually similar hand gestures, where classes differ by small changes in finger position or orientation. This reflects a known difficulty of static sign recognition, where temporal information and additional viewpoints are unavailable.

## Limitations

- Only a subset of static BSL alphabet signs was considered.
- Dynamic gestures requiring movement were outside the scope of the image-based classifier.
- Single-view images limit robustness to changes in viewpoint and orientation.
- The cleaned notebook reproduces the training-validation workflow; a fully reproducible dedicated held-out test split would strengthen future versions of the project.

## Future work

Potential extensions include:

- recognising the complete BSL alphabet;
- collecting more varied backgrounds, viewpoints and lighting conditions;
- real-time webcam inference;
- temporal modelling for dynamic gestures;
- attention-based or lightweight transformer architectures;
- deployment to an accessibility-focused web or mobile application.
