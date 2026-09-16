Electric Vehicles Specification Analysis (2025)
Exploratory Data Analysis, Statistical Testing & Visual Insights

A Python-based data analytics project examining the specifications of 478 electric vehicle models available in 2025. The project walks through 10 guided questions covering data cleaning, descriptive statistics, correlation analysis, hypothesis testing, and visualization, and closes with business recommendations for manufacturers, consumers, and policymakers.

📊 Dataset
File: electric_vehicles_spec_2025.csv
Source: ev-database.org
Size: 478 vehicle models × 22 columns
Fields: brand, model, top speed, battery capacity & type, number of cells, torque, efficiency, range, acceleration, fast-charging power, drivetrain, segment, body dimensions, body type, and more
🛠️ Tools & Libraries
Python: Pandas, NumPy, Matplotlib, Seaborn, SciPy
Notebook environment: Jupyter (nbformat / nbclient for reproducible, programmatically-built execution)
🔍 Key Data Quality Findings

Before analysis, EDA surfaced several inconsistencies that shaped how later questions were approached:

battery_type is constant — all 478 vehicles use Lithium-ion chemistry, so there is no chemistry variation to compare against.
model is a near-unique identifier (477 distinct values across 477 non-null rows), not a repeatable category — direct "group by model" charts are uninformative, so car_body_type / segment were used as meaningful proxy groupings where appropriate.
cargo_volume_l was stored as text and contained a non-numeric entry ("10 Banana Boxes"), requiring coercion to numeric.
Missing values were present in number_of_cells (~42%), torque_nm, fast_charging_power_kw_dc, towing_capacity_kg, and fast_charge_port.
number_of_cells is heavily right-skewed with extreme outliers, reflecting different battery-pack cell architectures across manufacturers.
📓 Questions Covered
#	Question	Techniques Used
1	EDA & data cleaning	Pandas, missing-value/duplicate checks, dtype coercion
2	top_speed_kmh vs battery_type	Pandas groupby, descriptive statistics
3	battery_capacity_kWh across model	Matplotlib bar charts
4	number_of_cells across model categories	Seaborn boxplots, IQR outlier detection
5	Correlation matrix of numerical variables	Seaborn heatmap
6	Top vs. bottom performing vehicles	Pandas ranking & comparison
7	Quartiles, variance, std deviation	NumPy (percentile, var, std)
8	Independent t-test (AWD vs FWD top speed)	SciPy (ttest_ind, Levene's test)
9	4+ combined visualizations	Matplotlib & Seaborn (scatter, regplot, histograms, jointplot, violin)
10	Business insights & recommendations	Narrative synthesis
📈 Highlights
Battery capacity and cell count scale with vehicle class — SUVs and estate/station wagons carry the largest packs; hatchbacks and vans the smallest.
Top speed correlates only weakly with battery capacity — motor/drivetrain choice matters more than pack size for outright speed.
AWD vehicles show a statistically significant top-speed advantage over FWD vehicles (independent t-test, p < 0.05), consistent with AWD's more common use in performance/luxury segments.
Roughly 1 in 10 vehicles is a cell-count outlier by the IQR rule, pointing to differing cell-format strategies across manufacturers rather than data errors.
📁 Repository Contents
├── electric_vehicles_spec_2025.csv   # Source dataset
├── EV_2025_Analysis.ipynb            # Full executed Jupyter notebook (all 10 questions)
├── EV_2025_Analysis.pdf              # PDF export of the executed notebook
└── README.md
▶️ Running the Notebook
bash
pip install pandas numpy matplotlib seaborn scipy jupyter
jupyter notebook EV_2025_Analysis.ipynb

Data Analytics Coursework Submission — Source: electric_vehicles_spec_2025.csv, 478 records.
