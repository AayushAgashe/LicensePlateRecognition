
#  License Plate Recognition – Detection & OCR

This repository contains a full pipeline for **Automatic License Plate Recognition (ALPR)** using deep learning techniques for plate detection and OCR for character recognition.

---

###  Project Overview

This project focuses on automatic license plate recognition (ALPR), specifically tackling two core tasks:

1. **License Plate Detection** – Identifying and locating license plates within full vehicle images using bounding box coordinates.  
2. **Character Recognition (OCR)** – Reading the alphanumeric characters on each license plate.

---

###  Dataset Structure

The dataset is organized into three distinct sets:

- **`train1/`**: 900 full vehicle images with bounding box annotations in `train1.csv` for license plate locations (`ymin`, `xmin`, `ymax`, `xmax`).
- **`train2/`**: 900 cropped license plate images with corresponding text labels in `train2.csv`.
- **`test/`**: 201 full vehicle images. Evaluation is based on predictions compared to `test.csv`, which contains per-character labels.
- Drive Link to Dataset : [Click Here](https://drive.google.com/file/d/1YgnADBcBG2TCT5LBET6ipYEe21jPVUv8/view?usp=sharing)
---

###  Model Architecture

- **Detection**: A YOLO-based object detection model (YOLOv5) is used to predict license plate bounding boxes from full vehicle images.
- **OCR**: [EasyOCR](https://github.com/JaidedAI/EasyOCR), a lightweight and open-source OCR tool, is applied to cropped license plates to extract alphanumeric text.

---

###  Project Workflow

1. Detect license plate bounding boxes in `test/` using the trained YOLO model.
2. Crop detected regions from vehicle images.
3. Run EasyOCR on the crops to extract text.
4. Postprocess and evaluate predictions against ground truth.

---

###  Observations and Challenges

- ✅ **Numerical Recognition**: The system performs well on **numeric characters (0–9)**, achieving high accuracy even on test data. This consistency reflects the reliability of both detection and OCR in recognizing digits.
  
- ⚠️ **Arabic-style Characters**: Some license plates contain stylized characters resembling **Arabic letters** (e.g., 'ت' or 'ن'). These are intended to be interpreted as Latin characters such as `'T'` or `'N'`. However, general-purpose OCR tools like EasyOCR often misinterpret them as visually similar Latin characters (`'U'`, `'S'`, `'M'`, etc.), leading to reduced accuracy in the alphabetic portion of predictions.

---

###  Future Improvements

- Train a **custom CRNN (Convolutional Recurrent Neural Network)** model on the `train2` dataset to better handle non-standard fonts and character sets.
- Implement **image preprocessing techniques** (contrast adjustment, character separation, skew correction).
- Apply **postprocessing character remapping** for ambiguous letter predictions (e.g., mapping `'U'` to `'T'` based on position/shape priors).

---


### 👤 Author
**Aayush Agashe**  
📧 Email: aayushagashe@gmail.com  
---

