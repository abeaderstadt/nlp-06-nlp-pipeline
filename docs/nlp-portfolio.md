# NLP Portfolio: Web Mining and Applied NLP
**Author:** [Alissa Beaderstadt](https://github.com/abeaderstadt)<br>
**Course:** Web Mining and Applied NLP<br>
**Date:** 04/16/2026<br>

---

## Overview
This portfolio brings together the NLP work I’ve built throughout this course, focusing on turning messy, real-world text into something structured and usable.<br>

Across these projects, I worked with web pages, APIs, and domain-specific datasets, building EVTL pipelines to extract, clean, and analyze text data. I also started incorporating more advanced NLP features like keyword extraction and domain-specific scoring, especially for biomedical and toxicology-related text.<br>

Overall, my goal was not just to process text, but to make it easier to interpret, analyze, and reuse for analysis.<br>

---

## Key Projects

| Project | Description | Skills | Link |
|--------|------------|--------|------|
| Project 6: NLP Pipeline with spaCy | End-to-end pipeline combining web scraping, preprocessing, and NLP analysis | spaCy, pipeline design, feature engineering | [View Repo](https://github.com/abeaderstadt/nlp-06-nlp-pipeline) |
| Project 5: Biomedical Web Pipeline | Extracted and analyzed arXiv abstracts with domain-specific scoring | BeautifulSoup, text cleaning, domain NLP | [View Repo](https://github.com/abeaderstadt/nlp-05-web-documents) |
| Project 4: API JSON Pipeline | Built pipeline for structured API data with validation and feature creation | API handling, JSON parsing, data validation | [View Repo](https://github.com/abeaderstadt/nlp-04-api-text-data) |

---

## 1. NLP Techniques Implemented

Across these projects, I used a mix of NLP techniques to process and analyze text data:<br>

- **Tokenization**
  - Converted raw text into structured tokens across web, API, and corpus-based datasets.
  - This was one of the first steps in every project and helped make the text easier to work with downstream.
  - Evidence:
    - Web scraping notebook: [web_words_beaderstadt.ipynb](https://github.com/abeaderstadt/nlp-01-getting-started/blob/main/notebooks/web_words_beaderstadt.ipynb)
    - Text preprocessing notebook: [text_preprocessing_beaderstadt.ipynb](https://github.com/abeaderstadt/nlp-02-text-preprocessing/blob/main/notebooks/text_preprocessing_beaderstadt.ipynb)
    - Corpus exploration notebook: [nlp_corpus_explore_beaderstadt.ipynb](https://github.com/abeaderstadt/nlp-03-text-exploration/blob/main/notebooks/nlp_corpus_explore_beaderstadt.ipynb)

- **Frequency Analysis (Unigrams & Bigrams)**
  - Computed word and phrase frequencies to identify dominant patterns and themes in text.
  - I used this as a quick way to sanity-check whether my cleaning steps were actually improving the data.
  - Evidence:
    - Frequency visualization (Project 6): [top tokens chart](https://github.com/abeaderstadt/nlp-06-nlp-pipeline/blob/main/data/processed/beaderstadt_top_tokens.png)
    - Bigram analysis output: [top bigrams chart](https://github.com/abeaderstadt/nlp-06-nlp-pipeline/blob/main/data/processed/beaderstadt_top_bigrams.png)

- **Text Cleaning and Normalization**
  - Applied lowercasing, punctuation removal, stopword filtering, and custom cleaning (e.g., hyphen splitting, HTML noise removal, API artifact cleanup).
  - Cleaning made a huge difference when working with HTML, where navigation text can dominate results if not removed.
  - Evidence: preprocessing pipelines and transformation stages

- **Feature Engineering**
  - Designed and implemented derived features including:
    - token length and average word length
    - word count and content length categories
    - metadata flags (e.g., `has_author`)
    - domain-specific scores (e.g., `bio_tox_relevance_score`)
  - I especially focused on creating features that made the data more interpretable, not just more complex.
  - Evidence: Transformation pipeline (web NLP): [stage03_transform_beaderstadt.py](https://github.com/abeaderstadt/nlp-05-web-documents/blob/main/src/nlp/stage03_transform_beaderstadt.py)

- **Co-occurrence and Context Analysis**
  - Analyzed relationships between words using context windows and bigram modeling.
  - Increasing the context window helped reveal more meaningful relationships between terms.
  - Evidence: co-occurrence analysis and [bigram outputs](https://github.com/abeaderstadt/nlp-06-nlp-pipeline/blob/main/data/processed/beaderstadt_top_bigrams.png)

- **Keyword Extraction**
  - Extracted meaningful terms from structured text after stopword filtering.
  - Removing stopwords here made the output much more representative of the actual content.
  - Evidence: `top_keywords` output fields

- **Web Scraping and API Processing**
  - Extracted text from HTML pages using BeautifulSoup and processed structured JSON from APIs.
  - This required handling very different data formats, which made the pipeline design more important.
  - Evidence:
    - Web pipeline: [pipeline_web_html.py](https://github.com/abeaderstadt/nlp-05-web-documents/blob/main/src/nlp/pipeline_web_html.py)
    - API pipeline: [pipeline_api_json.py](https://github.com/abeaderstadt/nlp-04-api-text-data/blob/main/src/nlp/pipeline_api_json.py)

- **Advanced NLP with spaCy**
  - Used spaCy for tokenization, stopword removal, and linguistic preprocessing.
  - This made the pipeline more efficient and consistent compared to manual preprocessing.
  - Evidence: [stage03_transform_beaderstadt.py](https://github.com/abeaderstadt/nlp-06-nlp-pipeline/blob/main/src/nlp/stage03_transform_beaderstadt.py)

---

## 2. Systems and Data Sources

I worked with multiple types of data sources:<br>

- **Web Pages (HTML)**
  - Wikipedia article (Shih Tzu breed)
  - arXiv abstracts (biomedical AI and toxicity prediction)

- **APIs (JSON)**
  - NewsAPI (live news article data with nested JSON structure)

- **Text Datasets**
  - Custom toxicology lab notes: [text_data_beaderstadt.txt](https://github.com/abeaderstadt/nlp-02-text-preprocessing/blob/main/data/text_data_beaderstadt.txt)
  - Structured corpus + NIOSH dataset: [corpus analysis notebook](https://github.com/abeaderstadt/nlp-03-text-exploration/blob/main/notebooks/nlp_corpus_explore_beaderstadt.ipynb)

**Data Challenges:**

- **Noisy and unstructured text**
  - The raw HTML included navigation elements (e.g., "main", "menu", "sidebar") that introduced noise.
  - I handled this by removing non-content sections and filtering navigation-related terms during preprocessing.

- **General text cleaning and validation**
  - Required punctuation removal, casing normalization, and stopword filtering.
  - I also validated inputs by checking for empty records, duplicates, and formatting issues before processing.

- **Handling different data structures**
  - JSON data included nested fields that required careful parsing.
  - Some fields were inconsistent or missing (e.g., author), which required additional validation and feature engineering.

- **Domain-specific adjustments**
  - Custom toxicology text required tailored stopword filtering.
  - I also created labeled categories (Exposure, Guidance, Definition, Regulatory) to support comparison.
  - Biomedical relevance required custom keyword weighting to better capture meaningful signals.

---

## 3. Pipeline Structure (EVTL)

My projects followed a structured EVTL pipeline:<br>

- **Extract**
  - Retrieved data from HTML pages, APIs, and local text files.
  - Evidence:
    - Extraction steps across notebooks
    - Extract stage script: [stage01_extract.py](https://github.com/abeaderstadt/nlp-06-nlp-pipeline/blob/main/src/nlp/stage01_extract.py)

- **Validate**
  - Performed checks for structure, missing values, duplicates, and formatting issues.
  - For example, I compared raw vs cleaned word counts to confirm preprocessing was working as expected.
  - Evidence:
    - Validation steps across notebooks
    - Validation script: [stage02_validate_beaderstadt.py](https://github.com/abeaderstadt/nlp-05-web-documents/blob/main/src/nlp/stage02_validate_beaderstadt.py)

- **Transform**
  - Applied NLP preprocessing and feature engineering including tokenization, cleaning, and derived feature creation.
  - This ended up being one of the most useful parts of the pipeline, especially once I started applying it to new datasets and refining both the cleaning steps and feature logic.
  - Evidence:
    - Corpus notebook: [nlp_corpus_explore_beaderstadt.ipynb](https://github.com/abeaderstadt/nlp-03-text-exploration/blob/main/notebooks/nlp_corpus_explore_beaderstadt.ipynb)
    - Transformation pipeline: [stage03_transform_beaderstadt.py](https://github.com/abeaderstadt/nlp-06-nlp-pipeline/blob/main/src/nlp/stage03_transform_beaderstadt.py)

- **Analyze**
  - Computed frequency distributions, co-occurrence patterns, and domain-specific signals.
  - Evidence:
    - Processed dataset: [beaderstadt_processed.csv](https://github.com/abeaderstadt/nlp-06-nlp-pipeline/blob/main/data/processed/beaderstadt_processed.csv)

- **Load**
  - Saved outputs to CSV files and visualizations for downstream analysis.
  - Evidence:
    - Processed outputs: [processed data folder](https://github.com/abeaderstadt/nlp-06-nlp-pipeline/tree/main/data/processed)

---

## 5. Insights

My analysis revealed several meaningful insights:<br>

![Top Tokens Example](https://github.com/abeaderstadt/nlp-06-nlp-pipeline/blob/main/data/processed/beaderstadt_top_tokens.png)

This visualization shows how quickly dominant terms emerge after cleaning, which helped confirm that the preprocessing steps were working as intended.

### Data Quality and Cleaning
- Removing noise (especially HTML navigation text and API artifacts) made a huge difference because those terms were dominating frequency results before cleaning.
- Validation steps helped ensure the dataset was consistent and reliable before analysis.

### Text Patterns and Structure
- Frequent terms aligned with expected domain vocabulary (e.g., lab terms, breed traits).
- Token distributions and category comparisons showed clear structural differences in the data.

### Context and Meaning
- Increasing the context window improved co-occurrence insights.
- Bigram analysis helped capture more meaningful phrase-level patterns.

### Feature Engineering and Signals
- Word count and average word length were useful for estimating text complexity.
- Domain-specific scoring (biomedical/toxicology) provided a more meaningful way to interpret relevance.
  - Evidence: [Processed output with bio_tox_relevance_score](https://github.com/abeaderstadt/nlp-05-web-documents/blob/main/data/processed/beaderstadt_processed.csv)

### Pipeline and Reusability
- Structuring the workflow as an EVTL pipeline made the process more modular and reusable.
- In most cases, I was able to reuse the pipeline on new data by just changing the input source (e.g., URL).

---

## Final Notes

This portfolio reflects my progression from basic text preprocessing to building more structured, reusable NLP pipelines. Moving forward, I’m interested in extending this work by incorporating machine learning models for tasks like classification and prediction, especially in areas like biomedical text analysis.
