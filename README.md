# Highlight-KPE: An Unsupervised Keyword Extraction Method Integrating Summary and Contribution Information from Academic Papers

## Overview
<b> The code and dataset for this paper: Highlight-KPE: An Unsupervised Keyword Extraction Method Integrating Summary and Contribution Information from Academic Papers

The primary objective of this paper is to investigate how the integration of highlight information, which describes the contributions of academic papers, can enhance the performance of unsupervised keyword extraction in traditional research that solely relies on abstracts. We have selected the following four extraction models:
* TextRank      https://aclanthology.org/W04-3252/
* PositionRank  https://aclanthology.org/P17-1102/
* MDERank       https://aclanthology.org/2022.findings-acl.34/
* PromptRank    https://aclanthology.org/2023.acl-long.545/

On this basis, we have investigated several approaches to integrating summaries with highlight information:
* Direct text concatenation; we considered the order of concatenation, assessing the differences in extraction performance when using "Abstract + Highlights" versus "Highlights + Abstract" as inputs for the extraction model.
* Given that summaries may contain much information irrelevant to keyword extraction, we segmented the abstract into a set of sentences and utilized the similarity between sentences and highlights to filter out sentences in the abstract that are less relevant to the current task. This process yields a filtered abstract. Subsequently, we concatenated the filtered abstract with the highlights.

We utilized datasets from both the computer science and library information science fields to test the performance of the method proposed in this study.

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
