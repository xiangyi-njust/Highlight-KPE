# Enhancing Unsupervised Keyword Extraction in Academic Papers through the Integration of Highlights and Abstracts

## Overview
<b> The code and dataset for this paper: Enhancing Unsupervised Keyword Extraction in Academic Papers through the Integration of Highlights and Abstracts.</b> 

The primary objective of this paper is to investigate how the integration of highlight information, which describes the contributions of academic papers, can enhance the performance of unsupervised keyword extraction in traditional research that solely relies on abstracts. We have selected the following four extraction models:
  - [TextRank](https://aclanthology.org/W04-3252/)
  - [PositionRank](https://aclanthology.org/P17-1102/)
  - [MDERank](https://aclanthology.org/2022.findings-acl.34/)
  - [PromptRank](https://aclanthology.org/2023.acl-long.545/)
    
We have investigated several approaches to integrating summaries with highlight information:

  - Direct text concatenation: we considered the order of concatenation, assessing the differences in extraction performance when using "Abstract + Highlights" versus "Highlights + Abstract" as inputs for the extraction model.

  - Given that summaries may contain much information irrelevant to keyword extraction, we segmented the abstract into a set of sentences and utilized the similarity between sentences and highlights to filter out sentences in the abstract that are less relevant to the current task. This process yields a filtered abstract. Subsequently, we concatenated the filtered abstract with the highlights.

We utilized datasets from both the computer science(CS) and library information science(LIS) fields to test the performance of the method proposed in this study. The results are as follows:

<b>Table1. Keyword extraction performance under different inputs on the LIS dataset</b>
<table>
	<tr>
		<th rowspan="2">F1@K</th>
		<th rowspan="2">Method</th>
		<th colspan="7">Input</th>
	</tr>
	<tr>
		<td>A</td>
		<td>H</td>
		<td>FA</td>
		<td>A+H</td>
		<td>H+A</td>
		<td>FA+H</td>
		<td>H+FA</td>
	</tr>
	<tr>
		<td rowspan="4">5</td>
		<td>TextRank</td>
		<td>17.79</td>
		<td>12.09</td>
		<td>17.71</td>
		<td>17.77</td>
		<td>17.69</td>
		<td>17.53</td>
		<td>17.60</td>
	</tr>
	<tr>
		<td>PositionRank</td>
		<td>17.68</td>
		<td>12.40</td>
		<td>17.47</td>
		<td>17.64</td>
		<td>18.02</td>
		<td>17.55</td>
		<td>17.63</td>	
	</tr>
	<tr>
		<td>MDERank</td>
		<td>19.48</td>
		<td>16.97</td>
		<td>18.35</td>
		<td>22.32</td>
		<td>22.20</td>
		<td>21.37</td>
		<td>21.41</td>	
	</tr>
	<tr>
		<td>PromptRank</td>
		<td>22.33</td>
		<td>16.14</td>
		<td>21.92</td>
		<td>23.06</td>
		<td>23.71</td>
		<td>22.56</td>
		<td>22.49</td>	
	</tr>
	<tr>
		<td rowspan="4">10</td>
		<td>TextRank</td>
		<td>17.66</td>
		<td>10.82</td>
		<td>16.63</td>
		<td>18.01</td>
		<td>18.02</td>
		<td>17.47</td>
		<td>17.51</td>
	</tr>
	<tr>
		<td>PositionRank</td>
		<td>17.06</td>
		<td>10.78</td>
		<td>16.36</td>
		<td>17.58</td>
		<td>18.24</td>
		<td>17.19</td>
		<td>17.28</td>
	</tr>
	<tr>
		<td>MDERank</td>
		<td>18.91</td>
		<td>15.7</td>
		<td>18.66</td>
		<td>21.36</td>
		<td>21.37</td>
		<td>20.69</td>
		<td>20.61</td>		
	</tr>
	<tr>
		<td>PromptRank</td>
		<td>21.72</td>
		<td>13.78</td>
		<td>19.75</td>
		<td>22.78</td>
		<td>23.08</td>
		<td>21.73</td>
		<td>21.68</td>			
	</tr>
	<tr>
		<td rowspan="4">15</td>
		<td>TextRank</td>
		<td>15.56</td>
		<td>9.49</td>
		<td>13.95</td>
		<td>16.29</td>
		<td>16.45</td>
		<td>15.35</td>
		<td>15.31</td>
	</tr>
	<tr>
		<td>PositionRank</td>
		<td>15.26</td>
		<td>9.50</td>
		<td>13.71</td>
		<td>15.97</td>
		<td>16.41</td>
		<td>15.19</td>
		<td>15.16</td>		
	</tr>
	<tr>
		<td>MDERank</td>
		<td>17.17</td>
		<td>13.27</td>
		<td>16.89</td>
		<td>19.21</td>
		<td>19.27</td>
		<td>18.49</td>
		<td>18.52</td>		
	</tr>
	<tr>
		<td>PromptRank</td>
		<td>18.78</td>
		<td>12.76</td>
		<td>16.37</td>
		<td>19.95</td>
		<td>20.28</td>
		<td>18.39</td>
		<td>18.34</td>		
	</tr>
</table>

<b>Table2. Keyword extraction performance under different inputs on the CS dataset</b>
<table>
	<tr>
		<th rowspan="2">F1@K</th>
		<th rowspan="2">Method</th>
		<th colspan="7">Input</th>
	</tr>
	<tr>
		<td>A</td>
		<td>H</td>
		<td>FA</td>
		<td>A+H</td>
		<td>H+A</td>
		<td>FA+H</td>
		<td>H+FA</td>
	</tr>
	<tr>
		<td rowspan="4">5</td>
		<td>TextRank</td>
		<td>11.76</td>
		<td>6.69</td>
		<td>10.98</td>
		<td>12.22</td>
		<td>12.22</td>
		<td>11.31</td>
		<td>11.40</td>
	</tr>
	<tr>
		<td>PositionRank</td>
		<td>12.52</td>
		<td>6.96</td>
		<td>10.55</td>
		<td>12.89</td>
		<td>12.70</td>
		<td>11.32</td>
		<td>11.45</td>
	</tr>
	<tr>
		<td>MDERank</td>
		<td>12.02</td>
		<td>8.95</td>
		<td>11.11</td>
		<td>14.02</td>
		<td>13.99</td>
		<td>13.07</td>
		<td>12.88</td>
	</tr>
	<tr>
		<td>PromptRank</td>
		<td>16.44</td>
		<td>8.44</td>
		<td>14.24</td>
		<td>16.91</td>
		<td>16.53</td>
		<td>14.84</td>
		<td>14.53</td>
	</tr>
	<tr>
		<td rowspan="4">10</td>
		<td>TextRank</td>
		<td>11.43</td>
		<td>5.64</td>
		<td>9.74</td>
		<td>11.98</td>
		<td>12.03</td>
		<td>10.90</td>
		<td>10.92</td>
	</tr>
	<tr>
		<td>PositionRank</td>
		<td>11.46</td>
		<td>5.66</td>
		<td>9.48</td>
		<td>12.19</td>
		<td>12.12</td>
		<td>10.64</td>
		<td>10.64</td>
	</tr>
	<tr>
		<td>MDERank</td>
		<td>12.18</td>
		<td>8.06</td>
		<td>11.49</td>
		<td>13.88</td>
		<td>13.95</td>
		<td>12.76</td>
		<td>12.91</td>
	</tr>
	<tr>
		<td>PromptRank</td>
		<td>15.03</td>
		<td>7.50</td>
		<td>12.31</td>
		<td>15.89</td>
		<td>15.82</td>
		<td>13.80</td>
		<td>13.64</td>
	</tr>
	<tr>
		<td rowspan="4">15</td>
		<td>TextRank</td>
		<td>9.99</td>
		<td>5.04</td>
		<td>7.95</td>
		<td>10.64</td>
		<td>10.81</td>
		<td>9.18</td>
		<td>9.18</td>
	</tr>
	<tr>
		<td>PositionRank</td>
		<td>9.94</td>
		<td>5.02</td>
		<td>7.84</td>
		<td>10.70</td>
		<td>10.74</td>
		<td>9.10</td>
		<td>9.10</td>
	</tr>
	<tr>
		<td>MDERank</td>
		<td>11.54</td>
		<td>7.06</td>
		<td>10.58</td>
		<td>12.80</td>
		<td>12.88</td>
		<td>11.71</td>
		<td>11.69</td>
	</tr>
	<tr>
		<td>PromptRank</td>
		<td>12.59</td>
		<td>7.19</td>
		<td>10.42</td>
		<td>13.90</td>
		<td>13.85</td>
		<td>11.69</td>
		<td>11.60</td>
	</tr>
</table>

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

> Yi Xiang, Chengzhi Zhang\*. Enhancing Unsupervised Keyword Extraction in Academic Papers through the Integration of Highlights and Abstracts. ***Information Processing and Management***, 2024, (submitted)  [[doi]]() [[Dataset & Source Code]](https://github.com/xiangyi-njust/Highlight-KPE)
