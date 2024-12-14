

# Ecommerce Analysis
### Dashboard: PDF and PBIX is attached in this repository 
## Problem Statement

The objective of this analysis is to optimize the eCommerce platform's performance by increasing sales, reducing operating costs, and enhancing customer satisfaction. Specifically, we aim to: 
- Maximize customer reach and sales by implementing effective cross-selling strategies, promoting relevant products at the point of purchase, and upselling higher-priced alternatives or larger quantities of products.
- Identify opportunities to reduce operating costs through shipment consolidation, optimizing package dimensions, and leveraging the shipment of larger quantities.
- Analyze customer purchase behavior to uncover products that are frequently bought together, using correlation analysis to identify patterns in the data, enabling targeted recommendations.
- Implement a correlation matrix to assess the relationship between purchased items and improve recommendations and marketing strategies.
The scope of this analysis is identifying potential improvements in sales strategies and operational efficiencies.
### Steps followed 
- Step 1 : Load data into Power BI Desktop, dataset is a csv file.
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- Step 4 : It was observed that none of the columns have errors but "Invoice No" column have all valid transactional value, so need to remove the empty invoice values.
- Step 5 : Need to build a few customer metrics to understand how many customers the company has their total business. We calculate validate no of sales by cross checking with invoice count and staewise customer count.
![Data Understanding1.png…](https://github.com/user-attachments/assets/a42f2589-4d78-4ca2-9e92-b6951159437c)

- Step 6 : To understand product that sells in higher quantities and total sale they generated, along with product with higher shipping cost. For this we will visualize the following: Tree Map that visualize total sales by product category, Bar chart with Avg shipping cost by product description and another bar chart shows Avg Quantity by description of the product. 
![Uploading Product Understanding.png…](https://github.com/user-attachments/assets/d1029106-3f30-49ee-85be-f8ebe9742f0e)
- Step 7 : To understand the relationship between shipped quantity and shipping cost, we'll visualize total sale by quantity (invoice quantity and Sales Quantity)
![Uploading Quantity Understanding.png…](https://github.com/user-attachments/assets/6ea328fb-b63b-4d16-aac2-4c3b41e8bd8f)
- Step 8 : Market basket analysis: to understand customer purchasing patterns, if they buy one product what else do they buy?
    Build Market Basket Analysis Visualization:     
    Create a simple visualization to display which products are bought together. Use product selection filters to dynamically show related products purchased.
    
    Create the necessary DAX measures or calculated columns to identify associations between products.

![Uploading Market Basket Analysis.png…](https://github.com/user-attachments/assets/0a417866-c31f-48f6-b3ce-12d87145998a)


- Step 9: Sales by State Mapping
	1. Create Sales by State Visual:
		○ Add a map visual to display sales by state.
		○ Use the state-region mapping table to ensure accurate geographical visualization.
	2. Prepare Visuals for Final Dashboard:
		○ Refine the map and ensure all visuals are ready for the dashboard by formatting them properly.

- Step 10: Shipping Costs Analysis (What-If Analysis Part 1)

	1.  Create Metrics for Shipping Costs: 
		○ Build the necessary DAX measures for shipping costs	○ Integrate any other shipping-related data or assumptions.

- Step 11: Shipping Costs What-If Analysis (Part 2)
	1. Add What-If Scenarios for Shipping: 
		○ Create parameters for different shipping scenarios, allowing dynamic changes in the shipping rate as the quantity changes.
		○ Display the baseline shipping costs and the hypothetical "what-if" shipping costs for comparison.

- Step 12: Shipping Costs by Product
	1. Shipping Costs Breakdown: 
		○ Use the previously created shipping metrics to visualize the shipping costs by product.
		○ Allow the user to change the quantity parameter and see how shipping costs fluctuate.

- Step 13: Key Metrics and Running Total Calculation
	1. Calculate Running Total for Shipping Costs:
		○ Create a new DAX measure for the running total of baseline shipping costs using the SUMX function across the Sales table. 
		For Shipping (Baseline)

			Shipping (Baseline) = SUMX(Sales, IF(Sales[Quantity]=1,Sales[Shipping Cost],Sales[Shipping Cost]+(((Sales[Quantity])-1)*(Sales[Shipping Cost]*0.7))))
		
			Shipping (What-if) = SUMX(Sales,IF(Sales[Quantity]=1,Sales[Shipping Cost],Sales[Shipping Cost]+(((Sales[Quantity])-1)*(Sales[Shipping Cost]*[Blended Shipping Cost Factor]))))
			
			Shipping (Difference) = [Shipping (Baseline)] - [Shipping (What-if)]


	

	2. Display Key Metrics:
		○ Create KPI visuals to display total shipping costs (baseline, what-if, and differences).
		○ Show the breakdown of shipping costs by product.

![Uploading Shipping Matrix.png…](https://github.com/user-attachments/assets/6243cfef-68df-4e0d-8e5b-7c28c6fd00e9)	

- Step 14: Revenue and Profits Analysis
	1. Create Revenue and Profit KPIs: 
		○ Calculate and display key metrics like revenue, profits, and top customers.
		○ Use geographic visuals (like maps) to show sales performance by state.

- Step 15: Build Executive Summary Dashboard
	1. Assemble Executive Summary:
		○ Build a dashboard with core KPIs like total sales, profits, and expenses.
		○ Add interactivity to filter by product, customer, or location.
	2. Add Drill-Downs:
		○ Implement drill-downs or slicers for different dimensions like product category or region.

- Step 16: Profit Percentage Treemap
	1. Create Treemap for Profit Margin Breakdown: 
		○ Build a treemap to visualize profit percentage by product.
		○ Adjust interactions between the treemap and other visuals on the dashboard.

- Step 17: Product Recommendations for Cross-Selling
	1. Add Visual for Product Recommendations: 
		○ Use the market basket analysis to suggest products for cross-selling during the checkout process.
		○ Visualize these recommendations clearly for easy decision-making.

- Step 18: Shipping Costs Breakdown by Geography and Upsell Recommendations
	1. Shipping Costs Dashboard: 
		○ Create a detailed visualization for shipping costs, broken down by geography (region, state, etc.).
		○ Provide insights and suggestions on quantity upsell strategies.

- Step 19: Finalize and Format Dashboards
	1. Revisit Dashboard Layouts:
		○ Ensure all visuals are arranged in a clear, executive-friendly format.
		○ Review and adjust the layout for the Executive Summary and Market Basket Analysis pages.
	2. Format and Customize:
		○ Adjust the format for all data types and ensure the visuals are readable.
		○ Customize the Power BI theme to match the company’s preferences (e.g., color scheme, fonts).
	3. Final Touches:
		○ Add headers, tooltips, and labels where necessary.
		○ Test the interactivity of filters and slicers to ensure everything is working smoothly.

![Uploading Executive Summary.png…](https://github.com/user-attachments/assets/b8be3317-d703-4bc1-9d42-6d2b41507b15)

Here is a comprehensive Power BI dashboard that addresses Whiskique's key business insights, including sales trends, shipping costs, and product recommendations.


