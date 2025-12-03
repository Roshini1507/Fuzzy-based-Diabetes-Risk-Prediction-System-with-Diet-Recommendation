# Fuzzy Diabetes Risk Prediction and Minimal Diet Recommender

## Objective
Build a Mamdani fuzzy inference system for diabetes risk prediction and a small diet recommender (minimal). The fuzzy system uses interpretable membership functions and rules.

## Dataset
PIMA Indians Diabetes dataset (9 columns: Pregnancies, Glucose, BloodPressure, SkinThickness, Insulin, BMI, DiabetesPedigreeFunction, Age, Outcome).
Train/test split: 70/30 stratified.

## Inputs (with MF summary)
- Glucose (0-300): low, normal, high (trap/trimf)
- BMI (10-60): under, normal, over, obese
- BloodPressure (40-200): low, normal, high
- Insulin (0-900): low, normal, high
- Age (10-100): young, middle, old
- DiabetesPedigreeFunction (0-3): low, med, high

## Output
- Risk (0-100): low (0-35), medium (30-70), high (65-100). Defuzzification: centroid.

## Rules (selected)
~16 rules used. Examples:
1. IF Glucose IS high THEN Risk IS high.
2. IF Glucose IS normal AND BMI IS normal THEN Risk IS low.
3. IF Glucose IS high AND Age IS old THEN Risk IS high.
4. IF BMI IS obese AND BloodPressure IS high THEN Risk IS medium.
5. IF BloodPressure IS high AND Insulin IS low THEN Risk IS high.
... (see script/notebook for full rule list)

## Diet Recommender
Minimal mapping from risk score to brief diet guidance:
- Low risk: balanced diet, maintain calories, avoid sugary drinks.
- Medium risk: modest calorie reduction (~10%), limit simple carbs, increase fiber.
- High risk: stronger calorie & carb control (~15-20%), consult clinician.

## Notes & Future Work
- The fuzzy system is interpretable but may not beat tuned ML models for raw accuracy.
- Future work: tune MFs/rules using ANFIS or optimization, add clinical features, build GUI.
