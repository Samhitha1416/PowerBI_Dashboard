# BI_Assignment

#### Prepared by Gunti Samhitha (160122737147) and M Sudha Jennifer (160122737150) from IT 3 , 4th year
## Question 1: Perform ETL for Retail Data

### Customers Table
- Columns renamed for clarity:
  - `City` → `CustomerCity`
  - `Age` → `CustomerAge`
- Makes column names more descriptive and easier to use in the model.
- Table. RenameColumns (#"Changed Type", {{"City", "CustomerCity"}, {"Age", "CustomerAge"}})

<img width="1359" height="716" alt="Screenshot 2025-09-08 225354" src="https://github.com/user-attachments/assets/5c2d30c6-dc63-4aaf-a844-4c2effcae8f7" />


### Sales Table
- Columns renamed and new calculated column created:
  - `Product` → `ProductName`
  - `Order ID` → `OrderID`
  - New column `Sales` = `Quantity × Price` (total sales amount for each order).
  - Table. RenameColumns (#"Changed Type", {{"Product", "ProductName"}})

<img width="1359" height="719" alt="Screenshot 2025-09-08 225448" src="https://github.com/user-attachments/assets/f23e5648-eebf-4b32-9d4c-f1d098ea5847" />


### Dates Table
- Data types adjusted for correct handling:
  - `DateID` → `Int64.Type`
  - `Date` → `Date.Type`
  - `Month` → correct type (text/number depending on usage).
- Ensures correct time-based analysis in Power BI.
- Table. TransformColumnTypes (#"Promoted Headers", {{"DateID", Int64.Type}, {"Date", Int64. Type}, {"Month", type}})

<img width="1359" height="719" alt="Screenshot 2025-09-08 225422" src="https://github.com/user-attachments/assets/215e6a8b-e458-43f3-893b-1c80dfe0782e" />

### Visualizations (Dashboard)

- **Pie Chart:** Sum of Price by ProductName → shows top revenue-contributing products.  
- **Clustered Column Chart:** Sum of Quantity & Sales by Category → compares sales volume vs. value.  
- **Scatter Chart:** Price vs. Sales by ProductName & Category → shows product performance patterns.  
- **Line Chart:** CustomerAge by CustomerCity → highlights demographic trends.  
- **Bar & Donut Charts:** Price by ProductName and CustomerID by City → insights into product performance and customer distribution.

  <img width="1359" height="716" alt="Screenshot 2025-09-08 230752" src="https://github.com/user-attachments/assets/937b2ac0-90a2-470d-9ac6-48662d982635" />

---
## Question 2: Design OLAP Cube

<img width="1359" height="664" alt="OLAP_Cube" src="https://github.com/user-attachments/assets/b7c21fb3-695a-4218-9732-5564133da055" />

An OLAP (Online Analytical Processing) cube is used for multidimensional analysis of the data.  
It allows slicing, dicing, and drilling down into data across different dimensions.

### Cube Structure

- **Axis 1 (Rows):** Cities from the **Customers** table  
  - Hyderabad, Bangalore, Delhi, Mumbai, Chennai  

- **Axis 2 (Columns):** Months from the **Dates** table  
  - Jan, Feb, Mar, Apr  

- **Axis 3 (Diagonal):** Products from the **Sales** table  
  - Laptop, Phone, Tablet, Monitor  

### Purpose
- Enables analysis of **sales data** across multiple perspectives (City, Month, Product).  
- Example: Compare Laptop sales in **Hyderabad (Rows)** during **March (Columns)**.  
- Helps identify trends and insights quickly using a multidimensional structure.

---

## Question 3: Design Star Schema


<img width="1359" height="616" alt="star_schema" src="https://github.com/user-attachments/assets/e8f65527-7b5c-445c-b298-bd2b923417d4" />

### 1. Fact Table (Sales)
- **OrderID:** Unique sales transaction ID  
- **CustomerID:** Links to Customers table  
- **DateID:** Links to Dates table  
- **ProductID:** Links to Products table  
- **Quantity:** Number of items sold  
- **Price:** Price per item  
- **TotalSales:** Calculated as Quantity × Price (main metric)  

### 2. Dimension Tables
- **Customers**
  - CustomerID (PK), CustomerName, CustomerAge, CustomerCity  
- **Products**
  - ProductID (PK), ProductName, Category, Price  
- **Dates**
  - DateID (PK), Date, Month, Year  

### 3. Relationships
- **One-to-Many**:
  - One customer → many sales  
  - One product → many sales  
  - One date → many sales

  
