# 📌 Dataverse Schema: Alison Manufacturing Order & Inventory Management

## 1. **Customer Table**
This table stores customer information.

| Column Name     | Data Type     | Description                          |
|-----------------|---------------|--------------------------------------|
| CustomerID      | INT (PK)      | Unique identifier for each customer |
| FirstName       | VARCHAR(255)  | Customer's first name               |
| LastName        | VARCHAR(255)  | Customer's last name                |
| Email           | VARCHAR(255)  | Customer's email address            |
| Phone           | VARCHAR(15)   | Customer's phone number             |

---

## 2. **Order Table**
This table stores customer orders.

| Column Name     | Data Type     | Description                             |
|-----------------|---------------|-----------------------------------------|
| OrderID         | INT (PK)      | Unique identifier for each order       |
| CustomerID      | INT (FK)      | Foreign key referencing Customers      |
| OrderDate       | DATETIME      | Date when the order was placed         |
| Status          | VARCHAR(50)   | Status of the order (e.g., Pending)     |
| ShippingAddress | VARCHAR(255)  | Shipping address for the order         |
| PaymentStatus   | VARCHAR(50)   | Payment status (e.g., Paid, Pending)   |
| TotalAmount     | DECIMAL(10, 2)| Total amount for the order             |


---

## 3. **Order Item Table**
This table list out all the individual items that have been ordered. It provides information about which ordereach item belongs to.

| Column Name     | Data Type     | Description                             |
|-----------------|---------------|-----------------------------------------|
| OrderItemID     | INT (PK)      | Unique identifier for each order item  |
| OrderID         | INT (FK)      | Foreign key referencing Orders         |
| ProductID       | INT (FK)      | Foreign key referencing Products       |
| Quantity        | INT           | Quantity of the product in the order   |
| PriceAtTime     | DECIMAL(10, 2)| Price of the product at the time of order |
| TotalAmount     | DECIMAL(10, 2)| Total amount for the item in the order |


---

## 4. **Product Table**
It stores key information about the product.

| Column Name     | Data Type     | Description                             |
|-----------------|---------------|-----------------------------------------|
| ProductID       | INT (PK)      | Unique identifier for each product     |
| ProductName     | VARCHAR(255)  | Name of the product                    |
| ProductDescription | TEXT       | Description of the product             |
| Category        | VARCHAR(100)  | Category the product belongs to        |
| Price           | DECIMAL(10, 2)| Current price of the product           |
| StockQuantity   | INT           | Quantity of product in stock           |
| ReorderLevel    | INT           | Reorder level to trigger restocking    |
| SupplierID      | INT (FK)      | Foreign key referencing Suppliers      |

---

## 5. **Inventory Table**
An organized summary of every product Alison has in stock.

| Column Name     | Data Type     | Description                             |
|-----------------|---------------|-----------------------------------------|
| InventoryID     | INT (PK)      | Unique identifier for the inventory record |
| ProductID       | INT (FK)      | Foreign key referencing Products       |
| StockQuantity   | INT           | Current stock quantity in the warehouse|
| WarehouseLocation | VARCHAR(100) | Location of the product in the warehouse|
| LastRestocked   | DATETIME      | Date when the product was last restocked |


---

## 6. **Payment Table**
Monetary details of all payments towards each order.

| Column Name     | Data Type     | Description                             |
|-----------------|---------------|-----------------------------------------|
| PaymentID       | INT (PK)      | Unique identifier for each payment     |
| OrderID         | INT (FK)      | Foreign key referencing Orders         |
| PaymentDate     | DATETIME      | Date when the payment was made         |
| PaymentAmount   | DECIMAL(10, 2)| Total payment amount                   |
| PaymentMethod   | VARCHAR(50)   | Method of payment (e.g., Credit Card)  |
| PaymentStatus   | VARCHAR(50)   | Status of payment (e.g., Completed)    |


---

## 7. **Employee Table**
This table stores employee in charge of order approval and inventory.

| Column Name     | Data Type     | Description                             |
|-----------------|---------------|-----------------------------------------|
| EmployeeID      | INT (PK)      | Unique identifier for each employee    |
| FirstName       | VARCHAR(255)  | Employee's first name                  |
| LastName        | VARCHAR(255)  | Employee's last name                   |
| Email           | VARCHAR(255)  | Employee's email address               |
| Phone           | VARCHAR(15)   | Employee's phone number                |
| Role            | VARCHAR(100)  | Job role (e.g., Sales, Manager, etc.)  |


---

- **Customers → Orders**: One **Customer** can place many **Orders**.
  - **Customers** (CustomerID) → **Orders** (CustomerID)

- **Orders → Order Items**: One **Order** can have many **Order Items**.
  - **Orders** (OrderID) → **Order Items** (OrderID)

- **Order Items → Products**: Many **Order Items** can refer to one **Product**.
  - **Order Items** (ProductID) → **Products** (ProductID)

- **Orders → Payments**: One **Order** may have one or multiple **Payments**.
  - **Orders** (OrderID) → **Payments** (OrderID)

- **Orders → Shippers**: Many **Orders** can be shipped by one **Shipper**.
  - **Orders** (ShipperID) → **Shippers** (ShipperID)

- **Products → Inventory**: Each **Product** has exactly one corresponding **Inventory** record.
  - **Products** (ProductID) → **Inventory** (ProductID)

- **Employees → Orders**: Many **Orders** can be processed by one **Employee**.
  - **Employees** (EmployeeID) → **Orders** (EmployeeID)


