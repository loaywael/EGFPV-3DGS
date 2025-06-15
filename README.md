# 🔬 Mini Project: 3DGS on FPV Drone Footage
<br>

## 🎯 Project Strategy
![alt text](image-1.png)

<br>


## 📊 Evaluation Metrics

| Model Variant               | SSIM    | PSNR (dB) | LPIPS   | Link |
|----------------------------|---------|-----------|---------|------|
| **7K Iteration**           | 0.937   | 33.21     | 0.158   | [🔗 View](https://splatter.app/s/wej-55b) |
| **30K Iteration**          | 0.924   | 33.59     | 0.224   | [🔗 View](https://splatter.app/s/iz3-zha) |
| **7K + Depth Regularized** | 0.920   | 29.26     | 0.201   | [🔗 View](https://splatter.app/s/rhb-qc5) |
| **30K + Depth Regularized**| 0.924   | 33.59     | 0.220   | [🔗 View](https://splatter.app/s/9gd-64n) |

---
<br>

#### Structural Similarity Index Measure (SSIM)

`Definition`: SSIM quantifies the perceived similarity between two images by comparing their luminance (brightness), contrast, and structural features (patterns of pixel intensities).

`Range`: 20–40 dB, with >30 dB considered high quality.

`Focus`: Emphasizes human visual perception, capturing how well the structural content
  (e.g., edges, textures) of the rendered image matches the ground truth.
  indicating the rendered image closely matches the ground truth at the pixel level.

#### Peak Signal-to-Noise Ratio (PSNR)

`Definition`: PSNR measures the pixel-level difference between two images, 
  quantifying the ratio of the maximum possible signal (pixel intensity)
  to the noise (error) introduced by rendering.

`Range`: High SSIM (e.g., >0.9) AND Low SSIM (e.g., <0.7)

`Focus`: Emphasizes exact pixel matching, sensitive to small intensity differences.

#### Learned Perceptual Image Patch Similarity (LPIPS)

`Definition`: LPIPS measures perceptual similarity between two images using features extracted from a pre-trained deep neural network (e.g., VGG or AlexNet). It compares patch-level features to mimic human visual perception.

`Range`: 0 to 1 (or higher), where 
  0 indicates perceptually identical images
  higher values indicate greater perceptual differences.
  Low LPIPS (e.g., <0.2): The rendered image is perceptually similar to the ground truth, 
    with similar textures, colors, and details as perceived by humans.
  High LPIPS (e.g., >0.4): Noticeable perceptual differences, 
    such as distorted textures or unnatural colors, indicating poor visual quality.

`Focus`: Captures high-level perceptual differences (e.g., texture quality, color coherence) that pixel-based metrics like PSNR miss, aligning closely with human judgment.

<br>

## 🧠 Key Observations

- ✅ **7K Iteration (Baseline)** delivered **the best perceptual quality** (SSIM: 0.937, LPIPS: 0.158), with balanced structural and visual fidelity.
- 📈 **30K Iteration** improved PSNR slightly but **worsened SSIM and LPIPS**, suggesting **overfitting** to pixel values.
- 🧩 **Depth regularization** significantly **improved geometry** (confirmed in point cloud visualizations), though it caused PSNR and SSIM degradation at 7K.
- 🔁 At **30K with depth**, geometry improved **without harming SSIM**, but LPIPS still didn’t fully recover—suggesting texture inconsistency persists even with geometric accuracy.

---
<br>

## 🧭 Summary & Motivation

This short experiment gave me a **hands-on understanding of the trade-offs** between:
- Pixel accuracy (PSNR),
- Structural fidelity (SSIM),
- Perceptual similarity (LPIPS),
- And **geometry accuracy with depth regularization**.



