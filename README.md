# Superstore Sales Analysis and Forecasting 

### 1. OBJECTIVE
**Background**

Effective sales analysis is critical for organizations to optimize revenue generation, improve strategic planning, and enhance profitability. Understanding historical sales patterns, regional performance, product category contributions, and discount effects enables businesses to refine their approach to pricing, inventory management, and marketing. Moreover, forecasting future sales ensures better decision-making, aiding in budgeting and resource allocation.

**Problem Statement**

The company lacks a comprehensive understanding of sales performance across different time periods, regions, and product categories. Additionally, the effect of discounts on sales volume and profitability remains unclear, making it challenging to design an optimal pricing strategy. The impact of shipping modes on sales also needs evaluation to identify cost-effective logistics solutions. Furthermore, the absence of reliable sales forecasting impedes effective demand planning and revenue projections.

**Business Objectives**

1.	Trend Analysis: Examine historical sales data to identify yearly trends, helping in strategic decision-making.
2.	Regional Comparison: Assess sales performance across different regions to pinpoint top-performing and underperforming areas.
3.	Product Category Contribution: Identify which product categories and subcategories drive the highest sales and profitability.
4.	Discount Impact Analysis: Determine how discounts influence sales volume and overall profitability to optimize pricing strategies.
5.	Shipping Mode Evaluation: Analyse the correlation between sales and different shipping methods to improve logistics efficiency.
6.	Sales Forecasting: Develop predictive models to forecast future sales, aiding in inventory and resource planning.

By addressing these objectives, the company will be better equipped to enhance sales strategies, optimize pricing structures, and improve operational efficiency for sustained growth and profitability.

### 2. DATASET

To conduct the sales analysis, data has been sourced from three different channels, ensuring a comprehensive and diverse dataset for accurate insights.

1.	CSV File - The dataset, sourced from Kaggle, contains transactional sales data from 2011 to 2015. It provides structured sales records, including order details, customer information, and product performance.
Link - *https://www.kaggle.com/datasets/jr2ngb/superstore-data?select=superstore_dataset2011-2015.csv*

2.	SQL Database - The CSV data from Kaggle has been converted into an SQL database to facilitate efficient querying and relational data analysis.
Link - *https://www.kaggle.com/datasets/fatihilhan/global-superstore-dataset*

3.	API Integration - Additional data is accessed via an API, providing supplementary sales insights to enhance analytical depth and accuracy.
Link - *https://www.kaggle.com/datasets/shekpaul/global-superstore*

The dataset contains these columns.
* Row ID – Unique identifier for each row in the dataset.
* Order ID – Unique identifier for each order.
* Order Date – The date when the order was placed.
* Ship Date – The date when the order was shipped.
* Ship Mode – The shipping method used (e.g., Standard Class, First Class).
* Customer ID – Unique identifier for each customer.
* Customer Name – Name of the customer who placed the order.
* Segment – The customer segment (e.g., Consumer, Corporate, Home Office).
* City – The city where the order was placed.
* State – The state where the order was placed.
* Country – The country where the order was placed.
* Market – The market region.
* Region – The geographic region where the order was placed.
* Product ID – Unique identifier for each product.
* Category – The category of the product (e.g., Office Supplies, Technology, Furniture).
* Sub-Category – The sub-category of the product (e.g., Chairs, Phones, Binders).
* Product Name – The name of the specific product ordered.
* Sales – The total sales amount for the order.
* Quantity – The number of units of the product ordered.
* Discount – The discount applied to the order.
* Profit – The profit generated from the sale.
* Shipping Cost – The cost incurred for shipping the order.
* Order Priority – The priority level of the order (e.g., Low, Medium, High, Critical)

### 3. ETL PIPELINE

To standardize and streamline data usage, data from all three sources (CSV, SQL database, and API) have been merged into a single dataset. This unified dataset is stored in the form of a CSV file, making it easier to process and analyse. Python has been used as the primary programming language to handle data extraction, transformation, and loading (ETL), ensuring efficient data manipulation and integration.

<img width="780" height="454" alt="image" src="https://github.com/user-attachments/assets/6172d330-a14e-49a4-ba97-85e9fd9e124a" />

                                  Fig – Architecture for the ETL Pipeline

