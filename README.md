# TALL: Deepfake Video Detection via Thumbnail Layout Learning

## 📌 Authors

* Arya Pandey
* Adhikansh Goel

## 🧠 Overview

TALL is a novel approach for detecting deepfake videos by leveraging **Thumbnail Layout Learning**. By stitching sampled video frames into a single image (thumbnail), the model efficiently captures both **spatial and temporal** patterns. The system is trained using the **Swin Transformer** and compared with a **ResNet-50** baseline.

---

## 🎯 Motivation

Deepfake technologies are advancing rapidly, creating highly realistic yet fake video content. Traditional frame-by-frame detection methods struggle to capture temporal dependencies.
TALL solves this by:

* Combining frames into a 2x2 grid thumbnail.
* Leveraging the Swin Transformer for layout-based learning.

---

## 📁 Dataset

We use a **subset of Celeb-DF v2**, a high-quality deepfake dataset:

* **126 real** videos
* **900 fake** videos
* Diversity in **lighting**, **compression**, and **identities**

---

## 🛠️ Data Pipeline

1. **Load videos** (real/fake) from Celeb-DF v2 subset
2. **Sample N frames** (uniformly spaced)
3. **Resize frames** to 224×224
4. **Construct grid** layout (e.g. 2×2)
5. **Save thumbnail image** (final size: 224×224)
6. **Assign label**: Real or Fake

📦 Tools Used:

* `OpenCV` – frame extraction
* `PIL` – image grid composition

---

## 🧪 Models

### ✅ TALL + Swin Transformer

* Uses a **grid of frames** to learn spatial-temporal features.
* Trained on 224×224 thumbnails.
* **Shifted window** mechanism allows localized attention with global context.

### 🆚 ResNet-50 Baseline

* Pretrained on ImageNet.
* Final FC layer adapted for binary classification.
* Same thumbnails used as input.
* Limitation: No explicit modeling of inter-frame relationships.

---

## 📊 Results

| Model     | Accuracy | AUC    |
| --------- | -------- | ------ |
| Swin      | 0.8780   | 0.7418 |
| ResNet-50 | 0.8683   | 0.6942 |

✅ Swin outperforms ResNet50, especially in capturing spatial inconsistencies typical in deepfakes.

---

## ⚙️ Tech Stack

* Python
* PyTorch
* OpenCV
* PIL
* Swin Transformer
* ResNet-50

---

## 🚀 Future Work

* Extend with **larger models** and **motion cues**
* Real-world deployment for scalable video moderation
* Explore **real-time detection**

---

## 📝 License

MIT License (or specify if different)

---

## 🙏 Acknowledgments

* [Celeb-DF v2 Dataset](https://github.com/yuezunli/Celeb-DF)
* Authors and contributors of Swin Transformer and ResNet

---
