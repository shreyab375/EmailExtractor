# Email Extractor Project



## Overview

The Email Extractor project is designed to automate the processing of customer support emails, focusing on intent classification, named entity recognition (NER), urgency and sentiment detection, priority scoring, and intelligent routing. This repository explores two distinct methodologies: a traditional machine learning (ML) approach and a modern approach utilizing Large Language Models (LLMs) within an n8n automation framework.

##  Project Structure

The repository is organized into two primary folders, each representing a distinct methodology:

```
Email-Extractor/
├── Method 1 - Traditional ML Approach/
│   ├── email_extractor.ipynb
│   └── test emails/
│       ├── email1.txt
│       ├── email2.txt
│       └── ... (10 test files)
└── Method 2 - LLM Approach/
    ├── streamlit app/
    │   └── dashboard.py
    └── n8n_workflow.json
```

##  Method 1: Traditional ML Approach

This approach utilizes conventional machine learning techniques, specifically Logistic Regression and Random Forest classifiers, alongside a hybrid approach for entity extraction. The pipeline simulates a real-world email processing workflow.

### Key Features

- **Data Generation**: Synthetic emails are generated using the `AdvancedEmailGenerator` class to create a diverse training dataset across four intents:
  - Refund request
  - Technical issue
  - Account inquiry
  - Product inquiry

- **Intent Classification**: The `MultiModelEmailClassifier` combines ML models with a rule-based classifier for high-accuracy intent prediction using TF-IDF vectorization

- **Named Entity Recognition (NER)**: The `AdvancedEntityExtractor` utilizes pattern-based extraction (regular expressions) for key entities such as names, products, and dates

- **Priority Scoring and Routing**: The `EmailPriorityScorer` and `EmailRoutingEngine` determine the priority of emails and route them to the appropriate department with dynamic Service-Level Agreements (SLAs)

### Performance Highlights

The traditional ML approach demonstrated excellent performance on the test dataset (10 .txt files):

- **Intent Classification**: 100% accuracy
- **Entity Extraction**: 100% accuracy for customer names, products, and dates
- **Average Confidence Score**: 0.94
- **Average Priority Score**: 97.74

### Files in Method 1 Folder

- **`email_extractor.ipynb`**: Complete implementation of the ML pipeline, including data generation, training, evaluation, and end-to-end demonstration
- **`test emails/`**: Contains 10 .txt files used for model evaluation on unstructured email inputs

##  Method 2: LLM Approach using n8n Automations

This approach implements the Email Extractor using n8n, an open-source workflow automation platform, leveraging OpenAI's gpt-4o-mini for advanced email processing. This method provides a scalable, automated pipeline integrated with a real-time monitoring dashboard.

### Workflow Architecture and Features

- **Gmail Trigger**: The workflow starts by automatically monitoring incoming emails via the Gmail trigger node
- **LLM-Powered Processing**: Uses gpt-4o-mini for both intent classification and detailed information extraction (NER)
- **Structured Output**: System prompts guide the LLM to output structured JSON data based on predefined schemas
- **Dynamic Routing**: Automated routing recommendations direct emails to specific departments based on classified intent
- **Google Sheets Integration**: Processed data is automatically appended to a Google Sheet for persistent storage

### Real-Time Visualization with Streamlit

A Streamlit dashboard provides a real-time, interactive interface for monitoring processed emails and LLM pipeline results.

##  How to Use Method 2

### Live Demo

1. **Access the Streamlit Dashboard**: [https://emailextractordashboard.streamlit.app/](https://emailextractordashboard.streamlit.app/)
2. **Send a test email to**: `pegatest2025@gmail.com`
3. **Monitor results**: The n8n workflow will process the email, and structured output will appear on the Streamlit dashboard in real-time

### Files in Method 2 Folder

- **`streamlit app/`**: Contains the Streamlit dashboard application code
- **`n8n_workflow.json`**: The n8n workflow configuration file for the LLM-powered extraction pipeline

##  Installation and Setup

### Method 1 Requirements

```bash
pip install pandas scikit-learn numpy matplotlib seaborn nltk
```

### Method 2 Requirements

For the Streamlit dashboard:
```bash
pip install streamlit pandas plotly
```

For n8n workflow:
- n8n instance (self-hosted or cloud)
- OpenAI API key
- Gmail API credentials
- Google Sheets API credentials

##  Comparison of Approaches

| Feature | Traditional ML | LLM Approach |
|---------|----------------|--------------|
| Accuracy | 100% on test data | Dynamic based on LLM |
| Scalability | Limited | High |
| Real-time Processing | No | Yes |
| Setup Complexity | Low | Medium |
| Cost | Low | Variable (API costs) |
| Flexibility | Limited | High |




