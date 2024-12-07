# Real-Time Stock Data Processing with Azure Event Hubs and Stream Analytics

## Overview
This project demonstrates a real-time streaming data pipeline that filters stock data with prices over $30 and stores the results in Azure Blob Storage. Azure Event Hubs is used as the data ingestion layer, and Azure Stream Analytics processes the data. The final filtered data is stored in Azure Blob Storage.

---

## Steps to Implement the Pipeline

### 1. Event Hub Setup
- **Create an Event Hub Namespace** and an Event Hub instance.
- **Send Sample Data**:
  - Used the Data Explorer feature in Event Hubs to send stock data in JSON format.

Example stock data payload:
```json
{
  "symbol": "AAPL",
  "price": {
    "value": 45
  },
  "timestamp": "2024-12-07T12:45:00Z"
}
```

### 2. Azure Blob Storage Setup
- Created an **Azure Blob Storage account**.
- Configured a **storage container** to store the processed data.

### 3. Azure Stream Analytics Job
- **Input Configuration**:  
  Connected the Stream Analytics job to the Event Hub input.

- **Query**:  
  The following query was used to filter stock prices greater than $30 and select relevant fields:
  ```sql
  SELECT
      symbol AS Symbol,
      price.value AS Price,
      System.Timestamp AS EventTime
  INTO
      [BlobOutput]
  FROM
      [EventHubInput]
  WHERE 
      price.value > 30
  ```
  ### 4. Testing and Verification
- **Data Ingestion**:  
  Sample stock data was sent to the Event Hub using the Data Explorer feature.  
  Example data payload:
  ```json
  {
    "symbol": "MSFT",
    "price": {
      "value": 35
    },
    "timestamp": "2024-12-07T12:50:00Z"
  }


 ### 5. Screenshots


 
 

 

 

