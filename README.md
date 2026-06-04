# Customer Feedback Agentic Workflow

## Overview

Customer feedback is one of the most valuable sources of information for businesses. However, manually reviewing every response, identifying customer sentiment, categorizing issues, and prioritizing actions is time-consuming and difficult to scale.

This project automates the customer feedback analysis process using an Agentic AI Workflow built in n8n.

The workflow collects customer feedback submitted through a Google Form, analyzes the feedback using multiple AI agents powered by Gemini, generates structured insights, assigns priority levels, and stores the results in Google Sheets for further action.

---

# Problem Statement

### Target User

Business owners, customer support teams, product managers, and startup founders who receive customer feedback regularly.

### Pain Point

Organizations often receive a large volume of feedback from customers. Manually reviewing every response to determine:

* Customer sentiment
* Feedback category
* Business impact
* Priority level

requires significant effort and can lead to delays in addressing critical issues.

### Proposed Solution

An automated AI-powered workflow that:

1. Collects customer feedback.
2. Analyzes sentiment.
3. Categorizes feedback.
4. Generates actionable insights.
5. Assigns a priority level.
6. Stores structured results for decision-making.

### Expected Output

A structured analysis of each feedback entry containing:

* Sentiment
* Category
* Insight
* Priority

---

# Workflow Architecture

Google Form Submission

↓

Google Sheets Trigger

↓

Data Preparation Node

↓

Sentiment Analyzer Agent

↓

Category Classifier Agent

↓

Insights Generator Agent

↓

Combine Analysis

↓

Google Sheets Result Update

---

# Workflow Breakdown

## Step 1: Customer Feedback Collection

Customers submit feedback using a Google Form containing:

* Name
* Email
* Feedback
* Rating

The responses are automatically stored in Google Sheets.

---

## Step 2: Trigger Workflow

A Google Sheets Trigger continuously monitors new form submissions.

When a new response is detected, the workflow automatically starts.

---

## Step 3: Data Preparation

A JavaScript node extracts and structures the relevant data from the incoming Google Sheets record.

This ensures a clean and consistent input for all AI agents.

---

## Step 4: Sentiment Analyzer Agent

### Responsibility

Determine the overall sentiment of the customer feedback.

### Input

Customer feedback text.

### Output

```json
{
  "sentiment": "positive"
}
```

Possible values:

* Positive
* Neutral
* Negative

---

## Step 5: Category Classifier Agent

### Responsibility

Classify the feedback into a business category.

### Input

Customer feedback text.

### Output

```json
{
  "category": "support"
}
```

Possible categories:

* Service
* Support
* Product
* Shipping
* Billing
* Other

---

## Step 6: Insights Generator Agent

### Responsibility

Generate a concise business insight and assign a priority level.

### Input

Customer feedback text.

### Output

```json
{
  "insight": "Poor service quality",
  "priority": "high"
}
```

Priority levels:

* Low
* Medium
* High

---

## Step 7: Combine Analysis

A deterministic JavaScript node combines outputs from all AI agents into a single structured response.

Example:

```json
{
  "sentiment": "negative",
  "category": "support",
  "insight": "Poor service quality",
  "priority": "high"
}
```

---

## Step 8: Store Results

The workflow updates the original Google Sheets row with the generated AI analysis.

Additional columns:

* Sentiment
* Category
* Insight
* Priority

---

# Agentic Design Concepts Used

This project applies multiple agentic workflow principles.

## 1. Role-Based Agents

Each AI component has a specific responsibility:

| Agent               | Responsibility                         |
| ------------------- | -------------------------------------- |
| Sentiment Analyzer  | Detect sentiment                       |
| Category Classifier | Categorize feedback                    |
| Insights Generator  | Generate business insight and priority |

---

## 2. Task Decomposition

Instead of using a single prompt for everything, the workflow decomposes the problem into specialized tasks.

This improves:

* Accuracy
* Maintainability
* Explainability

---

## 3. Structured Outputs

Each agent returns JSON-only responses.

Example:

```json
{
  "sentiment": "positive"
}
```

This enables reliable downstream processing.

---

## 4. Tool Usage

The workflow integrates multiple external tools:

* Google Forms
* Google Sheets
* Gemini API
* n8n Automation Platform

---

## 5. Deterministic Control

Non-AI operations are handled through deterministic workflow nodes:

* Trigger handling
* Data extraction
* JSON parsing
* Data combination
* Google Sheets updates

This ensures workflow reliability.

---

# AI vs Deterministic Components

## AI Components

Used where reasoning and interpretation are required.

### Sentiment Analyzer

Determines emotional tone.

### Category Classifier

Identifies business category.

### Insights Generator

Produces business insight and priority.

---

## Deterministic Components

Used where predictable control logic is required.

### Google Sheets Trigger

Detects new responses.

### JavaScript Nodes

* Data preparation
* JSON parsing
* Result combination

### Google Sheets Update

Stores analysis results.

---

# Sample Input

```text
The support team was very slow and unhelpful.
```

---

# Sample Output

```json
{
  "sentiment": "negative",
  "category": "support",
  "insight": "Poor service quality",
  "priority": "high"
}
```

---

# Technologies Used

* n8n
* Google Forms
* Google Sheets
* Gemini API
* JavaScript

---

# Screenshots

Screenshots of the workflow, execution logs, Google Form, and result sheet are available in the `/screenshots` directory.

---

# Workflow Export

The exported n8n workflow is included as:

```text
workflow.json
```

---
