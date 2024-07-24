# Highlight-KPE: An Unsupervised Keyword Extraction Method Integrating Summary and Contribution Information from Academic Papers

## Overview
<b> The code and dataset for this paper: Highlight-KPE: An Unsupervised Keyword Extraction Method Integrating Summary and Contribution Information from Academic Papers

The primary objective of this paper is to investigate how the integration of highlight information, which describes the contributions of academic papers, can enhance the performance of unsupervised keyword extraction in traditional research that solely relies on abstracts. We have selected the following four extraction models:
<pre>
* TextRank      https://aclanthology.org/W04-3252/
* PositionRank  https://aclanthology.org/P17-1102/
* MDERank       https://aclanthology.org/2022.findings-acl.34/
* PromptRank    https://aclanthology.org/2023.acl-long.545/
</pre>

On this basis, we have investigated several approaches to integrating summaries with highlight information:
* Direct text concatenation; we considered the order of concatenation, assessing the differences in extraction performance when using "Abstract + Highlights" versus "Highlights + Abstract" as inputs for the extraction model.
* Given that summaries may contain much information irrelevant to keyword extraction, we segmented the abstract into a set of sentences and utilized the similarity between sentences and highlights to filter out sentences in the abstract that are less relevant to the current task. This process yields a filtered abstract. Subsequently, we concatenated the filtered abstract with the highlights.

We utilized datasets from both the computer science and library information science fields to test the performance of the method proposed in this study.

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

<pre>
Highlight-KPE
├─ README.md
├─ code
│    ├─ EDA.ipynb
│    ├─ LLM.ipynb
│    ├─ LLMClassify.ipynb
│    ├─ PositionRank.ipynb
│    ├─ TextRank.ipynb
│    └─ prompt.ini
├─ crawl
│    ├─ crawl-cs.ipynb
│    └─ crawl-lis.ipynb
└─ data
     ├─ Elsevier-CS
     │    ├─ Keywords.json
     │    ├─ Texts_3000-lite-abstract.xlsx
     │    └─ Texts_3000.xlsx
     └─ Elsevier-LIS
    	  ├─ Keywords.json
	  ├─ Texts-lite-abstract.xlsx
	  ├─ Texts.xlsx
</pre>

## Citation
Please cite the following paper if you use these codes and datasets in your work.

> 
