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

### Table: Cities
- Role: Dimension table containing city-level information.
- Primary Key: CityID
- Key Columns: CityID, CityName, ZipCode, CountyID
- Relationships:
   - One-to-many (1:*) with Customers and Employees
   - Connects to Countries via CountyID
- Notes: Ensures geographic breakdown of customers and employees.

### Table: Countries
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

### Table: Sales
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

### Table: Categories
- Missing Values: None
- Duplicates: None in CategoryID
- Data Types: All valid
- Value Count: 6 categories
- Spelling: Clean
- Unused Keys: All used in Products
- Primary Key Confirmed: Yes (CategoryID)
✅ Status: Clean and ready

### Table: Cities 

- Missing Values: None found ✅
- Duplicates: No duplicates in CityID ✅
- Data Types: Correct (CityID = number, ZipCode = text) ✅
- CityName: Spelling consistent; cleaned casing ✅
- CountryID: All values valid and match Countries table ✅
- Primary Key Confirmed: CityID ✅
- Relationships Confirmed:
   - Used in Customers and Employees
✅ Status: Clean and Ready

### Table: Countries

- Missing Values: None ✅
- Duplicates: CountryID is unique ✅
- Data Types:
   - CountryID: Whole Number ✅
   - CountryCode: Text ✅
   - CountryName: Text ✅
- CountryName: Cleaned, consistent casing ✅
- Unused Foreign Keys: All CountryIDs used in Cities ✅
- Primary Key Confirmed: Yes ✅
✅ Status: Clean and ready

### Table - Customers 

- Missing Values: None in CustomerID or CityID ✅
- Names: Some blanks in MiddleInitial (acceptable) ✅
- Duplicates: CustomerID is unique ✅
- Data Types: All valid ✅
- Spelling/Consistency: Names cleaned and capitalized ✅
- Unused Keys: All CustomerIDs used in Sales ✅
- Primary Key Confirmed: Yes ✅
✅ Status: Clean and ready

### Table - Employees 

- Missing Values:
   - None in EmployeeID or CityID ✅
   - BirthDate & HireDate complete ✅
- Duplicates: EmployeeID is unique ✅
- Data Types:
   - Dates properly formatted ✅
   - Gender values standardized (M/F) ✅
- Spelling/Consistency: Names and Gender cleaned ✅
- Unused Keys: All EmployeeIDs linked with Sales ✅
- Primary Key Confirmed: Yes ✅
✅ Status: Clean and ready

### Table - Products 

- Missing Values: None in critical columns ✅
- Duplicates: ProductID is unique ✅
- Data Types:
   - Price = Decimal ✅
   - ModifyDate = Date ✅
   - CategoryID, VitalityDays = Whole Number ✅
   - IsAllergic and Resistant: Cleaned and standardized ✅
- Spelling/Consistency: Fixed Class and Resistant values ✅
- Foreign Keys:
   - All ProductIDs used in Sales ✅
   - All CategoryIDs match Category table ✅
- Primary Key Confirmed: Yes ✅
✅ Status: Clean and ready

### Table - Sales 

- Missing Values: None in key columns ✅
- Duplicates: SalesID is unique ✅
- Data Types:
   - Dates and numbers validated ✅
   - Discounts between 0–1 confirmed ✅
- Value Ranges:
   - Quantity and TotalPrice > 0 ✅
- Foreign Keys:
   - All linked to Products, Customers, Employees ✅
- Primary Key Confirmed: Yes ✅
✅ Status: Clean and analysis-ready

## Data Modeling














