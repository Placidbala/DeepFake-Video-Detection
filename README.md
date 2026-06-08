# Deffo — DeepFake Detection for Digital Media

A production-level deepfake video detection system using **Xception CNN + Bidirectional LSTM** architecture, achieving **83.93% ROC-AUC** and **100% fake recall** on the Google DeepFakeDetection dataset.

---

## Results

| Metric | Score |
|--------|-------|
| ROC-AUC | 83.93% |
| Fake Recall | 100% |
| Dataset | Google DFD (Kaggle) |
| Loss Function | Focal Loss (γ = 2.0) |

---

## Architecture

```
Video → 50 Uniform Frames → MTCNN Face Crop
      → Xception CNN (ImageNet Pretrained, 2048-d features)
      → Bidirectional LSTM (128 units)
      → Fake / Real + Confidence Score
```

---

## Tech Stack

| Component | Technology |
|-----------|------------|
| Deep Learning Framework | TensorFlow / Keras |
| CNN Backbone | Xception (ImageNet pretrained) |
| Sequence Model | Bidirectional LSTM |
| Face Detection | MTCNN |
| Augmentation | Albumentations |
| Deployment | Flask REST API |

---

## Model Details

- **Backbone:** Xception pretrained on ImageNet (transfer learning)
- **Sequence Model:** Bidirectional LSTM (128 units) for temporal modeling
- **Loss:** Focal Loss (γ=2.0) to handle class imbalance
- **Frames:** 50 uniform samples per video
- **Face Detection:** MTCNN for precise facial crop per frame
- **Dataset:** Google DeepFakeDetection (DFD) — Kaggle

---

## Project Structure

```
deffo/
├── app.py                 # Flask server & REST API
├── deepfake_train.py      # End-to-end training pipeline
├── requirements.txt       # Dependencies
├── templates/
│   └── index.html         # Frontend UI
└── README.md
```

---

## Setup

### 1. Clone repo
```bash
git clone https://github.com/anantbarjatya/deepfake-detector--DEFFO.git
cd deepfake-detector--DEFFO
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Add dataset
```
dataset/
  real/   ← original videos
  fake/   ← deepfake videos
```

### 4. Train model
```bash
python3 deepfake_train.py
```

### 5. Run server
```bash
python3 app.py
```

### 6. Open browser
```
http://127.0.0.1:5001
```

---

## Author

**Anant Barjatya**
[GitHub](https://github.com/anantbarjatya) · [LinkedIn](https://www.linkedin.com/in/anant-barjatya-1340b627b)
