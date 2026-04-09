# Restaurant Review Sentiment Analysis System

A sentiment analysis pipeline built for small food businesses, designed to automatically classify customer reviews and generate appropriate responses. Built using the Zomato reviews dataset.

---

## What It Does

This project takes a customer review and star rating as input and classifies it into one of three categories — **Happy**, **Mixed**, or **Angry** — then triggers an automated response based on that classification:

- **Happy Review** → Sends a thank-you message to the customer
- **Mixed Review** → Sends a thank-you and invites the customer to share more detail to improve their next experience
- **Angry Review** → Flags a manager for human intervention

---

## How It Works

### Step 1 — Sentiment Scoring with RoBERTa
Each review is first passed through the `cardiffnlp/twitter-roberta-base-sentiment` model from Hugging Face, which returns a sentiment label (Positive, Neutral, Negative) and a confidence score.

### Step 2 — Smart Categorization Logic
A hybrid categorization function combines the RoBERTa output with the star rating using a confidence threshold of 0.80:

- If sentiment is **Neutral** → always classified as Mixed
- If confidence **≥ 0.80** → trust the sentiment score (Positive = Happy, Negative = Angry)
- If confidence **< 0.80** → fall back to star rating (4–5 = Happy, 3 = Mixed, 1–2 = Angry)

This fallback approach handles ambiguous short reviews (e.g. "nice", "okay") more reliably.

### Step 3 — Model Training & Comparison
The categorized labels were used to train and compare two deep learning classifiers:

| Model | Architecture | Best Validation Accuracy |
|---|---|---|
| Baseline | Embedding + GlobalAveragePooling + Dense | 78.28% |
| Improved (CNN) | Embedding + Conv1D + MaxPooling + Dropout + Dense | 78.83% |

Both models were trained on 4,931 reviews and validated on 548. The CNN model was selected for the final response system.

**Dataset breakdown:**
- Angry Reviews: 1,993
- Happy Reviews: 1,968
- Mixed Reviews: 1,518

### Step 4 — Evaluation
The CNN model was evaluated using precision, recall, and F1-score across all three classes:

| Class | Precision | Recall | F1-Score |
|---|---|---|---|
| Happy | 0.75 | 0.83 | 0.79 |
| Mixed | 0.77 | 0.76 | 0.77 |
| Angry | 0.84 | 0.77 | 0.80 |

Overall accuracy: **78.83%** on 548 validation samples (431 correct, 117 errors, 21.35% error rate).

The most common misclassification was short or ambiguous reviews being predicted as Mixed — expected behavior given limited context in very brief reviews.

### Step 5 — Automated Response System
The final system takes a live review + star rating as input, runs it through the full pipeline (RoBERTa → categorization → CNN), and generates the appropriate automated response or manager alert.

---

## Tech Stack

- **Python 3** (Google Colab)
- **TensorFlow / Keras** — model building and training
- **Hugging Face Transformers** — `cardiffnlp/twitter-roberta-base-sentiment` (RoBERTa)
- **Pandas / NumPy** — data handling
- **NLTK** — text preprocessing and stopword removal
- **Matplotlib** — visualizations
- **Scikit-learn** — train/test split, classification report, confusion matrix

---

## Dataset

Zomato restaurant reviews dataset containing customer reviews paired with star ratings (1–5). Reviews were cleaned, preprocessed, and labeled using the hybrid RoBERTa + star rating categorization system described above.

---

## Key Design Decisions

- **Confidence threshold fallback:** Short reviews like "nice" or "okay" often get low confidence scores from RoBERTa. Rather than misclassifying these, the system falls back to star rating as a reliable signal.
- **Three-class framing:** Rather than binary positive/negative, the Mixed category captures nuanced feedback and triggers a more thoughtful response designed to retain customers.
- **Manager escalation:** Angry reviews are intentionally not handled by automation — the system flags them for a human, recognizing that unhappy customers need genuine attention.
