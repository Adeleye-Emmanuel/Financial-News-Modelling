# Financial News Topic Modeling & Market Sentiment Clustering

## 🧾 Overview

This project represents my first deep dive into the application of Large Language Models (LLMs) and unsupervised NLP techniques to real-world financial data. The goal was to explore how massive volumes of financial news headlines can be distilled into structured insights using advanced topic modeling, sentiment analysis, and temporal visualization.

By synthesizing multiple datasets—including the FNSPID annotated financial headlines, the Financial Phrasebank sentiment corpus, and a 6,000+ headline news collection—I created a unified system capable of:

- Clustering financial headlines into high-quality topic groups
- Modeling the most central themes driving financial news cycles
- Tracking sentiment volatility across time
- Analyzing the trend patterns of top financial topics across tickers and timeframes

The result is a flexible and scalable analysis pipeline that can help analysts, investors, and fintech platforms uncover emergent trends and sentiment shifts from unstructured market text.

## 🚧 Problem Statement

The financial markets are heavily influenced by news, yet the constant flow of headlines creates information overload. Understanding **what** topics are trending, **how** they relate to specific companies, and **whether** the sentiment is volatile or consistent can offer a valuable edge.

However, few tools exist that:
- **Aggregate multi-source financial news** into coherent topic groups
- **Cluster sentiment and themes** without hand-labeled training data
- **Track topic volatility** and **emerging sentiment trends** over time

This project addresses that gap by developing a system that:
- Classifies financial headlines into dynamically discovered topics
- Aligns those topics with companies and dates
- Tracks the rise, fall, and sentiment fluctuation of those themes

A practical use case: An analyst can quickly identify stocks currently associated with trending or volatile news topics—whether driven by macroeconomics, company earnings, or market sentiment.

## 🌟 Why This Project Stands Out

What sets this project apart is not just its use of modern NLP tooling, but its **end-to-end integration** of clustering, topic modeling, and temporal insight:

- ✅ Combined datasets for comprehensive topic coverage across financial domains
- ✅ Clustering with HDBSCAN to uncover hidden structure in headline data
- ✅ Topic modeling with BERTopic to generate interpretable themes
- ✅ Temporal analysis of topic popularity and sentiment volatility
- ✅ Visualizations for top 30 themes and top 15 topic trends across time

The result is a **data storytelling framework** that turns raw financial text into actionable narrative signals.

## 📦 Datasets Used

To ensure topic and sentiment coverage across a wide range of financial contexts, this project draws from multiple well-known and community-curated datasets:

1. **Daily Financial News (6,000+ headlines)**  
   - Source: Kaggle  
   - Description: A rich corpus of dated financial news headlines, ideal for time-series analysis and topic trend visualization.

2. **Financial Phrasebank**  
   - Source: University of Helsinki  
   - Description: Expert-annotated dataset of financial phrases labeled for sentiment. Used to supplement the sentiment clustering component.

3. **FNSPID Dataset** (loaded and preprocessed but not used in modeling because of memory considerations)  
   - Description: A large-scale dataset of financial sentences with tagged named entities. While not used due to hardware limitations, it is included in the repo for users with higher memory capacity who want to integrate entity tagging or finer-grained analysis.

4. **NASDAQ Financial News Dataset** (loaded but not used in modeling because of memory considerations)  
   - Description: External dataset containing massive-scale financial headlines related to NASDAQ-listed stocks. Also provided for exploratory synthesis by advanced users.

> 💡 **Note:** All datasets are preprocessed and partially deduplicated before clustering to maintain topic quality. Sampled subsets are used when memory optimization is required.

## ⚙️ Project Pipeline

This project uses a modular and memory-efficient pipeline designed for large-scale, unsupervised financial text analysis:

### 🔄 Preprocessing
- **Language Detection**: Ensure only English-language headlines are processed.
- **Deduplication**: Remove near-duplicate entries for clustering quality.
- **UMAP 2D Embedding (Batch Mode)**: Memory-aware dimensionality reduction using `batch_generation` for large-scale embeddings.

### 🧠 Clustering & Topic Modeling
- **HDBSCAN Clustering**: Unsupervised density-based clustering of embedded vectors to reveal topic structure.
- **Sampling Top 200,000 Clustered Documents**: Focused modeling on dense topic regions.
- **BERTopic**: Transformer-based topic modeling with interpretable labels.

### 📊 Sentiment Analysis
- **Phrasebank-Driven Sentiment Classification**: Assign sentiment scores to headlines using cross-mapped phrasebank techniques.
- **Volatility Analysis**: Measure standard deviation of sentiment over time for topics and stock tickers.

### 📈 Trend Analysis & Visualization
- **Topic Trends Over Time**: Temporal distribution of the top 15 most prominent topics.
- **Ticker-Topic Mapping**: Connect trending topics with relevant stock tickers.
- **Sentiment Distribution Over Time**: Monitor sentiment swings on both a topic and ticker level.

The result is an end-to-end analytical workflow that transforms raw text into structured insights ready for financial research or downstream modeling.

## 🎯 Key Features

- 🔍 **Unsupervised Topic Discovery**: Use HDBSCAN and BERTopic to discover coherent financial themes from raw text.
- 📊 **Sentiment Clustering**: Analyze sentiment polarity and volatility across time and stocks.
- 📅 **Temporal Topic Tracking**: Visualize how the top 15 themes change in prominence over time.
- 🧠 **Modular & Scalable Design**: Batch-processed embedding and sampling strategy enables handling of very large corpora.
- 🧾 **Analyst-Ready Visualizations**: Output includes visual plots of topic trends, sentiment swings, and volatility charts.
- 📁 **Extendable for Large Datasets**: NASDAQ and FNSPID datasets are preloaded and available for advanced synthesis by users with higher RAM capacity.
