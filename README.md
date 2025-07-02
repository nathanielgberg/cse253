# 🎵 Symbolic Music Generation

This project was completed for **CSE 253: Machine Learning for Music** at UC San Diego, and explores symbolic music generation using transformer-based and LSTM models trained on MIDI datasets.

## 📌 Overview

The project addresses two key tasks:

- **Task 1: Symbolic – Unconditioned Generation**  
  Train a model to learn a music distribution \( p(x) \) from a dataset and generate new music via sampling.

- **Task 2: Symbolic – Conditioned Generation**  
  Train a model to generate music conditioned on some input \( p(x | \text{input}) \), enabling controlled music generation.

## 🎼 Datasets Used

### MAESTRO (v3.0.0)
- 200+ hours of aligned audio and MIDI recordings from the International Piano-e-Competition.
- Preprocessed with aligned timestamps, trimmed segments, and standardized metadata.
- Already split into train/val/test (80/10/10).

### Lakh MIDI Dataset (LMD)
- Over 176K MIDI files, with rich annotations (tempo, key, time sig., etc.).
- Used for analyzing statistical features and training lightweight symbolic models.

## 🧠 Models

### GPT-2 Transformer (Task 1)
- 8-layer, 768-dim, 12-head autoregressive model.
- Tokenized MIDI using REMI encoding.
- Sampling one token at a time; loss based on cross-entropy over next-token prediction.

### BiLSTM (Task 2)
- Inputs: sequences of pitch, step, and duration.
- Outputs: next pitch (classification), step & duration (regression).
- Loss: weighted combo of cross-entropy and MSE + melodic coherence bonus.

## 📊 Evaluation

We used a combination of **objective metrics**, **musical structure analysis**, and **subjective listening**:

- **Objective**: perplexity, cross-entropy
- **Musical**: melodic coherence, pitch range validity, rhythm consistency, diversity
- **Subjective**: audio sample listening + piano roll visualizations

### Baseline Comparisons
- Compared against random and rule-based MIDI generation.
- Showed stronger melodic and rhythmic consistency across both models.

## 🎧 Samples

You can listen to generated audio samples for both tasks:

- Task 1:
  - Conservative Output
  - Creative Output
- Task 2:
  - Conditioned Generation Output

## 🔍 Key Contributions

- Implemented a full pipeline for MIDI-based symbolic generation: **data prep → training → generation → evaluation → visualization**.
- Introduced **melodic coherence loss** to improve musical structure.
- Developed evaluation metrics tailored to symbolic music (step/pitch/duration validity, entropy, etc.).

## 📚 Related Work

- Compared to models like **Music Transformer**, **MuseNet**, and **MusicVAE**.
- Our method integrates training-time constraints and real-time sampling quality checks (e.g., pitch diversity, interval control), unlike many prior works.

---

> This project is for educational purposes. The datasets used are publicly available under their respective licenses.
