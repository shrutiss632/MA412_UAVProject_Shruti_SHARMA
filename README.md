#UAV Engine Failure Detection Using Machine Learning
#Author: Shruti Sharma
#Course: MA412 – Machine Learning
#Institution: IPSA Paris

#Overview:
This project develops a machine learning–based engine failure detection system for Unmanned Aerial Vehicles (UAVs) using airspeed data. The main idea is that engine failures cause early and measurable deviations between the commanded airspeed (what the UAV is instructed to fly at) and the measured airspeed (what the UAV actually achieves)

#Using these deviations, supervised learning models were trained to classify flights as normal or engine-failure scenarios.

#The project uses the ALFA UAV flight dataset, which contains real logs from stress-tested UAV flights.

#Objectives:
-Detect engine failures based solely on airspeed data
-Compare multiple supervised classification models
-Evaluate performance using safety-critical metrics, especially recall
-Implement an adjusted safety threshold to reduce missed failures
-Provide an interpretable and reproducible ML pipeline

#Dataset: The dataset comes from the ALFA UAV project and contains flight logs in CSV format.

#Category	Number of flight files:
Normal flights	9
Engine failure flights	22
(The dataset is intentionally imbalanced because it comes from stress-testing experiments where engine failures occur more frequently than in standard operations)

#A total of 57,464 data points were used, extracted only from airspeed logs.
The following columns were used:
- %time
- field.commanded
- field.measured
- label (0 = normal, 1 = failure)
- flight_id

#Methods
- All relevant CSV files were loaded from the processed ALFA dataset.
- Key airspeed features (commanded and measured) were extracted.
- Data was labeled based on filenames.
- StandardScaler was used to normalize features.
- A stratified train-test split (75/25) was applied to preserve class ratios.

#Models Implemented
Four supervised learning models were trained and compared:
- Logistic Regression
- Support Vector Machine (RBF kernel)
- Random Forest Classifier
- Multi-Layer Perceptron (Neural Network)

Evaluation metrics included precision, recall, F1-score, confusion matrices, ROC curves, and probability-based analysis.

#Results: The Random Forest model achieved the best performance
- Accuracy: approximately 91 percent
- Recall for engine failures: approximately 99 percent
- Recall for normal flights: approximately 58 percent
(Engine failure recall was prioritised, as missing a failure poses a high safety risk.)

#Feature Importance
Random Forest analysis showed:
- Commanded airspeed: ~65 percent importance
- Measured airspeed: ~35 percent importance
The model primarily detects the growing gap between expected and actual speed during failures.

#Safety Threshold
The default classification threshold (0.50) was lowered to 0.40 to reduce the chance of missed failures.
A lower threshold increases recall but also increases false alarms.
In safety-critical UAV applications, this trade-off is acceptable.

#Visualisations
The notebook includes the following plots:
- Airspeed distributions (normal vs failure)
- Time-series comparison of commanded vs measured airspeed
- ROC curves for all models
- Confusion matrices
- Precision-recall curve
- Feature importance chart
  
#Repository Structure
MA412_Project.ipynb – Main notebook with full pipeline

README.md – Documentation

#How to Run

1. Open the notebook in Google Colab.

2. Mount Google Drive.

3. Update dataset paths if needed.

4. Run the cell
