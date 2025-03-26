# 🎥 ICG-BreakingBias2-DataWizards

This repository contains a deep learning model that classifies videos into two categories: **Brawl (Violent)** and **Peace (Non-Violent)**. The model is implemented in an **IPython Notebook** and utilizes deep learning techniques for video classification. It also includes the `prediction.csv` file for testing data and a `demo.mp4` for the bonus task.

---

## 📂 Dataset Requirements

✅ Ensure that you have a dataset of labeled videos categorized into **Brawl** and **Peace**.
✅ The dataset should contain two folders: **Brawl** and **Peace**, each containing `.mp4` video files.

---

## 🔧 Dependencies

Before running the notebook, install the required dependencies:

```bash
pip install -r requirements.txt
```

---

## 🏃 Running the Model (`code.ipynb`)

### 1️⃣ Load and Preprocess Data

🔹 Extract frames from videos.
🔹 Resize frames to the required input size (**64x64**).
🔹 Prepare sequences of frames as input to the model.

💡 **Note:** Make sure to change the directories to match your folder containing the **Brawl** and **Peace** folders.

---

### 2️⃣ Train the Model

The model is a **SlowFast-inspired 3D CNN** designed for video classification. It consists of two pathways:

- **Slow Pathway:** Processes every **α=4** frames, capturing high-level temporal semantics with **3D convolutions** and **MaxPooling layers**.
- **Fast Pathway:** Processes all frames but with **shallower filters**, focusing on fine-grained motion details.

✨ **Both pathways undergo feature extraction** with **Conv3D + BatchNorm + Pooling**, then fuse via **1x1x1 convolutions**. The fused features pass through **3D residual blocks**, **Global Average Pooling**, and a **Dense classifier**. The model is optimized with **AdamW and mixed precision training** for efficiency. 🚀

---

### 3️⃣ Evaluate the Model

📊 The model is evaluated using **precision, recall, and F1-score**.

📌 **Classification Report:**

```
            precision    recall  f1-score   support

            0       0.91      0.90      0.90       200
            1       0.90      0.91      0.91       200

    accuracy                           0.91       400
    macro avg       0.91      0.91      0.90       400
    weighted avg    0.91      0.91      0.90       400
```

🏆 **Final Model F1-Score:** **0.91**

---

### 4️⃣ Save and Use the Model

💾 The trained model is saved as **`final_model.keras`** for later use.
🎬 Load the model to classify new videos.

---

## 🎯 Bonus Task

### 🔧 Dependencies
Before running the notebook, install the required dependencies:

```bash
pip install -r requirements_bonus.txt
```
### 🧠 Model Pipeline
✨ Detection Pathway:
   *YOLOv8*: Detects persons in each frame using confidence-based filtering.

✨ Tracking Pathway:
   *DeepSORT*: Assigns unique IDs and maintains trajectories for detected persons across frames.

✨ Classification Pathway:
    *MoBiLSTM*: Crops, resizes, and classifies each tracked person as "Brawl" or "Peace".
    
### 🎬 Running the Code (`code(bonus).ipynb`)

📌 Run the notebook in order.
🎥 Add your own video to see the code in action.

---

