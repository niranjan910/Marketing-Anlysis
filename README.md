## **Power BI Sales Intelligence Dashboard for a Multinational Grocery Retail Chain**
- Built a dynamic Power BI dashboard for a multinational grocery chain using 7 interrelated tables. Delivered insights on sales trends, product performance, customer    behavior, and employee productivity. Used DAX, interactive visuals, and drill-downs to support strategic business decisions

---

## Data Understanding

Table: Categories
- Role: Dimension table that stores product category information.
- Primary Key: CategoryID
- Key Columns: CategoryID, CategoryName
- Relationships: Connects to the Products table through CategoryID.
- Notes: Used to categorize products into groups (e.g., beverages, snacks).

Table: Cities
- Role: Dimension table containing city-level information.
- Primary Key: CityID
- Key Columns: CityID, CityName, ZipCode, CountyID
- Relationships:
   - One-to-many (1:*) with Customers and Employees
   - Connects to Countries via CountyID
- Notes: Ensures geographic breakdown of customers and employees.

Table: Countries
- Role: Dimension table containing country-level information.
- Primary Key: CountyID (used as CountryID)
- Key Columns: CountyID, CountyCode, CountryName
- Relationships:
   - One-to-many (1:*) with Cities table via CountyID
- Notes:
   - Enables regional analysis (sales, customers) by country.
   - CountyID acts as the joining key; ensure Cities[CountyID] has matching values.

### Table: Customers
- Role: Dimension table storing customer details.
- Primary Key: CustomerID
- Key Columns: CustomerID, FirstName, LastName, MiddleInitial, Address, CityID
- Relationships:
   - Many-to-one ( *:1 ) with Cities (via CityID)
   - One-to-many ( 1:* ) with Sales (via CustomerID)
- Notes:
   - Enables demographic and geographic sales analysis.
   - Address info can be enhanced by joining with Cities → Countries.

### Table: Employees
- Role: Dimension table that stores employee (salesperson) information.
- Primary Key: EmployeeID
- Key Columns: EmployeeID, FirstName, LastName, Gender, BirthDate, HireDate, CityID
- Relationships:
   - Many-to-one ( *:1 ) with Cities via CityID
   - EmployeeID is used in Sales table as SalesPersonID (check for mapping)
- Notes:
   - Enables sales performance tracking by salesperson
   - CityID links employees to locations for geographic analysis

### Table: Products
- Role: Dimension table that stores detailed product information.
- Primary Key: ProductID
- Key Columns:
   - ProductID
   - ProductName
   - Price
   - CategoryID
   - Class, IsAllergic, Resistant, VitalityDays
- Relationships:
   - One-to-many (1:*) with Sales via ProductID
   - Many-to-one (*:1) with Categories via CategoryID
- Notes:
   - CategoryID connects to Categories table for grouping
   - Enables product-level sales insights (e.g., top products, allergy filters, etc.)

Table: Sales
- Role: Fact table containing transaction-level sales data.
- Primary Key: SalesID (or TransactionNumber if SalesID is not unique)
- Key Columns:
   - SalesID / TransactionNumber
   - CustomerID
   - ProductID
   - SalesPersonID (EmployeeID)
   - SalesDate
   - TotalPrice, Discount, Quantity
- Relationships:
   - Many-to-one (*:1) with:
     - Customers via CustomerID
     - Products via ProductID
     - Employees via SalesPersonID
- Notes:
   - Core table for all revenue, customer behavior, and product sales analysis.
   - Make sure no missing foreign keys (i.e., all IDs should match related tables).

## Data Exploration 

Table: Categories
- Missing Values: None
- Duplicates: None in CategoryID
- Data Types: All valid
- Value Count: 6 categories
- Spelling: Clean
- Unused Keys: All used in Products
- Primary Key Confirmed: Yes (CategoryID)
✅ Status: Clean and ready











