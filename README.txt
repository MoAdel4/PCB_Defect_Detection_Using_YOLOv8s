This repository contains the code for a PCB defect detection system implemented using YOLOv8s. Portions of the code are adapted from publicly available sources under the Apache License 2.0.
Repository Structure:

1. Dataset Registration and Preprocessing
   - Dataset Registration: Code for mounting Google Drive and registering the dataset from local storage.
   - Annotation Parsing & Conversion: Parsing XML annotation files to extract bounding box coordinates and converting them into YOLO-compatible format.
   - Image & Annotation Resizing: Functions to standardize image dimensions (resizing to 640×640) and proportionally adjust bounding box coordinates.

2. Dataset Splitting
   - Code that splits the dataset into training (85%), validation (15%).
   - The split code creates directories and organizes images and corresponding YOLO labels for each split.

3. K-Fold Cross-Validation and Training Code
   - Implements a 3-fold cross-validation on the training subset for robust hyperparameter tuning.
   - The code builds a DataFrame of image class frequencies, assigns each image to train/validation splits for each fold, and copies the data into fold-specific directories.

4. Final Model Training and Inference Code
   - Final training code that uses the best hyperparameters from the cross-validation phase to retrain the model on the entire training subset.
   - Inference code that runs on the validation set to generate evaluation metrics (mAP, Precision, Recall, F1-score) and save outputs (predicted bounding boxes with confidence scores).
   - A post-processing module converts YOLO outputs back to original image dimensions for visual comparison.
   - Evaluation and Annotation Conversion
   - Functions to convert YOLO model predictions to original-scale annotations
