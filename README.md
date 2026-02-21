# deep-dispatch
DeepDispatch: An intelligent spatiotemporal system for NYC taxi demand and revenue prediction using K-Means clustering and Deep Learning (LSTM/Transformers).

DeepDispatch addresses the persistent spatial mismatch between taxi supply and passenger demand by replacing reactive driver intuition with proactive, data-driven fleet repositioning. Built on the NYC Yellow Taxi Trip dataset, the system forecasts a future potential revenue heatmap one hour in advance to guide drivers toward high-value zones.

The pipeline integrates spatial clustering, hourly aggregation, and extensive feature engineering including lag features, rolling statistics, cyclical time encoding, and contextual signals such as weekends and extreme weather events. Instead of predicting noisy continuous values, DeepDispatch transforms revenue into five interpretable revenue potential classes (Quiet to Surge), producing a stable and actionable signal for dispatch decisions.

Baseline experiments across Logistic Regression, Random Forest, and XGBoost demonstrate strong performance, with XGBoost currently leading at approximately 79% test accuracy and high ordinal consistency. These results indicate that the engineered spatiotemporal features successfully capture meaningful demand patterns and support reliable taxi fleet repositioning.

Next steps focus on implementing deep learning models (LSTM and Transformer) to better capture long-term temporal dependencies, followed by final evaluation and deployment of the interactive DeepDispatch heatmap for driver decision support.
