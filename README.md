# Land Cover Classification with Machine Learning

A comprehensive machine learning pipeline for satellite image classification using Random Forest and K-Nearest Neighbors algorithms. This project analyzes land cover types from satellite imagery using the DeepGlobe dataset.

## 🎯 Project Overview

This notebook implements a pixel-level land cover classification system that identifies seven different land types from satellite imagery:

- **Urban** - Cities and built-up areas
- **Agriculture** - Farmland and cultivated areas
- **Rangeland** - Grasslands and shrublands
- **Forest** - Wooded areas
- **Water** - Rivers, lakes, and oceans
- **Barren** - Desert and bare land
- **Unknown** - Unclassified regions

## 🚀 Features

- **Parallel Processing**: Efficient image processing using joblib parallelization
- **Feature Engineering**: 
  - RGB color features
  - Spectral indices (NDVI, brightness)
  - Texture features (local standard deviation and range)
- **Model Comparison**: Side-by-side evaluation of KNN and Random Forest classifiers
- **Comprehensive Visualization**: 
  - Input-output comparison dashboard
  - Confidence maps
  - Error analysis
  - Feature importance plots
- **Scalable Design**: Configurable sampling rate and image size for different computational resources

## 📋 Requirements

```
numpy
pandas
opencv-python (cv2)
scikit-learn
matplotlib
seaborn
joblib
```

## 💻 Installation

1. Clone this repository:
```bash
git clone https://github.com/yourusername/land-cover-classification.git
cd land-cover-classification
```

2. Install required packages:
```bash
pip install numpy pandas opencv-python scikit-learn matplotlib seaborn joblib
```

3. Download the DeepGlobe Land Cover Classification dataset from [Kaggle](https://www.kaggle.com/datasets/balraj98/deepglobe-land-cover-classification-dataset)

## 📊 Dataset

This project uses the **DeepGlobe Land Cover Classification Dataset**, which contains:
- High-resolution satellite images (2448x2448 pixels)
- Pixel-level segmentation masks with 7 land cover classes
- RGB color-coded ground truth labels

**Dataset Structure:**
```
/kaggle/input/
├── *_sat.jpg    # Satellite images
└── *_mask.png   # Corresponding segmentation masks
```

## 🔧 Usage

### Basic Usage

1. Open the notebook in Jupyter or Google Colab
2. Update the `Config.BASE_SEARCH_PATH` to point to your dataset location
3. Run all cells sequentially

### Configuration Options

Modify the `Config` class to customize the pipeline:

```python
class Config:
    IMG_SIZE = (512, 512)          # Target image size
    SAMPLE_RATE = 0.10             # Percentage of pixels to sample per image
    MAX_IMAGES = 100               # Maximum number of images to process
    USE_TEXTURE_FEATURES = True    # Include texture features
    USE_SPECTRAL_INDICES = True    # Include spectral indices
    TEST_SIZE = 0.2                # Train-test split ratio
```

### Training Models

The notebook trains two classifiers:

**K-Nearest Neighbors (KNN)**
```python
knn = KNeighborsClassifier(n_neighbors=5, weights='distance', n_jobs=-1)
knn.fit(X_train_scaled, y_train)
```

**Random Forest**
```python
rf = RandomForestClassifier(
    n_estimators=100,
    max_depth=20,
    min_samples_split=5,
    random_state=42,
    n_jobs=-1
)
rf.fit(X_train_scaled, y_train)
```

## 📈 Results

Typical performance metrics (may vary based on configuration):

| Model | Accuracy | F1-Score |
|-------|----------|----------|
| KNN | ~82-85% | ~0.81-0.84 |
| Random Forest | **~85-88%** | **~0.84-0.87** |

**Key Findings:**
- Random Forest generally outperforms KNN by 3-5%
- Texture features significantly improve classification accuracy
- Model struggles most with Rangeland and Agriculture (similar spectral signatures)

## 🖼️ Visualizations

The notebook provides several visualization tools:

1. **Comprehensive Dashboard**: Side-by-side comparison of input, ground truth, predictions, and errors
2. **Confusion Matrices**: Per-class performance analysis
3. **Confidence Maps**: Visual representation of model uncertainty
4. **Feature Importance**: Analysis of which features contribute most to predictions

## 🗂️ Project Structure

```
land-cover-classification/
├── ml.ipynb                 # Main notebook
├── README.md               # This file
└── outputs/                # Generated outputs (created automatically)
    ├── rf_model.pkl        # Trained Random Forest model (optional)
    ├── knn_model.pkl       # Trained KNN model (optional)
    └── scaler.pkl          # Feature scaler (optional)
```

## 🛠️ Pushing to GitHub

1. Initialize git repository:
```bash
git init
```

2. Add your files:
```bash
git add ml.ipynb README.md
git commit -m "Initial commit: Land cover classification project"
```

3. Create a new repository on GitHub, then:
```bash
git remote add origin https://github.com/yourusername/land-cover-classification.git
git branch -M main
git push -u origin main
```

## 🎓 Technical Details

### Feature Extraction Pipeline

1. **RGB Features**: Raw pixel values (3 channels)
2. **Spectral Indices**: 
   - NDVI (proxy): (G-R)/(G+R)
   - Brightness: (R+G+B)/3
3. **Texture Features**:
   - Local standard deviation
   - Local range (max-min in neighborhood)

### Data Processing

- Images resized to 512x512 for consistent processing
- 10% pixel sampling per image to reduce computational load
- RobustScaler used for feature normalization (handles outliers better)
- Stratified train-test split to maintain class balance

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📝 License

This project is open source and available under the [MIT License](LICENSE).

## 🙏 Acknowledgments

- DeepGlobe Challenge organizers for the dataset
- Kaggle community for dataset hosting
- scikit-learn and OpenCV communities for excellent libraries

## 📧 Contact

For questions or feedback, please open an issue on GitHub.

---

**Note**: This project is designed for educational purposes and demonstrates practical machine learning techniques for remote sensing applications.
