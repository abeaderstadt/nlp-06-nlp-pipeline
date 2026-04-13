# NLP Portfolio: Web Mining and Applied NLP
**Author:** [Alissa Beaderstadt](https://github.com/abeaderstadt)<br>
**Course:** Web Mining and Applied NLP<br>
**Date:** 04/13/2026<br>

---

## Overview
This portfolio showcases my work applying NLP techniques to real-world text data from web pages, APIs, and domain-specific documents. My projects focus on building structured, repeatable pipelines to clean, analyze, and extract meaningful insights from both structured and unstructured data.<br>

A key theme across my work is transforming messy, real-world text into usable datasets and engineering features that improve interpretability and analysis, particularly in technical and biomedical contexts.<br>

---

## Key Project Links
- [Project 6: NLP Pipeline with spaCy](https://github.com/abeaderstadt/nlp-06-nlp-pipeline)
- [Project 5: Biomedical Web Pipeline](https://github.com/abeaderstadt/nlp-05-web-documents)
- [Project 4: API JSON Pipeline](https://github.com/abeaderstadt/nlp-04-api-text-data)

---

## 1. NLP Techniques Implemented

I applied a range of NLP techniques across multiple projects to process and analyze text data:<br>

- **Tokenization**
  - Converted raw text into structured tokens across web, API, and corpus-based datasets.
  - Evidence:
    - Web scraping notebook:[web_words_beaderstadt.ipynb](https://github.com/abeaderstadt/nlp-01-getting-started/blob/main/notebooks/web_words_beaderstadt.ipynb)
    - Text preprocessing notebook:[text_preprocessing_beaderstadt.ipynb](https://github.com/abeaderstadt/nlp-02-text-preprocessing/blob/main/notebooks/text_preprocessing_beaderstadt.ipynb)
    - Corpus exploration notebook:[nlp_corpus_explore_beaderstadt.ipynb](https://github.com/abeaderstadt/nlp-03-text-exploration/blob/main/notebooks/nlp_corpus_explore_beaderstadt.ipynb)

- **Frequency Analysis (Unigrams & Bigrams)**
  - Computed word and phrase frequencies to identify dominant patterns and themes in text.
  - Evidence:
    - Frequency visualization (Project 6)[top tokens chart](https://github.com/abeaderstadt/nlp-06-nlp-pipeline/blob/main/data/processed/beaderstadt_top_tokens.png)
    - Bigram analysis output: [top bigrams chart](https://github.com/abeaderstadt/nlp-06-nlp-pipeline/blob/main/data/processed/beaderstadt_top_bigrams.png)

- **Text Cleaning and Normalization**
  - Applied lowercasing, punctuation removal, stopword filtering, and custom cleaning (e.g., hyphen splitting, HTML noise removal, API artifact cleanup).
  - Evidence: preprocessing pipelines and transformation stages

- **Feature Engineering**
  - Designed and implemented derived features including:
    - token length and average word length
    - word count and content length categories
    - metadata flags (e.g., `has_author`)
    - domain-specific scores (e.g., `bio_tox_relevance_score`)
  - Evidence: Transformation pipeline (web NLP):[stage03_transform_beaderstadt.py](https://github.com/abeaderstadt/nlp-05-web-documents/blob/main/src/nlp/stage03_transform_beaderstadt.py)

- **Co-occurrence and Context Analysis**
  - Analyzed relationships between words using context windows and bigram modeling.
  - Evidence: co-occurrence analysis and [bigram outputs](https://github.com/abeaderstadt/nlp-06-nlp-pipeline/blob/main/data/processed/beaderstadt_top_bigrams.png)

- **Keyword Extraction**
  - Extracted meaningful terms from structured text after stopword filtering.
  - Evidence: `top_keywords` output fields

- **Web Scraping and API Processing**
  - Extracted text from HTML pages using BeautifulSoup and processed structured JSON from APIs.
  - Evidence:
    - Web pipeline:[pipeline_web_html.py](https://github.com/abeaderstadt/nlp-05-web-documents/blob/main/src/nlp/pipeline_web_html.py)
    - API pipeline:[pipeline_api_json.py](https://github.com/abeaderstadt/nlp-04-api-text-data/blob/main/src/nlp/pipeline_api_json.py)

- **Advanced NLP with spaCy**
  - Used spaCy for tokenization, stopword removal, and linguistic preprocessing.
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
  - Custom toxicology lab notes:[text_data_beaderstadt.txt](https://github.com/abeaderstadt/nlp-02-text-preprocessing/blob/main/data/text_data_beaderstadt.txt)
  - Structured corpus + NIOSH dataset:[corpus analysis notebook](https://github.com/abeaderstadt/nlp-03-text-exploration/blob/main/notebooks/nlp_corpus_explore_beaderstadt.ipynb) (categorized text)

**Data Challenges:**
- The raw HTML included navigation text (e.g., "main", "menu", "sidebar") that introduced noise into the dataset.
- I addressed this by removing non-content HTML sections and filtering out common navigation-related words during preprocessing.
- The dataset required cleaning to remove punctuation, normalize casing, and eliminate stop words.
- I validated the dataset by checking for empty inputs, duplicate lines, and formatting inconsistencies before processing.
- The custom dataset required tailored stopword filtering to better match domain-specific language.
- I structured the corpus into labeled categories (Exposure, Guidance, Definition, Regulatory) to enable comparative analysis.
- The JSON structure included nested fields (e.g., articles list) that required careful parsing.
- Some fields were inconsistent or missing (e.g., author), requiring validation and feature engineering.
- The content field included truncated text artifacts (e.g., "[+xxx chars]") that needed cleaning.
- HTML pages required parsing to isolate meaningful content from structural elements.
- Keyword extraction required removing stopwords to avoid noisy or uninformative outputs.
- Domain-specific relevance required custom weighting of biomedical and toxicity-related terms.
- Required additional cleaning for hyphenated terms to improve tokenization quality.
- Needed to balance general NLP processing with domain-specific interpretation (machine learning vs biomedical terms).

---

## 3. Pipeline Structure (EVTL)

My projects followed a structured EVTL pipeline:<br>

- **Extract**
  - Retrieved data from multiple sources including HTML web pages, APIs, and local text files.
  - Evidence:
    - Extraction stage across notebooks
    - Extract stage script:[stage01_extract.py](https://github.com/abeaderstadt/nlp-06-nlp-pipeline/blob/main/src/nlp/stage01_extract.py)

- **Validate**
  - Performed checks for structure, missing values, duplicates, and formatting issues.
  - Example: compared raw vs cleaned word counts; validated JSON schema.
  - Evidence:
    - Validation steps across notebooks
    - Validation script:[stage02_validate_beaderstadt.py](https://github.com/abeaderstadt/nlp-05-web-documents/blob/main/src/nlp/stage02_validate_beaderstadt.py)

- **Transform**
  - Applied NLP preprocessing and feature engineering including tokenization, cleaning, and derived feature creation.
  - Evidence:
    - Corpus notebook:[nlp_corpus_explore_beaderstadt.ipynb](https://github.com/abeaderstadt/nlp-03-text-exploration/blob/main/notebooks/nlp_corpus_explore_beaderstadt.ipynb)
    - Transformation pipeline:[stage03_transform_beaderstadt.py](https://github.com/abeaderstadt/nlp-06-nlp-pipeline/blob/main/src/nlp/stage03_transform_beaderstadt.py)

- **Analyze**
  - Computed frequency distributions, co-occurrence patterns, and domain-specific signals.
  - Evidence:
    - Processed dataset:[beaderstadt_processed.csv](https://github.com/abeaderstadt/nlp-06-nlp-pipeline/blob/main/data/processed/beaderstadt_processed.csv)

- **Load**
  - Saved outputs to CSV files, visualizations, and structured datasets for downstream analysis.
  - Evidence:
  - Processed outputs:[processed data folder](https://github.com/abeaderstadt/nlp-06-nlp-pipeline/tree/main/data/processed)

---

## 4. Signals and Analysis Methods

I computed and analyzed several key signals:<br>

- **Word Frequency**
  - Computed word frequency counts to identify the most common terms in the Shih Tzu article.
  - Identified the most common tokens in the dataset using Polars.
  - Compared dominant tokens across categories.
  - Identified dominant tokens in the abstract.

- **Token Length Distribution**
  - Analyzed the distribution of token lengths using a histogram to better understand text structure.

- **Visualization**
  - Created a bar chart of the top 15 most frequent words to better understand dominant themes.
  - Generated a word cloud to visually summarize term importance.

- **Bigrams**
  - Identified commonly co-occurring word pairs to understand local structure.
  - Captured phrase-level patterns such as "supervised learning".

- **Text Complexity**
  - Measured average word length to estimate technical complexity.

- **Co-occurrence (Context Windows)**
  - Analyzed relationships between words using a sliding window approach.

- **Category Comparison**
  - Visualized token distributions across categories using horizontal bar charts.

- **Word Count Analysis**
  - Measured article length in terms of word count to better represent content depth.

- **Metadata Completeness**
  - Used a `has_author` flag to analyze missing metadata across articles.

- **Content Categorization**
  - Grouped articles into length-based categories to support future analysis and visualization.

- **Keyword Extraction**
  - Identified key terms from abstracts to summarize core topics.

- **Sentiment / Subjectivity**
  - Measured writing formality using a custom scoring system based on pronoun usage.

- **Domain-Specific Scoring**
  - Computed a biomedical/toxicology relevance score using weighted keywords.

- **Domain Signal Analysis**
  - Compared machine learning terms vs biomedical terms to assess thematic focus.

**Evidence:**
- Notebooks (Projects 1-3)
  - Web scraping + frequency analysis:
    [web_words_beaderstadt.ipynb](https://github.com/abeaderstadt/nlp-01-getting-started/blob/main/notebooks/web_words_beaderstadt.ipynb)

  - Text preprocessing pipeline:
    [text_preprocessing_beaderstadt.ipynb](https://github.com/abeaderstadt/nlp-02-text-preprocessing/blob/main/notebooks/text_preprocessing_beaderstadt.ipynb)

  - Corpus exploration + co-occurrence analysis:
    [nlp_corpus_explore_beaderstadt.ipynb](https://github.com/abeaderstadt/nlp-03-text-exploration/blob/main/notebooks/nlp_corpus_explore_beaderstadt.ipynb)

- Processed Data Outputs (Project 4)
  - Cleaned and engineered dataset (CSV output):
    [beaderstadt_processed.csv](https://github.com/abeaderstadt/nlp-04-api-text-data/blob/main/data/processed/beaderstadt_processed.csv)

- Derived NLP Features (Projects 5-6)
  - Web document NLP pipeline outputs:
    - `top_keywords`
    - `formality_score`
    - `bio_tox_relevance_score`
  - spaCy-enhanced frequency + feature outputs:
    - token frequency charts
    - bigram analysis
    - derived linguistic features

---

## 5. Insights

My analysis revealed several meaningful insights:<br>

### Data Quality and Cleaning
- Removing noise (HTML navigation, stopwords, API artifacts) significantly improved analysis quality.
- Validation steps ensured clean, consistent datasets with no duplicates or formatting issues.

### Text Patterns and Structure
- Frequent terms aligned with expected domain vocabulary (e.g., lab terms, breed traits).
- Token distributions and category comparisons revealed clear structural differences in text.

### Context and Meaning
- Increasing context window size improved co-occurrence insights.
- Bigram analysis revealed meaningful phrase-level patterns.

### Feature Engineering and Signals
- Word count and average word length provided better measures of content complexity.
- Domain-specific scoring successfully captured biomedical relevance.
  - Evidence: [Processed output with bio_tox_relevance_score](https://github.com/abeaderstadt/nlp-05-web-documents/blob/main/data/processed/beaderstadt_processed.csv)

### Pipeline and Reusability
- EVTL structure improved modularity and reproducibility.
- Pipelines worked across multiple datasets with minimal changes (often just a URL update).


---

## 6. Representative Work

### Project 4: API-Based NLP Pipeline (News Data)
**Link:** GitHub repository:[View Project 4](https://github.com/abeaderstadt/nlp-04-api-text-data)<br>

This project demonstrates my ability to build a full EVTL pipeline using live API data. I extended the base pipeline by adding validation for real-world JSON structures and engineering new features to improve data quality and analytical usefulness.<br>

### Project 5: Web Document NLP Pipeline (Biomedical AI)
**Link:** GitHub repository:[View Project 5](https://github.com/abeaderstadt/nlp-05-web-documents)<br>

This project demonstrates my ability to build a reusable EVTL pipeline for extracting and analyzing structured web content. I extended the pipeline with domain-specific scoring and keyword extraction to evaluate biomedical relevance in academic abstracts.<br>

### Project 6: End-to-End NLP Pipeline with spaCy
**Link:** GitHub repository:[View Project 6](https://github.com/abeaderstadt/nlp-06-nlp-pipeline)<br>

This project demonstrates my ability to build an end-to-end NLP pipeline that integrates web scraping, text preprocessing, and linguistic analysis. I extended the pipeline with spaCy-based processing and additional analytical features to extract deeper insights from technical text.<br>

---

## 7. Skills

Through these projects, I developed the following skills:<br>

- Building end-to-end NLP pipelines using EVTL architecture
- Extracting and processing text from HTML (BeautifulSoup) and JSON APIs
- Cleaning and normalizing messy, real-world text data
- Engineering custom NLP features (word count, keyword extraction, domain-specific scoring)
- Performing frequency, bigram, and co-occurrence analysis
- Using spaCy for efficient text processing and linguistic analysis
- Working with structured and unstructured data across multiple formats
- Communicating analytical results using Markdown, charts, and visualizations

---

## Final Notes

This portfolio reflects my growth from basic text processing to building reusable, production-style NLP pipelines. Moving forward, I would like to expand these workflows by incorporating machine learning models and applying them to more advanced NLP tasks such as classification and prediction.
