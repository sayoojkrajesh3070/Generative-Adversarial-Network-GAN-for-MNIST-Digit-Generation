# Generative Adversarial Network (GAN) for MNIST Digit Generation

This project implements a Deep Convolutional Generative Adversarial Network (DCGAN) using TensorFlow and Keras. The model is trained on the MNIST dataset to generate realistic handwritten digits from random noise.

## 🚀 Project Overview
The core of this project is the adversarial relationship between two neural networks:
* **The Generator**: Learns to create "fake" images that look like real handwritten digits.
* **The Discriminator**: Learns to distinguish between real images from the MNIST dataset and the fake images produced by the Generator.

As training progresses, the Generator becomes better at creating realistic images, while the Discriminator becomes better at detecting subtle flaws.

## 🛠️ Architecture Summary

### Generator
| Layer Type | Output Shape | Activation |
| :--- | :--- | :--- |
| Input (Noise) | (100,) | - |
| Dense | (7 * 7 * 256,) | LeakyReLU |
| Batch Normalization | (7 * 7 * 256,) | - |
| Conv2DTranspose | (7, 7, 128) | LeakyReLU |
| Conv2DTranspose | (14, 14, 64) | LeakyReLU |
| Conv2DTranspose | (28, 28, 1) | Tanh |

### Discriminator
| Layer Type | Input Shape | Activation |
| :--- | :--- | :--- |
| Conv2D | (28, 28, 1) | LeakyReLU |
| Dropout (0.3) | (14, 14, 64) | - |
| Conv2D | (14, 14, 128) | LeakyReLU |
| Flatten | (6272,) | - |
| Dense | (1,) | Sigmoid |

## 📈 Training Details
- **Dataset:** MNIST (Handwritten digits 0-9)
- **Normalization:** Images scaled to the range `[-1, 1]` to match the Tanh activation of the Generator.
- **Optimizer:** Adam (Learning Rate: 0.0002, Beta_1: 0.5)
- **Loss Function:** Binary Cross-Entropy
- **Batch Size:** 256
- **Epochs:** 20+

## 📊 Results & Visualization
The notebook includes automated plotting for:
1.  **Loss Curves:** Tracking the competition between `gen_loss` and `disc_loss`.
2.  **Sample Generation:** Visualizing the progress of generated digits at regular intervals (every 5 epochs).

## 💻 Requirements
To run this notebook, you will need:
- Python 3.x
- TensorFlow 2.x
- NumPy
- Matplotlib
