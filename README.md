# Flight Delay Minutes Prediction
### End-to-End Machine Learning System | XGBoost | Streamlit | Docker | AWS
Live App: https://flight-delay-app.streamlit.app/

## Problem Statement
Flight delays create major operational challenges for airlines and airports, impacting customer satisfaction, scheduling, and costs.
Most publicly available datasets provide historical insights but do not offer a predictive, interactive system for estimating future delay impact.

This project builds a production-ready machine learning system to predict total monthly delay minutes for any U.S. airline–airport combination using historical DOT (BTS) data.

## Why This Project Matters
Accurate delay estimation helps with:

- Capacity planning
- Crew scheduling
- Resource allocation
- Disruption management
- Customer experience optimization

This project goes beyond modeling and demonstrates a full ML lifecycle:
from raw data → features → model → deployment → user-facing application.

## Dataset
Source: U.S. Department of Transportation (BTS)
Size: 170,000+ monthly aggregated records
Granularity: Airline × Airport × Month
Time Range: Multi-year historical data

Key Variables

- Airline (carrier)
- Airport
- Month / Year
- Arrival flight counts
- Cancellations and diversions
- Delay causes (weather, NAS, carrier, etc.)
- Target: Total delay minutes

## Approach
#### 1. Exploratory Data Analysis (EDA)

- Delay distribution across airlines
- Seasonal and monthly patterns
- Airport-wise congestion analysis
- Correlation analysis of delay causes

#### 2. Feature Engineering

- Seasonal encoding
- Temporal features
- Airline- and airport-specific behavior patterns
- Aggregated delay cause features

#### 3. Modeling

- Trained and compared multiple regression models
- Selected XGBoost for its non-linearity handling and generalization

#### 4. Evaluation

- Used R², RMSE, and MAE for performance comparison
- Conducted error analysis to understand failure cases

#### 5. Deployment

- Built an interactive Streamlit app
- Containerized using Docker
- Deployed on AWS EC2

## Model Performance
Final Model: XGBoost Regressor
| Metric | Value |
| ------ | ----- |
| R²     | 0.947 |
| RMSE   | 456   |
| MAE    | 280   |

XGBoost was chosen due to its ability to capture nonlinear relationships and perform well on structured tabular data.

## Web Application Features
#### User Inputs
- Airline
- Airport
- Year & Month
- Season
- Arrival flights
- Cancelled/diverted flights
- Delay rate
- Delay cause breakdown

#### Outputs
- Predicted total delay minutes
- Converted to:
  - Hours
  - Days
    - Clear UI with tooltips and explanations

This allows users to run what-if scenarios and explore delay behavior interactively.

## Test Cases
Predefined test cases are available in test_cases.txt to validate:
- High-delay scenarios
- Low-delay scenarios
- Airline-specific patterns
- Seasonal variations

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

## Tech Stack
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

## Run Locally with Docker
#### Build the image
```
docker build -t flight-delay-app .
```

#### Run the container
```
docker run -p 8501:8501 flight-delay-app
```

☁️ Production Deployment (AWS EC2)
#### Install Docker
```
sudo apt update
sudo apt install -y docker.io
sudo systemctl start docker
sudo usermod -aG docker ubuntu
```

#### Clone the repository
```
git clone https://github.com/muhammadadnanmomin/flight-delay-prediction.git
cd flight-delay-prediction
```

#### Build and run
```
docker build -t flight-delay-app .
docker run -d -p 80:8501 flight-delay-app
```

## Key Learnings

- Importance of feature engineering for structured data
- Tradeoffs between model complexity and interpretability
- Handling seasonality in tabular ML problems
- Designing consistent training vs inference pipelines
- Deploying ML systems for real-world usage

## Author

Adnan Momin

LinkedIn: https://www.linkedin.com/in/adnanmomin/

GitHub: https://github.com/muhammadadnanmomin
