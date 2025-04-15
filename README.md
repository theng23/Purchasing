# 📊Purchasing Bicycle Dashboard| Power BI
## I. Introduction
### 📖 What is this project about?
- This project leverages the AdventureWorks dataset to analyze business operations and extract insights for a fictional bicycle purchasing company.
- The purchasing department will be responsible for purchasing goods, raw materials, and semi-finished products for production.

### 👤 Who is this project for?

➡️ The dashboard empowers **Directors** to efficiently manage orders, optimal import rices, and ordering on time.

  
### ❓**Business question** 
- The management expects that the **goods ordered** are sufficient for sales, on time, and at **optimal import prices**.
- Create an **Operation Dashboard** to provide a visual and easy-to-understand picture to helping them make better decisions and operations.
- **Total Order and Total Purchase**: What strategies can be implemented to enhance performance monitoring and overall efficiency in purchasing of orders?
- **Status Order**: How can Directors accurately evaluate orders through status of orders.

## 📂II. Dataset
### 📌Data Source
- Dataset: adventureworks2019 (public Google BigQuery dataset) 
- Dataset Schema: [AdventurWorks](https://drive.google.com/drive/u/0/folders/1zz25TcfnzJVS_lJN-tLqmSpiAwdAfbHR)
- Dataset access: 
  - Log in to your Google Cloud Platform account and create a new project.
  - Navigate to the BigQuery console and select your newly created project.
  - In the navigation panel, select "Add Data" and then "Star a project by name".
  - Enter the project name "adventurework2019"

### Data Structure & Relationships
#### 1️⃣ Consists of **7** data tables
#### 2️⃣ Table Schema

<details> 
<summary>Table 1: Product_Product</summary>

| Field Name | Data Type | Description |
|-------|-------|-------|
| ProductID           | Integer       | Unique identifier for each product.                                    |
| Name                | String        | The name of the product.                                               |
| ProductNumber       | String        | A unique number assigned to each product.                              |
| SafetyStockLevel    | Integer       | The minimum quantity of stock that must be kept on hand to prevent stockouts. |
| ReorderPoint        | Integer       | The inventory level at which a new order should be placed to replenish stock. |
| StandardCost        | Decimal       | The standard cost to produce or purchase the product.                  |
| ListPrice           | Decimal       | The price at which the product is listed for sale.                     |
| Style               | String        | The style or category of the product.                                  |
| ProductSubcategoryID| Integer       | Identifier for the subcategory to which the product belongs.           |
| SellStartDate       | Date          | The date when the product became available for sale.                   |
| SellEndDate         | Date          | The date when the product was no longer available for sale.            |
| DiscontinuedDate    | Date          | The date when the product was discontinued.                            |
| ModifiedDate        | Date          | The date when the product information was last modified.               |


</details>

<details> 
<summary>Table 2: Product_ProductTable</summary>

| Field Name | Data Type | Description |
|-------|-------|-------|
| ProductID            | Integer     | Unique identifier for each product.                  |
| Name                 | String      | The name of the product.                             |
| ProductCategoryID    | Integer     | Identifier for the category to which the product belongs. |
| ProductSubcategoryID | Integer     | Identifier for the subcategory to which the product belongs. |
| Category             | String      | The category of the product.                         |
| Subcategory          | String      | The subcategory of the product.                      |


</details>


<details> 
<summary>Table 3: Purchasing_OrderDetail</summary>

| Field Name | Data Type | Description |
|-------|-------|-------|
| PurchaseOrderID        | Integer     | Unique identifier for each purchase order.                 |
| PurchaseOrderDetailID  | Integer     | Unique identifier for each detail line within a purchase order. |
| DueDate                | Date        | The date when the order is due to be received.             |
| OrderQty               | Integer     | The quantity of items ordered.                             |
| ProductID              | Integer     | Unique identifier for each product.                        |
| UnitPrice              | Decimal     | The price per unit of the product ordered.                 |
| LineTotal              | Decimal     | The total cost for the line item (OrderQty * UnitPrice).    |
| ReceivedQty            | Integer     | The quantity of items actually received.                   |
| StockedQty             | Integer     | The quantity of items stocked.                             |
| ModifiedDate           | Date        | The date when the purchase order detail was last modified. |
| RejectedQty            | Integer     | The quantity of items that were rejected.                  |

</details>

<details> 
<summary>Table 4: Purchasing_OrderHeader</summary>

| Field Name | Data Type | Description |
|--------------------|-------------|--------------------------------------------------------------|
| PurchaseOrderID    | Integer     | Unique identifier for each purchase order.                  |
| RevisionNumber     | Integer     | The revision number of the purchase order.                  |
| Status             | Integer     | The status of the purchase order.                           |
| EmployeeID         | Integer     | Identifier for the employee associated with the order.       |
| VendorID           | Integer     | Identifier for the vendor associated with the order.         |
| ShipMethodID       | Integer     | Identifier for the shipping method used for the order.       |
| OrderDate          | Date        | The date when the purchase order was created.               |
| ShipDate           | Date        | The date when the order is expected to be shipped.          |
| SubTotal           | Decimal     | The subtotal amount of the order.                           |
| TaxAmt             | Decimal     | The amount of tax applied to the order.                     |
| Freight            | Decimal     | The shipping cost associated with the order.                |
| TotalDue           | Decimal     | The total amount due for the order.                         |
| ModifiedDate       | Date        | The date when the purchase order was last modified.         |



</details>

<details> 
<summary>Table 5: Purchasing_ProductVendor</summary>

| Field Name | Data Type | Description |
|----------------------|-------------|--------------------------------------------------------------|
| ProductID            | Integer     | Unique identifier for each product.                         |
| BusinessEntityID     | Integer     | Unique identifier for each business entity.                 |
| AverageLeadTime      | Integer     | The average lead time for the product.                      |
| StandardPrice        | Decimal     | The standard price of the product.                          |
| LastReceiptCost      | Decimal     | The cost of the last receipt of the product.                |
| LastReceiptDate      | Date        | The date of the last receipt of the product.                |
| MinOrderQty          | Integer     | The minimum order quantity for the product.                 |
| MaxOrderQty          | Integer     | The maximum order quantity for the product.                 |
| OnOrderQty           | Integer     | The quantity of the product currently on order.             |
| ModifiedDate         | Date        | The date when the product information was last modified.    |
| CostDiffRatio        | Decimal     | The cost difference ratio for the product.                  |






</details>


<details> 
<summary>Table 6: Purchasing_Vendor</summary>

| Field Name | Data Type | Description |
|------------------------|-------------|-------------------------------------------------------------|
| BusinessEntityID       | Integer     | Unique identifier for each business entity.                |
| AccountNumber          | String      | The account number associated with the business entity.    |
| Name                   | String      | The name of the business entity.                           |
| CreditRating           | Integer     | The credit rating of the business entity.                  |
| PreferredVendorStatus  | Boolean     | Indicates whether the vendor is a preferred vendor.         |
| ActiveFlag             | Boolean     | Indicates whether the business entity is active.           |
| ModifiedDate           | Date        | The date when the business entity information was last modified. |



</details>


<details> 
<summary>Table 7: ProductInventory</summary>

| Field Name | Data Type | Description |
|------------------------|-------------|-------------------------------------------------------------|
| ProductID       | Integer     | Product identification number. Foreign key to Product.ProductID.               |
| LocationID          | Integer     | Inventory location identification number. Foreign key toLocation.LocationID.    |
| Shelf                   | String      | Storage compartment within an inventory location.                           |
| Bin           | Integer     | Storage container on a shelf in an inventory location.                  |
| Quantity  | Boolean     | Quantity of products in the inventory location. Default: 0      |
| rowguid             | uniqueidentifier     | ROWGUIDCOL number uniquely identifying the record. Used to support a merge replication sample. Default: newid()          |
| ModifiedDate          | Date        |Date and time the record was last updated. Default: getdate(). |

</details>


## II. Design thinking mindset.

Here are the five steps of design thinking:
### Step 1 - Empathize

➡️ Applied 5W1H to define the problem

![3cc5c765-4550-4204-a100-76632fc9b70c](https://github.com/user-attachments/assets/79544489-dfd7-4179-98c7-7d133c7b9a1a)

➡️ Empathy for Stakeholders

![cc62559c-9c5c-4136-919e-44d0ede79bd1](https://github.com/user-attachments/assets/f07b841c-2157-4728-9889-a2a6879b0782)



### Step 2 - Define


![Step2](https://github.com/user-attachments/assets/be73c46c-a73f-4919-b69e-b18eaa495201)

### Step 3 - Ideate


![Step3](https://github.com/user-attachments/assets/ba1ee5d9-2364-4e80-959d-1c95e16367f9)

### Step 4-5 - Prototype & Review

![Step4-5](https://github.com/user-attachments/assets/aadf9f27-7c6f-4d52-908e-23ea95e08881)

## III. Visualization
### 1. Overview
![Overview](https://github.com/user-attachments/assets/5eab8a72-f42c-4488-9c0e-f361d8a7f4c1)
### 2. Status Orders
![Status-Order](https://github.com/user-attachments/assets/0f5425ed-2c09-4da6-9d7a-44e249e35f71)

## IV. Insight and Recommendation:
### Insight
1. Overall Performance:
  - Total orders: 8,845.
  - Total purchase value: $63.79M.
  - Average Order Value (AOV): Indicates a consistent performance trend across the analyzed years.
  - Total Quantity Order: 2.35M
2. Yearly Trends:
  - There appears to be a gradual increase in total orders and total purchase value over the years, with significant growth in specific periods like 2013–2014.
3. Top Performing Categories:
  - The Components category has the highest total purchase value at 41.92% of overall sales.
  - Pedals and Brakes subcategories dominate the performance within Components.
4. Top Products:
  - HL Crankarm leads with a purchase value of $3.36M.
  - Other high-performing products include ML Mountain Pedal, ML Road Pedal, and Front/Rear Brakes.
5. Order Status Analysis:
  - A majority of orders are categorized as Approved and Complete, which reflects good operational efficiency.
  - A smaller percentage of orders are Pending or Rejected, highlighting areas for improvement.
    
### Recommendations:
1. Boost High-Performing Products:
  - Focus marketing and sales efforts on high-performing items like HL Crankarm and Chainring Bolts from Other Category, as they have shown strong demand and revenue generation.
2. Optimize Inventory Management:
  - Address rejected quantities by reviewing quality control processes and ensuring suppliers meet higher standards.
3. Expand Strong Categories:
  - Increase product diversity in the Components and Accessories categories to leverage their established popularity.
4. Monitor Pending and Rejected Orders:
  - Regularly review the reasons behind pending or rejected orders to identify and address bottlenecks in the order processing system.
5. Yearly Growth Strategy:
  - Analyze what led to the significant increase in orders and purchase value during 2013–2014, and replicate those strategies in future operations.
