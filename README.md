# 🧠 Power BI Sales Intelligence Dashboard  
**Multinational Grocery Retail Chain (End-to-End Project)**

This project presents a comprehensive **Power BI dashboard** built using **seven interrelated tables** from a multinational grocery retail dataset. It delivers key insights into **sales trends**, **product performance**, **customer demographics**, and **employee contributions** to support strategic decision-making.

---

## 📁 Dataset Overview

**Tables Used:**  
1. Categories  
2. Cities  
3. Countries  
4. Customers  
5. Employees  
6. Products  
7. Sales  

---

## 🔍 Data Understanding

### 🟦 Categories
- **Role:** Product grouping dimension
- **Primary Key:** `CategoryID`
- **Columns:** `CategoryID`, `CategoryName`
- **Relationship:** Linked to `Products` via `CategoryID`
- **Use Case:** Product segmentation

---

### 🟩 Cities
- **Role:** Geographic dimension
- **Primary Key:** `CityID`
- **Columns:** `CityID`, `CityName`, `ZipCode`, `CountyID`
- **Relationships:**
  - One-to-many with `Customers`, `Employees`
  - Many-to-one with `Countries` via `CountyID`
- **Use Case:** City-level sales and staffing analysis

---

### 🌍 Countries
- **Role:** Geographic hierarchy
- **Primary Key:** `CountyID` (used as `CountryID`)
- **Columns:** `CountyID`, `CountyCode`, `CountryName`
- **Relationship:** One-to-many with `Cities`
- **Use Case:** Regional performance breakdown

---

### 👥 Customers
- **Role:** Buyer dimension
- **Primary Key:** `CustomerID`
- **Columns:** `CustomerID`, `FirstName`, `LastName`, `MiddleInitial`, `Address`, `CityID`
- **Relationships:**
  - Many-to-one with `Cities`
  - One-to-many with `Sales`
- **Use Case:** Customer profiling and location mapping

---

### 👨‍💼 Employees
- **Role:** Sales team dimension
- **Primary Key:** `EmployeeID`
- **Columns:** `EmployeeID`, `FirstName`, `LastName`, `Gender`, `BirthDate`, `HireDate`, `CityID`
- **Relationships:**
  - Many-to-one with `Cities`
  - Referenced by `Sales` via `SalesPersonID`
- **Use Case:** Employee-level sales tracking

---

### 📦 Products
- **Role:** SKU-level product data
- **Primary Key:** `ProductID`
- **Columns:** `ProductID`, `ProductName`, `Price`, `CategoryID`, `Class`, `IsAllergic`, `Resistant`, `VitalityDays`, `ModifyDate`
- **Relationships:**
  - One-to-many with `Sales`
  - Many-to-one with `Categories`
- **Use Case:** Product performance and filtering (e.g., allergies, price)

---

### 💰 Sales (Fact Table)
- **Role:** Transaction-level fact table
- **Primary Key:** `SalesID` or `TransactionNumber`
- **Columns:** `SalesID`, `TransactionNumber`, `CustomerID`, `ProductID`, `SalesPersonID`, `SalesDate`, `TotalPrice`, `Discount`, `Quantity`
- **Relationships:** 
  - Many-to-one with `Customers`, `Products`, `Employees`
- **Use Case:** Central table for all KPIs and visualizations

---

## 🧪 Data Exploration Summary

### ✅ Categories
- No missing values or duplicates
- All IDs and names validated
- All foreign keys used
- ✔️ Clean & Ready

### ✅ Cities
- Valid data types and IDs
- Consistent spelling and casing
- Foreign keys correctly mapped to `Countries`
- ✔️ Clean & Ready

### ✅ Countries
- Unique `CountyID`s
- No missing values
- Country names and codes standardized
- ✔️ Clean & Ready

### ✅ Customers
- No critical missing values
- Names formatted and capitalized
- Connected to `Cities` and `Sales`
- ✔️ Clean & Ready

### ✅ Employees
- Birth and hire dates validated
- Gender values standardized
- No missing keys
- ✔️ Clean & Ready

### ✅ Products
- Clean prices and categories
- Proper formatting for binary fields
- Foreign keys match with `Categories` and `Sales`
- ✔️ Clean & Ready

### ✅ Sales
- No missing values in critical columns
- Discounts within expected range
- Date, quantity, and price values validated
- ✔️ Clean & Ready

---

## 🔗 Data Modeling

### Relationship Summary

| Table 1     | Column          | ➡️ | Table 2     | Column       | Relationship Type |
|-------------|------------------|----|--------------|---------------|--------------------|
| Sales       | CustomerID       | ➡️ | Customers     | CustomerID     | Many-to-One        |
| Sales       | ProductID        | ➡️ | Products      | ProductID      | Many-to-One        |
| Sales       | SalesPersonID    | ➡️ | Employees     | EmployeeID     | Many-to-One        |
| Products    | CategoryID       | ➡️ | Categories    | CategoryID     | Many-to-One        |
| Customers   | CityID           | ➡️ | Cities        | CityID         | Many-to-One        |
| Employees   | CityID           | ➡️ | Cities        | CityID         | 🔸 *Inactive* (to avoid ambiguity) |
| Cities      | CountyID         | ➡️ | Countries     | CountyID       | Many-to-One        |

✔️ Model follows **Star Schema**, with `Sales` as the fact table surrounded by dimension tables.  

---

> ✅ **Next Step:** DAX Measures Creation

---
