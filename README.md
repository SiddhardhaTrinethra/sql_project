# sql_project
Grocery Store Management System
# Grocery Store Management (SQL)

A concise SQL project to model and analyze grocery store operations with a relational database. The project covers schema design, data loading, and analytical queries.

## Features

* **7-table schema**: suppliers, categories, employees, customers, products, orders, order\_details.
* **Clear relationships** with PK/FK constraints.
* **Sample data** for testing queries.
* **Example queries**: total revenue, average order value, top customers, low-stock alerts.
* **Performance tips**: indexing, CTE usage, window functions.

## Setup

1. Create `grocery_store` database.
2. Run `01_schema.sql` to create tables.
3. Run `02_seed.sql` to insert sample data.
4. Optionally run `03_indexes.sql` for performance.

## Example Query

**Average Order Value per Employee**:

```sql
WITH order_rev AS (
  SELECT o.emp_id, SUM(od.quantity * (od.unit_price * (1 - od.discount/100))) AS revenue
  FROM orders o
  JOIN order_details od ON od.order_id = o.order_id
  GROUP BY o.order_id, o.emp_id
)
SELECT emp_id, ROUND(AVG(revenue),2) AS avg_order_value
FROM order_rev
GROUP BY emp_id;
```

## Tech Stack

* **Database**: MySQL 8+
* **Optional**: Power BI or Python for visualization

## Author

<Your Name> — SQL & Data Analytics Enthusiast
