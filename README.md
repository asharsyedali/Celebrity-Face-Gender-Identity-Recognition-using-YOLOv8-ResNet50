

# 🎭 Celebrity Face, Gender & Identity Recognition using YOLOv8 + ResNet50

## 🔍 Project Overview

This project presents a robust two-stage deep learning pipeline that performs:

* 🧠 **Face Detection**
* 🚻 **Gender Classification**
* 👤 **Celebrity Identity Recognition**

We leverage **YOLOv8** for real-time face and gender detection, followed by a **ResNet50** model (via transfer learning) for classifying faces into 16 celebrity identity classes. The models are trained using robust data augmentation, custom annotations, and stratified validation to handle real-world complexity in pose, lighting, and occlusion.

---

## 📁 Dataset Summary

### 1. Roboflow Gender Dataset

* Initial dataset: 880 images
* Manually annotated: 320 images
* Auto-labeled using Roboflow tools

### 2. Celebrity Identity Dataset

* Provided by instructor (15 known celebrities + 1 unknown class)
* Total post-augmentation images: **2000+**

📊 Final dataset split:

* Training: 1800+ images
* Validation: 200+ images
* Testing: 100+ images

---

## 🔧 Data Augmentation

### YOLOv8 Detection & Gender Classification

* Performed in Roboflow
* Augmentations:

  * Horizontal/vertical flips
  * Random & fixed-angle rotations
  * Cropping and zoom
  * Shearing
  * Grayscale (15% of images)
  * Color jitter, blur, noise

### ResNet50 Identity Classification

* Implemented with **Albumentations**
* Augmentations:

  * Resized crop to 224×224
  * CLAHE and posterization
  * Brightness/contrast/color shifts
  * Coarse dropout
  * Gaussian blur and noise

---

## ⚙️ Model Configuration

| Configuration | YOLOv8 (Detection + Gender) | ResNet50 (Identity Classification) |
| ------------- | --------------------------- | ---------------------------------- |
| Epochs        | 40                          | 35 + 25 (fine-tuning)              |
| Batch Size    | 8                           | 16                                 |
| Optimizer     | AdamW                       | Adam                               |
| Loss Function | -                           | CrossEntropyLoss (Label Smoothing) |
| Scheduler     | -                           | ReduceLROnPlateau                  |
| Early Stop    | Patience = 8                | Patience = 6                       |
| Image Size    | 640×640                     | 224×224                            |

---

## 🧪 Inference Pipeline

1. Input image processed through **YOLOv8**
2. Detected faces cropped and resized
3. **ResNet50** predicts the celebrity identity
4. Final output:

   * 🟩 Green box for **Female**
   * 🟦 Blue box for **Male**
   * 🏷️ Predicted **Celebrity Name**

---

## 📊 Results Overview

### YOLOv8 Performance

* `mAP@0.5`: **> 0.96**
* `Precision`: \~**0.95**
* `Recall`: \~**0.93**

### ResNet50 Performance

* `Top-1 Accuracy`: **> 94%**
* `F1 Score`: **> 0.92**
* Clear confusion matrix separation between identities

📌 Qualitative results confirm excellent generalization in challenging test scenarios.

---

## 🧠 Key Learnings

* High-quality annotations and diverse augmentation are crucial for generalization.
* Batch visualizations and validation curves helped identify overfitting early.
* This modular design can easily be extended to tasks like age or emotion detection.

---

## 👨‍💻 Author

**Syed Mohammad Ali Ashar**
🎓 BS Artificial Intelligence
🏫 University of Management and Technology (UMT), Lahore
✉️ [asharshah986@gmail.com](mailto:asharshah986@gmail.com)

---



