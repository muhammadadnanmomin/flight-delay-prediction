# Flight Delay Minutes Prediction
### End-to-End Machine Learning Project | Streamlit App | Docker Deployment | AWS EC2

This project predicts total monthly delay minutes for any U.S. airline–airport combination using Machine Learning (XGBoost).
The system is deployed as a Dockerized Streamlit application on an AWS EC2 server.

## Live Demo

App URL: https://flight-delay-app.streamlit.app/

## Overview

Flight delays are a major challenge for airlines and airports.
This project uses historical U.S. Department of Transportation (BTS) data (170k+ records) to:

- Predict total monthly delay minutes

- Visualize features and important patterns

- Provide an interactive Streamlit dashboard

- Deploy using Docker + AWS

#### It demonstrates skills in:

- Machine Learning
- Feature Engineering
- Model Training & Evaluation
- Streamlit Web Development
- Docker Containerization
- Cloud Deployment (AWS EC2)
- GitHub Project Management

## Machine Learning Model

Model used: XGBoost Regressor

| Metric       | Score     |
| ------------ | --------- |
| **R² Score** | **0.947** |
| **RMSE**     | 456       |
| **MAE**      | 280       |

XGBoost was chosen for deployment due to its high accuracy and ability to generalize well.

## Project Structure

```flight-delay-prediction/
│
├── data/
│   └── Airline_Delay_Cause.csv          # Original dataset
│
├── models/
│   └── xgb_delay_predictor.pkl          # Trained Machine Learning model
│
├── notebooks/
│   └── notebook.ipynb                   # Jupyter notebook for EDA & model exploration
│
├── app.py                               # Streamlit application
├── Dockerfile                           # Docker configuration for deployment
├── requirements.txt                     # Python dependencies
├── README.md                            # Project documentation
├── test_cases.txt                       # Test cases
└── .gitignore                           # Git ignore rules
```

## Technologies Used

#### Languages & Libraries

  - Python
  - Pandas
  - NumPy
  - Scikit-learn
  - XGBoost
  - Joblib
  - Streamlit

#### Deployment

  - Docker
  - AWS EC2
  - Linux (Ubuntu 22.04)
  - Git + GitHub


## Streamlit App Features

#### 1. User Inputs

  - Airline (carrier)
  - Airport
  - Year & Month
  - Season
  - Arrival flights
  - Cancelled/diverted flights
  - Delay rate
  - Total delay causes

#### 2. Outputs

  - Predicted total delay minutes
  - Converted value:
  - Hours
  - Days
  - Clean UI with tooltips and explanations

## Test Cases

Sample test cases are included in **[test_cases.txt](test_cases.txt)**.  
Users can copy the values and enter them directly in the Streamlit app.

This helps quickly verify:
- High delay scenarios
- Low delay scenarios
- Different airlines
- Different airports
- Seasonal patterns

## Docker Deployment

#### Build image

```docker build -t flight-delay-app .```

#### Run container locally

```docker run -p 8501:8501 flight-delay-app```

## AWS EC2 Deployment (Production)

#### 1. Install Docker

```sudo apt update
sudo apt install -y docker.io
sudo systemctl start docker
sudo usermod -aG docker ubuntu
```

#### 2. Clone repository

```git clone https://github.com/muhammadadnanmomin/flight-delay-prediction.git
cd flight-delay-prediction
```

#### 3. Build image

```docker build -t flight-delay-app .```

#### 4. Run on port 80

```docker run -d -p 80:8501 flight-delay-app```

#### 5. Access the app

```http://16.16.251.222/```


## Model Training Pipeline
  
  1. Data cleaning
  2. Handling missing values
  3. Feature engineering
  4. Encoding categorical variables
  5. Train-test split
  6. Model training (XGBoost)
  7. Evaluation
  8. Saving model using Joblib

## EDA Highlights

  - Delay distribution across airlines
  - Delay causes (weather, carrier, NAS, etc.)
  - Monthly/seasonal patterns
  - Airport-wise delay analysis
  - Correlation heatmap

## Author

Adnan Momin

LinkedIn: https://www.linkedin.com/in/adnanmomin/

GitHub: https://github.com/muhammadadnanmomin
