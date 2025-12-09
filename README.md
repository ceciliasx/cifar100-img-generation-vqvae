# 🖼️ AI Image Generation with VQ-VAE

Dataset: **Telephone images**
Source: https://github.com/cyizhuo/CIFAR-100-dataset / https://www.cs.toronto.edu/~kriz/cifar.html

### **Model Architecture**
- **Encoder:** CNN compressing image into latent representation  
- **Vector Quantizer:** Discrete embedding space (core VQ-VAE component)  
- **Decoder:** Deconvolution layers reconstructing image  

Losses include:
- Reconstruction Loss  
- Quantization Loss  

### 📉 Training Analysis
Training loss ↓  
Validation loss ↑ → **overfitting**  

Generator learns low-frequency structure but struggles with detail.

### 🎨 Generated Images
- 500 synthetic images produced  
- Saved in `/generate/`

### 🔍 Comparison (Original vs Reconstructed)
Reconstructed images:
- Capture overall structure  
- Lack detail  
- Appear blurry → typical VAE limitations  

Possible improvements:
- Larger latent space  
- More training  
- Regularization tweaks  

---

# 3. 🆚 Real vs Fake Image Classification

A new dataset was constructed:

- Class 0 → **Original images**  
- Class 1 → **Generated (fake) images**  
Saved in `/dataset_classification/`.

### **CNN Architecture**
- 3 convolutional layers  
- MaxPooling layers  
- Dense + Dropout (0.3)  
- Sigmoid output  

Loss: Binary Crossentropy  
Optimizer: Adam (LR=1e-4)

### 📉 Training Analysis
- Training & validation accuracy ~96%  
- Slight overfitting after epoch 8  
- Good generalization overall  

### 🔧 Hyperparameter Tuning
Tuned model achieved:
- Smoother loss curves  
- Higher validation accuracy  
- Reduced overfitting  

### 🧪 Test Performance
- Test Accuracy: **97.17%**  
- Test Loss: **0.1119**  

**Classification Report:**
- Real: precision 0.97, recall 1.00  
- Fake: precision 1.00, recall 0.83  
- Macro F1: 0.95  
- Weighted F1: 0.97  

Confusion Matrix:
- Real images: **500 correctly classified**  
- Fake images: **17 misclassified**  

---

# 📈 Summary of Findings

### ✔ Temperature Prediction
- Baseline NN performs well  
- Tuning failed → over-regularization  
- More tuning or LSTM models may improve performance  

### ✔ VQ-VAE Generator
- Successfully generates 500 images  
- Struggles with sharpness  
- Overfitting detected  

### ✔ Fake Image Classifier
- CNN achieves **97% accuracy**  
- Very strong performance on real images  
- Minor weaknesses detecting fake images  

---

## 🛠️ Technologies Used
- Python  
- TensorFlow / Keras  
- NumPy  
- Matplotlib  
- scikit-learn
