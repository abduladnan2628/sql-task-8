Here is a complete **`README.md`** file you can include with your project for GitHub, based on your structured SQL implementation:

---

````markdown
# 🛒 Supermarket SQL Project

This project builds a **Supermarket Management System** using **MySQL**, showcasing how to use **reusable SQL blocks** with `CREATE PROCEDURE` and `CREATE FUNCTION`. It demonstrates how to manage products, customers, orders, and order details in a relational structure with reusable logic.

---

## 📦 Features

- Database design using normalized tables
- Foreign key relationships
- Reusable SQL blocks with:
  - ✅ `CREATE PROCEDURE` for conditional inserts
  - ✅ `CREATE FUNCTION` for calculations
- Demonstrates parameter handling and control flow with `IF` conditions

---

## 🧱 Database Schema

### 📌 Database: `Supermarket`

### Tables

#### 1. `Customers`
| Column      | Type           | Description            |
|-------------|----------------|------------------------|
| CustomerID  | INT, PK        | Auto-incremented ID    |
| Name        | VARCHAR(100)   | Customer name          |
| Email       | VARCHAR(100)   | Customer email         |
| Phone       | VARCHAR(15)    | Customer phone number  |

#### 2. `Products`
| Column      | Type            | Description              |
|-------------|-----------------|--------------------------|
| ProductID   | INT, PK         | Auto-incremented ID      |
| ProductName | VARCHAR(100)    | Product name             |
| Category    | VARCHAR(50)     | Product category         |
| Price       | DECIMAL(10,2)   | Unit price               |
| Stock       | INT             | Quantity in stock        |

#### 3. `Orders`
| Column      | Type            | Description                          |
|-------------|-----------------|--------------------------------------|
| OrderID     | INT, PK         | Auto-incremented ID                  |
| CustomerID  | INT, FK         | Linked to `Customers` table          |
| OrderDate   | DATE            | Date of the order                    |
| TotalAmount | DECIMAL(10,2)   | Total bill (optional, can be NULL)   |

#### 4. `OrderDetails`
| Column        | Type            | Description                        |
|---------------|-----------------|------------------------------------|
| OrderDetailID | INT, PK         | Auto-incremented ID                |
| OrderID       | INT, FK         | Linked to `Orders` table           |
| ProductID     | INT, FK         | Linked to `Products` table         |
| Quantity      | INT             | Quantity purchased                 |
| Price         | DECIMAL(10,2)   | Price at the time of order         |

---

## ⚙️ Stored Procedure

### `AddProduct`

This procedure inserts a new product, ensuring that the price is greater than zero.

```sql
CALL AddProduct('Detergent', 'Cleaning', 120.50, 50);
````

If the price is not valid (≤ 0), it throws an error using:

```sql
SIGNAL SQLSTATE '45000'
SET MESSAGE_TEXT = 'Price must be greater than 0';
```

---

## 🧮 Function

### `GetOrderTotal`

Calculates the total amount for an order by multiplying quantity and price from the `OrderDetails` table.

```sql
SELECT GetOrderTotal(1) AS TotalBill;
```

Returns `0` if the order does not exist or has no products.

---

## 📌 How to Run

1. Open your MySQL client or command line tool.
2. Paste and execute the SQL blocks from the following order:

   * `CREATE DATABASE` and `CREATE TABLE` scripts
   * Stored procedure `AddProduct`
   * Function `GetOrderTotal`
3. Use the `CALL` and `SELECT` commands to test.

---

## 🧠 Concepts Practiced

* SQL schema creation
* Data integrity via foreign keys
* Conditional logic with `IF`
* Error handling with `SIGNAL`
* Parameterized SQL procedures
* Value-returning SQL functions

---

## 📁 File Organization (Recommended)

```
supermarket-sql/
│
├── schema.sql              -- Contains CREATE DATABASE and CREATE TABLE statements
├── procedures.sql          -- Contains CREATE PROCEDURE block
├── functions.sql           -- Contains CREATE FUNCTION block
├── README.md               -- This documentation file
```

---

## ✅ Author

**Adnan Shafi**
SQL + Backend Learning Project | July 2025

---

## 📝 License

This project is open-source and available for educational or demo use. Feel free to modify and extend.

```

---

Let me know if you want me to generate the `.sql` files or example data insert scripts for testing!
```
