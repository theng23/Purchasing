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

#### 3️⃣ Data Relationships:

![e07b66e6-fa91-4431-92b5-88f9986acfba](https://github.com/user-attachments/assets/7e93ef88-4663-4b08-b9e4-8c1d5fdc6a61)



## 🧠II. Design thinking mindset.

Here are the five steps of design thinking:
### Step 1 - Empathize

➡️ Applied 5W1H to define the problem

![3cc5c765-4550-4204-a100-76632fc9b70c](https://github.com/user-attachments/assets/79544489-dfd7-4179-98c7-7d133c7b9a1a)

➡️ Empathy for Stakeholders

![cc62559c-9c5c-4136-919e-44d0ede79bd1](https://github.com/user-attachments/assets/f07b841c-2157-4728-9889-a2a6879b0782)



### Step 2 - Define
➡️ Find the North star metric

![0f86cdbe-9324-443f-8880-95532ec08f4f](https://github.com/user-attachments/assets/c4d8f500-c4ae-4b91-8ecf-6b5851053de9)

➡️ Define Point of View

![0cafe614-f140-44f3-8259-8d7092488305](https://github.com/user-attachments/assets/ec7b2a70-a557-49a3-99a2-64d8c829a135)

➡️ Growth Formula

![065c04c2-7e4d-43d9-90ce-8b1967af77c2](https://github.com/user-attachments/assets/1162de81-87bf-4685-83c4-5f0f65f731ed)

### Step 3 - Ideate
➡️ Brainstorming

![e03c591c-1205-4554-b34c-4a94746f9394](https://github.com/user-attachments/assets/62243049-e791-41b2-b672-dfc736a26675)

➡️ Structure Idea
![01d13775-76ca-4bae-bfd2-2f744ca6f062](https://github.com/user-attachments/assets/6316e574-88d4-48c9-beae-7e8968b5bea0)


### Step 4-5 - Prototype & Review

![Step4-5](https://github.com/user-attachments/assets/aadf9f27-7c6f-4d52-908e-23ea95e08881)

## 📊 III. Visualization
### 📌1. Overview

![8a70bb2c-7561-4b3c-838f-953a6748fa39](https://github.com/user-attachments/assets/d8d6e6d0-8f1b-4921-8442-3d3ca7d993f9)

- Sales Performance Over Time → Steady growth in total orders (8,845) and total purchase value (63.8M) from 2011 to 2014, reflecting increasing demand.
- Top-Selling Categories → Bikes, Clothing, Accessories, Components, and Other lead in total purchase value, with Technology dominating overall sales.
- High-Value Products & Subcategories → HL Crankarm, ML Mountain Pedal, Front Brakes, Rear Brakes, HL Mountain Tire among the top-performing items in terms of purchase value.
- Order Trends & Average Order Value (AOV) → AOV fluctuates across years and categories, requiring pricing and promotional optimization to enhance profitability.

### 📌2. Status Orders
**Overview of Status Orders**

![e5ec27d4-cadf-4f49-af35-6e627bc960b2](https://github.com/user-attachments/assets/fb38d547-6675-4117-bf4c-d61266bfe05a)

- Steady Growth in Total Orders → 8,845 orders, with increasing trend from 2011 to 2014, indicating strong demand.
- High Purchase Value → 63.8M total purchase, with an AOV (7.21K) showing stable customer spending.


📌**Approved**

![cc4a5ecc-7217-46a6-b329-42260fcf51c2](https://github.com/user-attachments/assets/b2f810bd-3718-4c76-982f-4abe69348e82)

- Significant Growth in Approved Orders → Orders jumped from 9 (2013) to 48 (2014), indicating strong demand increase.
- High Purchase Value in 2014 → Total purchase surged to 2.07M, with an AOV of 43K, reflecting larger transactions per order.
- Top-Selling Products → Short-Sleeve Classic Jersey (L, M, S, XL) each contributed 0.25M, followed by Men's Sports Shorts (L, M, XL) at 0.12M.
- Storage Locations Driving High Sales → Finished Goods Storage (Location 7) had the largest purchase value (997K), highlighting key inventory locations.

📌**Complete**


![f02b1ce6-94ba-4115-ae99-26e459a565b7](https://github.com/user-attachments/assets/182afc4f-7d16-4059-9bfa-794ebea34e79)

- Steady Growth in Total Orders → 8,169 orders, with an increasing trend across years, reflecting strong demand.
- High Purchase Value → 56.8M total purchases, with an AOV of 6.96K, indicating sizable transactions per order.
- Top-Selling Products → HL Crankarm (3.2M), ML Mountain Pedal (2.4M), and Front & Rear Brakes (2.1M each) dominate purchase value, signaling high market demand.
- Order Status Trends → Majority of orders marked as Complete, but monitoring Pending & Rejected cases could improve fulfillment efficiency.


📌**Pending**

![d67a60c2-5fc1-4cce-9397-96b57a40f83c](https://github.com/user-attachments/assets/502cba04-5647-46ff-8778-cf4b394b2cde)

- Surge in Pending Orders → 475 pending orders in 2014 compared to only 2 in 2011, indicating possible fulfillment bottlenecks.
- High Purchase Value with Moderate AOV → 3.5M total purchase, with an AOV of 7.35K, suggesting large transactions but potential delays in processing.
- Top Performing Products → HL Crankarm (181K), ML Mountain Pedal (159K), ML Road Pedal (159K) dominate purchase value, signaling high demand.
- Inventory Concentration → Most orders linked to Location IDs 1, 6, and 50, showing potential stock management inefficiencies.

📌**Reject**

![3ded7b04-aae7-46c3-9a63-e8c2204be52d](https://github.com/user-attachments/assets/31072d30-8af3-4168-9ecd-b16a8096d87b)

- Increase in Rejected Orders Over Time → Rejections rose significantly from 4 (2011) to 60 (2013) before dropping to 38 (2014), indicating fluctuations in order processing issues.
- Growth in Total Purchase Value Despite Rejections → Purchases increased from 0.38M (2012) to 0.48M (2013), showing a resilient demand despite rejection trends.
- High-Value Products Identified → ML Mountain Pedal (106K), Front & Rear Brakes (91K each), ML Road Pedal (80K), and ML Crankarm (77K) lead in total purchase value, suggesting strong customer preference.
- Inventory Locations Linked to High Purchases → Tool Crib, Miscellaneous Storage, and Subassembly repeatedly appear in high-value transactions, pointing to key stock management areas.


## IV. 🔎Recommendation:

- **Enhance Sales for Top Products** – Focus marketing efforts on high-performing products like the HL Crankarm, ML Mountain Pedal, and ML Road Pedal to maximize revenue.
- **Optimize Inventory Management** – Investigate rejected orders and improve quality control and supplier reliability to minimize losses.
- **Expand Popular Categories** – Introduce variations within Components and Accessories to leverage customer interest and grow revenue.
- **Refine Order Processing** – Analyze pending and rejected orders to identify inefficiencies and improve order fulfillment systems.
- **Leverage Growth Insights** – Examine the successful strategies from 2013-2014 that led to high growth and replicate similar approaches for sustained future performance.
