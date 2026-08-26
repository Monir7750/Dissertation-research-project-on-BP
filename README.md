Climate Risk Disclosure in FTSE 100 Energy Companies: A Longitudinal NLP Analysis of BP's Annual Reports (2015–2024)

MSc Business Analytics — Business Analytics Project (BUSI 1783) University of Greenwich

Author: Md Monir Hossain (Student ID: 001487750) Supervisor: Mr. Thamaraikani Chandrasooden.
1. Overview

This repository contains the full data and code for a longitudinal Natural Language Processing (NLP) study of how BP plc's climate risk disclosure language evolved across a full decade (2015–2024). The project applies computational text analysis to BP's annual reports to test whether the company's expanding climate vocabulary reflects substantive governance improvement or strategic impression management.

A distinctive feature of the design is the two-stream comparison of mandatory risk-factor disclosures (US Form 20-F) against voluntary risk-management narratives within the same annual report, which operationalises the theoretical tension between legitimacy theory (Suchman, 1995) and impression management theory (Merkl-Davies and Brennan, 2007).

Research Questions
RQ1: How have the thematic composition and linguistic tone of climate risk disclosures in BP's annual reports evolved between 2015 and 2024?
RQ2: To what extent do shifts in BP's climate risk disclosure language correspond to key external regulatory and strategic milestones?


2. Data Source
 
Item	Detail
Source	BP plc Annual Reports and Form 20-F, fiscal years 2015–2024 (10 documents)
Origin	Publicly available PDFs from BP's investor relations website (bp.com/annualreport)
Sections used	"Risk Factors" (mandatory / Form 20-F) and "Risk Management" (voluntary / strategic report)
Extraction	Sections identified manually and extracted programmatically with pdfplumber (multi-column aware)
Corpus size	20 documents (10 years × 2 streams), ≈ 49,839 words total
Ethics	Only public corporate documents; no human subjects, personal, or proprietary data; Kaggle not used

The processed dataset is provided in this repository as an Excel workbook with nine worksheets (README, Master WIDE, Master WIDE (full — 63 columns), Master LONG, Divergence (gap), Topic model, Event timeline, Corpus manifest, and Data dictionary).

3. Repository Structure
   
BP-Climate-Risk-NLP/
├── README.md                                   # This file
├── BP_Climate_Risk_NLP_Code File.ipynb            # Compiled Python notebook (full pipeline + charts)
├── BP_Climate_Risk_NLP_Dataset_SUBSECTION_20152024.xlsx   # Processed dataset (9 sheets)
├── data/
│   └── corpus/                                 # Extracted plain-text corpus (per year, per stream)
├── figures/                                    # Exported charts (PNG, 300 dpi)
└── requirements.txt                            # Python dependencies

4. Methodology

The analytical pipeline combines three complementary NLP techniques, triangulated to strengthen validity:

* Keyword Frequency Analysis — a TCFD-aligned climate lexicon (climate change, transition risk, physical risk, net zero, carbon, energy transition, Paris Agreement), normalised to occurrences per 1,000 words.
* Loughran–McDonald Sentiment Analysis — the finance-specific lexicon (negative, positive, uncertainty, litigious, constraining), with a net tone score computed per document and compared across the two streams.
* LDA Topic Modelling — Latent Dirichlet Allocation via Gensim, with the number of topics optimised by C_v coherence (Röder, Both and Hinneburg, 2015). The optimal solution was k = 3 (C_v = 0.613).

Pre-processing: lowercasing and tokenisation (NLTK), domain-specific stopword removal, and lemmatisation (spaCy).

5. Key Findings
   
#  Climate keyword intensity rose ~8× over the decade, from 1.11 to 9.03 per 1,000 words, with the sharpest inflection around BP's 2020 net-zero announcement.
#  A persistent negative tone gap (mean −0.386, negative in every year) between mandatory and voluntary streams — mandatory filings are consistently more cautious and legally constrained.
#  LDA (k = 3) shows a structural divergence: mandatory sections are dominated by an operational-threat topic throughout, while voluntary sections shift from board-oversight framing to a governance-leadership narrative after 2021.
Disclosure shifts align with regulatory/strategic milestones (TCFD 2017, net-zero pledge 2020, FCA mandatory rule 2022), but the mandatory–voluntary divergence is consistent with impression management rather than uniform substantive improvement.

6. Requirements
   
Python 3.9+
pdfplumber, spacy, nltk, gensim, pandas, numpy, matplotlib, seaborn, openpyxl, pyLDAvis
spaCy English model: python -m spacy download en_core_web_sm
NLTK data: stopwords, punkt, wordnet
Install dependencies:

pip install -r requirements.txt
python -m spacy download en_core_web_sm

7. How to Run:
   Clone the repository

   Install dependencies (see Section 6).
Open and run the ipynb notebook file top to bottom: with the dataset should be aligned exactly same path along with the jupyter notebook.
The notebook loads the corpus, runs all three analyses, and reproduces every chart and the dataset workbook.

8. Outputs

Running the notebook reproduces:

*  Time-series charts of climate keyword intensity (combined, mandatory, voluntary)
*  Loughran–McDonald sentiment and net-tone trends, including the mandatory–voluntary tone gap
*  The LDA coherence sweep, topic terms, and the 20-document topic-distribution matrix
An event-timeline overlay mapping metrics to ten regulatory/strategic milestones

9. Academic Integrity & AI Use

This work was completed in accordance with the University of Greenwich AI Usage Guidance. All substantive analysis, interpretation, and conclusions are the author's own. AI tools were used only for permitted support (outlining, proofreading, and understanding methods), as detailed in the accompanying Declaration of AI Use form. The analysis was conducted without tailoring or filtering NLP outputs to support pre-determined conclusions.

10. Key References
    
Loughran, T. and McDonald, B. (2011) 'When is a liability not a liability? Textual analysis, dictionaries, and 10-Ks', The Journal of Finance, 66(1), pp. 35–65.
Merkl-Davies, D.M. and Brennan, N.M. (2007) 'Discretionary disclosure strategies in corporate narratives', Journal of Accounting Literature, 26, pp. 116–196.
Röder, M., Both, A. and Hinneburg, A. (2015) 'Exploring the space of topic coherence measures', WSDM '15, pp. 399–408.
Suchman, M.C. (1995) 'Managing legitimacy: strategic and institutional approaches', Academy of Management Review, 20(3), pp. 571–610.
Task Force on Climate-related Financial Disclosures (TCFD) (2017) Recommendations of the TCFD: Final Report. Basel: Financial Stability Board.

This repository accompanies the MSc Business Analytics Project submitted at the University of Greenwich (2026).
