# ICG-BreakingBias2-DataWizards

This repository contains a deep learning model that classifies videos into two categories: **Brawl (Violent)** and **Peace (Non-Violent)**. The model is implemented in an IPython Notebook and utilizes deep learning techniques for video classification.

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
- The model architecture includes MobileNet for feature extraction followed by LSTMs for sequence learning.

### 3. Evaluate the Model

- The model is evaluated using precision, recall, and F1-score.
- The classification report is as follows:

  ```
            precision    recall  f1-score   support

            0       0.80      0.95      0.87       200
            1       0.94      0.76      0.84       200

    accuracy                           0.85       400
    macro avg       0.87      0.85      0.85       400
    weighted avg    0.87      0.85      0.85       400
  ```

- The final model achieves an **F1-score of 0.85**.

### 4. Save and Use the Model

- The trained model is saved as a `model.keras` file for later use.
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
