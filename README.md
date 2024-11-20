# Joins

## AIM:
 To study and implement different types of joins.
## THEORY:
```
 The SQL Joins clause is used to combine records from two or more tables in a database. A JOIN is a
 means for combining fields from two tables by using values common to each.The join is actually
 performed by the ‘where’ clause which combines specified rows of tables.
 Syntax:
 SELECT column1,column2,column3... FROM table_name1,
 table_name2
 WHEREtable_name1.column name = table_name2.columnname;
 Types of Joins:
 ● Inner Join
 ● Left (Outer) Join
 ● Right (Outer) Join
 ● Full(Outer) Join
 INNER JOIN
 The INNER JOIN keyword selects records that have matching values in both tables.
 Syntax:
 SELECTcolumn_name(s) FROM table1
 INNER JOIN table2
 ONtable1.column_name = table2.column_name;
 LEFT JOIN
 The LEFT JOIN keyword returns all records from the left table (table1), and the matching records
 from the right table (table2). The result is 0 records from the right side, if there is no match.
 Syntax:
 SELECT column_name(s)
 FROMtable1
 LEFT JOIN table2
 ON table1.column_name = table2.column_name;
RIGHT JOIN
 The RIGHT JOIN keyword returns all records from the right table (table2), and the matching records
 from the left table (table1). The result is 0 records from the left side, if there is no match.
 Syntax:
 SELECT column_name(s)
 FROMtable1
 RIGHT JOIN table2
 ONtable1.column_name = table2.column_name;
 FULL OUTERJOIN
 The FULL OUTER JOIN keyword returns all records when there is a match in left (table1) or right
 (table2) table records.
 FULL OUTERJOIN andFULL JOIN are thesame.
 Syntax:
 SELECT column_name(s)
 FROM table1
 FULL OUTERJOIN table2
 ON table1.column_name = table2.column_name
 WHERE condition;
```
```
Question 1:
 SQL statement to generate a report with customer name, city, order number, order date, order
 amount, salesperson name, and commission to determine if any of the existing customers have not
 placed orders or if they have placed orders through their salesman or by themselves.

 Answer:
 SELECT c.cust_name,c.city,o.ord_no,o.ord_date,o.purch_amt AS 'Order Amount',s.name,s.commission
 FROM customer c
 LEFT JOIN orders o ON c.customer_id=o.customer_id
 LEFT JOIN salesman s ON o.salesman_id =s.salesman_id;
 ```
