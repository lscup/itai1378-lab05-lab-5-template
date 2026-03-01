# Lab 5: Interactive Image Processing Application

In this lab, you will build an interactive image processing application using OpenCV, Matplotlib, and ipywidgets. The application will allow you to perform various operations on an image such as converting it to grayscale, adjusting its brightness, resizing, rotating, and plotting its histogram. You will also be able to save the processed image.

---

## 1. Overview

### Objectives
- Understand how to use OpenCV for basic image processing tasks
- Learn to manipulate images using widgets in Jupyter notebooks
- Implement an interactive application with a graphical user interface

### Prerequisites
- Basic understanding of Python programming
- Familiarity with Jupyter Notebooks
- Basics of image processing with OpenCV

---

## 2. Algorithm/Concept Background

Interactive image processing involves updating image data and visualizing the results in real-time as the user interacts with a graphical interface. The key operations include:

- **Grayscale Conversion**: Transform a color image to grayscale by averaging or desaturating the color channels.
- **Brightness Adjustment**: Modify the intensity of image pixels to make the image lighter or darker.
- **Resizing**: Change the dimensions of the image by scaling the width and height.
- **Rotation**: Rotate the image by a specified angle using predefined rotation matrices.
- **Histogram Plotting**: Visualize the distribution of pixel intensities.

| Operation            | Description                        |
|----------------------|------------------------------------|
| Grayscale Conversion | Reduces image to one color channel |
| Brightness Adjustment| Changes pixel intensity globally   |
| Resizing             | Alters image dimensions            |
| Rotation             | Rotates image by given angle       |
| Histogram Plotting   | Displays pixel intensity histogram |

Example code to convert an image to grayscale:

```python
# Convert image to grayscale
gray = cv2.cvtColor(original_rgb, cv2.COLOR_RGB2GRAY)
```
---

## 3. Your Coding Environment

### Workspace Layout
| Area               | What It Does                                          |
|--------------------|-------------------------------------------------------|
| Code Editor (left) | Edit your files using the tabbed editor               |
| Terminal (right)   | See output when you click the **Run** button          |
| AI Tutor (chat panel) | Ask your AI Tutor for help — it knows this lab and can guide you step by step |

### Workflow
1. Edit your code in the editor tabs
2. Click **Run** to execute and see output in the terminal
3. When ready, click **Commit** to save your work to GitHub and trigger the autograder
4. A ✅ (green check) or ❌ (red X) will appear showing whether tests passed

Tip: Commit early and often to track your progress!

---

## 4. Project Structure

```
|-- notebook.ipynb (YOUR WORK)
```

---

## 5. Step-by-Step Implementation

### Step 1: Import Dependencies

```python
# Import necessary libraries
import cv2
import numpy as np
import matplotlib.pyplot as plt
import ipywidgets as widgets
from IPython.display import display
import os
```
This code imports all the necessary libraries required for image processing and building the interactive interface.

### Step 2: Setup Output Directory

```python
output_path = './outputs'
os.makedirs(output_path, exist_ok=True)
```
This creates a directory to save the processed images, ensuring it exists without error.

### Step 3: Initialize Global Variables

```python
original_bgr = None
original_rgb = None
processed_rgb = None
```
Initialize the shared state for images. These variables will store our images in different states.

### Step 4: Create Output Widgets

```python
msg_out = widgets.Output()
img_out = widgets.Output()
hist_out = widgets.Output()
```
These widgets are used to display messages, images, and histograms respectively.

### Step 5: Implement `show_images()` Function

```python
def show_images(original_rgb, processed_rgb):
    with img_out:
        img_out.clear_output()
        fig, axes = plt.subplots(1, 2, figsize=(10, 5))
        axes[0].imshow(original_rgb)
        axes[0].set_title('Original Image')
        axes[0].axis('off')
        axes[1].imshow(processed_rgb)
        axes[1].set_title('Processed Image')
        axes[1].axis('off')
        plt.show()
```
This function displays the original and processed images side by side.

### Step 6: Implement `show_histogram()` Function

```python
def show_histogram(processed_rgb):
    with hist_out:
        hist_out.clear_output()
        gray = cv2.cvtColor(processed_rgb, cv2.COLOR_RGB2GRAY)
        plt.figure(figsize=(5, 3))
        plt.hist(gray.ravel(), bins=256, range=[0, 256], color='gray')
        plt.title('Histogram')
        plt.show()
```
Displays a histogram of the processed image.

### Step 7: Implement Callback Functions

Implement the callback functions for the buttons and sliders to perform the image processing operations.

### Step 8: Layout and Run the Application

Arrange the widgets and display the application interface.

---

## 6. Testing Your Code

### Run Your Code
Click **Run** to execute your code and check the output.

### Submit for Grading
Click **Commit**, enter a message, and look for ✅ or ❌ to check if your solution passed the tests.

Expected output:

```
Image loaded: test_image.png
```

---

## 7. Autograding

| Test                     | Points | What It Checks                      |
|--------------------------|--------|-------------------------------------|
| Syntax Check             | 20     | Checks for syntax errors            |
| Browse Image Functionality | 15     | Tests image loading functionality   |
| Convert to Grayscale     | 15     | Verifies grayscale conversion       |
| Adjust Brightness        | 15     | Tests brightness adjustment         |
| Resize Image             | 15     | Checks resizing functionality       |
| Rotate Image             | 10     | Verifies image rotation             |
| Plot Histogram           | 10     | Tests histogram plotting            |
| Save Image               | 10     | Checks image saving functionality   |

Total: 100 points

---

## 8. Lab Report

Please fill out your lab report in the README.md tab using the template below:

```
# Lab Report

## Student Information
- **Name:**
- **Date:**

## Key Concepts
- Describe the image processing techniques implemented in this lab.

## Tracing/Analysis
- Analyze the effect of each image processing operation on the example images.

## Complexity/Performance
| Operation            | Time Complexity | Space Complexity |
|----------------------|-----------------|-----------------|
| Grayscale Conversion | O(n)            | O(n)            |
| Brightness Adjustment| O(n)            | O(n)            |
| Resizing             | O(n)            | O(n)            |
| Rotation             | O(n)            | O(n)            |

## Reflection Questions
1. What challenges did you face while implementing this lab?
2. How can you extend this application with more image processing features?
3. What did you learn about interactive applications in Jupyter Notebooks?
```

---

## 9. Submission Checklist

- [ ] All functions implemented
- [ ] Click Run — output matches expected
- [ ] Click Commit — autograder shows green check
- [ ] Lab report completed in README.md
- [ ] Final commit with completed lab report

---

Remember, your AI Tutor is available to help guide you through any difficulties.