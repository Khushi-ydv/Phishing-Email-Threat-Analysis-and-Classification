# Phishing Email Threat Analysis and Classification

**AI in Cyber Security — Unit 1 Mini Project**
Khushi (2301730308)

This project uses machine learning and a basic neural network to detect **phishing emails**. Phishing is one of the most common cyber attacks: an attacker sends a fake email that looks like it comes from a trusted source, to trick the victim into clicking a malicious link, giving away a password, or downloading malware.

## Project Tasks

The notebook covers all four lab tasks in order:

1. **Workspace Bootstrap and Environment Setup** — installs and imports the Python libraries.
2. **Cyber Security Threat Landscape Analysis** — explores the data, builds simple phishing indicators from the email text (links, urgent words, money words, exclamation marks, length), and cleans the data by removing empty and duplicate emails.
3. **Basic Machine Learning-Based Threat Classification** — TF-IDF text features → TruncatedSVD → **Random Forest**.
4. **Introduction to Deep Learning** — the same features → **MLPClassifier**, a feed-forward Artificial Neural Network.

The two models are then compared with accuracy, precision, recall, F1-score, ROC-AUC, PR-AUC, confusion matrices, the number of missed phishing emails, and training time.

## Dataset

[Phishing Email Detection — Kaggle](https://www.kaggle.com/datasets/subhajournal/phishingemails) (`Phishing_Email.csv`)

| Column | Description |
|---|---|
| `Email Text` | Full body of the email |
| `Email Type` | `Safe Email` or `Phishing Email` |

- 18,650 emails in total: 11,322 safe and 7,328 phishing
- 17,535 emails remain after removing empty and duplicate emails
- Target used in the notebook: `label` = **1 for Phishing**, **0 for Safe**

## Key Findings from EDA

| Indicator | Safe emails | Phishing emails |
|---|---|---|
| Contains an urgent word (verify, password, bank, …) | 20.7% | 39.1% |
| Contains a money word (free, win, $, …) | 26.0% | 55.3% |
| Contains an exclamation mark | 21.8% | 57.9% |
| Contains a link | 39.6% | 34.3% |

Phishing emails rely heavily on pressure and fake offers. Links alone are not a strong sign, because many safe emails also contain links.

## Results

Test set: 3,507 emails (stratified 80/20 split).

| Model | Accuracy | Precision | Recall | F1-Score | ROC-AUC | Missed Phishing |
|---|---|---|---|---|---|---|
| Random Forest | 0.974 | 0.964 | 0.965 | 0.965 | 0.996 | 46 |
| MLPClassifier | 0.979 | 0.965 | 0.979 | 0.972 | 0.997 | 28 |

Both models detect phishing emails very well. The MLP misses fewer phishing emails, which matters most in cyber security, because every missed phishing email is an attack that reaches the user.

## Repository Files

| File | Description |
|---|---|
| `AI_Cybersecurity_Unit1_Mini_Project_Khushi.ipynb` | Main notebook with code, outputs, and explanations |
| `Phishing_Email.csv` | Dataset |
| `requirements.txt` | Python libraries needed |

## How to Run

**Google Colab**
1. Open the notebook in Colab.
2. Upload `Phishing_Email.csv` to the Colab session.
3. Run all cells.

**Locally**
```bash
git clone https://github.com/Khushi-ydv/Phishing-Email-Threat-Analysis-and-Classification.git
cd Phishing-Email-Threat-Analysis-and-Classification
pip install -r requirements.txt
jupyter notebook AI_Cybersecurity_Unit1_Mini_Project_Khushi.ipynb
```

## Tech Stack

Python · Pandas · NumPy · Scikit-learn · Matplotlib · Seaborn
