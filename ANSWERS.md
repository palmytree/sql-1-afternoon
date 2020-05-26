## Table - person

1. Create a table called person that records a person's id, name, age, height ( in cm ), city, favorite_color.
   - id should be an auto-incrementing id/primary key - Use type: SERIAL

```SQL
CREATE TABLE person (
  id SERIAL PRIMARY KEY,
  name VARCHAR(80),
  age INT,
  height INT,
  city VARCHAR(100),
  favorite_color VARCHAR(20)
);
```

2. Add 5 different people into the person database.
   - Remember to not include the person_id because it should auto-increment.

```SQL
INSERT INTO person
(name, age, height, city, favorite_color)
VALUES
('John Joe', 20, 150, 'Dallas', 'red'),
('Jake John', 21, 140, 'Houston', 'blue'),
('Joe Joe', 29, 190, 'San Antonio', 'pink'),
('Jake Joe', 40, 145, 'Austin', 'yellow'),
('John Jake', 69, 169, 'Plano', 'red');
```

3. List all the people in the person table by height from tallest to shortest.

```SQL
SELECT * FROM person
ORDER BY height DESC;
```

4. List all the people in the person table by height from shortest to tallest.

```SQL
SELECT * FROM person
ORDER BY height;
```

5. List all the people in the person table by age from oldest to youngest.

```SQL
SELECT * FROM person
ORDER BY age DESC;
```

6. List all the people in the person table older than age 20.

```SQL
SELECT * FROM person
WHERE age > 20;
```

7. List all the people in the person table that are exactly 18.

```SQL
SELECT * FROM person
WHERE age = 18;
```

8. List all the people in the person table that are less than 20 and older than 30.

```SQL
SELECT * FROM person
WHERE age < 20
OR age > 30;
```

9. List all the people in the person table that are not 27 (Use not equals).

```SQL
SELECT * FROM person
WHERE age != 27;
```

10. List all the people in the person table where their favorite color is not red.

```SQL
SELECT * FROM person
WHERE favorite_color != 'red';
```

11. List all the people in the person table where their favorite color is not red and is not blue.

```SQL
SELECT * FROM person
WHERE favorite_color != 'red'
AND favorite_color != 'blue';
```

12. List all the people in the person table where their favorite color is orange or green.

```SQL
SELECT * FROM person
WHERE favorite_color = 'orange'
OR favorite_color = 'green';
```

13. List all the people in the person table where their favorite color is orange, green or blue (use IN).

```SQL
SELECT * FROM person
WHERE favorite_color IN ('orange', 'green', 'blue');
```

14. List all the people in the person table where their favorite color is yellow or purple (use IN).

```SQL
SELECT * FROM person
WHERE favorite_color IN ('yellow', 'purple');
```

## Table - orders

1. Create a table called orders that records: order_id, person_id, product_name, product_price, quantity.

```SQL
CREATE TABLE orders (
  order_id SERIAL PRIMARY KEY,
  person_id INT,
  product_name VARCHAR(80),
  product_price FLOAT(2),
  quantity INT
);
```

2. Add 5 orders to the orders table.
   - Make orders for at least two different people.
   - person_id should be different for different people.

```SQL
INSERT INTO orders
(person_id, product_name, product_price, quantity)
VALUES
(2, 'OneWheel XR', 1799.99, 1),
(2, 'Float Plate', 49.99, 1),
(4, 'Fender Strat', 1299.99, 1),
(5, 'Coffee', 2.99, 2),
(1, '12pk White Claw', 12.99, 2);
```

3. Select all the records from the orders table.

```SQL
SELECT * FROM orders;
```

4. Calculate the total number of products ordered.

```SQL
SELECT sum(quantity) FROM orders;
```

5. Calculate the total order price.

```SQL
SELECT sum(quantity*product_price) FROM orders;
```

6. Calculate the total order price by a single person_id.

```SQL
SELECT sum(quantity*product_price) FROM orders
WHERE person_id = 2;
```

## Table - artist

1. Add 3 new artists to the artist table. ( It's already created )

```SQL
INSERT INTO artist
(name)
VALUES
('John Mayer'),
('Gary Clark Jr'),
('Stevie Ray Vaughan');
```

2. Select 10 artists in reverse alphabetical order.

```SQL
SELECT * FROM artist
ORDER BY name DESC
LIMIT 10;
```

3. Select 5 artists in alphabetical order.

```SQL
SELECT * FROM artist
ORDER BY name
LIMIT 5;
```

4. Select all artists that start with the word 'Black'.

```SQL
SELECT * FROM artist
WHERE name LIKE 'Black%';
```

5. Select all artists that contain the word 'Black'.

```SQL
SELECT * FROM artist
WHERE name LIKE '%Black%';
```

## Table - employee

1. List all employee first and last names only that live in Calgary.

```SQL
SELECT first_name, last_name FROM employee
WHERE city = 'Calgary';
```

2. Find the birthdate for the youngest employee.

```SQL
SELECT max(birth_date) FROM employee;
```

3. Find the birthdate for the oldest employee.

```SQL
SELECT min(birth_date) FROM employee;
```

4. Find everyone that reports to Nancy Edwards (Use the ReportsTo column).
   - You will need to query the employee table to find the Id for Nancy Edwards

```SQL
SELECT * FROM employee
WHERE reports_to = (SELECT employee_id FROM employee WHERE first_name = 'Nancy' AND last_name = 'Edwards');
```

5. Count how many people live in Lethbridge.

```SQL
SELECT count(*) FROM employee
WHERE city = 'Lethbridge';
```

## Table - invoice

1. Count how many orders were made from the USA.

```SQL
SELECT count(*) FROM invoice
WHERE billing_country = 'USA';
```

2. Find the largest order total amount.

```SQL
SELECT max(total) FROM invoice;
```

3. Find the smallest order total amount.

```SQL
SELECT min(total) FROM invoice;
```

4. Find all orders bigger than \$5.

```SQL
SELECT * FROM invoice
WHERE total > 5;
```

5. Count how many orders were smaller than \$5.

```SQL
SELECT count(*) FROM invoice
WHERE total < 5;
```

6. Count how many orders were in CA, TX, or AZ (use IN).

```SQL
SELECT count(*) FROM invoice
WHERE billing_state IN ('CA', 'TX', 'AZ');
```

7. Get the average total of the orders.

```SQL
SELECT avg(total) FROM invoice;
```

8. Get the total sum of the orders.

```SQL
SELECT sum(total) FROM invoice;
```
