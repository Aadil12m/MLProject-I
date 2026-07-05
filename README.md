# Student Performance Predictor

## Overview
This project is an end-to-end Machine Learning web application designed to predict student performance based on demographic and background variables. It features a scalable, object-oriented architecture with a fully automated CI/CD pipeline for cloud deployment.

## Architecture
The repository is structured as a custom Python package with modular components:
- **Data Ingestion**: Handles the reading and splitting of raw datasets into training and testing sets.
- **Data Transformation**: Manages feature engineering, missing value imputation, categorical encoding, and numerical scaling using Scikit-Learn pipelines.
- **Model Trainer**: Automatically evaluates multiple regression algorithms (including XGBoost, CatBoost, and Random Forest) and serializes the highest-performing model based on R-squared accuracy.
- **Prediction Pipeline**: A robust inference pipeline that loads serialized artifacts to serve real-time predictions.
- **Web Interface**: A RESTful web application built with Flask to collect user input and display predictions.

## Technology Stack
- **Language**: Python 3.10
- **Machine Learning**: Scikit-Learn, XGBoost, CatBoost, Pandas, NumPy
- **Web Framework**: Flask
- **DevOps & Cloud**: Docker, GitHub Actions, Microsoft Azure App Service, Azure Container Registry

## Setup and Installation

### Prerequisites
- Python 3.10
- Docker (optional, for containerized execution)

### Local Execution
1. Clone the repository:
   ```bash
   git clone https://github.com/Aadil12m/BasicMLProject.git
   cd BasicMLProject
   ```

2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Run the Flask application:
   ```bash
   python app.py
   ```

4. Access the web interface at `http://localhost:5000`.

## CI/CD Pipeline
This project utilizes GitHub Actions for continuous integration and deployment. Upon pushing to the `main` branch, the workflow automatically:
1. Builds a Docker image containing the application and its dependencies.
2. Pushes the image to an Azure Container Registry.
3. Triggers a webhook to deploy the latest container to a Microsoft Azure App Service instance.

## Repository Structure
- `src/`: Contains the core machine learning package modules, including custom logging and exception handling.
- `artifacts/`: Stores the serialized model (`model.pkl`) and data preprocessor (`preprocessor.pkl`).
- `templates/`: HTML templates for the Flask web application.
- `.github/workflows/`: Contains the YAML configuration for the GitHub Actions pipeline.
- `app.py`: The entry point for the Flask web application.
- `Dockerfile`: Instructions for containerizing the application.