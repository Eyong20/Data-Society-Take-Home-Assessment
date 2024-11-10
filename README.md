# Public Comments Analysis

## Project Overview
This project extracts, analyzes, and provides insights from public comments on a federal regulation docket.

## Setup Instructions
1. Install dependencies:
   ```bash
   pip install pandas requests beautifulsoup4 matplotlib seaborn wordcloud nltk scikit-learn textblob


### Folder Structure

```plaintext
project/
├── README.md
├── 1_federa_regulation_all_dockets.json
├── dockets_documents/
│   ├── FAR-2010-0076.json
│   ├── FAR-2014-0054.json
│   ├── .... all documents related to 'Federal Regulations' dockets
├── document_comments/
│   ├── FAR-2010-0076.json
│   ├── all the comment IDs on docket
├── final_comments/
│   ├── FAR-2010-0076.json
│   ├── the actual comments on documents
└── Federal_regulation_comments_analysis.ipynb
```

## Methodology

- Data Extraction
  - using API
  - using Manual Bulk Download option
- Data Preprocessing
- Exploratory Data Analysis
- Textual Data Analysis
  - Topics Analysis
  - Sentiment Analysis
  - Bot Text Analysis
- Use of LLM (only theoritical idea)

### Data Extraction
- **Data Components**
  - **Proposed Regulation Document**: The official text outlining the new regulation. 
  - **Public Comments**: Feedback from individuals, organizations, and businesses regarding the regulation.
- **Tools & Libraries**:
  - **Web Scraping**: Use libraries like BeautifulSoup, Scrapy, or Selenium to extract data.
  - **APIs**: https://open.gsa.gov/api/regulationsgov/
  - **Manual Download**: For smaller datasets, manually download and process the data.
- **Data Storage**:
  - Store the extracted data in structured formats like CSV, JSON, or databases (e.g., SQLite, PostgreSQL).

### Data Extraction using API
- Created API free version on https://open.gsa.gov/api/regulationsgov/
- Write code that extract all the **Dockets** using keywords such as “Federal Regulations”
- Then extract all the **documents** related to Dockets
- For each document, then I extracted all the **comments**
- Created dataset for analysis

### Data Preprocessing
- Remove data where there are no comments
- Remove which have comments like **See Attached File**
- Remove other records which have invalid comments **Decision, Request for Info etc**
- Only comments type are selected

### Textual Analysis
- Word Frequency Analysis (Unigram and Bigram)
  - This give me the top words/ terms used in commnets
  - We can identify the basic intent or focus of the comments
- Word Cloud
  - To see the top words visually
- Theme Identification
  - Topic Modelibg using LDA
    - Key terms/ topics/ Intent - this gave us the topics discussed in overall comments
  - Clustering using KMeans
    - This gave us different topics/ sub topics being discussed in comments
  - Keyword Extraction
    - Different keywords extraction methods gave us more insights about the topic discussed in comments
- Sentiment Analysis
  - The positive, neutral or negative perspective of the comments
- Comments from bot vs Human
  - We used simple method to see wether comments are posted by bot or human
  - Following are potential comments by bot
    - Same comments posted more than once on different documents
    - Comments posted on same document within very small amount of time

#### Bot vs. Human Comment Differentiation:

- Features to Consider:
   - Language Patterns: Bots might use repetitive or overly formal language. 
   - Timing Patterns: High-frequency submissions in short time frames. 
   - Metadata Analysis: Check for user activity patterns.
- Techniques:
  - Train a classifier using labeled data (if available) to distinguish between bot and human comments. 
  - Utilize anomaly detection methods to identify unusual patterns indicative of bots.
- Visualization:
  - Display sentiment distribution with pie charts or bar graphs. 
  - Correlate sentiment with themes to provide deeper insights.

#### Tech Stack Recommendations
- Programming Language: Python 
- Libraries:
  - Data Handling: pandas, numpy 
  - Web Scraping: BeautifulSoup, requests 
  - Text Processing: nltk, spaCy, gensim 
  - Machine Learning: scikit-learn, tensorflow/keras or pytorch for advanced models 
  - Visualization: matplotlib, seaborn, wordcloud 
  - Sentiment Analysis: TextBlob, VADER, transformers (for BERT-based models)
- Environment:
  - Jupyter Notebook: For interactive analysis and visualization
- Version Control: Git with GitHub or BitBucket
- Deployment:
  - Cloud Services: AWS (S3, Lambda, SageMaker), Google Cloud, or Azure 
  - CI/CD: GitHub Actions or similar for automated testing and deployment

## How to use this
- Clone this repo
```bash
git clone URL
```
- Install Jupyter Notebook and Launch
```bash
jupyter notebook
```
- Open Jupyter Notebook File
- Execute cell by cell to get results