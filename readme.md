From Understanding Humans → To Guiding Them

## Overview

This project builds a machine learning system that understands a user's emotional state from reflection text and contextual signals, then recommends meaningful actions to guide them toward a better mental state.

The system processes short user reflections collected after immersive sessions (forest, ocean, rain, mountain, café) along with contextual signals such as sleep, stress, energy level, and time of day.

The model predicts:

* **Emotional State**
* **Emotion Intensity**
* **Confidence Score**
* **Uncertainty Flag**

Based on these predictions, a **decision engine** recommends:

* **What the user should do**
* **When they should do it**

---

# Setup Instructions

## 1. Clone the repository

```
git clone <repository_url>
cd PROJECT1
```

## 2. Install dependencies

```
pip install -r requirements.txt
```

## 3. Run the notebook or script

 open and run the Jupyter/Kaggle notebook.

---

# Approach

The system follows a structured pipeline:

```
User Reflection Text
        ↓
Text Preprocessing
        ↓
TF-IDF Feature Extraction
        ↓
Metadata Feature Encoding
        ↓
Emotion Prediction Model
        ↓
Intensity Prediction Model
        ↓
Confidence & Uncertainty Detection
        ↓
Decision Engine
        ↓
Recommended Action & Timing
```

The system integrates both **textual information** and **contextual signals** to make informed decisions.

---

# Feature Engineering

Two types of features were used:

## 1. Text Features

The `journal_text` field was cleaned and converted into numerical features using **TF-IDF vectorization**.

Text preprocessing steps included:

* Lowercasing
* Removing URLs
* Removing punctuation
* Removing special characters

TF-IDF converts reflections into a sparse numerical representation capturing important emotional keywords.

Example emotional indicators:

* calm
* lighter
* drained
* focused
* quiet

## 2. Metadata Features

Contextual signals were also included:

* ambience_type
* duration_min
* sleep_hours
* energy_level
* stress_level
* time_of_day
* previous_day_mood
* face_emotion_hint
* reflection_quality

Categorical features were encoded using **one-hot encoding**.

These features help capture the user's **physiological and situational context**.

---

# Model Choice

Two RandomForest models were used:

## Emotional State Model

Predicts one of the following classes:

* calm
* focused
* mixed
* neutral
* overwhelmed
* restless

RandomForest was chosen because:

* It handles mixed feature types well
* It is robust to noise
* It performs well on tabular data
* It requires minimal tuning

## Intensity Model

Predicts emotional intensity on a **1–5 scale**.

This was implemented as a **classification task**.

---

# Uncertainty Modeling

To make the system aware of uncertainty, prediction probabilities were used.

```
confidence = max(predicted_class_probability)
```

If:

```
confidence < 0.60
```

the prediction is flagged as **uncertain**.

This ensures the system does not make overly confident recommendations when signals are weak or ambiguous.

---

# Decision Engine

A rule-based decision layer determines:

* **What the user should do**
* **When they should do it**

Inputs used:

* predicted emotion
* emotion intensity
* stress level
* energy level
* time of day

Example logic:

```
High stress → breathing exercise
Low energy → rest
Calm + high energy → deep work
Restless → movement
```

Timing recommendations include:

* now
* within_15_min
* later_today
* tonight
* tomorrow_morning

---

# How to Run the Project

1. Install dependencies:

```
pip install -r requirements.txt
```

2. Run the training pipeline notebook or script.

3. The system will generate:

```
predictions.csv
```

This file contains:

* predicted_state
* predicted_intensity
* confidence
* uncertain_flag
* what_to_do
* when_to_do

---

# Project Outputs

The final prediction file includes:

| Column              | Description                          |
| ------------------- | ------------------------------------ |
| id                  | User identifier                      |
| predicted_state     | Predicted emotional state            |
| predicted_intensity | Emotion intensity (1–5)              |
| confidence          | Model confidence score               |
| uncertain_flag      | Indicates low-confidence predictions |
| what_to_do          | Recommended action                   |
| when_to_do          | Recommended timing                   |

---

# Future Improvements

Possible improvements include:

* Transformer-based models (BERT / DistilBERT)
* Personalized models based on user history
* Reinforcement learning for adaptive recommendations
* Context-aware emotion understanding

---

# Conclusion

This project demonstrates an end-to-end system that goes beyond prediction by combining **emotion understanding, uncertainty awareness, and decision-making**.

The resulting system is capable of guiding users toward helpful actions based on their emotional and contextual state.
