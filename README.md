# SMS/Email Spam Detection App

A simple Streamlit web app that classifies a message as **Spam** or **Not Spam** using a pre-trained machine learning model and a TF-IDF vectorizer.

## Features

- Text preprocessing with NLTK (lowercasing, tokenization, stopword removal, stemming)
- TF-IDF vectorization using a saved `vectorizer.pkl`
- Spam prediction using a saved `model.pkl`
- Interactive web UI built with Streamlit

## Project Structure

```text
sms-spam-detection/
├── app.py             # Streamlit application
├── model.pkl          # Trained classification model
├── vectorizer.pkl     # Fitted TF-IDF vectorizer
└── README.md          # Project documentation
```

## Requirements

- Python 3.10+ (project tested in a local virtual environment)
- Packages:
  - `streamlit`
  - `nltk`
  - `scikit-learn`

> Note: `model.pkl` and `vectorizer.pkl` were created with specific library versions. If you see pickle/unpickle compatibility errors, install compatible versions of the libraries used to train/export the model.

## Setup

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd sms-spam-detection
   ```

2. **Create and activate a virtual environment** (recommended)
   - Windows (PowerShell):
     ```powershell
     python -m venv .venv
     .\.venv\Scripts\Activate.ps1
     ```
   - macOS/Linux:
     ```bash
     python3 -m venv .venv
     source .venv/bin/activate
     ```

3. **Install dependencies**
   ```bash
   pip install streamlit nltk scikit-learn
   ```

4. **Download required NLTK data** (first run only)
   ```bash
   python -c "import nltk; nltk.download('punkt'); nltk.download('punkt_tab'); nltk.download('stopwords')"
   ```

## Run the App

From the project directory:

```bash
streamlit run app.py
```

Then open the local URL shown in the terminal (usually [http://localhost:8501](http://localhost:8501)).

## Usage

1. Enter an SMS or email message in the input box.
2. Click **Predict**.
3. The app displays:
   - **Spam** — if the model predicts spam
   - **not spam** — if the model predicts ham/not spam

## How It Works

1. **Preprocess text** (`transform_text` in `app.py`)
   - Convert to lowercase
   - Tokenize text
   - Remove non-alphanumeric tokens
   - Remove English stopwords and punctuation
   - Apply Porter stemming
2. **Vectorize** the processed text with the saved TF-IDF vectorizer
3. **Predict** using the saved classifier
4. **Display** the result in the Streamlit UI

## Notes

- This repository includes pre-trained artifacts (`model.pkl`, `vectorizer.pkl`). Retraining code/data is not included here.
- For GitHub uploads, avoid committing local environment folders (e.g. `.venv/`, `__pycache__/`, `.idea/`) by adding a `.gitignore`.
- If you deploy this app, ensure NLTK resources are available in the deployment environment.

## Example Messages to Try

- Spam-like: `Congratulations! You've won a $1000 gift card. Call now to claim your prize.`
- Ham-like: `Hey, are we still meeting at 5 pm today?`
