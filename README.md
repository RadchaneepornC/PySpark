# 1. Introduction to PySpark 



**Spark** is a platform for cluster computing allowing us to spread data and computations over clusters with multiple nodes (think of each node as a separate computer), both data processing and computation are performed in parallel over the nodes in the cluster. Parallel computation can make certain types of programming tasks much faster, but it comes with greater complexity

 <details><summary>1.1  Getting to know PySpark </summary>

## Spark
- The cluster will be hosted on a remote machine called ```master```, this machine connected to all other nodes called ```worker``` and manage splitting up the data and computations
- The master sends the wokers data and calculation to run, and the worker sent their results back to the masters

- We use PySpark to create an instance of the ```SparkContext``` class as ```sc``` in order to connect to a Spark cluster and ```SparkSession``` called ```spark``` as the interface with that connection

- To verify there is a ```SparkContext``` in our environment

```python
print(cs)

#<SparkContext master=local[*] appName=pyspark-shell>3.2.0

```

- To see the version of Spark is running on our cluster

```python

print(sc.version)
#3.2.0
```

- Spark' core data structure is **R**esilient **D**istributed **D**ataset (RDD) which is a low level object making Spark splits data across multiple nodes in the cluster, but RDDs are hard to work with directly, we can use the Spark DataFrame abstraction built on top of RDDs since operation using DataFrame are automatically optimized over RDDs and DataFrame is like the SQL table



## Creating a SparkSession

- For checking if ```SparkSession``` is already created

the ```SparkSession.builder.getOrCreate()``` method returns an existing ```SparkSession``` if there is already one in the environment, or create a new one if necessary

```python

# Import SparkSession from pyspark.sql
from pyspark.sql import SparkSession

# Create my_spark
my_spark = SparkSession.builder.getOrCreate()

# Print my_spark
print(my_spark)

#<pyspark.sql.session.SparkSession object at 0x7fc0b6adc490>

```

## View the data in the cluster 

- the ```SparkSession``` has an attribute called ```catalog``` which list all the data inside the cluster

- the ```catalog``` attribute has many useful methods, one of them is ```.listTable()``` which returns the names of all the tables in your cluster as a list

```python

# Print the tables in the catalog
print(spark.catalog.listTables())
#[Table(name='flights', database=None, description=None, tableType='TEMPORARY', isTemporary=True)]

```

## DataFrame interface can run SQL queries on the table in our Spark cluster

- can run a query on the table using ```.sql()``` method on the ```SparkSession```, this method takes a string containing the query and returns a DataFrame with the result

```python

# Don't change this query
query = "FROM flights SELECT * LIMIT 10"

# Get the first 10 rows of flights
flights10 = spark.sql(query)

# Show the results
flights10.show()

```




</details>



 <details>
<summary>1.2 Manipulating data</summary>

</details>

<details>
<summary>1.3 Getting started with machine learning pipelines</summary>
</details>

<details>
<summary>1.4 Model tuning and selection</summary>
</details>

# 2. Big Data Fundamentals with PySpark


<details>
<summary>2.1 Introduction to Big Data analysis with Spark</summary>

</details>

<details>
<summary>2.2 Programming in PySpark RDD’s</summary>

</details>

<details>
<summary>2.3 PySpark SQL & DataFrames</summary>
</details>

<details>
<summary>2.4 Machine Learning with PySpark MLlib</summary>
</details>

# 3. Cleaning Data with PySpark

# 4. Feature Engineering with PySpark

# 5. Machine Learning with PySpark

# 6. Building Recommendation Engines with PySpark

# Other resource

- [PySpark vs Pandas: A Comprehensive Guide to Data Processing Tools](https://www.linkedin.com/pulse/pyspark-vs-pandas-comprehensive-guide-data-processing-deepak-lakhotia-hpfgc/)