### 4. EXPLORATORY DATA ANALYSIS

Data Structure & Quality Check:

* The dataset consists of 153,870 rows and 23 columns, containing essential information about orders, customers, products, and sales transactions.
* A thorough null value analysis was conducted, confirming that no missing values exist in any column.
* The date fields (Order Date, Ship Date) were stored as object (string) type initially and converted to datetime format for accurate time-based analysis. This conversion allowed:
  * Deriving additional features such as order month and year.

<img width="940" height="419" alt="image" src="https://github.com/user-attachments/assets/3475af9f-fe21-47ed-90bb-05e5c6f57dc5" />

Observations:
* The Central region has the highest sales, generating 8.47 million in revenue. This suggests a strong customer base or high demand in this region.
* South (4.80M), North (3.74M), and Oceania (3.30M) follow as strong markets. These regions contribute significantly but are not as dominant as Central.
* Canada (0.20M) and Caribbean (0.97M) show the lowest sales. This indicates low market penetration or lower demand in these areas.

<img width="940" height="688" alt="image" src="https://github.com/user-attachments/assets/391fc3ce-54d0-4ad4-a560-cec4e8a08cc1" />

Observations:
* The pie chart shows that Technology has the highest sales contribution at 37.53%, making it the dominant category.
* Furniture (32.52%) and Office Supplies (29.96%) have similar sales shares, indicating a relatively balanced revenue distribution across categories.
* The chart suggests that Technology is the key revenue driver, while Furniture and Office Supplies still play significant roles.

<img width="940" height="504" alt="image" src="https://github.com/user-attachments/assets/b3ef1991-a0f3-4bfc-8f5b-2a6dc9c5e71a" />

Observations:
* Phones (5.12M), Copiers (4.53M), Chairs (4.51M), and Bookcases (4.40M) are top sellers, showing a strong demand for office tech and ergonomics.
* Labels (0.22M), Fasteners (0.25M), and Envelopes (0.51M) lag, indicating these smaller consumables are overshadowed by higher-value items

<img width="940" height="296" alt="image" src="https://github.com/user-attachments/assets/6b7c1495-eef5-4bfc-831f-9a83d0513767" />

Observations:
* Consumers bring in the most revenue at 19.52M, showing that individual buyers are a big source of sales. This suggests a strong retail market.
* At 11.47M, corporate customers (businesses buying in bulk) are also important, but not as large as the consumer segment.
* Home office buyers generate 6.93M, which is smaller than the other segments but could grow further due to increasing remote work and targeted promotions

<img width="940" height="364" alt="image" src="https://github.com/user-attachments/assets/b4873647-2b3c-4232-b418-294b573b63a5" />

Observations:
* Technology leads in sales, with Phones and Copiers generating the highest revenue, while Machines have lower sales but still rank in the top 3.
* Furniture sales are driven by Chairs and Bookcases, whereas Tables, though in the top 3, contribute less to overall sales.
* Office Supplies have a more balanced sales pattern, with Storage and Appliances performing well, while Binders have the lowest sales among the top 3 in this category.

<img width="940" height="445" alt="image" src="https://github.com/user-attachments/assets/48ed510a-3c7c-44c5-82ce-84e13797ee1b" />

Observations:
* The U.S. dominates with 6.89M in sales, significantly higher than any other country, indicating a strong market presence and demand.
* Australia (2.78M) and France (2.58M) hold the second and third spots, suggesting a stable customer base but much lower than the U.S.
* Countries like China (2.10M), Germany (1.89M), India (1.77M), and Mexico (1.87M) show moderate sales, but with rising economies, they present expansion opportunities.

<img width="940" height="774" alt="image" src="https://github.com/user-attachments/assets/81f81496-a38e-4012-b709-ca506ffbde80" />

Observations:
* Apple Smart Phone (0.26M) leads sales, followed closely by Cisco, Motorola, and Nokia smartphones.
* Canon ImageCLASS 2200 Advanced Copier (0.18M) ranks high, showing continued reliance on office printing solutions.
* While smartphones dominate, chairs and copiers still maintain strong sales, suggesting that businesses continue to invest in both digital and physical workspaces.

