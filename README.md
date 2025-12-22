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

### Integration Approaches

We explored two primary strategies for integrating highlights with abstracts:

1. **Direct Concatenation**: Evaluated different concatenation orders:
   - Abstract + Highlights vs. Highlights + Abstract
   - Analysis of performance variations based on input ordering

2. **Filtered Abstract Integration**: Advanced approach leveraging semantic similarity:
   - Segmented abstracts into constituent sentences
   - Filtered sentences based on similarity to highlights
   - Concatenated filtered abstract with highlight information

### Datasets and Results

Experiments were conducted on datasets from two distinct domains:
- **Computer Science (CS)**: 3000 academic papers
- **Library Information Science (LIS)**: Academic papers from the library science domain

Performance metrics are reported using F1 scores at K = 5, 10, and 15 for comprehensive evaluation.

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

## Repository Structure

```
Highlight-KPE/
├── code/
│   ├── EDA.ipynb                      Exploratory data analysis, visualization, and result evaluation
│   ├── LLM.ipynb                      Large language model-based keyword extraction
│   ├── LLMClassify.ipynb              Sentence classification using large language models
│   ├── PositionRank.ipynb             PositionRank implementation for keyword extraction
│   ├── TextRank.ipynb                 TextRank implementation for keyword extraction
│   └── prompt.ini                     Prompt templates for LLM-based keyword extraction
│
├── data/
│   ├── Elsevier-CS/                   Computer Science dataset
│   │   ├── Keywords.json              Reference keywords for CS papers
│   │   └── Texts_3000-lite-abstract.xlsx  CS paper texts with abstracts and highlights
│   │
│   └── Elsevier-LIS/                  Library Information Science dataset
│       ├── Keywords.json              Reference keywords for LIS papers
│       └── Texts-lite-abstract.xlsx   LIS paper texts with abstracts and highlights
│
└── README.md                          This file
```

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

The code is organized in Jupyter notebooks. To run the experiments:

1. **Data Analysis**: Open `code/EDA.ipynb` to explore the datasets and visualize results
2. **TextRank Extraction**: Run `code/TextRank.ipynb`
3. **PositionRank Extraction**: Run `code/PositionRank.ipynb`
4. **LLM-based Extraction**: Run `code/LLM.ipynb`
5. **Sentence Classification**: Run `code/LLMClassify.ipynb`

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

Yi Xiang, Chengzhi Zhang*. Enhancing Unsupervised Keyword Extraction in Academic Papers through the Integration of Highlights and Abstracts. *Scientometrics*, 2025 (submitted).

## License

Please check the repository for license information.

## Contact

For questions or inquiries, please contact the authors via the repository.