## Output:
![Screenshot 2024-11-20 143813](https://github.com/user-attachments/assets/7f7ccb8c-ea05-4611-b420-783aa2aab18f)

```
 Question 2:
 Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased
 as "salesman_name") and the "cust_name" column from the "customer" table (aliased as "customer_name"),
 with a left join on the "salesman_id" column.

 Answer:
 SELECT s.name AS salesman_name,c.cust_name AS customer_name
 FROM Salesman s
 LEFT JOIN Customer c
 ON s.salesman_id=c.salesman_id;
```
 ## Output:
 ![Screenshot 2024-11-20 143820](https://github.com/user-attachments/assets/67b6e958-af6f-4063-9328-54324751792f)

```
 Question 3:
 From the following tables write a SQL query to find the salesperson(s) and the customer(s) he
 represents. Return Customer Name, city, Salesman, commission.

 Answer:
 SELECT c.cust_name AS 'Customer Name',c.city,s.name AS 'Salesman',s.commission
 FROM customer c
 JOIN salesman s
 ON c.salesman_id=s.salesman_id;
 ```
## Output:
![Screenshot 2024-11-20 143825](https://github.com/user-attachments/assets/56791156-f19f-4272-b5bd-b409807d6b2d)

```
 Question 4:
 From the following tables write a SQL query to find the details of an order. Return ord_no,
 ord_date, purch_amt, Customer Name, grade, Salesman, commission.

 Answer:
 SELECT o.ord_no,o.ord_date,o.purch_amt,c.cust_name AS 'Customer Name',c.grade,s.name AS
 'Salesman',s.commission
 FROM orders o
 LEFT JOIN customer c ON c.customer_id=o.customer_id
 LEFT JOIN salesman s ON s.salesman_id=c.salesman_id;
```
 ## Output:
 ![Screenshot 2024-11-20 143831](https://github.com/user-attachments/assets/6cd1198b-5ec5-4c19-b754-141c6f02dac4)

```
 Question 5:
 Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table
 (aliased as "c"), with a left join on the "customer_id" column and a condition filtering for orders with a purchase
 amount less than 100.
 
Answer:
 SELECT c.cust_name
 FROM customer c
 LEFT JOIN orders o
 ON c.customer_id=o.customer_id
 WHERE o.purch_amt<100;
```
 ## Output:
 ![Screenshot 2024-11-20 143837](https://github.com/user-attachments/assets/d6912443-f9fd-40c7-8c49-e1b4944a4cb5)

```
 Question 6:
 From the following tables write a SQL query to find those orders where the order amount exists
 between 500 and 2000. Return ord_no, purch_amt, cust_name, city.

 Answer:
 SELECT o.ord_no,o.purch_amt,c.cust_name,c.city
 FROM customer c
 JOIN orders o
 ON c.customer_id=o.customer_id
 WHERE o.purch_amt BETWEEN 500 AND 2000;
```
 ## Output:
 ![Screenshot 2024-11-20 143844](https://github.com/user-attachments/assets/e68b6bb3-2101-49b9-a130-c7826f76b887)

```
 Question 7:
 Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as
 "patient_name") and the specialization from the "doctors" table (aliased as "Doctor_specialization"), with an
 inner join on the "doctor_id" column and a condition filtering for patients admitted between '2024-01-01' and
 '2024-01-31'.
 
Answer:
 SELECT p.first_name AS patient_name,d.specialization AS Doctor_speciali
 FROM patients p
 INNER JOIN doctors d
 ON p.doctor_id=d.doctor_id
 WHERE p.admission_date BETWEEN '2024-01-01' AND '2024-01-31';
```
 ## Output:
 ![Screenshot 2024-11-20 143851](https://github.com/user-attachments/assets/07c6b511-7e88-4229-b37e-54f5e456d9eb)

```
 Question 8:
 Write the SQL query that achieves the selection of the first name from the "patients" table and all columns
 from the "surgeries" table, with an inner join on the "patient_id" column and a condition filtering for patients
 with a date of birth after '1990-01-01'.

 Answer:
 SELECT p.first_name,s.surgery_id,s.patient_id,p.doctor_id AS surgeon_id ,s.surgery_date
 FROM patients p
 INNER JOIN surgeries s
 ON p.patient_id=s.patient_id
 WHERE date_of_birth>'1990-01-01';
```
 ## Output:
 ![Screenshot 2024-11-20 143858](https://github.com/user-attachments/assets/82a69787-d692-4a88-8a72-48a664fb2711)

```
 Question 9:
 Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as
 "patient_name") and the first name from the "doctors" table (aliased as "doctor_name"), with an inner join on
 the "doctor_id" column and a condition filtering for patients with a null discharge date.
 
Answer:
 SELECT p.first_name AS patient_name, d.first_name AS doctor_name
 FROMpatients p
 INNER JOIN doctors d
 ONp.doctor_id=d.doctor_id
 WHEREp.discharge_date IS NULL;
```
 ## Output:
 ![Screenshot 2024-11-20 143903](https://github.com/user-attachments/assets/a9bc6840-8f6a-4b9a-af5a-c3f529c72c84)

```
 Question 10:
 Write a SQL statement to make a report with customer name, city, order number, order date,
 and order amount in ascending order according to the order date to determine whether any of the
 existing customers have placed an order or not.

 Answer:
 SELECT c.cust_name,c.city,o.ord_no,o.ord_date,o.purch_amt AS 'Order Amount'
 FROM customer c
 LEFT JOIN orders o
 ON c.customer_id=o.customer_id
 ORDER BY o.ord_date;
```
 ## Output:
 ![Screenshot 2024-11-20 143909](https://github.com/user-attachments/assets/ec1162ea-0ee6-4b9a-a868-a3e621add231)

 ## Result:
 Thus , the SQL queries to implement different types of joins have been executed successfully.
 
