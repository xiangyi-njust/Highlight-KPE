# Highlight-KPE: An Unsupervised Keyword Extraction Method Integrating Summary and Contribution Information from Academic Papers

## Overview
<b> The code and dataset for this paper: Highlight-KPE: An Unsupervised Keyword Extraction Method Integrating Summary and Contribution Information from Academic Papers

The primary objective of this paper is to investigate how the integration of highlight information, which describes the contributions of academic papers, can enhance the performance of unsupervised keyword extraction in traditional research that solely relies on abstracts. We have selected the following four extraction models:
* ** TextRank
* ** PositionRank
* ** MDERank
* ** PromptRank

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
