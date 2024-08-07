# Highlight-KPE: An Unsupervised Keyword Extraction Method Integrating Summary and Contribution Information from Academic Papers.

## Overview
<b> The code and dataset for this paper: Highlight-KPE: An Unsupervised Keyword Extraction Method Integrating Summary and Contribution Information from Academic Papers.</b> 

The primary objective of this paper is to investigate how the integration of highlight information, which describes the contributions of academic papers, can enhance the performance of unsupervised keyword extraction in traditional research that solely relies on abstracts. We have selected the following four extraction models:
<pre>
(a) TextRank      https://aclanthology.org/W04-3252/
(b) PositionRank  https://aclanthology.org/P17-1102/
(c) MDERank       https://aclanthology.org/2022.findings-acl.34/
(d) PromptRank    https://aclanthology.org/2023.acl-long.545/
</pre>

We have investigated several approaches to integrating summaries with highlight information:

(1) Direct text concatenation: we considered the order of concatenation, assessing the differences in extraction performance when using "Abstract + Highlights" versus "Highlights + Abstract" as inputs for the extraction model.

(2) Given that summaries may contain much information irrelevant to keyword extraction, we segmented the abstract into a set of sentences and utilized the similarity between sentences and highlights to filter out sentences in the abstract that are less relevant to the current task. This process yields a filtered abstract. Subsequently, we concatenated the filtered abstract with the highlights.

We utilized datasets from both the computer science(CS) and library information science(LIS) fields to test the performance of the method proposed in this study. The results are as follows:

LIS Dataset
|F1@K|Method||||Input||||
|:----|:----|:----|:----|:----|:----|:----|:----|:----|
| | |A|H|FA|A+H|H+A|FA+H|H+FA|
|5|TextRank|17.79|12.09|17.71|17.77|17.69|17.53|17.60|
| |PositionRank|17.68|12.40|17.47|17.64|18.02|17.55|17.63|
| |MDERank|19.48|16.97|18.35|22.32|22.20|21.37|21.41|
| |PromptRank|22.33|16.14|21.92|23.06|23.71|22.56|22.49|
|10|TextRank|17.66|10.82|16.63|18.01|18.02|17.47|17.51|
| |PositionRank|17.06|10.78|16.36|17.58|18.24|17.19|17.28|
| |MDERank|18.91|15.7|18.66|21.36|21.37|20.69|20.61|
| |PromptRank|21.72|13.78|19.75|22.78|23.08|21.73|21.68|
|15|TextRank|15.56|9.49|13.95|16.29|16.45|15.35|15.31|
| |PositionRank|15.26|9.5|13.71|15.97|16.41|15.19|15.16|
| |MDERank|17.17|13.27|16.89|19.21|19.27|18.49|18.52|
| |PromptRank|18.78|12.76|16.37|19.95|20.28|18.39|18.34|

CS Dataset
|F1@K|Method||||Input||||
|:----|:----|:----|:----|:----|:----|:----|:----|:----|
| | |A|H|FA|A+H|H+A|FA+H|H+FA|
|5|TextRank|11.76|6.69|10.98|12.22|12.22|11.31|11.40|
| |PositionRank|12.52|6.96|10.55|12.89|12.70|11.32|11.45|
| |MDERank|12.02|8.95|11.11|14.02|13.99|13.07|12.88|
| |PromptRank|16.44|8.44|14.24|16.91|16.53|14.84|14.53|
|10|TextRank|11.43|5.64|9.74|11.98|12.03|10.90|10.92|
| |PositionRank|11.46|5.66|9.48|12.19|12.12|10.64|10.64|
| |MDERank|12.18|8.06|11.49|13.88|13.95|12.76|12.91|
| |PromptRank|15.03|7.50|12.31|15.89|15.82|13.80|13.64|
|15|TextRank|9.99|5.04|7.95|10.64|10.81|9.18|9.18|
| |PositionRank|9.94|5.02|7.84|10.70|10.74|9.10|9.10|
| |MDERank|11.54|7.06|10.58|12.80|12.88|11.71|11.69|
| |PromptRank|12.95|7.19|10.42|13.90|13.85|11.69|11.60|

## Directory Structure
<pre>
Highlight-KPE

├─ code
│    ├─ EDA.ipynb		                Data Pattern Exploration, Result Analysis, and Visualization
│    ├─ LLM.ipynb                               Extracting Keywords Using Large Language Models
│    ├─ LLMClassify.ipynb                       Sentence Classify Using Large Language Models
│    ├─ PositionRank.ipynb                      Extracting Keywords Using PositionRank
│    ├─ TextRank.ipynb                          Extracting Keywords Using TextRank
│    └─ prompt.ini                              Designing Prompt Templates for Keyword Extraction Using Large Language Models
├─ crawl
│    ├─ crawl-cs.ipynb                          Data Crawling, Preprocessing, and Consolidation in the Field of Computer Science Research Papers
│    └─ crawl-lis.ipynb		                Data Crawling, Preprocessing, and Consolidation in the Field of Library Information Science Research Papers
└─ data
│    ├─ Elsevier-CS				Computer Science Papers
│    │    ├─ Keywords.json			Set of Keywords for the Paper	
│    │    ├─ Texts_3000-lite-abstract.xlsx	Text Content of the Paper, including the filter abstract and highlight
│    │    └─ Texts_3000.xlsx			Text Content of the Paper, including the abstract and highlight
│    └─ Elsevier-LIS				Library Information Papers
│    	  ├─ Keywords.json			Set of Keywords for the Paper
│	  ├─ Texts-lite-abstract.xlsx		Text Content of the Paper, including the filter abstract and highlight
│	  ├─ Texts.xlsx				Text Content of the Paper, including the abstract and highlight
├─ README.md
</pre>

## Citation
Please cite the following paper if you use these codes and datasets in your work.

> Yi Xiang, Chengzhi Zhang\*. Highlight-KPE: An Unsupervised Keyword Extraction Method Integrating Summary and Contribution Information from Academic Papers. ***Information Processing and Management***, 2024, (submitted)  [[doi]]() [[Dataset & Source Code]](https://github.com/xiangyi-njust/Highlight-KPE)