<img width="940" height="458" alt="image" src="https://github.com/user-attachments/assets/c2a1bb80-30ad-4a49-bc27-c77ecbabd9f1" />

Observations:
* 20.97M in sales happened at 0% discount, meaning a significant portion of customers are willing to pay full price.
* Discounts around 10% (4.73M), 20% (3.61M), and 40% (1.67M) still generate good sales, indicating these are effective discount ranges.
* Sales decline sharply beyond 40-50% discounts, suggesting that deep discounts do not necessarily drive higher revenue.

<img width="940" height="355" alt="image" src="https://github.com/user-attachments/assets/e96040ec-2921-44e0-95ab-e61779a9aa45" />

Observations:
* 22.73M in sales, making it the preferred and most cost-effective shipping option for customers.
* Second Class (7.69M) and First Class (5.49M) have moderate sales, indicating some demand for quicker deliveries but at a higher cost.
* Only 2.00M in sales, suggesting that customers may not prioritize ultra-fast shipping, possibly due to higher costs or less frequent urgent needs.

<img width="940" height="495" alt="image" src="https://github.com/user-attachments/assets/c1613085-f77e-40eb-aa8c-326f84d3382a" />

Observations:
* Sales have shown a steady increase from 2011 to 2014, growing from 6.77M in 2011 to 12.89M in 2014.
* The growth rate has accelerated each year, with significant jumps between 2012-2013 and 2013-2014, indicating rising market demand or expansion efforts.
* If this trend continues, investing in key markets, high-performing products, and customer segments could further boost revenue.

<img width="940" height="445" alt="image" src="https://github.com/user-attachments/assets/549c0415-f5e1-403a-8138-852edf323309" />

Observations:
* From 2011 to 2014, sales for Phones, Chairs, Bookcases, and Copiers increased steadily, indicating growing demand.
* While Phones led sales in all years, Copiers experienced rapid growth, surpassing Chairs and Bookcases by 2014. This suggests strong demand for technology-related products, possibly due to increased business and office needs.
* Chairs and Bookcases maintained consistent growth, but their sales increased at a slower rate than Phones and Copiers. This indicates steady market demand for furniture, though less aggressive growth compared to technology-related products.

<img width="940" height="439" alt="image" src="https://github.com/user-attachments/assets/1f5c7442-6d03-420c-b567-98f4e6a9395a" />

Observations:
* United States dominates sales across all months, consistently contributing the largest portion, indicating it is the primary revenue driver.
* Sales show a clear increasing trend over the months, peaking in November and December, suggesting a seasonal effect, possibly due to holiday shopping or end-of-year business spending.
* Other countries contribute variably, with France, China, and Germany showing strong performances in some months, while India appears only in May, indicating occasional spikes in sales from different regions.

### 5. MODELLING FOR FORECASTING

To build accurate sales forecasting models, various machine learning and deep learning techniques were implemented. The primary models evaluated were LSTM (Long Short-Term Memory), Random Forest Regressor, and XGBoost Regressor.

**Data Preprocessing:**
* The dataset was smoothed using a rolling mean (window = 50) to reduce noise and fluctuations.
* The first 50 NaN values (due to smoothing) were dropped, reducing the dataset to 1,381 rows and 2 columns.
* The Order Date column was converted from string format to datetime format.
* The data was split into train (70%) and test (30%) sets.
* StandardScaler was used to normalize the sales values for improved model convergence

**LSTM Model:**
* A two-layer LSTM network was implemented with 512 and 256 neurons, followed by dense layers.
* The model was trained using the Adam optimizer with a learning rate of 0.0001.
* EarlyStopping and ReduceLROnPlateau were applied to optimize training and prevent overfitting.
* The LSTM model achieved a Train R² score of 0.9843 and a Test R² score of 0.9849.
* Future predictions were generated for 30 days using the trained model.

<img width="940" height="411" alt="image" src="https://github.com/user-attachments/assets/c01de6e2-d6b7-42a2-9e02-02e7924e57a7" />

