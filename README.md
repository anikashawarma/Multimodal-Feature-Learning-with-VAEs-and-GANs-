# 🧩 Multimodal Feature Learning with VAEs and GANs for CLIP-Synthesized Images

## 📘 Overview

This research introduces a **hybrid deep learning framework** that integrates **Variational Autoencoders (VAEs)** and **Generative Adversarial Networks (GANs)** to extract and analyze latent features from **CLIP-synthesized images**.
The framework bridges the gap between **generative** and **contrastive learning** paradigms, enhancing multimodal representation learning and improving interpretability of features in text-to-image synthesis.

---

## ⚙️ Methodology

### 1️⃣ Data Collection

* Used **Flickr8k** dataset to curate **semantically diverse text prompts**.
* Generated **2,000 synthetic images** using **Stable Diffusion** guided by **CLIP embeddings**.
* Ensured high **semantic alignment** between text prompts and generated visuals.
* Dataset split: **1,600 training** and **400 testing** images.

---

### 2️⃣ Image Generation (CLIP + Stable Diffusion)

* **CLIP Embeddings:** Text prompts encoded into joint embedding space.
* **Stable Diffusion:** Generates images by maximizing CLIP-text similarity.
* **Post-processing:** Artifact removal (noise, distortion) and alignment verification.

---

### 4️⃣ VAE-GAN Hybrid Architecture

#### 🧩 Encoder

* Maps input image `x` → latent Gaussian distribution `q(z|x)`
* CNN-based layers extract features with downsampling.
* Two outputs:

  * Mean (μ): Center of distribution
  * Log variance (σ²): Stability in training

#### 🌀 Latent Space

* Probabilistic latent space ensures feature disentanglement.

#### ⚔️ GAN Discriminator (Integrated in Latent Space)

* Operates on **latent vectors** instead of pixel data.
* Classifies latent features as **discriminative / non-discriminative**.
* Uses **Binary Cross-Entropy (BCE) Loss** for adversarial optimization.

#### 🧠 Decoder

* Acts as both **VAE reconstructor** and **GAN generator**.
* Trained to reconstruct images preserving **CLIP alignment**.

#### 🧮 Loss Functions

| Component               | Description                                 |
| ----------------------- | ------------------------------------------- |
| **Reconstruction Loss** | Measures pixel-level fidelity               |
| **KL Divergence**       | Regularizes latent distribution             |
| **Adversarial Loss**    | Encourages realistic latent representations |

---

### 🔄 CLIP Alignment

Decoder outputs are trained so that reconstructed images’ CLIP embeddings **closely match** their corresponding text prompts, ensuring **semantic consistency** between modalities.

---

## 📊 Experimental Results

### 🧪 Initial Training

| Metric                 | Result |
| ---------------------- | ------ |
| Reconstruction Loss    | 6.22   |
| KL Divergence          | 0.83   |
| Discriminator Loss     | 124.93 |
| Discriminator Accuracy | 50.3%  |
| Validation Loss        | 0.07   |
| Validation Accuracy    | 52.8%  |

🧩 Interpretation:

* Model effectively learns structured latent spaces.
* Discriminator exhibits balanced generalization (≈50% accuracy).

### ⚖️ Comparison with Baseline

| Model                | Convergence    | Representation Quality |
| -------------------- | -------------- | ---------------------- |
| **Baseline VAE**     | Slow, unstable | Moderate               |
| **Proposed VAE-GAN** | Fast, stable   | High                   |

---


### Future Directions:

* Implement **β-VAEs** and **Hierarchical VAEs** for better disentanglement.
* Expand to **text + image multimodal fusion** tasks (e.g., VQA, sentiment analysis).
* Optimize for **real-time multimodal understanding** in generative AI systems.
* Evaluate on larger datasets (e.g., MS-COCO, LAION).

---

## 🧰 Tools & Frameworks

* **Python**, **PyTorch/TensorFlow**
* **OpenAI CLIP**, **Stable Diffusion**
* **NumPy**, **Matplotlib**, **Scikit-learn**
* **CUDA** for GPU-accelerated training

---

## 👩‍💻 Authors

**School of CSET, Bennett University, India**

* Shivani Pahuja – [shivanipahuja04@gmail.com](mailto:shivanipahuja04@gmail.com)
* Satyam – [e22cseu0192@bennett.edu.in](mailto:e22cseu0192@bennett.edu.in)
* Anika Sharma – [e22cseu0191@bennett.edu.in](mailto:e22cseu0191@bennett.edu.in)
* Yash Bindra – [e22cseu0200@bennett.edu.in](mailto:e22cseu0200@bennett.edu.in)
* Riti Kushwaha – [riti.kushwaha@bennett.edu.in](mailto:riti.kushwaha@bennett.edu.in)
* Akanksha Singh – [akansha1.singh@bennett.edu.in](mailto:akansha1.singh@bennett.edu.in)

---

## 📖 Citation

If you reference this work, please cite:

> Pahuja, S., Sharma, A., Satyam, Y., Kushwaha, R., & Singh, A. *Multimodal Feature Learning with VAEs and GANs for CLIP-Synthesized Images.* Bennett University, 2025.
