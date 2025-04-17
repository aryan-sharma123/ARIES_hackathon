# ARIES_hackathon
analysis of research papers


# Research Paper Quality Classifier

This project is a machine learning system that classifies research papers as either **"Publishable"** or **"Non-Publishable"** based on various textual features extracted from the PDF documents. The classifier uses the **Random Forest** algorithm and provides explanations for its predictions using **SHAP** values.

### Use of Shap
- shap is used to enhance the reason behind the predicitions.
- but i am not able to show it in CSV file. here is the screenshot what the model will give output
- ![Screenshot](/Screenshot 2025-04-17 194217.png)

### Models Used

- **SentenceTransformer ('all-MiniLM-L6-v2')**  
  Used to compute semantic similarity between sections of a research paper, especially between the Introduction and Conclusion. This helps assess the logical consistency and completeness of the paper.

- **RandomForestClassifier**  
  A machine learning model used to classify papers as *Publishable* or *Non-Publishable* based on extracted features. It uses 100 decision trees (`n_estimators=100`) and a fixed random seed (`random_state=42`) 
  to ensure consistent results.


### train test split is done keeping in mind the biasness of the given data


## Features

The system analyzes research papers based on the following features:

### Structural Features
- **Introduction-Conclusion Similarity**: Semantic similarity using sentence transformers.
- **Section Detection**: Identifies and extracts sections like Introduction, Methodology, Conclusion, etc.

### Readability Metrics

The system uses common readability scores to measure how easy a paper is to understand:

#### 1. Flesch-Kincaid Grade Level
Estimates the U.S. school grade level needed to understand the text. Higher scores mean easier readability.

#### 2. Dale-Chall Readability Score
Checks how many difficult or uncommon words are used. Lower scores mean the text is easier to read.

#### 3. Automated Readability Index (ARI)
Uses characters per word and words per sentence to estimate the reading grade level.

#### 4. Word Count
Total number of words in the paper. Helps measure overall length and supports other features like citation density.


### Citation Analysis
- **Number of In-text Citations**
- **Reference Count in Bibliography**
- **Citation Density**: Citations per 1000 words
- Count author-based citations like (Smith et al., 2020). use et al. to find 
- Count numbered citations like [1], [2,3], etc. use []  to find.\

### Use of certain words are located
- like  'better than', 'outperforms', 'compared to', 'improves upon',
        'achieves higher', 'higher accuracy', 'lower error', 'state-of-the-art',
        'compared with', 'previous methods', 'surpasses', 'yields better results'

### comparison of introduction and result/conclusion 

### Improvement Detection
- Detects phrases indicating comparisons to previous works and improvements.

## Requirements

To run this project, you need the following:

- **Python 3.8+**
  
### Required Packages:
- pandas
- numpy(version  = 1.24.4 ) is used here
- scikit-learn
- PyPDF2
- sentence-transformers
- textstat
- shap
- for numpy 1.24.4 version is used with numba = 0.57.1

### Future aspects
- model can be enhanced by doing a comparison with the past papers similar to this.
- We can hit an API request to the websites like SemanticScholars and extracting previous papers using heading of the current paper and then comparing results and conclusion.
- We can also compare citations of both the papers. 



Install all the required packages with:

```bash

research-paper-classifier/
│
├── Publishable/                # Folder containing PDFs of publishable papers
├── Non-Publishable/            # Folder containing PDFs of non-publishable papers
├── unlabeled_predictions.csv   # Output file with prediction results
├── Research_Paper_Classifier.ipynb  # Main Jupyter notebook
└── README.md                   # This file


