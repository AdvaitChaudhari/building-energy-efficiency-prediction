# Building heating & cooling load prediction

How much heating and cooling does a building need, judged only from its design?
Regression on the UCI *Energy Efficiency* dataset (Tsanas & Xifara, 2012): 768 simulated buildings,
8 design inputs (compactness, surface/wall/roof area, height, orientation, glazing area and distribution)
and two targets, heating load and cooling load in kWh/m².

**Models:** linear regression, decision tree, random forest, gradient boosting.
Evaluated with 5-fold CV on the training set plus a 20 % hold-out test set.

**Results (hold-out test set)**

| Model | Heating R² | Heating MAE | Cooling R² | Cooling MAE |
|---|---|---|---|---|
| Linear regression | 0.912 | 2.18 | 0.893 | 2.20 |
| Decision tree | 0.996 | 0.43 | 0.956 | 1.16 |
| Random forest | **0.998** | **0.35** | 0.967 | 1.08 |
| Gradient boosting | 0.997 | 0.39 | **0.975** | **1.06** |

MAE is in kWh/m². 5-fold CV R² on the training set agrees within ±0.01.

**Takeaways**
- Tree ensembles clearly beat linear regression. Height in particular acts more like a switch than a linear effect.
- Cooling load is harder to predict than heating load.
- Roof area, height and compactness dominate. Glazing area is the most important parameter a designer
  can still change once the building's shape is fixed.

Files: `building_energy_efficiency.ipynb`, `ENB2012_data.csv`, report: `Gr_H_Building_Energy_Efficiency_Prediction.pdf`

*University group project (Group H), M.Sc. Smart Energy Systems.*
