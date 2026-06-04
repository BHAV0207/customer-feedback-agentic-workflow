# Customer Feedback Analyzer

## Overview

This workflow automatically analyzes customer feedback submitted through a Google Form.

The workflow:

1. Captures feedback responses
2. Performs sentiment analysis
3. Classifies feedback category
4. Generates actionable insights
5. Assigns priority level
6. Updates results in Google Sheets

---

## Workflow Architecture

Google Form
↓
Google Sheets Trigger
↓
Sentiment Analyzer
Category Classifier
Insights Generator
↓
Combine Analysis
↓
Save To Results Sheet

---

## AI Outputs

### Sentiment

- Positive
- Neutral
- Negative

### Category

- Service
- Product
- Support
- Shipping

### Priority

- Low
- Medium
- High

---

## Technologies Used

- n8n
- Google Forms
- Google Sheets
- Gemini API

---

## Screenshots

See `/screenshots` folder.

---

## Workflow Export

Workflow JSON is included as:

workflow.json