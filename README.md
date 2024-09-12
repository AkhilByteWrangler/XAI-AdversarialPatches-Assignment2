# **Assignment 2: Adversarial Patch Attacks**

This repository contains the code and resources for **Assignment 2** of the course, which focuses on **adversarial patch attacks** on images, including technical and creative explorations. The goal is to apply adversarial patches to fool a pre-trained neural network, and later, to creatively use these patches on meme images to evaluate how effectively the network can be deceived.

---

## **Table of Contents**

- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Patch Attack Process](#patch-attack-process)
- [Creative Part: Meme Patch Attack](#creative-part-meme-patch-attack)
- [Results](#results)

---

## **Project Overview**

This assignment is divided into two major parts:

### 1. **Adversarial Patch Attack on ImageNet Subset**
We use pre-trained models (ResNet34) and apply adversarial patches to fool the network into misclassifying objects in the **ImageNet** subset. The adversarial patches are optimized to be as small as possible while achieving a high fooling rate.

### 2. **Creative Part: Adversarial Patch Attack on Memes**
For the creative part of the project, we apply adversarial patches to various **meme images**. The goal is to see if we can fool the network using the patches designed for specific classes, while minimizing the patch size.

---

## **Dataset**

- **ImageNet Subset**: We use a subset of the **TinyImageNet** dataset to perform initial adversarial patch attacks.
- **Meme Images**: For the creative component, we apply the adversarial patches to meme images stored in the `my_images/memes/` folder.

### **Classes Targeted in the Attack**
We focused on the following classes from the ImageNet dataset:
- **Hotdog**
- **Goldfish**
- **Great White Shark**
- **Skunk**
- **Oxygen Mask**
- **Dam**

---

## **Patch Attack Process**

### **1. Adversarial Patch Generation**
- We create adversarial patches targeting the classes mentioned above using the ResNet34 pre-trained on ImageNet.
- Patches are optimized using different patch sizes: **32x32**, **48x48**, and **64x64**.

### **2. Patch Application**
- **Patch Placement**: The patch is applied at multiple random locations on each image to find the position that maximizes fooling ability.
- **Optimization**: We balance patch size with fooling ability, ensuring smaller patches are prioritized but are still effective in reducing the model’s confidence.

### **3. Fooling Score**
- We evaluate the **fooling score**, which measures the decrease in the model’s confidence for the true class after the patch is applied.
- A **fooling threshold of 80%** is set to ensure that patches need to reduce the confidence for the true class by at least 80% to be considered successful.

---

## **Creative Part: Meme Patch Attack**

### **Meme Images and Target Classes**
For the creative component, we applied the adversarial patches to a set of **memes**:

- **Hotdog** patch on `my_images/memes/hotdogmeme.jpeg`
- **Great White Shark** and **Goldfish** patches on `my_images/memes/dukeuncrivarlymeme.jpeg`
- **Dam** patch on `my_images/memes/damnmeme.jpeg`
- **Skunk** patch on `my_images/memes/hungrydogmeme.jpeg`
- **Oxygen Mask** patch on `my_images/memes/maskmeme.jpeg`

### **Patch Attack on Memes**
We used the same logic from the patch attack process to:
- Apply the patch to memes.
- Test different patch sizes (32x32, 48x48, 64x64).
- Find the best fooling position for the patch on each meme image.
- Visualize the results with side-by-side comparisons of the original meme and the patched meme, along with the model’s predictions.

---

## **Results**

### **Adversarial Patch Attack (TinyImageNet Subset)**
- The adversarial patches successfully fooled the ResNet34 model on several images from the TinyImageNet dataset.
- Smaller patch sizes (32x32) performed well on certain classes, but larger patches (64x64) were more effective for classes like **Goldfish** and **Great White Shark**.

### **Meme Patch Attack**
- **Hotdog Meme**: The hotdog patch successfully reduced the model's confidence by over 80%, using a 48x48 patch.
- **Duke-Unc Meme (Goldfish & Shark)**: The 64x64 patch for both **Goldfish** and **Great White Shark** provided the best fooling results.
- **Mask Meme**: The **Oxygen Mask** patch, despite being smaller (32x32), was highly effective.
- **Skunk & Dam Memes**: Larger patches (64x64) were needed to fool the network consistently.

---
