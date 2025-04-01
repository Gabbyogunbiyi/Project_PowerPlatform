# 📌 Dataverse Schema: Alison Manufacturing Order & Inventory Management

## 1. **Customer Table**
This table stores customer information.

| Column Name      | Data Type   | Description                             |
|------------------|-------------|-----------------------------------------|
| customer_id      | INT         | Primary Key, Unique ID for the customer |
| name             | VARCHAR(100) | Customer's full name                   |
| address          | TEXT        | Customer's address                     |
| phone            | VARCHAR(15) | Customer's phone number                |
| email            | VARCHAR(100) | Customer's email address               |
| contact_person   | VARCHAR(100) | Primary contact at the customer site   |
| created_at       | TIMESTAMP   | Date and time when the customer was added |
| updated_at       | TIMESTAMP   | Date and time when customer information was last updated |

---

## 2. **Product Table**
This table stores product information that will be sold to customers.

| Column Name      | Data Type   | Description                            |
|------------------|-------------|----------------------------------------|
| product_id       | INT         | Primary Key, Unique ID for the product |
| product_name     | VARCHAR(255) | Name of the product                   |
| description      | TEXT        | Description of the product            |
| unit_price       | DECIMAL(10, 2) | Price of one unit of the product      |
| stock_quantity   | INT         | Quantity of the product in stock      |
| created_at       | TIMESTAMP   | Date and time the product was added   |
| updated_at       | TIMESTAMP   | Date and time the product was last updated |

---

## 3. **Order Table**
This table stores customer orders.

| Column Name      | Data Type   | Description                                 |
|------------------|-------------|---------------------------------------------|
| order_id         | INT         | Primary Key, Unique ID for the order        |
| customer_id      | INT         | Foreign Key to `Customer` table             |
| order_date       | TIMESTAMP   | Date and time when the order was placed     |
| total_amount     | DECIMAL(10, 2) | Total amount of the order                  |
| order_status     | VARCHAR(50) | Status of the order (Pending, Shipped, Delivered, etc.) |
| payment_status   | VARCHAR(50) | Payment status (Paid, Pending, etc.)        |
| shipment_status  | VARCHAR(50) | Shipment status (In Transit, Delivered, etc.) |
| delivery_date    | TIMESTAMP   | Expected delivery date                     |

---

## 4. **Order Item Table**
This table stores details of the items ordered in a particular order. A single order can have multiple products.

| Column Name      | Data Type   | Description                                 |
|------------------|-------------|---------------------------------------------|
| order_item_id    | INT         | Primary Key, Unique ID for the order item   |
| order_id         | INT         | Foreign Key to `Order` table                |
| product_id       | INT         | Foreign Key to `Product` table              |
| quantity         | INT         | Quantity of the product ordered            |
| unit_price       | DECIMAL(10, 2) | Price of one unit of the product at time of order |
| total_price      | DECIMAL(10, 2) | Total price (quantity * unit_price)        |

---

## 5. **Inventory Movement Table**
This table stores the movements of inventory, such as restocks and sales.

| Column Name      | Data Type   | Description                                 |
|------------------|-------------|---------------------------------------------|
| inventory_id     | INT         | Primary Key, Unique ID for inventory movement |
| product_id       | INT         | Foreign Key to `Product` table              |
| quantity_in      | INT         | Quantity added to inventory (positive value) |
| quantity_out     | INT         | Quantity removed from inventory (negative value) |
| movement_type    | VARCHAR(50) | Type of movement (Restock, Sale, Return)   |
| date             | TIMESTAMP   | Date and time of inventory movement        |

---

## 6. **Employee Table (Optional)**
This table stores information about employees who are involved in managing orders and inventory.

| Column Name      | Data Type   | Description                             |
|------------------|-------------|-----------------------------------------|
| employee_id      | INT         | Primary Key, Unique ID for the employee |
| name             | VARCHAR(100) | Full name of the employee              |
| role             | VARCHAR(50)  | Role of the employee (Sales, Warehouse, etc.) |
| email            | VARCHAR(100) | Employee's email address               |
| phone            | VARCHAR(15) | Employee's phone number                |
| created_at       | TIMESTAMP   | Date and time the employee was added   |

---

## 7. **Shipment Table**
This table stores details about shipments for customer orders.

| Column Name      | Data Type   | Description                                 |
|------------------|-------------|---------------------------------------------|
| shipment_id      | INT         | Primary Key, Unique ID for the shipment     |
| order_id         | INT         | Foreign Key to `Order` table                |
| shipment_date    | TIMESTAMP   | Date the order was shipped                  |
| shipment_method  | VARCHAR(50) | Method of shipment (Courier, Local Delivery, etc.) |
| tracking_number  | VARCHAR(50) | Shipment tracking number                   |

---

## 8. **Payment Table (Optional)**
This table stores payment information related to customer orders.

| Column Name      | Data Type   | Description                                |
|------------------|-------------|--------------------------------------------|
| payment_id       | INT         | Primary Key, Unique ID for the payment     |
| order_id         | INT         | Foreign Key to `Order` table               |
| payment_date     | TIMESTAMP   | Date when the payment was made             |
| payment_method   | VARCHAR(50) | Method of payment (Credit Card, Bank Transfer, etc.) |
| payment_amount   | DECIMAL(10, 2) | Amount paid                             |
