# 📸 Image Compression Using SVD  
### CSE281 – Image Processing

---

## 📌 Overview
This project demonstrates a lossy image compression technique using Singular Value Decomposition (SVD).  
The goal is to reduce image storage size while maintaining acceptable visual quality.

---

## ❓ Problem Statement
Digital images require large storage and bandwidth.  
This project explores:

> How many singular values are sufficient to reconstruct an image with acceptable quality?

---

## 🗂️ Dataset
The project uses 5 benchmark images from `scikit-image`:

- camera
- coins
- moon
- clock
- page

All images:
- Converted to grayscale  
- Stored as float64  
- Pixel range: [0, 255]

---

## ⚙️ Methodology

### 1. Image Preprocessing
- Load images using `skimage.data`
- Convert to float64

### 2. Singular Value Decomposition
Each image matrix A is decomposed into:
A = U × Σ × Vᵀ

### 3. Rank-k Approximation
A_k = U_k × Σ_k × V_kᵀ

Tested k values:
5, 10, 20, 30, 50, 75, 100, 150, 200, 250, 300

### 4. Compression Ratio (CR)
CR = (m × n) / (k × (m + n + 1))

### 5. PSNR (Quality)
PSNR = 10 × log10(MAX² / MSE)

- MAX = 255  
- Higher PSNR = better quality  

---

## 🧠 Key Functions

- `svd_compress(img, k)` → Performs compression  
- `compression_ratio(shape, k)` → Calculates CR  
- `compute_psnr(original, reconstructed)` → Measures quality  
- `display_image()` → Displays images  

---

## 📊 Results

### Compression Behavior
- Small k → High compression, low quality  
- Large k → Low compression, high quality  

### PSNR Behavior
- Rapid improvement at small k  
- Slower improvement after k ≈ 50–100  

### Observations
- Smooth images compress better  
- Textured images need higher k  
- Text images are hardest to compress  

---

## 📈 Example Results

| Image  | k  | Compression Ratio | PSNR |
|--------|----|------------------|------|
| camera | 5  | ~25:1            | ~22  |
| camera | 20 | ~7:1             | ~31  |
| camera | 50 | ~3:1             | ~38  |
| Full   | -  | 1:1              | ∞    |

---

## ✅ Conclusion

- Few singular values capture most image information  
- Clear trade-off between compression and quality  
- Optimal k depends on image complexity  
- SVD is educational but less efficient than JPEG  

---

## 🚀 Future Work

- Apply SVD on RGB images  
- Compare with JPEG compression  
- Add SSIM metric  
- Improve performance  

---

## 👨‍💻 Team Members

- Shaimaa Mohamed Kotit 

**Supervisor:** Dr. Essam Abdellatef  

---

## 🛠️ Technologies

- Python  
- NumPy  
- Matplotlib  
- scikit-image  

---

## ▶️ How to Run

```bash
pip install numpy matplotlib scikit-image
python main.py
