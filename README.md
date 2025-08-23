# Image Denoising by GAN

## Introduction

Path tracing is a rendering technique widely used in high-end animation studios such as Pixar and DreamWorks to produce photorealistic frames. It works by emitting thousands of Monte Carlo rays per pixel, which interact with objects in the scene through reflection, refraction, or absorption. The colors returned by these rays are averaged to compute each pixel’s final value. Although accurate, this process is computationally expensive — producing a single frame can take **8–16 hours**.  

This project explores a **Generative Adversarial Network (GAN)-based denoising approach** to accelerate rendering. Instead of requiring tens of thousands of samples per pixel (e.g., 32K spp), the renderer outputs a noisy image with as few as **4–8 spp**. The GAN then reconstructs a high-quality, photorealistic image in a fraction of a second, reducing rendering time from hours to seconds.


#### Table of Contents

* [Installation](#installation)
* [Dataset](#dataset)
* [Running](#running)
* [Hyperparameters](#hyperparameter)
* [Results](#results)
* [Credits](#credits)

## Installation

To run the project you will need:
 * python 3.5
 * tensorflow (v1.1 or v1.0)
 * PIL
 * [CKPT FILE](https://uofi.box.com/shared/static/21a5jwdiqpnx24c50cyolwzwycnr3fwe.gz)
 * [Dataset](https://uofi.box.com/shared/static/gy0t3vgwtlk1933xbtz1zvhlakkdac3n.zip)

## Dataset
For training, I sampled 40 images from Pixar titles and synthesized noise by adding Gaussian perturbations across a 5×5 design of standard-deviation settings (five sets, each spanning five σ values), producing 1,000 training samples (40 × 25). For validation, I used 10 images not present in the training set and applied Gaussian noise. The test set includes both synthetically noised images and real path-traced noisy renders.

## Running

1. Once you have all the depenedencies we are ready for the main part and follow the steps: 
2. Download the dataset extract it to a folder named 'dataset' in your directory.
3. Extract the CKPT files to a folder named 'Checkpoints'
4. Runing the main.py -- python3 main.py
5. After that go to the browser and if you are running it on a server then [ip-address]:8888 or if you are on your local machine then localhost:8888

## Hyperparameters
* Number of iterations - 10K
* Adversarial Loss Factor - 0.5
* Pixel Loss Factor - 1.0
* Feature Loss Factor - 1.0
* Smoothness Loss Factor - 0.0001

## Results

Real noise images:
<img src="assets/result2.png" alt="Denoised sample" width="960" height="480">
 
## Credits

* [SRGAN](https://arxiv.org/pdf/1609.04802.pdf)
* [Image De-raining using conditional generative adversarial network](https://arxiv.org/pdf/1701.05957.pdf)
* [Creating photorealistic images from gameboy camera](http://www.pinchofintelligence.com/photorealistic-neural-network-gameboy/)

