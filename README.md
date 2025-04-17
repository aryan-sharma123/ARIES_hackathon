# ARIES_hackathon
analysis of research papers


# Research Paper Quality Classifier

This project is a machine learning system that classifies research papers as either **"Publishable"** or **"Non-Publishable"** based on various textual features extracted from the PDF documents. The classifier uses the **Random Forest** algorithm and provides explanations for its predictions using **SHAP** values.

## Features

The system analyzes research papers based on the following features:

### Structural Features
- **Introduction-Conclusion Similarity**: Semantic similarity using sentence transformers.
- **Section Detection**: Identifies and extracts sections like Introduction, Methodology, Conclusion, etc.

### Readability Metrics
- **Flesch-Kincaid Grade Level**
- **Dale-Chall Readability Score**
- **Automated Readability Index (ARI)**
- **Word Count**

### Citation Analysis
- **Number of In-text Citations**
- **Reference Count in Bibliography**
- **Citation Density**: Citations per 1000 words

### Improvement Detection
- Detects phrases indicating comparisons to previous works and improvements.

## Requirements

To run this project, you need the following:

- **Python 3.8+**
  
### Required Packages:
- pandas
- numpy
- scikit-learn
- PyPDF2
- sentence-transformers
- textstat
- shap

Install all the required packages with:

```bash
pip install -r requirements.txt
research-paper-classifier/
│
├── Publishable/                # Folder containing PDFs of publishable papers
├── Non-Publishable/            # Folder containing PDFs of non-publishable papers
├── Unlabeled/                  # Folder for PDFs to be classified
├── unlabeled_predictions.csv   # Output file with prediction results
├── Research_Paper_Classifier.ipynb  # Main Jupyter notebook
└── README.md                   # This file
