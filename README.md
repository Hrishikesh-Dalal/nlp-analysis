# Edmunds Car Reviews NLP Analysis (NLTK + Transformers)

This project analyzes Edmunds car reviews using classic NLP techniques with NLTK and modern sentiment analysis with Hugging Face Transformers. It downloads the dataset from Kaggle, performs tokenization, stop-word filtering, stemming, POS tagging, chunking/chinking, named entity recognition, concordance and dispersion visualizations, frequency distributions, and runs a sentiment pipeline over example reviews.

## Contents
- `NLP_Analysis.ipynb`: End-to-end notebook performing the analysis and visualizations.

## Prerequisites
- Python 3.9+ (recommended 3.10+)
- VS Code with Python and Jupyter extensions
- Internet access (for NLTK data and model downloads)
- Kaggle account and API token (`kaggle.json`)

## Setup (Windows)
1. Create and activate a virtual environment (optional but recommended):

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

2. Install required packages:

```powershell
pip install nltk kaggle pandas matplotlib transformers
```

3. Configure Kaggle credentials:
	- Place your `kaggle.json` in `%USERPROFILE%\.kaggle\kaggle.json` (create the folder if needed).
	- Alternatively set `KAGGLE_CONFIG_DIR` to your chosen folder containing `kaggle.json`.

```powershell
$env:KAGGLE_CONFIG_DIR = "$env:USERPROFILE\.kaggle"
```

## Download the Dataset
Use the Kaggle CLI to download and unzip the dataset used in the notebook:

```powershell
kaggle datasets download -d sourabhsabharwal/sentiment-analysis-car-reviews --unzip
```

After download, verify `Car_Reviews_Database.csv` exists in the workspace root.

## Run the Notebook
1. Open the workspace in VS Code.
2. Open `NLP_Analysis.ipynb`.
3. Select a Python kernel (your virtual environment if created).
4. Run cells top-to-bottom. The notebook will:
	- Install or import libraries.
	- Download required NLTK resources (`punkt`, `stopwords`, `averaged_perceptron_tagger`, `wordnet`, `maxent_ne_chunker`, `words`).
	- Load `Car_Reviews_Database.csv` (with fallback to `latin-1` if UTF-8 fails).
	- Perform the analysis steps and show textual outputs and plots.

## What the Notebook Does
- Tokenization: Sentence and word tokenization of the combined review text.
- Stop Words: Removes common English stop words and non-alpha tokens.
- Stemming: Applies `PorterStemmer` to filtered words.
- POS Tagging: Tags parts of speech for filtered words.
- Lemmatization: Uses `WordNetLemmatizer` on filtered words.
- Chunking/Chinking: Extracts and refines noun phrase chunks with custom grammars.
- Named Entity Recognition (NER): Identifies named entities from POS-tagged tokens.
- Concordance: Shows concordance lines for words like “good”.
- Dispersion Plot: Visualizes relative positions of key terms.
- Frequency Distributions: Top terms, lemmatized terms, POS tags, and named entities.
- Sentiment Analysis: Runs Hugging Face `pipeline("sentiment-analysis")` on sample reviews.

## Example Commands
Common actions you may run outside the notebook:

```powershell
# In a fresh shell
cd C:\Users\1010h\OneDrive\Desktop\Development\nlp-analysis
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install nltk kaggle pandas matplotlib transformers
$env:KAGGLE_CONFIG_DIR = "$env:USERPROFILE\.kaggle"
kaggle datasets download -d sourabhsabharwal/sentiment-analysis-car-reviews --unzip
```

## Troubleshooting
- Kaggle 401/403 or “Unauthorized”: Ensure `kaggle.json` is in `%USERPROFILE%\.kaggle` and holds valid credentials. If using a custom location, set `KAGGLE_CONFIG_DIR` accordingly.
- UnicodeDecodeError on CSV: The notebook already falls back to `latin-1` if UTF-8 fails.
- Missing NLTK data errors: Run `import nltk; nltk.download("punkt")` etc. as prompted in the notebook.
- Transformers model download issues: Ensure internet access; the first pipeline use downloads the model.

## Notes
- Some NLTK resource names may vary across versions; the notebook attempts compatible downloads when needed.
- Plots (matplotlib) render inline in the notebook.

## Credits
Hrishikesh Dalal