# Image Denoising with GAN

## Introduction

Path tracing is a rendering technique widely used in high-end animation studios such as Pixar and DreamWorks to produce photorealistic frames. It works by emitting thousands of Monte Carlo rays per pixel, which interact with objects in the scene through reflection, refraction, or absorption. The colors returned by these rays are averaged to compute each pixel's final value. Although accurate, this process is computationally expensive — producing a single frame can take 8–16 hours.

This project explores a Generative Adversarial Network (GAN)-based denoising approach to accelerate rendering. Instead of requiring tens of thousands of samples per pixel (e.g., 32K spp), the renderer outputs a noisy image with as few as 4–8 spp. The GAN then reconstructs a high-quality, photorealistic image in a fraction of a second, reducing rendering time from hours to seconds.

## Installation

**Requirements:**
- Python 3.10
- TensorFlow (v1.0 or v1.1)
- PIL
- [Checkpoint file](https://uofi.box.com/shared/static/21a5jwdiqpnx24c50cyolwzwycnr3fwe.gz)
- [Dataset](https://uofi.box.com/shared/static/gy0t3vgwtlk1933xbtz1zvhlakkdac3n.zip)

## Dataset

For training, 40 images were sampled from Pixar titles, and noise was synthesized by adding Gaussian perturbations across a 5×5 grid of standard-deviation settings (five sets, each spanning five σ values), producing 1,000 training samples (40 × 25).

For validation, 10 images not present in the training set were used, with Gaussian noise applied. The test set includes both synthetically noised images and real path-traced noisy renders.

## Running

1. Download the dataset and extract it to a folder named `dataset` in your project directory.
2. Extract the checkpoint files to a folder named `Checkpoints`.
3. Run the main script:
```bash
   python3 main.py
```
4. Open your browser and navigate to:
   - `localhost:8888` if running locally
   - `[ip-address]:8888` if running on a server

## Hyperparameters

| Parameter | Value |
|---|---|
| Iterations | 10K |
| Adversarial loss factor | 0.5 |
| Pixel loss factor | 1.0 |
| Feature loss factor | 1.0 |
| Smoothness loss factor | 0.0001 |

## Results

Denoising applied to real noisy renders:

<img src="assets/result2.png" alt="Denoised sample" width="960" height="480">

## Reference 

- [SRGAN](https://arxiv.org/pdf/1609.04802.pdf)
- [Creating Photorealistic Images from Game Boy Camera](http://www.pinchofintelligence.com/photorealistic-neural-network-gameboy/)
