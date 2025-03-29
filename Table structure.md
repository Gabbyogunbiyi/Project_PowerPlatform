# 📌 Dataverse Schema: Alison Manufacturing Order & Inventory Management

## 🏢 Overview
This repository contains a **Dataverse table schema** to streamline **customer order** and **inventory management** in a manufacturing company. This setup optimizes workflows in **Power Apps**, **Power Automate**, and **Power BI**.

## 🗄️ Tables & Fields

### 1️⃣ Customers Table (`crms_Customers`)
Stores customer details.
```plaintext
- Customer ID (Primary Key, AutoNumber)
- First Name (Text, Required)
- Last Name (Text, Required)
- Email (Email, Required, Unique)
- Phone (Phone)
- Address (Text)
- City (Text)
- State (Text)
- Zip Code (Text)
- Created On (DateTime, Auto)
```

### 2️⃣ Products Table (`crms_Products`)
Manages inventory.
```plaintext
- Product ID (Primary Key, AutoNumber)
- Product Name (Text, Required)
- Description (Multiline Text)
- Price (Currency, Required)
- Stock Quantity (Whole Number, Required)
- Reorder Level (Whole Number, Required)
- Created On (DateTime, Auto)
```

### 3️⃣ Orders Table (`crms_Orders`)
Tracks customer purchases.
```plaintext
- Order ID (Primary Key, AutoNumber)
- Customer (Lookup, `crms_Customers`, Required)
- Order Date (DateTime, Auto)
- Total Amount (Currency, Calculated)
- Order Status (Choice: Pending, Processing, Shipped, Delivered, Cancelled)
- Created On (DateTime, Auto)
```

### 4️⃣ Order Details Table (`crms_OrderDetails`)
Handles many-to-many relationships between orders and products.
```plaintext
- Order Detail ID (Primary Key, AutoNumber)
- Order (Lookup, `crms_Orders`, Required)
- Product (Lookup, `crms_Products`, Required)
- Quantity (Whole Number, Required)
- Unit Price (Currency, Required)
- Subtotal (Currency, Calculated: `Quantity * Unit Price`)
- Created On (DateTime, Auto)
```

### 5️⃣ Inventory Transactions Table (`crms_InventoryTransactions`)
Tracks stock changes.
```plaintext
- Transaction ID (Primary Key, AutoNumber)
- Product (Lookup, `crms_Products`, Required)
- Transaction Type (Choice: Restock, Sale)
- Quantity Changed (Whole Number, Required)
- Transaction Date (DateTime, Auto)
- Created On (DateTime, Auto)
```

## 🔗 Relationships
```plaintext
1️⃣ Customers ↔ Orders (One-to-Many) → Each customer can place multiple orders.
2️⃣ Orders ↔ Order Details (One-to-Many) → Each order contains multiple products.
3️⃣ Products ↔ Order Details (Many-to-Many) → Each product appears in multiple orders.
4️⃣ Products ↔ Inventory Transactions (One-to-Many) → Each product has stock updates.
```

## 🚀 Features & Benefits
✅ **Automated Inventory Updates** → Stock adjusts when an order is placed.
✅ **Reorder Alerts** → Alerts when stock goes below the **Reorder Level**.
✅ **Real-time Order Tracking** → Status updates (Pending, Shipped, etc.).
✅ **Power Platform Integration** → Works with **Power Apps** & **Power Automate**.
✅ **Customer Insights** → Analyze frequent buyers & sales trends.

## 📌 Next Steps
Would you like to add **Suppliers**, **Shipping**, or **Employee Management** tables? 🤔
