# cardiovascular_disease_model
Comparing multiple models in Python to predict cardiovascular disease based on patient vitals.

Input variables:

ID: Unique identifier for each patient. <br />
age: Age of the patient in days. <br />
age_years: Age of the patient in years (derived from age). <br />
gender: Gender of the patient. Categorical variable (1: Female, 2: Male). <br />
height: Height of the patient in centimeters.
weight: Weight of the patient in kilograms.
ap_hi: Systolic blood pressure.
ap_lo: Diastolic blood pressure.
cholesterol: Cholesterol levels. Categorical variable (1: Normal, 2: Above Normal, 3: Well Above Normal).
gluc: Glucose levels. Categorical variable (1: Normal, 2: Above Normal, 3: Well Above Normal).
smoke: Smoking status. Binary variable (0: Non-smoker, 1: Smoker).
alco: Alcohol intake. Binary variable (0: Does not consume alcohol, 1: Consumes alcohol).
active: Physical activity. Binary variable (0: Not physically active, 1: Physically active).
cardio: Presence or absence of cardiovascular disease. Target variable. Binary (0: Absence, 1: Presence).
bmi: Body Mass Index, derived from weight and height. Calculated as BMI = (weight in kg) / (height in m)^2

Output:
bp_category: Blood pressure category based on ap_hi and ap_lo variables. Multi-class variable that includes "Normal", "Elevated", "Hypertension Stage 1", "Hypertension Stage 2", and "Hypertensive Crisis".
error_score: Custom evaluation metrics using functions imported from sklearn.metrics to get false positives and negatives, and also evaluate individual model performance. 


## Sources

Kaggle Cardiovascular Disease Dataset
https://www.kaggle.com/datasets/colewelkins/cardiovascular-disease?select=cardio_data_processed.csv
