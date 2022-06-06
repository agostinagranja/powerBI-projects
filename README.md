# Power BI projects
#### This repository helps me gather all of the Power BI dashboards I make. You will find a _description_ of each project, a _screenshoot_ of the dashboard, and the _PBIX file_.

## Content
1. Personal finances
2. Sales
3. Sales II

### _Personal finances_
#### Description
This project is born after noticing the difficulty in making forecasts in my personal finances sphere. After some research, I realized that it was due to the lack of tracking and **analysis of income and expenses** (or at least it would be a great place to start).

The **project objective** is to build an interactive dashboard analyzing the magnitude, structure, and trends of income and expenses up to date.

At first, I developed it just for me and then personalized it for friends and family. Feel free to adapt it to your necessities and do not hesitate to propose improvements.

#### Implementation process
1. Incremental ETL. Frequency: once a month 
2. Modelling: 
   - Relationships
   - Identification of facts: income and expenses, both real and targeted
   - Identification of dimensions: date, cathegory, and concept
3. Measures: 
   - Sum of income and expenses
   - Sum month to date (MTD)
   - Sum year to date (YTD)
   - Change month over month (MoM%) 
   - Count of dimensions
4. Visualizations
   - Matrix: show income/expenses and saving per month in numbers. Also includes KPIs indicating if target saving was reached or not.
   - Stacked column chart: show current liquidity.
   - Gauge: compare target income/expenses to the actual ones.
   - Line and stacked column charts: show the income/expenses per month and the corresponding change MoM%.
   - Donut chart: show income/expenses amount by cathegory.
   - Treemap: show income/expenses amount by concept.
   - Cards: show summarization of income/expenses.
   - Multi-row card: show various stats like dimension counting.
5. Filters
   - Year
   - Month
   - Cathegory
   - Concept

#### Results
* [PBIX file](docs/CONTRIBUTING.md)
* ![Preview](docs/CONTRIBUTING.md)

### _Sales_
#### Description
This is the **capstone project** developed as a team for the subject "computerized management" in the last year of my accounting degree. It is in Spanish, but you should know that I am working on its translation to English. 

The **project objective** is to build an interactive dashboard to:
1.	Obtain valuable insights into the magnitude, structure, and trends of sales/ profit
2.	Making sales forecasting

You can peek at the dashboard in the **video** I attach in the next section. I also include the **PBIX file** in this repo.

#### Implementation process
1. Prepare and clean the database
2. Modelling: 
   - Relationships[^1]
   - Identification of facts: transactions (sales and cost)
   - Identification of dimensions: date, branch, customer, currency, places, products, cathegory, paying method

[^1]: Image: relationships modelling

3. Measures: 
   - Sum of sales, expresed in argentine pesos (taking into account inflation) and in dollars
   - Change month over month (MoM%) 
   - TopN of products and customers
   - Profit margin
   - Count of dimensions
4. Visualizations
   - Column charts: show sales and margin agreggated by month.
   - Decomposition tree: shows the composition of the amount of sales according to category and products.
   - Line chart: shows units sold per month and forecasts sales units.
   - Treemap: show sales by cathegories.
   - Table: show top 5 products and customers measured according to units sold and profit margin, respectively.
   - Donut chart: show sales amount by payment method.
   - Map: show influx of customers, sized by sales amount.
   - Cards: show sum of main measures like sales and change over last month.
   - Multi-row card: show various stats like dimension counting.
5. Filters
   - Year
   - Branch
   - Currency
   - Cathegory
   - Top products/customers

#### Demonstration

**_video_**

### _Sales II_
#### Description
This is a project developed for **learning purposes**. 

The **project objective** is to build an interactive dashboard to:
1.	Analyze sales and profit, in different dashbaords
2.	Visualize KPIs

You can peek at the dashboard in the **video** I attach in the next section. I also include the **PBIX file** in this repo.

#### Implementation process
1. Load data
2. Modelling: 
   - Identification of facts: sales and cost
   - Identification of dimensions: date, segment, country, product, discount band
3. Measures: 
   - Sum of sales
   - Profit
   - Previous sales
   - Previous profit
   - Profit margin
4. Visualizations
   - Stacked column chart: show sales, cost and profit per month
   - KPI: compare the profits/sales of the current month with the last month
   - Line chart: displays units sold and forecasted
   - Map: show profit/sales per country
5. Filters
   - Year
   - Month
   - Segment

#### Demonstration

**_video_**

