
# Addressing Inefficiencies in Order Processing and Inventory Management

To improve the operations of the manufacturing company and address inefficiencies, it is important to build a database that efficiently manages customer orders, inventory, and related operations. Below, I will define the tables, their columns with appropriate data types, and the relationships between these tables. This will help streamline processes and reduce errors.

![image](https://github.com/user-attachments/assets/f7cfe636-6902-4db9-9693-bafafb5d8f46)
![image](https://github.com/user-attachments/assets/c21fe397-5c80-48ba-8344-a2dc055a3238)
![image](https://github.com/user-attachments/assets/a2c348c2-a1b0-409c-a024-74470e6f6207)
![image](https://github.com/user-attachments/assets/085c407a-3e59-4697-b257-4c60b922ae19)
![image](https://github.com/user-attachments/assets/69189221-8bee-477b-ab26-8cf036796804)
![image](https://github.com/user-attachments/assets/2c90ad99-bdfe-4d84-9f77-54e060647eef)






---

### Entity Relationships

1. **Customers ↔ Orders**
   - `CustomerID` in **Orders** creates a **One-to-Many** relationship between **Customers** and **Orders**.
     - A single customer can place multiple orders.

2. **Orders ↔ OrderDetails**
   - `OrderID` in **OrderDetails** creates a **One-to-Many** relationship between **Orders** and **OrderDetails**.
     - An order can have multiple associated products (via order details).

3. **OrderDetails ↔ Products**
   - `ProductID` in **OrderDetails** creates a **Many-to-One** relationship between **OrderDetails** and **Products**.
     - Multiple order details can reference the same product.

4. **Products ↔ Inventory**
   - `ProductID` in **Inventory** creates a **One-to-One** relationship between **Products** and **Inventory**.
     - Each product corresponds to a single inventory record.

5. **Products ↔ Suppliers**
   - `SupplierID` in **Products** creates a **Many-to-One** relationship between **Products** and **Suppliers**.
     - Multiple products can be provided by a single supplier.


[Click here to view the presentation](https://m365x54021218-my.sharepoint.com/:p:/g/personal/gabriel_ogunbiyi_gabbee_com_ng/EWGL6I9yyllHkCIVqeUpRDEBfkQuFK75PRoDuYfmYbIjBw?e=nCaGsw)


