# Satellite Image Classification with a CNN

A convolutional neural network, built with TensorFlow/Keras, that classifies satellite images into four land-cover classes: **cloudy, desert, green area and water**. The notebook covers dataset indexing, augmentation, training, evaluation (learning curves and confusion matrix) and single-image inference.

## Data

[`DataSet/`](DataSet) holds **5,631 RGB images** from a public satellite-image dataset, one folder per class:

| Class | Images |
|---|---:|
| Cloudy | 1,500 |
| Desert | 1,131 |
| Green area | 1,500 |
| Water | 1,500 |

[`image_dataset_CSV.csv`](image_dataset_CSV.csv) indexes every image path with its label. It was generated in Google Colab, so the paths point to a Google Drive folder and need rewriting to run locally.

## Model and training

```mermaid
flowchart LR
    A[Images + labels CSV] --> B[80/20 split<br/>4,504 train · 1,127 test]
    B --> C[ImageDataGenerator<br/>rescale, shear, zoom, rotation,<br/>horizontal + vertical flip]
    C --> D[CNN<br/>4 × Conv2D + MaxPool]
    D --> E[Dense 128 + Dropout 0.5]
    E --> F[Softmax · 4 classes]
```

- **Input:** 255 × 255 × 3, pixel values scaled to [0, 1]
- **Feature extractor:** Conv2D 32 → 32 → 64 → 128 filters (3 × 3, ReLU), each followed by 2 × 2 max pooling
- **Classifier:** Flatten → Dense(128, ReLU) → Dropout(0.5) → Dense(4, softmax)
- **Training:** Adam, categorical cross-entropy, batch size 32, **5 epochs**; augmentation on the training set only

![CNN architecture](findings_image/CNN%20model%20architecture.png)

## Results

The saved notebook output shows **86.25% accuracy on the 1,127-image test set** after five epochs.

| Training vs validation accuracy | Training vs validation loss | Confusion matrix |
|:---:|:---:|:---:|
| ![Accuracy](findings_image/accuracy%20for%20training%20and%20validation.png) | ![Loss](findings_image/loss%20for%20training%20and%20Validation.png) | ![Confusion matrix](findings_image/confussion%20matrix.png) |

The notebook also loads a single image from disk and prints the predicted class.

## Repository structure

```text
Satellite_Image_Classification_By_CNN/
├── Satellite_Image_Classification_With_CNN_model.ipynb   # Full pipeline
├── DataSet/{cloudy,desert,green_area,water}/             # Images
├── image_dataset_CSV.csv                                 # Path → label index
└── findings_image/                                       # Plots and architecture diagram
```

## Running the notebook

```bash
git clone https://github.com/hasansust32/Satellite_Image_Classification_By_CNN.git
cd Satellite_Image_Classification_By_CNN
python -m venv .venv && source .venv/bin/activate
pip install jupyter tensorflow pandas numpy scikit-learn matplotlib pillow
jupyter notebook Satellite_Image_Classification_With_CNN_model.ipynb
```

The repository is large (about 56 MB of images). Replace the Google Drive base path with `DataSet/` before running. Training on CPU is slow (the saved run took roughly 19 minutes per epoch on Colab); a GPU runtime is recommended.

## Limitations

- Only five epochs; the learning curves suggest the model had not converged.
- The test set doubles as the validation set during training, so the reported accuracy is not from data unseen during model selection.
- No transfer-learning baseline (e.g. a pretrained ResNet or EfficientNet) for comparison.
- No per-class precision and recall in the saved outputs.

## Future improvements

- Separate train / validation / test splits and early stopping.
- Compare against a fine-tuned pretrained backbone.
- Wrap the trained model in a small inference API that accepts an image upload or URL.

## Author

**S M Mahamudul Hasan** · [GitHub](https://github.com/hasansust32) · [Portfolio](https://www.hasansm.com/) · [LinkedIn](https://www.linkedin.com/in/sm-mahamudul-hasan/)
