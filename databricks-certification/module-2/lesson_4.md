### JSON, Array, and Function

- **JSON (JavaScript Object Notation)** is a lightweight data interchange format that is easy for humans to read and write, and easy for machines to parse and generate. It is commonly used for transmitting data in web applications.
  - Example of a JSON object:
    ```json
    {
      "name": "John Doe",
      "age": 30,
      "is_student": false,
      "courses": ["Math", "Science", "History"],
      "address": {
        "street": "123 Main St",
        "city": "Anytown",
        "zip": "12345"
      }
    }
    ```
    - **Manipulating JSON**:
      - Accessing values: `json_object["name"]` returns `"John Doe"`
      - Iterating through arrays: Loop through `json_object["courses"]` to get each course.

- **Array** is a data structure that can hold a fixed-size sequential collection of elements of the same type. In programming languages, arrays are used to store multiple values in a single variable.
  - Example of an array in Python:
    ```python
    numbers = [1, 2, 3, 4, 5]
    ```

- **Function** is a block of organized, reusable code that performs a single action or task. Functions help in modularizing code, making it easier to read, maintain, and debug.
  - Example of a function in Python:
    ```python
    def greet(name):
        return f"Hello, {name}!"
    ```

- **Using JSON in Databricks**:
  - Databricks provides built-in support for reading and writing JSON data using Spark DataFrames.
  - Example of reading a JSON file into a DataFrame:
    ```python
    df = spark.read.json("path/to/json/file.json")
    df.show()
    ```
  - Example of writing a DataFrame to a JSON file:
    ```python
    df.write.json("path/to/output/json/file.json")
    ```

- **Working with Arrays in Databricks**:
  - Spark SQL provides functions to work with arrays, such as `explode`, `array_contains`, and `size`.
  - Example of using `explode` to flatten an array column:
    ```python
    from pyspark.sql.functions import explode

    df = spark.createDataFrame([("John", ["Math", "Science"]), ("Jane", ["History"])], ["name", "courses"])
    df_exploded = df.select("name", explode("courses").alias("course"))
    df_exploded.show()
    ```
- **Defining and Using Functions in Databricks**:
  - You can define user-defined functions (UDFs) in Databricks to extend Spark's functionality.
  - Example of defining a UDF in Python:
    ```python
    from pyspark.sql.functions import udf
    from pyspark.sql.types import StringType

    def to_uppercase(name):
        return name.upper()
    uppercase_udf = udf(to_uppercase, StringType())
    df = spark.createDataFrame([("John",), ("Jane",)], ["name"])
    df_with_uppercase = df.withColumn("name_uppercase", uppercase_udf("name"))
    df_with_uppercase.show()
    ```

- **Combining JSON, Arrays, and Functions**:
  - You can read JSON data containing arrays, manipulate the data using functions, and write the results back to JSON.
  - Example:
    ```python
    # Read JSON data
    df = spark.read.json("path/to/json/file.json")

    # Explode array column
    df_exploded = df.select("name", explode("courses").alias("course"))

    # Define a UDF to format course names
    def format_course(course):
        return course.title()
    format_course_udf = udf(format_course, StringType())

    # Apply UDF to format course names
    df_formatted = df_exploded.withColumn("formatted_course", format_course_udf("course"))

    # Write the result back to JSON
    df_formatted.write.json("path/to/output/json/file.json")
    ```

