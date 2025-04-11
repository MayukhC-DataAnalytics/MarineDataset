# MarineDataset

Data Cleaning:
 Checked for 1. Duplicates 2. Handle Missing Values 3. Standardise Formats 4. Correct Data Types

Calculated Columns & Measures:
I created advanced DAX measures to enrich the data and derive meaningful insights:
•	Failure Risk: Categorized engines as "Critical," "High," or "Normal" based on exhaust temperature, oil pressure, and vibration levels.
Failure Risk = IF(
    marine_engine_data[exhaust_temp] > 500 && marine_engine_data[oil_pressure] < 30, "Critical",
    IF(marine_engine_data[vibration_level] > 7, "High", "Normal")
)
•	Fuel Efficiency Index: Evaluated efficiency by dividing total fuel consumption by engine load and RPM.
Fuel Efficiency Index = DIVIDE([Sum.Fuel_Consumption], [SumX_EngineLoad_RPM], 0)
•	Thermal Stress: Flagged engines under "High Stress" conditions when exhaust temperature exceeded 450°C or engine temperature surpassed 95°C.
Thermal Stress = IF(marine_engine_data[exhaust_temp] > 450 || marine_engine_data[engine_temp] > 95, "High Stress", "Normal")
Visualizations:
•	A scatter plot of exhaust vs. engine temperature highlights thermal stress patterns.
•	A pie chart shows the percentage contribution of engines under normal vs. high thermal stress.
•	Additional visuals analyse maintenance status by fuel type and coolant temperature vs. engine load.
Insights Derived from the Dashboard Page 1
1. Thermal Stress Distribution
•	Observation: The pie chart shows that 91.35% of the data points fall under "Normal" thermal stress, while only 8.65% are categorized as "High Stress."
•	Insight: Most engines operate within safe thermal ranges, but a small percentage experience high stress, which could lead to potential failures or reduced efficiency.
2. Relationship Between Exhaust Temperature and Engine Temperature
•	Observation: The scatter plot reveals a clustering of data points around normal exhaust and engine temperature ranges, with outliers indicating higher exhaust temperatures nearing 450°C and engine temperatures exceeding 80°C.
•	Insight: Engines operating near these thresholds are at higher risk of thermal stress. Identifying these engines can help prioritize maintenance or operational adjustments.
3. Engine Type Contribution
•	Observation: The dashboard includes filters for engine types (e.g., "2-stroke Low-Speed," "4-stroke High-Speed"), allowing users to segment data and analyze performance across different engine categories.
•	Insight: Different engine types may exhibit varying levels of thermal stress due to their design and operational profiles. This segmentation enables targeted analysis for specific engine types.
Clarified by the Dashboard
1. What percentage of engines experience high thermal stress?
•	Answered by the pie chart: 8.65% of engines fall under "High Stress," providing a clear understanding of the scale of the issue.
2. Are there any correlations between exhaust temperature and engine temperature?
•	Answered by the scatter plot: A positive correlation is evident, with higher exhaust temperatures often accompanied by elevated engine temperatures.
3. Which engine types are more prone to thermal stress?
•	Answered using filters: By selecting specific engine types, users can identify which categories are more susceptible to high stress conditions.
4. How can operational thresholds be defined for thermal stress?
•	Based on scatter plot trends, thresholds for exhaust temperature (>450°C) and engine temperature (>80°C) can be set as warning levels for proactive monitoring.

-----------------------------------------------------------------------------------------------------------------
Insights Delivered by Report Page 2

Maintenance Status vs. Fuel Type (Stacked Bar Chart):
o	Displays the count of engines in 'Normal', 'Requires Maintenance', and 'Critical' status, segmented by 'Diesel' and 'HFO' fuel types.
o	Observation 1: Both fuel types have a significant number of engines in 'Normal' condition.
o	Observation 2: HFO appears to have a higher proportion of engines in the 'Requires Maintenance' and 'Critical' categories compared to Diesel.
•	Coolant Temp Vs Engine Load (Scatter Plot):
o	Shows the relationship between 'Coolant Temperature' and 'Engine Load'.
o	Observation 1: A general positive trend exists: as 'Engine Load' increases, 'Coolant Temperature' tends to increase.
o	Observation 2: There's considerable variability in 'Coolant Temperature' at different 'Engine Load' levels, suggesting other influencing factors.

•	Exhaust Temp Vs Engine Load (Scatter Plot):
o	Illustrates the correlation between 'Exhaust Temperature' and 'Engine Load'.
o	Observation 1: A strong positive correlation is evident: higher 'Engine Load' typically corresponds to higher 'Exhaust Temperature'.
o	Observation 2: Some instances of relatively high 'Exhaust Temperature' are observed even at lower 'Engine Load'.
•	Engine Type and Manufacturer Filter:
o	Allows users to filter the data based on different engine types and different engine makers (e.g., 2-stroke Low-Speed, 4-stroke High-Speed).
Insights Clarified by the Visualization:
•	Insight 1 (Fuel & Maintenance): There is a preliminary indication that HFO-fuelled engines might experience more maintenance issues compared to Diesel-fuelled engines within this dataset.
•	Insight 2 (Coolant & Load): 'Coolant Temperature' generally increases with 'Engine Load', but the variability suggests a non-linear or multi-faceted relationship.
•	Insight 3 (Exhaust & Load): 'Exhaust Temperature' is strongly influenced by 'Engine Load', with deviations potentially signalling operational anomalies.
•	Insight 4 (Engine Type Segmentation): The dashboard allows for targeted analysis of engine health and performance characteristics based on specific engine technology.

 Why This Dashboard Matters for the Maritime Industry
1️. Proactive Maintenance:
Identify high-risk engines early, reducing unplanned downtime and repair costs.
2️. Fuel Efficiency Optimization:
Insights into fuel consumption patterns help improve operational efficiency and reduce emissions.
3️. Data-Driven Decision Making:
Empower engine makers, technical departments of ship owners, ship building industries with real-time analytics for better engine fitting and management.
4️. Scalable Application basis engine requirements.

