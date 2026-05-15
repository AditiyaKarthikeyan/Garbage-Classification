# E-Waste Image Classification Using EfficientNetV2B0

![TensorFlow](https://img.shields.io/badge/TensorFlow-%23FF6F00.svg?style=for-the-badge&logo=TensorFlow&logoColor=white)
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Jupyter Notebook](https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=for-the-badge&logo=jupyter&logoColor=white)
![Gradio](https://img.shields.io/badge/Gradio-FF7C00?style=for-the-badge&logo=gradio&logoColor=white)

## Overview
E-waste represents a growing environmental and health challenge globally. Proper sorting and categorization of e-waste is essential for efficient recycling, but manual classification is labor-intensive and error-prone. 

This project implements an automated computer vision system using deep learning to accurately categorize different types of electronic waste, serving as a critical first step for automated recycling systems.

---

## Technical Architecture

### Data Processing
* **Classes:** 10 distinct categories (Battery, Keyboard, Microwave, Mobile, Mouse, PCB, Player, Printer, Television, Washing Machine).
* **Dataset Split:** 2400 training images, 300 validation images, and 300 test images.
* **Preprocessing:** Images standardized to 128x128 pixels, processed in batches of 32.
* **Augmentation:** Applied horizontal flipping, random rotation (10%), and random zooming (10%) to improve model robustness.

### Model Details
* **Framework:** TensorFlow / Keras
* **Base Architecture:** EfficientNetV2B0 (Transfer learning utilizing ImageNet weights).
* **Custom Top Layers:** Global Average Pooling, 0.2 Dropout, and a Dense softmax layer for 10-class output.
* **Training Strategy:** * Initial phase: 15 epochs with early stopping (Adam optimizer).
  * Fine-tuning phase: 5 epochs with unfreezing of later base layers at a lower learning rate (1e-5) to enhance specific feature extraction.

---

## Performance and Results
* **Test Accuracy:** 89.33%
* Detailed evaluation metrics (Precision, Recall, F1-Score) and Confusion Matrices were utilized to analyze performance bottlenecks across specific consumer electronics.
* The finalized weights are exported and saved locally as `efficientnet_ewaste_model.keras`.

---

## Deployment Interface
The project includes a web-based user interface built with the **Gradio** framework.
* Accepts direct image uploads.
* Automatically applies necessary preprocessing (`preprocess_input`, resizing to 128x128).
* Outputs the predicted E-Waste category alongside the model's confidence score.

---

## Getting Started

To explore the code or run the classification model locally:

1. **Clone the repository:**
   ```bash
   git clone https://github.com/AditiyaKarthikeyan/Garbage-Classification.git
   cd Garbage-Classification
   ```

2. **Install dependencies:**
Ensure you have Python 3.8+ installed. Install the required libraries using pip:

   ```bash
   pip install tensorflow numpy pandas matplotlib jupyter gradio
   ```

3. **Run the Notebook:**
Launch Jupyter and open the core notebook to view the training process, inference results, and launch the Gradio web interface:
  
   ```bash
   jupyter notebook course-materials/ewaste_classifier_efficientnet.ipynb
   ```
   
