# DAiSEE_Competition
unbalanced dataset

leaderboard https://tasneem-mselim.github.io/DAiSEE_Competition/

# Video Engagement Classification Challenge (DAiSEE Features)

## 📌 Overview

This repository hosts the **Video Engagement Classification Challenge**, a deep learning competition based on features extracted from the **DAiSEE** videos. Participants are required to design and train **deep learning models** (e.g., 1D-CNN, LSTM/GRU, Transformer) to classify each video into one of **four engagement levels** using the frame-level features extracted from it.

## Difficulty level

Each video is provided as a **sequence of ~300 frames with ~670 features per frame**, so models must learn temporal patterns from high-dimensional, noisy facial and gaze signals rather than from a single image.

## 🏆 Leaderboard

- Leaderboard scores are automatically updated based on accuracy.
- View the live leaderboard:
👉 **[Leaderboard](LEADERBOARD_LINK_HERE)**

---

## 🧠 Task Description

* Each CSV file represents **one video**.
* Each row in a CSV is **one video frame**, and each column is an extracted feature (gaze, eye landmarks, head pose, face landmarks, action units, ...).
* Each video belongs to **one of 4 classes**: `0`, `1`, `2`, `3`.

### Objective

Train a model that accurately predicts the class label of **unlabeled test videos**, using:

* The frame-level features in each video CSV
* The temporal order of the frames

---

## 📊 Dataset Details

The dataset is derived from the **DAiSEE** video dataset. Features were extracted from every video and stored as one CSV file per video.

| Property          | Value                                                                  |
| ----------------- | ---------------------------------------------------------------------- |
| Samples           | One CSV file per video                                                 |
| Frames per video  | ~300 (rows)                                                            |
| Features          | ~670 numeric columns per frame                                         |
| Classes           | 4 (`0`, `1`, `2`, `3`)                                                 |
| Train videos      | NUMBER_OF_TRAIN_VIDEOS                                                 |
| Validation videos | NUMBER_OF_VALIDATION_VIDEOS                                            |
| Test videos       | NUMBER_OF_TEST_VIDEOS (labels hidden)                                  |

### Feature columns

Each CSV contains:

* **Meta columns:** `frame`, `face_id`, `timestamp`, `confidence`, `success`
* **Gaze:** gaze direction vectors and angles
* **Eye landmarks:** 2D / 3D eye region landmarks
* **Head pose:** head location and rotation
* **Face landmarks:** 2D / 3D facial landmarks
* **Action units:** facial action unit intensities and presence

> Column names may contain leading spaces; strip them when loading (`df.columns = df.columns.str.strip()`).

---

### Public Files

##### These files are available in the dataset folder for participants:

```
Dataset/
├── train/
│   ├── 0/   *.csv      (videos of class 0)
│   ├── 1/   *.csv
│   ├── 2/   *.csv
│   └── 3/   *.csv
├── validate/
│   ├── 0/   *.csv
│   ├── 1/   *.csv
│   ├── 2/   *.csv
│   └── 3/   *.csv
└── test/
    ├── prediction.csv  (template: list of test ids, empty labels)
    └── ...   *.csv     (videos to be classified, no labels)
```

1- `train/` — labeled videos, the class is the name of the sub-folder

2- `validate/` — labeled videos for validation and model selection

3- `test/` — unlabeled videos to classify

4- `test/prediction.csv` — template containing the test ids

### Private Files

- Test labels → Hidden ground-truth data used for automatic evaluation

---

## 📝 How to Submit Your Results

Follow the steps below to submit your predictions to the competition leaderboard.

---

### Step 1: Fork the Repository

### Step 2: Navigate to Your Forked Repository

### Step 3: Go to the Submission Folder

### Step 4: Prepare the prediction .csv locally

#### 📝 Submission Format

Participants must submit a CSV file named **`prediction.csv`** with the following format:

```csv
id,label
8264120240,2
8264120241,0
8264120242,3
...
```

#### Rules

* `id` must match the ids in the provided `test/prediction.csv` (the video file name without `.csv`)
* `label` must be an integer in `{0, 1, 2, 3}`
* Every test id must have exactly one label

### Step 5: Place Your Submission in the Submission Folder

Upload your `prediction.csv` to the submission folder in your forked repo.

> If the competition uses encrypted submissions, first run:
> `python encrypt_submission.py prediction.csv prediction.enc public_key.pem`
> and upload both `prediction.enc` and `prediction.enc.key` instead of the CSV.

### Step 6: Create a Pull Request

✅ Your submission will be reviewed and evaluated, and the results will be added to the leaderboard.

**Only one submission** is allowed for each participant/team. Subsequent submissions will be automatically rejected.

---

## 📈 Evaluation Metric

Submissions are evaluated using:

* **Accuracy**

Evaluation is performed on a **hidden test set** to prevent data leakage.

---

## ✅ Allowed Methods

* Any **deep learning** architecture (CNN, RNN/LSTM/GRU, Transformer, hybrid models)
* Feature selection, preprocessing, and normalization
* Padding / cropping / resampling of the frame sequences
* Data augmentation
* Hyperparameter tuning

## ❌ Not Allowed

* Using test labels
* Modifying test ids
* Training on test videos
* Using the original DAiSEE labels or raw videos of the test set

---

## 🏆 Baseline

A starter notebook (`classify_video_features.ipynb`) with a simple **1D-CNN** in Keras is provided as the baseline. Participants are encouraged to improve upon it using:

* Deeper or temporal architectures (LSTM, GRU, Transformer)
* Attention mechanisms
* Regularization techniques (dropout, batch norm, early stopping)
* Class balancing and data augmentation

---

## 📚 References

* Gupta, A., D'Cunha, A., Awasthi, K., & Balasubramanian, V. (2016). *DAiSEE: Towards User Engagement Recognition in the Wild*. arXiv:1609.01885.
* Baltrusaitis, T., Zadeh, A., Lim, Y. C., & Morency, L.-P. (2018). *OpenFace 2.0: Facial Behavior Analysis Toolkit*. IEEE FG.

---

## 👩‍💻 Organizer

**YOUR NAME**
YOUR TITLE / AFFILIATION
If you face issues with the repository or evaluation:
- Contact me at YOUR_EMAIL

---

Good luck, and happy learning 🚀

