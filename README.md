# Ad Fraud Detection System


## Overview
The Ad Fraud Detection System is designed to identify fraudulent activities in online advertising data using Python, Pandas, and SQL. The system analyzes logs, detects anomalies, and helps optimize ad performance.


## Features
- **Data Ingestion**: Reads ad logs from CSV or databases.
  
- **Preprocessing**: Cleans and prepares the data.
  
- **Fraud Detection**: Identifies fraudulent clicks and impressions.
  
- **Visualization**: Provides insights using graphs and charts.
  
- **Database Integration**: Stores results in an SQL database.
  

## Installation

### Prerequisites

- Python 3.7+
  
- Pandas
  
- SQLAlchemy
  
- Matplotlib
  
- SQLite3
  

### Setup
```sh
pip install pandas sqlalchemy matplotlib sqlite3
```


## Usage
### Step 1: Load Data
```python
import pandas as pd

data = pd.read_csv("ad_logs.csv")
print(data.head())
```


### Step 2: Detect Fraud
```python
def detect_fraud(df):
    df["fraud"] = df["clicks"].apply(lambda x: 1 if x > 100 else 0)
    return df

data = detect_fraud(data)
```


### Step 3: Store Results in SQL
```python
from sqlalchemy import create_engine

engine = create_engine("sqlite:///ad_fraud.db")
data.to_sql("fraud_detection", engine, if_exists="replace", index=False)
```


### Step 4: Visualize Data
```python
import matplotlib.pyplot as plt

data["fraud"].value_counts().plot(kind="bar")
plt.title("Fraudulent vs. Non-Fraudulent Ads")
plt.show()
```


## Sample Output
The system generates:
1. **A dataset with flagged fraudulent ads**
2. **A stored SQL table with fraud data**
3. **A bar chart showing fraud trends**

## Future Enhancements
- Implement machine learning for fraud prediction.
- Integrate with real-time data sources.
- Deploy as a web-based dashboard.

## License
This project is open-source under the MIT License.

