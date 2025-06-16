## **Power BI Sales Intelligence Dashboard for a Multinational Grocery Retail Chain**
- Built a dynamic Power BI dashboard for a multinational grocery chain using 7 interrelated tables. Delivered insights on sales trends, product performance, customer    behavior, and employee productivity. Used DAX, interactive visuals, and drill-downs to support strategic business decisions

---

## Data Understanding

### Table: Categories
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


