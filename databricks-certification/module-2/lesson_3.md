### Data Transformation

- Data transformation is the process of converting raw data into a structured and usable format for analysis and reporting.
- Common transformation operations include filtering, aggregating, joining, and enriching data.
- In Databricks, data transformation can be performed using various tools and languages, including:
  - **SQL**: Using SQL queries to manipulate and transform data in Delta Tables.
  - **DataFrames**: Using Spark DataFrames in Python, Scala, or R for more complex transformations.
  - **Delta Live Tables**: A framework for building reliable, maintainable, and testable data pipelines with declarative transformations.

- **CRUD**:
    - **Create**:
        - `CREATE` and `INSERT` statements to add new data to Delta Tables.
    - **Read**:
        - `SELECT` statements to query and retrieve data from Delta Tables.
    - **Update**:
        - `UPDATE` statements to modify existing data in Delta Tables.
        - `ALTER` statements to change table schema or properties.
        - `INSERT` with `OVERWRITE` to replace data.
        - `DELETE` statements to remove data from Delta Tables.
    - **Delete**:
        - `DROP` statements to remove entire Delta Tables.

- **Duplication Removal**:
    - Use `SELECT DISTINCT` to retrieve unique records.
    - Use
    ```sql
    SELECT col1, MIN(col2)
    FROM table_name
    GROUP BY col1;
    ```
    to get unique records based on specific columns.

- **JOIN Types**:
    - **Inner Join**: Returns records with matching values in both tables.
    - **Left Join**: Returns all records from the left table and matched records from the right table.
    - **Right Join**: Returns all records from the right table and matched records from the left table.
    - **Full Outer Join**: Returns all records when there is a match in either left or right table.
    - **Cross Join**: Returns the Cartesian product of both tables.

- **COUNT**:
    - Use `COUNT(column_name)` to count non-null values in a specific column.
    - Use `COUNT(*)` to count all rows in a table, including those with null values.
    - Use `COUNT(DISTINCT column_name)` to count unique non-null values in a specific column.
    - Use `COUNT_IF(condition)` to count rows that meet a specific condition.

- And others SQL operations for data transformation as needed.