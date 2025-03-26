# ICG-BreakingBias2-DataWizards

This repository contains a deep learning model that classifies videos into two categories: **Brawl (Violent)** and **Peace (Non-Violent)**. The model is implemented in an IPython Notebook and utilizes deep learning techniques for video classification. It also contains the `prediction.csv` file for the testing data along with a `demo.mp4` for the bonus task.

## Dataset Requirements

- Ensure that you have a dataset of labeled videos categorized into **Brawl** and **Peace**.
- The dataset should contain two folders: **Brawl** and **Peace**, each containing `.mp4` video files.

## Dependencies

Before running the notebook, install the required dependencies:

```bash
pip install -r requirements.txt
```

## Running the Model (`code.ipynb`)

### 1. Load and Preprocess Data

- Extract frames from videos.
- Resize frames to the required input size (64x64).
- Prepare sequences of frames as input to the model.
- **Note:** Make sure to change the directories to match your folder containing the **Brawl** and **Peace** folders.

### 2. Train the Model
The model is a SlowFast-inspired 3D CNN designed for video classification. It consists of two pathways
- Slow Pathway: Processes every α=4 frames, capturing high-level temporal semantics with 3D convolutions and MaxPooling layers.
- Fast Pathway: Processes all frames but with shallower filters, focusing on fine-grained motion details.

Both pathways undergo feature extraction with Conv3D + BatchNorm + Pooling, then fuse via 1x1x1 convolutions. The fused features pass through 3D residual blocks, Global Average Pooling, and a Dense classifier. The model is optimized with AdamW and mixed precision training for efficiency.

### 3. Evaluate the Model

- The model is evaluated using precision, recall, and F1-score.
- The classification report is as follows:

  ```
            precision    recall  f1-score   support

            0       0.91      0.90      0.90       200
            1       0.90      0.91      0.91       200

    accuracy                           0.91       400
    macro avg       0.91      0.91      0.90       400
    weighted avg    0.91      0.91      0.90       400
  ```

- The final model achieves an **F1-score of 0.91**.

### 4. Save and Use the Model

- The trained model is saved as a `final_model.keras` file for later use.
- Load the model to classify new videos.


## Bonus Task

### Dependencies
Before running the notebook, install the required dependencies:

```bash
pip install -r requirements_bonus.txt
```

### Running the Code (`code(bonus).ipynb`)

- Run the notebook in order.
- Add your own video to see the code in action.
