<p align="center">
  <a href="https://www.uit.edu.vn/" title="Trường Đại học Công nghệ Thông tin" style="border: none;">
    <img src="https://i.imgur.com/WmMnSRt.png" alt="Trường Đại học Công nghệ Thông tin | University of Information Technology" width="300">
  </a>
</p>

<h1 align="center">CS231.P21.KHTN - Computer Vision</h1>

<p align="center">
  <img src="https://img.shields.io/badge/University-UIT-blueviolet" alt="UIT">
  <img src="https://img.shields.io/badge/Semester-2%202024--2025-green" alt="Semester">
  <img src="https://img.shields.io/badge/License-MIT-yellow" alt="License">
</p>

---

## 📖 Table of Contents
- [Introduction](#-introduction)
- [Team Members](#-team-members)
- [Course Information](#-course-information)
- [Final Project](#-final-project-animals-classification)
- [Resources](#-resources)

---

## 🌟 Introduction
Welcome to the repository for **CS231.P21.KHTN - Computer Vision**, a course offered at the University of Information Technology (UIT), VNU-HCM. This course explores fundamental and advanced topics in computer vision, including image processing, feature detection, and deep learning techniques. Our team’s final project focuses on **Animals Classification**, leveraging machine learning to identify animal species from images.

---

## 👥 Team Members
| **Student ID** | **Member**          | **Email**                    |
|----------------|---------------------|------------------------------|
| 23520945       | Nguyen Van Minh     | 23520945@gm.uit.edu.vn       |
| 23521408       | Phan Nhat Tan       | 23521408@gm.uit.edu.vn       |

---

## 📚 Course Information
- **University**: University of Information Technology - VNUHCM UIT
- **Faculty**: Computer Science
- **Semester**: 2
- **Year**: 2024 - 2025
- **Teacher**: TS. Mai Tien Dung
- **Course Length**: 15 weeks
- **Final Project**: Animals Classification

---

## 💻 Final Project: Animals Classification
### Overview
This project develops a machine learning model to classify animal species from images. We use the [Animal Image Dataset - 90 Different Animals](https://www.kaggle.com/datasets/iamsouravbanerjee/animal-image-dataset-90-different-animals/data) from Kaggle, containing 5,400 images across 90 species, to train and evaluate our model.
### Technologies
- **Python**: Core programming language
- **TensorFlow**: Deep learning frameworks
- **OpenCV**: Image processing
- **Jupyter Notebook**: For experimentation and visualization

### Repository Structure
- `./models/`: Trained models and weights
- `./notebooks/`: Jupyter notebooks for analysis
- `./src/`: Source code for the project
- `./git/`: Source to commit git
- `./cv-fe/`: source of frontend 
### Example Code
```python

base_model = EfficientNetB3(weights='imagenet', include_top=False, input_shape=(224, 224, 3))
for layer in base_model.layers[-50:]:
    layer.trainable = True

model = Sequential([
    base_model,
    GlobalAveragePooling2D(),
    Dense(512, activation='relu'),
    Dropout(0.5),
    Dense(len(animal_names), activation='softmax')
])

model.compile(optimizer='adam', loss='sparse_categorical_crossentropy')

model.load_weights("../models/my_model_weights.h5")

model.summary()

y_pred = np.argmax(model.predict(X_test), axis=-1)
print(classification_report(y_test, y_pred, target_names=label_encoder.classes_))

fig, axes = plt.subplots(2, 5, figsize=(20, 8))
axes = axes.flatten()
for i, ax in enumerate(axes):
    ax.imshow(X_test[i])
    ax.axis('off')
    ax.set_title(f'Actual: {label_encoder.inverse_transform([y_test[i]])[0]}\nPredicted: {label_encoder.inverse_transform([y_pred[i]])[0]}')
plt.tight_layout()
plt.show()

```

## 📚 Resources
- [Animal Image Dataset - 90 Different Animals](https://www.kaggle.com/datasets/iamsouravbanerjee/animal-image-dataset-90-different-animals/data)
- [EfficientNet Paper](https://arxiv.org/abs/1905.11946)
- [TensorFlow Documentation](https://www.tensorflow.org/api_docs)
- [OpenCV Documentation](https://docs.opencv.org/)
- [Computer Vision Course Materials](https://site.uit.edu.vn)