**Random Forest Regressor:**
* A Random Forest model with 50 estimators was trained on reshaped time-series data.
* The model performed exceptionally well on training data (Train R² = 0.9993), but showed overfitting issues on test data (Test R² = 0.5426).
* Future sales predictions were made using the trained model.

<img width="940" height="411" alt="image" src="https://github.com/user-attachments/assets/28cf58aa-b5d1-4531-af17-ee6c5055a654" />

**XGBoost Regressor:**
* A boosted decision tree model (XGBoost) with 50 estimators was trained.
* The model achieved an impressive Train R² score of 0.9999, but lower generalization on test data (Test R² = 0.4671).
* Future sales were predicted using the XGBoost model.

<img width="940" height="410" alt="image" src="https://github.com/user-attachments/assets/dc6fd91f-a81e-45c1-a1a3-7bcd709c2c3e" />

### 6.RESULTS

<img width="715" height="85" alt="image" src="https://github.com/user-attachments/assets/a1e62b4f-f26d-441d-b766-5450e05354ec" />

### 7. TABLEAU DASHBOARD

<img width="940" height="595" alt="image" src="https://github.com/user-attachments/assets/1e507644-7e39-43be-9d44-5d700d059c88" />

### 8. CONCLUSIONS
* Sales trends have shown consistent growth from 2011 to 2014, increasing from 6.77M to 12.89M, with peak sales occurring in November and December due to holiday shopping and year-end business purchases. This trend suggests a growing market demand, which businesses should leverage through targeted promotions, inventory optimization, and marketing campaigns during peak seasons.
* Regional analysis indicates that the Central region (8.47M) leads in revenue, followed by South (4.80M) and North (3.74M), while Canada (0.20M) and the Caribbean (0.97M) have the lowest sales, highlighting low market penetration. To address this, businesses should expand marketing and promotional efforts in underperforming regions while continuing to capitalize on the high-performing areas.
* The Technology category (37.53%) contributes the highest sales, followed by Furniture (32.52%) and Office Supplies (29.96%). Within these, Phones (5.12M), Copiers (4.53M), Chairs (4.51M), and Bookcases (4.40M) are the best-selling subcategories. Labels (0.22M), Fasteners (0.25M), and Envelopes (0.51M) lag, suggesting that businesses should prioritize investments in high-performing product lines while reassessing the market demand for lower-performing categories.
* Discount analysis reveals that 20.97M in sales occurred with no discount, showing that many customers are willing to pay full price. Discounts between 10-20% generate good sales (4.73M and 3.61M, respectively), while deeper discounts beyond 40% reduce profitability. The optimal strategy is to focus on 10-20% discount ranges and limit deep discounting, as it does not significantly drive revenue.
* Regarding shipping modes, Standard Class (22.73M) dominates, followed by Second Class and First Class, while Same-Day shipping is underutilized. To improve efficiency, businesses should optimize Standard Class logistics, explore customer interest in Same-Day delivery, and implement tiered shipping incentives to encourage higher sales conversions.
* The sales forecasting models indicate that the LSTM model performed best, with a Train R² of 0.9843 and Test R² of 0.9849, making it the most reliable predictor for future demand. In contrast, Random Forest (Test R² = 0.5426) and XGBoost (Test R² = 0.4671) overfit training data. This suggests that LSTM should be used for future forecasting, while the Random Forest and XGBoost models require further optimization.

**Final Business Strategy:**
* Plan for seasonal sales peaks by increasing stock and running promotions during high-demand months (Nov-Dec).
* Invest in strong regions like Central, South, and North while improving sales strategies in weaker markets (Canada, Caribbean).
* Focus on high-performing product categories (Technology, Furniture) while reassessing low-selling products.
* Improve shipping efficiency by optimizing Standard Class delivery and assessing demand for faster shipping options.
* Use LSTM-based forecasting for accurate demand predictions and better business planning.
By following these strategies, businesses can maximize sales.

### 9. REFERENCES

1.	*https://www.kaggle.com/datasets/jr2ngb/superstore-data?select=superstore_dataset2011-2015.csv*
2.	*https://www.kaggle.com/datasets/fatihilhan/global-superstore-dataset*
3.	*https://www.kaggle.com/datasets/fatihilhan/global-superstore-dataset*
