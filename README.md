DataInsight AI

DataInsight AI is an AI-powered analytics service that automatically analyzes tabular datasets and generates business insights using automated exploratory data analysis (EDA) and a locally hosted large language model via Ollama.

The system allows users to upload a CSV dataset through a FastAPI endpoint. The application performs automated data validation, computes statistical summaries using pandas, and converts those findings into human-readable insights such as executive summaries, key observations, business risks, and strategic recommendations.

The project demonstrates how traditional data analytics pipelines can be combined with generative AI systems to automate data interpretation and decision-support reporting.

Architecture Overview
CSV Upload
   ↓
FastAPI API
   ↓
Data Validation & Cleaning
   ↓
EDA using pandas
   ↓
Prompt Builder
   ↓
Ollama LLM
   ↓
Business Insights
   ↓
JSON API Response
Key Features

CSV dataset upload via REST API

Automated data validation and preprocessing

Exploratory Data Analysis (EDA) using pandas

Aggregation of sales, profit, quantity, and category-level metrics

Prompt orchestration for LLM-based interpretation

Business insight generation using Ollama

Structured API responses with Pydantic models

Logging for production-style observability

Docker containerization for deployment

Tech Stack

Python

FastAPI

pandas

Pydantic

Ollama (LLM)

Uvicorn

Docker

Project Structure
datainsight-ai
│
├── app
│   ├── main.py
│   ├── services
│   │   ├── analysis_service.py
│   │   ├── prompt_service.py
│   │   └── llm_service.py
│   │
│   ├── models
│   │   └── response_models.py
│   │
│   └── utils
│       └── logger.py
│
├── data
│   └── sample
│
├── Dockerfile
├── requirements.txt
└── README.md
API Endpoints
Health Check
GET /health

Response:

{
 "status": "ok"
}
Analyze Dataset
POST /analyze

Upload a CSV dataset and receive automated insights.

Response Example:

{
 "summary": {
   "total_rows": 9994,
   "total_sales": 2297200,
   "total_profit": 286397,
   "top_region_sales": {
     "West": 725457,
     "East": 678781
   }
 },
 "insights": "Executive Summary... Key Observations... Recommendations..."
}
How It Works

User uploads a CSV dataset.

The system validates the dataset and checks required columns.

Pandas performs exploratory data analysis to compute key statistics.

A structured prompt is generated from the dataset summary.

The prompt is sent to a locally hosted LLM via Ollama.

The LLM produces human-readable business insights.

The API returns both the raw summary and generated insights.

Running the Application Locally

Install dependencies:

pip install -r requirements.txt

Run the FastAPI server:

uvicorn app.main:app --reload

Open the interactive API docs:

http://127.0.0.1:8000/docs
Running with Docker

Build the image:

docker build -t datainsight-ai .

Run the container:

docker run -p 8000:8000 datainsight-ai
Future Improvements

Excel dataset support

Visualization dashboards

BigQuery / SQL data source integration

Anomaly detection using machine learning

RAG-based analytics assistant

Human feedback loop for insight evaluation

Author

Chandrayee Kumar
Python Developer | AI/ML Engineer | Data Systems Enthusiast