### Unity Catalog

- Centralized governance solution for data and AI assets in Databricks
- Provides fine-grained access control, auditing, and data lineage across all workspaces
- Key features include:
  - **Centralized Data Governance**: Manage access policies for data assets across multiple workspaces
  - **Fine-Grained Access Control**: Control access at the table, column, and row levels
  - **Data Lineage**: Track the origin and transformations of data for compliance
  - **Integration with Cloud IAM**: Leverage existing cloud identity and access management systems
- **Unity Catalog Structure**:
  - **Metastore**: Central repository for all data assets and their metadata
  - **Catalogs**: Top-level containers for databases and tables
  - **Schemas (Databases)**: Logical grouping of tables and views within a catalog
  - **Tables and Views**: Actual data storage and queryable objects
- **Creating a Unity Catalog**:
  ```sql
  CREATE CATALOG catalog_name;
  ```
- **Creating a Schema (Database) in Unity Catalog**:
  ```sql
  CREATE SCHEMA catalog_name.schema_name;
  ```
- **Creating a Table in Unity Catalog**:
  ```sql
  CREATE TABLE catalog_name.schema_name.table_name (column1 TYPE, column2 TYPE, ...);
  ```
- The `SHOW GRANTS ON <object>` command displays the access permissions for a specified data object in Unity Catalog.
- The `DESCRIBE DETAIL <table_name>` command provides detailed information about a table in Unity Catalog, including its schema, location, and properties.
- **Access Control Example**:
  ```sql
  GRANT SELECT ON TABLE catalog_name.schema_name.table_name TO `user_or_group`;
  ```
- **Row-Level Security Example**:
  ```sql
  CREATE ROW ACCESS POLICY policy_name
  AS (user STRING)
  USING (user = current_user());
  ```
- **Attaching Row Access Policy to Table**:
  ```sql
  ALTER TABLE catalog_name.schema_name.table_name
  ADD ROW ACCESS POLICY policy_name TO COLUMN column_name;
  ```
- Unity Catalog integrates with Delta Lake to provide governance for Delta Tables, ensuring secure and compliant data management.

### Object Hierarchy in Unity Catalog
- Unity Catalog follows a hierarchical structure:
  - **Catalog**: The top-level container for data assets.
  - **Schema (Database)**: A logical grouping of tables and views within a catalog.
  - **Table/View**: The actual data storage and queryable objects.
- This hierarchy allows for organized management and access control of data assets across multiple workspaces.
- Example structure:
  ```
  Catalog: sales_catalog
    ├── Schema: public
    │   ├── Table: customers
    │   ├── Table: orders
    │   └── View: customer_orders
    └── Schema: analytics
        ├── Table: sales_summary
        └── View: monthly_sales
  ```
- Each level in the hierarchy can have its own access control policies, allowing for granular management of data permissions.

