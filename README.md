# NYC Citi Bike – Bike Redistribution using Machine Learning

## Project Overview
This project builds a Machine Learning model to support bike redistribution planning for NYC Citi Bike stations.  
The goal is to determine **how many bikes of each type should be redistributed to each station every morning during the first week of July and November** in order to **minimize bike shortages during rush hours before the evening**.

This project was completed as part of the **Commons XR Predictive Analytics (DS / MLE) assessment**.

---

## Business Question
For the months of **July and November**, how many bikes of each type should be redistributed to each station every morning in the **first week of the month** to reduce shortages during **rush hours (before evening)**?

---

## Dataset
- **Source:** Official NYC Citi Bike Trip Data  
- **Time Period Used:** July 2019 and November 2019  
- **Restrictions Followed:**
  - Data used is **prior to December 2019**
  - Only NYC datasets (no JC datasets)
  - First week of each month (days 1–7)

The dataset contains trip-level records including:
- Trip start and end time
- Start and end station
- Bike type (when available)

---

## Methodology

### 1. Data Preparation
- Uploaded Citi Bike trip data into Google Colab
- Standardized column names across datasets
- Filtered trips to:
  - First week of July and November
  - Rush hours between **7 AM and 4 PM**

### 2. Shortage Definition
A station shortage is approximated using **net bike outflow**:
If more bikes leave a station than arrive during rush hours, the station is assumed to need redistribution.

### 3. Feature Engineering
Features used for modeling:
- Station ID
- Bike type
- Month
- Year
- Day of week

Target variable:
- Predicted bike shortage per station per day

---

## Machine Learning Model
- **Model Used:** HistGradientBoostingRegressor (scikit-learn)
- **Why this model:**  
  - Handles non-linear relationships well  
  - Efficient for medium-to-large datasets  
  - Strong baseline for structured tabular data

### Training Strategy
- **Training Data:** July 2019 (first week)
- **Testing Data:** November 2019 (first week)
- **Encoding:** One-hot encoding for categorical variables

---

## Model Evaluation
Model performance was evaluated using:
- **Mean Absolute Error (MAE)**
- **Root Mean Squared Error (RMSE)**

These metrics measure how close the predicted shortages are to actual observed shortages.

---

## Output
The final output consists of two CSV files:
- `redistribution_plan_july.csv`
- `redistribution_plan_november.csv`

Each file contains:
- Date
- Station ID
- Bike type
- Recommended number of bikes to add each morning

These files represent the recommended daily redistribution plan.

---

## Assumptions
- Rush hours are assumed to be between **7 AM and 4 PM**
- Morning redistribution affects availability throughout the day
- Net bike outflow is a reasonable proxy for station-level shortages
- Bike capacity at stations is not explicitly modeled

---

## Future Improvements
- Include station capacity data
- Add weather and event data
- Use multi-year historical data
- Incorporate real-time bike availability snapshots
- Train separate models for different bike types or station clusters

---

## How to Run
1. Open the notebook inside the `notebooks/` folder
2. Upload the required Citi Bike CSV files to Colab
3. Run all cells from top to bottom
4. Output CSV files will be generated in the `output/` folder

---

## Tools & Libraries
- Python
- Pandas
- NumPy
- scikit-learn
- Google Colab

---

## Author
This project was completed as part of a predictive analytics assessment for Commons XR.

