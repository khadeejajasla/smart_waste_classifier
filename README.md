# ♻️ Smart Waste Classifier

An image recognition system that identifies waste into 9 categories from a photo and gives a simple tip on how to dispose of it.

🔗 **Live Demo:** [Click here to open the website](https://khadeejajasla-waste-classifier.static.hf.space)

---

## 📌 Objective

To build a deep learning model that classifies waste images into material types, and to make it available as a public website anyone can use.

---

## 📊 Dataset

- **Source:** RealWaste image classification dataset (Kaggle)
- **Size:** about 4,750 real photos taken in a landfill environment
- **Categories (9):** Cardboard, Food Organics, Glass, Metal, Miscellaneous Trash, Paper, Plastic, Textile Trash, Vegetation
- **Split:** 80% training, 20% validation

---

## 🧠 Approach

- Resized all images to 224 × 224 and scaled pixel values
- Used **transfer learning** with **MobileNetV2** (pretrained on ImageNet), with a new classification head on top
- Trained the new layers first, then **fine-tuned the last 20 layers** with a low learning rate
- Evaluated with a confusion matrix and a per-category classification report

---

## 📈 Results

| Stage | Training Accuracy | Validation Accuracy |
|---|---|---|
| Transfer learning (frozen base) | ~95% | ~84% |
| After fine-tuning | ~94% | ~85% |

---

## 💡 Key Insights

- Vegetation was the easiest category to recognize, because of its distinct color and texture
- Plastic was the hardest. It was most often confused with Metal and Glass, likely because of shiny and transparent surfaces
- Cardboard and Paper were sometimes mixed up because of similar texture
- Textile Trash performed well even though it was the smallest category

---

## 🌐 Deployment

The trained model was converted to TensorFlow.js and deployed as a public website on Hugging Face Spaces. The model runs directly in the browser, so no server is needed. Users upload a photo and get the predicted category, a confidence score and a disposal tip.

---

## ⚙️ Tech Stack

Python, TensorFlow / Keras, MobileNetV2, NumPy, Matplotlib, Seaborn, scikit-learn, TensorFlow.js, HTML, CSS, JavaScript, Hugging Face Spaces
