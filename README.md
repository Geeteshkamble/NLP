# NLP-Driven Equity Query Classifier

This project implements an advanced natural language processing (NLP) pipeline designed to interpret, classify, and respond to complex financial queries. Using BERT embeddings, SpaCy, and machine learning techniques, the pipeline supports various financial query types, such as metric inquiries, historical performance, comparative analysis, and financial forecasting.

## Key Features
1. **Multi-label Intent Classification**: Classifies financial queries into multiple intents using BERT embeddings and logistic regression.
2. **Custom Financial Entity Extraction**: Utilizes SpaCy’s Named Entity Recognition (NER) model and custom regex rules to identify financial-specific terms.
3. **Action Mapping for Financial Queries**: Maps classified intents and extracted entities to simulated data retrieval actions.
4. **Dynamic Query Decomposition**: Breaks down complex queries with multiple intents for more detailed responses.

## Table of Contents
1. [Installation](#installation)
2. [Usage](#usage)
3. [Project Structure](#project-structure)
4. [Pipeline Workflow](#pipeline-workflow)
5. [Examples](#examples)
6. [Future Enhancements](#future-enhancements)
7. [License](#license)

## Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/YOUR_USERNAME/nlp-driven-equity-query-classifier.git
   cd nlp-driven-equity-query-classifier
   ```

2. **Install dependencies**:
   To install the necessary dependencies for this project, run the following command:
   ```bash
   pip install -r requirements.txt
   ```

3. **Download SpaCy Language Models**:
   Download the required SpaCy language models:
   ```bash
   python -m spacy download en_core_web_sm
   python -m spacy download en_core_web_trf  # For transformer-based model (optional)
   ```

4. **Dataset Setup**:
   Place any datasets in the `data/` directory or configure the paths as specified in the code.

## Usage

To run the main pipeline on a sample query, execute the following command:

```bash
python financial_nlp_pipeline.py
```

Customize the sample queries or add new ones within `financial_nlp_pipeline.py` to test different classifications and entity extraction outputs.

## Project Structure

```
nlp-driven-equity-query-classifier/
├── README.md                    # Project overview and usage instructions
├── requirements.txt             # List of dependencies
├── financial_nlp_pipeline.py    # Main code implementing the NLP pipeline
└── data/                        # Directory for sample datasets and financial data
```

## Pipeline Workflow

### Intent Classification

Queries are converted into BERT embeddings and classified into multiple financial intents, such as:
- Metric Inquiry
- Historical Performance
- Comparative Analysis
- Fundamental Data Request
- News Impact
- Forecasting & Predictions

### Financial Entity Extraction

SpaCy’s NER model is used to extract standard entities such as companies, dates, and amounts. Custom regex rules further enhance recognition for financial terms (e.g., “P/E ratio”, “EPS”, “dividend yield”).

### Query Decomposition

Breaks down complex queries into simpler subqueries if they involve multiple intents or comparisons.

### Action Mapping

Maps classified intents and extracted entities to specific data retrieval actions (e.g., fetching metrics, comparing companies). The `retrieve_financial_data` function simulates data retrieval based on query needs.

## Examples

### Sample Query

```python
query = "Compare Apple and Microsoft on EPS growth and P/E ratio over the last 5 years."
```

### Expected Output

```
Processing Subqueries:
Predicted Intents for Subquery: Comparative Analysis, Metric Inquiry
Extracted Entities: {'companies': ['Apple', 'Microsoft'], 'metrics': ['EPS growth', 'P/E ratio'], 'time_periods': ['last 5 years']}
Mapped Actions for Subquery:
Executing action: Compare metrics between Apple and Microsoft with metrics: EPS growth, P/E ratio
```

## Future Enhancements

Potential areas for further improvements:

1. **Advanced Model Tuning**: Consider fine-tuning the BERT model on a larger financial dataset to improve intent classification accuracy.
2. **Real-Time Data Integration**: Integrate with financial APIs (e.g., Alpha Vantage, Yahoo Finance) to dynamically fetch real-time data for responses.
3. **Sentiment Analysis for Financial News**: Use sentiment analysis on recent news articles to provide insights into stock movements.
4. **Additional Financial Intent Types**: Expand supported intents to cover a broader range of financial queries.

## License

This project is licensed under the MIT License. See the LICENSE file for more details.
```
