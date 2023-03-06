# SQL Server Overview

SQL Server is a relational database management system (RDBMS) developed by Microsoft. It is used to store and manage large amounts of data for various types of applications. SQL Server is a powerful and widely used RDBMS that provides a range of features and tools for managing and analyzing data. SQL (Structured Query Language) is a programming language used to manage and manipulate relational databases. __Here are some basic SQL statements with examples:__

<br/>


## SELECT statement

The SELECT statement is used to retrieve data from one or more tables in a database.

```SQL
  SELECT * FROM customers;


```



## SELECT statement

The SELECT DISTINCT statement is used to retrieve unique values from a column. Here's an example:

```SQL
  SELECT DISTINCT category
    FROM products;


```


## INSERT statement

The INSERT statement is used to add new rows to a table.

```SQL
  INSERT INTO customers(first_name, last_name, email)
    VALUES 
        ('John', 'Doe', 'johndoe@example.com');


```

## UPDATE statement

The UPDATE statement is used to modify existing rows in a table.

```SQL
  UPDATE customers
    SET email = 'newemail@example.com'
        WHERE customer_id = 1;


```

## DELETE statement

The DELETE statement is used to delete rows from a table.

```SQL
  DELETE FROM customers
    WHERE customer_id = 1;


```

## CREATE statement

The CREATE statement is used to create a new table in a database.

```SQL
    CREATE TABLE orders 
    (
        order_id    INT PRIMARY KEY,
        customer_id INT,
        order_date  DATE,
        total       DECIMAL(10, 2)
    )
    GO


```


## ALTER statement

The ALTER statement is used to modify the structure of an existing table in a database.

```SQL
    ALTER TABLE customers
        ADD address VARCHAR(100);


```


## SELECT with WHERE clause

The SELECT statement can also be used with a WHERE clause to filter the results based on a certain condition.

```SQL
    SELECT * FROM customers
        WHERE city = 'New York';


```

## ORDER BY statement

The ORDER BY statement is used to sort the results of a SELECT statement in ascending or descending order based on one or more columns.

```SQL
    SELECT * FROM customers
        ORDER BY last_name ASC, first_name ASC;


```

## GROUP BY statement

The GROUP BY statement is used to group the results of a SELECT statement by one or more columns.

```SQL
   SELECT city, COUNT(*) FROM customers
        GROUP BY city;


```

The `GROUP BY` clause in SQL is used to group rows based on the values in one or more columns. The resulting groups can then be used to perform aggregate functions, such as `SUM, AVG, MAX, MIN, or COUNT`.

Here's an example of how to use `GROUP BY` to find the total sales for each product category in a table called sales:

```SQL
  SELECT category, SUM(amount) as total_sales
    FROM sales
      GROUP BY category;
      
```

## JOIN statements


In SQL, the JOIN clause is used to combine rows from two or more tables based on a related column between them. There are several types of joins, each with its own syntax and purpose. Here are a few examples of how to use `JOIN` in SQL:

#### Inner Join: 
The most common type of join is the inner join, which returns only the rows from both tables that have matching values in the specified columns. Here's an example:

```SQL
    SELECT customers.customer_name, orders.order_date
      FROM customers
        INNER JOIN orders
        ON customers.customer_id = orders.customer_id;


```


#### Left Join: 
A left join returns all the rows from the left table and the matching rows from the right table. If there is no matching row in the right table, the result will contain NULL values. Here's an example:

```SQL
    SELECT customers.customer_name, orders.order_date
      FROM customers
        LEFT JOIN orders
        ON customers.customer_id = orders.customer_id;


```


#### Full Outer Join: 
A full outer join returns all the rows from both tables, including those where there is no matching row in the other table. If there is no matching row, the result will contain NULL values. Here's an example:

```SQL
    SELECT customers.customer_name, orders.order_date
      FROM customers
        FULL OUTER JOIN orders
        ON customers.customer_id = orders.customer_id;


```


#### Self Join:
A self join is a join where a table is joined with itself. This is often used when you have a hierarchical or nested structure in your data. Here's an example:

```SQL
    SELECT e1.employee_name, e2.employee_name as manager_name
      FROM employees e1
      INNER JOIN employees e2
      ON e1.manager_id = e2.employee_id;


```
