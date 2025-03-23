# InfluenceIQ - AI-Powered Influencer Ranking

## Overview
InfluenceIQ is an AI-powered system designed to measure and rank influencers based on their *engagement, credibility, and sentiment analysis. Traditional popularity metrics like likes and followers often misrepresent an influencer's true impact. Our system introduces a **data-driven approach* to identify individuals with *long-term influence* rather than fleeting viral success.

## Features
- *Data Processing & Cleaning*: Handles missing values, feature engineering, and normalization.
- *Engagement Scoring*: Calculates influencer impact based on likes, comments, and views.
- *Credibility Ranking*: Uses metrics like verification status, follower count, and sentiment analysis.
- *Sentiment Analysis: Evaluates audience perception using a fine-tuned **RoBERTa* model.
- *AI-Driven Ranking*: Implements a weighted scoring system to provide a reliable influencer ranking.

## Methodology
### 1. **Dataset Processing (dataset.ipynb)**
- Loads influencer data and cleans it by handling missing values.
- Computes *average likes, comments, and views* for each influencer.
- Calculates *engagement rate*:
  \[ \text{Engagement Rate} = \frac{\text{avgLikes} + \text{avgComments} + \text{avgViews}}{\text{followersCount}} \]
- Assigns a credibility score based on:
  \[ \text{credibilityScore} = \text{verified bonus} + 10 \log_{10}(\text{followers} + 1) + 5 \log_{10}(\text{posts} + 1) \]

### 2. **Influencer Ranking (app.ipynb)**
- *Min-Max Normalization* to standardize values:
  \[ X' = \frac{X - X_{\min}}{X_{\max} - X_{\min}} \]
- *Ranking Score Calculation*:
  \[ \text{ranking score} = 0.15 \times \text{normalized engagement} + 0.85 \times \text{normalized credibility} \]
- Uses *Dense Ranking Method* to rank influencers based on ranking_score.

### 3. *Sentiment Analysis for Credibility*
- Uses *tw-roberta-base-sentiment-FT-v2* model to classify audience comments as *positive, neutral, or negative*.
- Computes *Net Sentiment Score*:
  \[ \text{Net Sentiment} = \frac{\text{Positive} - \text{Negative}}{\text{Positive} + \text{Negative}} \]
- Adjusts credibility score using sentiment-driven engagement metrics.

## Installation & Usage
### Prerequisites
Ensure you have Python installed along with the following libraries:
bash
pip install pandas numpy transformers torch scikit-learn


### Running the Notebooks
1. *Dataset Preparation:* Run dataset.ipynb to clean and preprocess influencer data.
2. *Ranking & Sentiment Analysis:* Execute app.ipynb to compute credibility scores and rank influencers.

## Conclusion
InfluenceIQ provides a *reliable, AI-powered ranking system* that helps brands, investors, and the public identify *true industry leaders* based on *data-driven insights*, rather than just social media popularity.