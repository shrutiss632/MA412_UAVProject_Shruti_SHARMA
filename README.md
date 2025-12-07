# MA412_UAVProject_Shruti_SHARMA
UAV Engine Failure Detection Using Machine Learning Airspeed-Based Classification Using the ALFA Dataset

Author: Shruti Sharma Course: MA412 – Machine Learning Institution: IPSA – Paris

1. Overview
This project develops a machine learning–based engine failure detection system for Unmanned Aerial Vehicles (UAVs). The detection uses only airspeed data — commanded (expected speed) and measured (actual speed) — extracted from the ALFA aerodynamic flight dataset.

Engine failures typically cause measurable and early changes in airspeed. This project demonstrates how those deviations can be learned to predict failures reliably.

2. Objectives
Detect engine failures using supervised machine learning

Compare four ML classifiers

Evaluate performance using safety-critical metrics (recall)

Add a custom safety threshold to reduce missed failures

Provide a simple, interpretable pipeline for UAV anomaly detection

3. Dataset
The dataset is sourced from the ALFA UAV flight test logs.

Category Number of Flight Files Normal flights 9 Engine failure flights 22

Total data points: 57,464

Only airspeed logs were used:

%time

field.commanded

field.measured

label (0 = normal, 1 = failure)

flight_id

Dataset is imbalanced because ALFA is a stress-testing dataset. Failure flights are intentionally more frequent.

4. Methods & Preprocessing
Loaded all airspeed CSV logs

Extracted key columns

Labeled based on filename

Standardized features (StandardScaler)

Train-test split (75–25, stratified)

5. Models Implemented
Four supervised learning models were trained:

Logistic Regression

Support Vector Machine (RBF kernel)

Random Forest Classifier

Multi-Layer Perceptron (Neural Network)

All models were evaluated using:

Precision

Recall

F1-score

Confusion matrices

ROC curves

6. Results Summary
Random Forest achieved the best performance:

Accuracy: 91%

Failure Recall: 99% (very important for safety)

Normal Recall: ~58%

Why high recall? Because missing a failure is far worse than a false alarm.

7. Feature Importance
Random Forest revealed:

Measured airspeed = 35% importance

Commanded airspeed = 65% importance

The model detects the gap between commanded and measured speed, which widens during engine failures.

8. Safety Threshold (0.40)
The default probability threshold is 0.50. We lowered it to 0.40 to:

Catch borderline failures

Reduce missed detections

Increase recall (safety priority)

This does increase false positives — but that is acceptable in a safety-critical system.

9. Visualizations
The notebook includes:

Airspeed distributions

Time-series flight plots

ROC curves

Confusion matrices

Precision–recall curve

Feature importance bar chart
