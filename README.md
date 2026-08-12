# Image Classification with CNNs (CIFAR-10)

## Project Overview
This project demonstrates the end-to-end workflow of building, training, and testing a Convolutional Neural Network (CNN) for image classification. Built using TensorFlow and Keras, the model is trained to automatically categorize images into ten distinct classes. 

Beyond just training a model, this repository includes a pipeline for custom inference, allowing you to upload your own real-world images (like a photo of your pet) and see what the AI predicts.

## The Dataset
This model is trained on the standard benchmark CIFAR-10 dataset, which contains 60,000 color images (32x32 pixels) spread evenly across 10 classes:
* **Vehicles:** Aeroplane, Automobile, Ship, Truck
* **Animals:** Bird, Cat, Deer, Dog, Frog, Horse

## Technology Stack
* **Deep Learning Framework:** TensorFlow & Keras
* **Language:** Python 3
* **Data Manipulation:** NumPy
* **Image Processing & Visualization:** Pillow (PIL) & Matplotlib
* **Environment:** Jupyter Notebook / Google Colab

## Model Architecture & Workflow

1. **Data Preprocessing:** 
   * Loaded the CIFAR-10 dataset directly via Keras.
   * Normalized pixel values to a `float32` scale of 0.0 to 1.0 for faster convergence.
   * Applied One-Hot Encoding to the categorical labels using `to_categorical`.
2. **CNN Architecture:** A Sequential model combining feature extraction and classification:
   * **Conv2D Layers:** For extracting spatial features (using ReLU activation and MaxNorm constraints).
   * **MaxPooling2D:** For downsampling and reducing computational load.
   * **Dropout Layers (0.2 & 0.5):** To prevent overfitting during training.
   * **Flatten & Dense Layers:** A fully connected network ending in a 10-node Softmax layer to output class probabilities.
3. **Compilation:** Used Stochastic Gradient Descent (`SGD`) optimizer with a learning rate of 0.01 and momentum of 0.9, utilizing Categorical Crossentropy for loss calculation.
4. **Training:** Trained over 10 epochs with a batch size of 32, achieving roughly 68% accuracy on unseen test data.

## Custom Image Inference
A key feature of this notebook is the ability to test the model on external images. The pipeline handles:
1. Loading an image via `PIL`.
2. Ensuring standard RGB formatting and resizing to 32x32 pixels.
3. Normalizing the custom image array (dividing by 255.0) so it mathematically matches the training data.
4. Outputting the predicted class and visualizing the original image with Matplotlib.

### How to test your own images:
Simply upload a `.jpg` or `.png` to your working directory and update the path in the final cell:
```python
# Change this to the name of your uploaded file
image_path = "/content/your_image.jpg"
