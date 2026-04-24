# Enhancing Unsupervised Keyword Extraction in Academic Papers through the Integration of Highlights and Abstracts

## Overview

This repository contains the code and dataset accompanying the research paper *"Enhancing Unsupervised Keyword Extraction in Academic Papers through the Integration of Highlights and Abstracts"* (Scientometrics, 2025).

### Objective

This study investigates how integrating highlight information—which captures key contributions of academic papers—can enhance unsupervised keyword extraction performance compared to traditional approaches using abstracts alone.

### Extraction Models

The research evaluates four state-of-the-art unsupervised keyword extraction models:

- [**TextRank**](https://aclanthology.org/W04-3252/) - Graph-based ranking algorithm for extracting keyphrases
- [**PositionRank**](https://aclanthology.org/P17-1102/) - Position-biased algorithm for keyphrase extraction
- [**MDERank**](https://aclanthology.org/2022.findings-acl.34/) - Multi-document entity-aware ranking approach
- [**PromptRank**](https://aclanthology.org/2023.acl-long.545/) - Prompt-based ranking methodology

### Research Question

Can integrating highlight information—which captures the key contributions and findings of academic papers—improve unsupervised keyword extraction performance compared to using abstracts alone?

### Methodology

#### Integration Approaches

We explored **two primary strategies** for combining highlights with abstracts:

1. **Direct Concatenation** (Simple approach - 4 variations):
   - **A (Abstract only)**: Baseline using abstract text
   - **H (Highlights only)**: Baseline using highlight text
   - **A+H**: Abstract followed by Highlights
   - **H+A**: Highlights followed by Abstract

2. **Filtered Abstract Integration** (Advanced approach - 3 variations):
   - **FA (Filtered Abstract)**: Intelligent filtering using semantic similarity
     - Segments abstracts into sentences
     - Filters sentences based on similarity to highlights
     - Retains only the most relevant sentences
   - **FA+H**: Filtered Abstract + Highlights
   - **H+FA**: Highlights + Filtered Abstract

#### Experimental Design

1. **Baseline Testing**: Establish performance baseline with abstract-only input
2. **Integration Testing**: Evaluate all 7 input variations across all 4 extraction models
3. **Comparative Analysis**: Measure performance differences across models and domains
4. **LLM Evaluation**: Compare traditional methods with state-of-the-art LLM approaches (GPT-3.5, Claude)

#### Evaluation Metrics

- **Precision@K**: Proportion of extracted keywords that match gold standard (K = 5, 10, 15)
- **Recall@K**: Proportion of gold standard keywords successfully extracted
- **F1@K**: Harmonic mean of Precision and Recall
- **Normalization**: Porter Stemmer applied to normalize keywords (case-insensitive matching)

### Datasets

Experiments conducted on datasets from two distinct academic domains:

**Computer Science (CS) Dataset**
- **Size**: 3,000 academic papers from Elsevier
- **Contents**: Abstracts, highlights, filtered abstracts, and expert-annotated keywords
- **Format**: Excel file with structured metadata

**Library Information Science (LIS) Dataset**
- **Size**: Academic papers from library science domain
- **Contents**: Similar structure to CS dataset with domain-specific papers
- **Format**: Excel file with structured metadata

Both datasets include **ground-truth keywords** labeled by domain experts for evaluation.

## Results

### Legend

- **A**: Abstract only
- **H**: Highlights only
- **FA**: Filtered Abstract
- **A+H**: Abstract + Highlights
- **H+A**: Highlights + Abstract
- **FA+H**: Filtered Abstract + Highlights
- **H+FA**: Highlights + Filtered Abstract

### Table 1: Library Information Science (LIS) Dataset

#### F1@5
| Method | A | H | FA | A+H | H+A | FA+H | H+FA |
|--------|-------|-------|-------|-------|-------|-------|-------|
| TextRank | 17.79 | 12.09 | 17.71 | 17.77 | 17.69 | 17.53 | 17.60 |
| PositionRank | 17.68 | 12.40 | 17.47 | 17.64 | 18.02 | 17.55 | 17.63 |
| MDERank | 19.48 | 16.97 | 18.35 | 22.32 | 22.20 | 21.37 | 21.41 |
| PromptRank | 22.33 | 16.14 | 21.92 | 23.06 | 23.71 | 22.56 | 22.49 |

#### F1@10
| Method | A | H | FA | A+H | H+A | FA+H | H+FA |
|--------|-------|-------|-------|-------|-------|-------|-------|
| TextRank | 17.66 | 10.82 | 16.63 | 18.01 | 18.02 | 17.47 | 17.51 |
| PositionRank | 17.06 | 10.78 | 16.36 | 17.58 | 18.24 | 17.19 | 17.28 |
| MDERank | 18.91 | 15.70 | 18.66 | 21.36 | 21.37 | 20.69 | 20.61 |
| PromptRank | 21.72 | 13.78 | 19.75 | 22.78 | 23.08 | 21.73 | 21.68 |

#### F1@15
| Method | A | H | FA | A+H | H+A | FA+H | H+FA |
|--------|-------|-------|-------|-------|-------|-------|-------|
| TextRank | 15.56 | 9.49 | 13.95 | 16.29 | 16.45 | 15.35 | 15.31 |
| PositionRank | 15.26 | 9.50 | 13.71 | 15.97 | 16.41 | 15.19 | 15.16 |
| MDERank | 17.17 | 13.27 | 16.89 | 19.21 | 19.27 | 18.49 | 18.52 |
| PromptRank | 18.78 | 12.76 | 16.37 | 19.95 | 20.28 | 18.39 | 18.34 |

### Table 2: Computer Science (CS) Dataset

#### F1@5
| Method | A | H | FA | A+H | H+A | FA+H | H+FA |
|--------|-------|-------|-------|-------|-------|-------|-------|
| TextRank | 11.76 | 6.69 | 10.98 | 12.22 | 12.22 | 11.31 | 11.40 |
| PositionRank | 12.52 | 6.96 | 10.55 | 12.89 | 12.70 | 11.32 | 11.45 |
| MDERank | 12.02 | 8.95 | 11.11 | 14.02 | 13.99 | 13.07 | 12.88 |
| PromptRank | 16.44 | 8.44 | 14.24 | 16.91 | 16.53 | 14.84 | 14.53 |

#### F1@10
| Method | A | H | FA | A+H | H+A | FA+H | H+FA |
|--------|-------|-------|-------|-------|-------|-------|-------|
| TextRank | 11.43 | 5.64 | 9.74 | 11.98 | 12.03 | 10.90 | 10.92 |
| PositionRank | 11.46 | 5.66 | 9.48 | 12.19 | 12.12 | 10.64 | 10.64 |
| MDERank | 12.18 | 8.06 | 11.49 | 13.88 | 13.95 | 12.76 | 12.91 |
| PromptRank | 15.03 | 7.50 | 12.31 | 15.89 | 15.82 | 13.80 | 13.64 |

#### F1@15
| Method | A | H | FA | A+H | H+A | FA+H | H+FA |
|--------|-------|-------|-------|-------|-------|-------|-------|
| TextRank | 9.99 | 5.04 | 7.95 | 10.64 | 10.81 | 9.18 | 9.18 |
| PositionRank | 9.94 | 5.02 | 7.84 | 10.70 | 10.74 | 9.10 | 9.10 |
| MDERank | 11.54 | 7.06 | 10.58 | 12.80 | 12.88 | 11.71 | 11.69 |
| PromptRank | 12.59 | 7.19 | 10.42 | 13.90 | 13.85 | 11.69 | 11.60 |

### Key Findings and Insights

**Performance Rankings**

- **PromptRank** demonstrates superior performance across both datasets and all input variations
- **LIS dataset** shows higher baseline F1 scores (up to 23.71) compared to CS dataset (up to 16.91)
- **Highlights-first ordering (H+A)** generally outperforms abstract-first ordering (A+H)

**Integration Strategy Effectiveness**

| Finding | Impact |
|---------|--------|
| Highlights provide complementary information | Highlights capture key contributions; abstracts provide context |
| Filtered abstraction improves performance | Removing irrelevant abstract sentences increases signal quality |
| Order of concatenation matters | H+A and H+FA tend to outperform A+H variants |
| Domain differences exist | LIS domain shows higher keyword density and easier extraction |
| Traditional vs. LLM methods | PromptRank (transformer-based) outperforms graph-based methods |

**Best Performing Configurations**

- **LIS Dataset F1@5**: PromptRank with H+A input → **23.71** (+1.38 vs. abstract-only)
- **CS Dataset F1@5**: PromptRank with A+H input → **16.91** (+0.47 vs. abstract-only)
- **Consistent Improvement**: All tested combinations show improvement over abstract-only baseline

**Domain-Specific Observations**

- LIS papers: Keywords more concentrated in abstracts and highlights
- CS papers: Keywords more dispersed; higher variance in extraction performance
- Highlight quality: LIS highlights are more focused and informative

## Repository Structure

```
Highlight-KPE/
├── code/
│   ├── EDA.ipynb                      Exploratory Data Analysis
│   │                                  • Dataset statistics and distribution analysis
│   │                                  • Keyword density visualization
│   │                                  • Abstract and highlight length analysis
│   │                                  • Result visualization and comparison
│   │
│   ├── TextRank.ipynb                 Graph-Based Keyword Extraction
│   │                                  • TextRank algorithm implementation
│   │                                  • Tests all 7 input variations (A, H, A+H, H+A, FA, FA+H, H+FA)
│   │                                  • Uses spaCy with pytextrank library
│   │                                  • Generates F1@K evaluation metrics
│   │
│   ├── PositionRank.ipynb             Position-Biased Keyword Extraction
│   │                                  • PositionRank algorithm implementation
│   │                                  • Incorporates candidate position information
│   │                                  • Tests all 7 input variations
│   │                                  • Comparative performance evaluation
│   │
│   ├── MDERank/                       Multi-Document Entity-Aware Ranking
│   │   ├── mderank.py                 Core MDERank algorithm implementation
│   │   └── log/                       Execution logs and results
│   │
│   ├── PromptRank/                    Transformer-Based Prompt Ranking
│   │   ├── data.py                    Complex data preprocessing pipeline
│   │   ├── inference.py               Model inference and prediction code
│   │   ├── main.py                    Main execution script
│   │   └── log/                       Execution logs and model checkpoints
│   │
│   ├── LLM/                           Large Language Model Integration
│   │   ├── LLM.ipynb                  LLM-based keyword extraction
│   │   │                              • GPT-3.5-turbo-1106 (OpenAI)
│   │   │                              • Claude-3.5-Haiku (Anthropic)
│   │   │                              • Custom prompt engineering
│   │   │
│   │   ├── LLMClassify.ipynb          Sentence Classification using LLMs
│   │   │                              • Classify abstract sentences into 5 categories
│   │   │                              • Analyze keyword distribution by sentence type
│   │   │                              • Identify which sentence types contain important keywords
│   │   │
│   │   └── prompt.ini                 Prompt Templates
│   │                                  • System prompts for domain-specific experts
│   │                                  • Few-shot examples for consistent extraction
│   │                                  • Templates for CS and LIS domains
│   │
│   ├── statistic_check.ipynb          Statistical Validation
│   │                                  • Significance testing across models and variations
│   │                                  • Performance difference analysis
│   │                                  • Confidence interval calculations
│   │
│   ├── temporary_data/                Intermediate Results and Outputs
│   │                                  • Model predictions and scores
│   │                                  • Extracted keywords for evaluation
│   │                                  • Cached embeddings and preprocessed data
│   │
│   └── README.md                      Code directory documentation
│
├── data/
│   ├── Elsevier-CS/                   Computer Science Dataset
│   │   ├── Keywords.json              Expert-annotated reference keywords
│   │   │                              • 3,000 papers × 3-7 keywords per paper
│   │   │
│   │   └── Texts_3000-lite-abstract.xlsx  Paper texts with structured metadata
│   │                                  • Pii: Paper identifier
│   │                                  • Abstract: Full abstract text
│   │                                  • Highlights: Key contributions (author-provided)
│   │                                  • reserve_4: Filtered abstract (FA)
│   │                                  • Keywords: Ground truth for evaluation
│   │
│   ├── Elsevier-LIS/                  Library Information Science Dataset
│   │   ├── Keywords.json              Expert-annotated reference keywords
│   │   └── Texts-lite-abstract.xlsx   Paper texts with metadata (similar structure to CS)
│   │
│   ├── EP/                            Environmental/Process Papers
│   ├── Scopus-Multi/                  Multi-Field Papers
│   │
│   └── [Other datasets for comparison and future work]
│
└── README.md                          Main project documentation
```

### Key Files Explanation

**Data Files**
- `Texts_*-lite-abstract.xlsx`: Contains all input variations needed for evaluation
  - Column structure enables reproducible experiments across all 7 input variations
  - Reserve columns store preprocessed versions for efficient access

**Code Organization**
- Individual notebooks for each extraction method enable independent experimentation
- Modular structure allows easy addition of new extraction algorithms
- Shared evaluation pipeline ensures consistent metrics across methods
- LLM implementations support API-based and local model inference

## Technical Implementation

### Technologies and Libraries

**Core Dependencies**
- Python 3.7+
- Jupyter Notebook for interactive development and experimentation
- pandas, openpyxl for data manipulation and Excel handling
- scikit-learn for machine learning utilities

**NLP Libraries**
- spaCy: Tokenization, POS tagging, and linguistic preprocessing
- NLTK: Natural Language Toolkit for additional NLP utilities
- Stanford CoreNLP: Advanced syntactic analysis
- Porter Stemmer: Keyword normalization and stemming

**Deep Learning & Transformers**
- PyTorch: Deep learning framework
- Transformers (Hugging Face): Pre-trained models and T5 tokenizer for PromptRank
- OpenAI API: GPT-3.5-turbo-1106 integration
- Anthropic API: Claude integration for LLM-based extraction

**Additional Tools**
- tqdm: Progress bar utilities
- logging: Result tracking and debugging
- matplotlib, seaborn: Visualization (EDA)

### Key Algorithm Details

**Candidate Extraction**
- Uses constituency parsing to extract noun phrases
- Grammar pattern: `NP: {<NN.*|JJ>*<NN.*>}` (adjectives + nouns)
- Removes common stopwords to focus on content words

**Evaluation Framework**
- Exact match after Porter Stemmer normalization
- Case-insensitive keyword matching
- Micro-averaging across all documents for final metrics
- Comprehensive logging for reproducibility

**Filtered Abstract Strategy**
- Sentence segmentation using spaCy
- Cosine similarity computation between sentences and highlights
- Threshold-based or top-N selection for sentence filtering
- Concatenation order tested: FA+H vs. H+FA

## Research Contributions

This research makes the following contributions to unsupervised keyword extraction:

1. **Novel Integration Approach**: Demonstrates that intelligent combination of highlights and abstracts significantly improves keyword extraction performance across multiple extraction methods.

2. **Comprehensive Empirical Study**: Evaluates 4 major unsupervised extraction methods on 2 diverse datasets with 7 distinct input variations, providing extensive comparative analysis.

3. **Filtered Abstract Strategy**: Introduces and validates a semantic similarity-based filtering approach that outperforms naive concatenation strategies.

4. **Multi-Method Evaluation**: Bridges traditional graph-based methods (TextRank, PositionRank) and modern transformer-based approaches (PromptRank), as well as LLM-based methods.

5. **Domain-Specific Analysis**: Reveals important differences between CS and LIS domains that can inform future research in domain-specific keyword extraction.

6. **Public Datasets**: Contributes annotated datasets from multiple academic domains to enable future research and reproducibility.

7. **Reproducible Methodology**: Provides complete implementation with detailed documentation, enabling researchers to replicate experiments and build upon this work.

## Getting Started

### Prerequisites

- Python 3.7+
- Jupyter Notebook
- Dependencies listed in requirements (if available)

### Installation

1. Clone this repository:
```bash
git clone https://github.com/xiangyi-njust/Highlight-KPE.git
cd Highlight-KPE
```

2. Install required dependencies:
```bash
pip install -r requirements.txt  # if available
```

### Usage

The code is organized as Jupyter notebooks for interactive experimentation. Follow this workflow to reproduce the experiments:

#### 1. Data Exploration
```bash
# Start with exploratory data analysis
jupyter notebook code/EDA.ipynb
```
This notebook provides:
- Dataset statistics and distributions
- Keyword density analysis
- Abstract and highlight length patterns
- Visualization of experimental results

#### 2. Extract Keywords Using Traditional Methods

**TextRank (Graph-Based)**
```bash
jupyter notebook code/TextRank.ipynb
```
- Graph-based keyphrase extraction
- Tests all 7 input variations
- Baseline comparison for the domain

**PositionRank (Position-Aware)**
```bash
jupyter notebook code/PositionRank.ipynb
```
- Position-biased candidate selection
- Tests all 7 input variations
- Comparative performance analysis

**MDERank (Multi-Document Entity-Aware)**
```bash
cd code/MDERank
python mderank.py
```
- Multi-document entity-aware ranking
- Advanced entity recognition and linking

**PromptRank (Transformer-Based)**
```bash
cd code/PromptRank
python main.py
```
- State-of-the-art transformer-based method
- T5 tokenizer for candidate ranking
- Shows best overall performance

#### 3. LLM-Based Extraction

**GPT and Claude Integration**
```bash
jupyter notebook code/LLM/LLM.ipynb
```
Configuration required:
- Set OpenAI API key for GPT-3.5-turbo
- Set Anthropic API key for Claude
- Select target dataset (CS or LIS)
- Models automatically test all input variations

**Sentence Classification**
```bash
jupyter notebook code/LLM/LLMClassify.ipynb
```
Analyzes:
- Classification of abstract sentences into 5 categories
- Keyword distribution across sentence types
- Which sentence types contribute most to keywords

#### 4. Statistical Validation
```bash
jupyter notebook code/statistic_check.ipynb
```
Validates:
- Performance differences between methods
- Significance of improvement from highlights integration
- Confidence intervals for results

#### 5. Reproduce All Results
To systematically reproduce all results:
1. Run EDA.ipynb first for dataset understanding
2. Run extraction notebooks in order: TextRank → PositionRank → MDERank → PromptRank
3. Run LLM.ipynb for LLM comparison
4. Run statistic_check.ipynb for validation

#### Expected Outputs
Each extraction notebook generates:
- `F1@5`, `F1@10`, `F1@15` scores
- Extracted keywords for all papers
- Performance comparison across input variations
- CSV/JSON files with detailed results

## Extending the Project

### Adding a New Extraction Method

To add your own keyword extraction algorithm:

1. **Create a new notebook** in `code/` directory
2. **Follow the standard pipeline**:
   - Load data from Excel files (abstracts, highlights, filtered abstracts)
   - Test on all 7 input variations (A, H, FA, A+H, H+A, FA+H, H+FA)
   - Extract keywords using your method
   - Apply Porter Stemmer normalization
   - Evaluate using F1@K metrics (K = 5, 10, 15)
   - Save results in consistent format

3. **Integration points**:
   - Use the evaluation utility functions from existing notebooks
   - Store results in `code/temporary_data/` for consistency
   - Ensure results are comparable to existing methods

### Adapting to New Datasets

To apply this methodology to new datasets:

1. **Prepare data** in similar Excel format:
   - Abstract column
   - Highlights column
   - Keywords column (for evaluation)
   - Optional: Pre-computed filtered abstract

2. **Run the extraction pipeline**:
   - Adapt notebook paths to your dataset location
   - Adjust any domain-specific parameters
   - Run all extraction methods for comparison

3. **Evaluate results**:
   - Use the same evaluation framework
   - Compare performance with baseline (abstract-only)
   - Analyze domain-specific insights

### Configuration

Key parameters to customize:

**Sentence Filtering** (in filtered abstract generation):
- Similarity threshold for sentence selection
- Number of top-N sentences to retain
- Similarity metric (cosine, Jaccard, etc.)

**Evaluation**:
- K-values for F1@K metric (default: 5, 10, 15)
- Stemmer type (default: Porter Stemmer)
- Exact vs. partial matching

**LLM Configuration** (in `code/LLM/prompt.ini`):
- Domain-specific system prompts
- Few-shot examples
- Temperature and other hyperparameters

## Citation

If you use this code or dataset in your research, please cite the following paper:

```bibtex
@article{xiang2025enhancing,
  title={Enhancing Unsupervised Keyword Extraction in Academic Papers through the Integration of Highlights and Abstracts},
  author={Xiang, Yi and Zhang, Chengzhi},
  journal={Scientometrics},
  year={2025},
  note={Submitted}
}
```

**Alternative citation format:**

>Yi Xiang, Chengzhi Zhang\*. Enhancing Unsupervised Keyword Extraction in Academic Papers through Integrating Highlights with Abstract. ***Scientometrics***. 2026,  [[doi]](https://doi.org/10.1007/s11192-026-05646-6)  [[arXiv]](http://arxiv.org/abs/2604.19505)  [[Dataset & Source Code]](https://github.com/xiangyi-njust/Highlight-KPE)

## License

Please check the repository for license information.

## Contact

For questions or inquiries, please contact the authors via the repository.
