# Basic-SELECT-Queries.

Task 3: Writing Basic SELECT Queries

 Objective:Extract data from one or more tables.
 Tools :DB Browser for SQLite / MySQL Workbench
 Deliverables:SQL script with SELECT, WHERE, ORDER BY, LIMIT

 Hints/Mini Guide:
 1.Use SELECT * and specific columns
 2.Apply WHERE, AND, OR, LIKE, BETWEEN
 3.Sort with ORDER BY
 Outcome:Clear understanding of how to retrieve data

--Creted two tables.

create table Person(
Person_id int Primary Key,
Name varchar(100));

create table Passport(
Passport_id int Primary key,
Issue_date Date,
Person_id int,
FOREIGN key (person_id) REFERENCES  Person(Person_id));

---Retrieve all columns from both Person and Passport.

Select * from Person;
Select * from Passport;

---Retrieve Specific columns from both Person and Passport.

Select Passport_id from passport;
select Name from person;

--Filtering with WHERE Find all passports issued for 101,103,104.

select * from passport where passport_id in('101','103','104');

--Find entries where the passport was issued in 2025 and the person's name starts with "J"

Select * from person where name like 'J%';

--Select passports issued between '2023-06-01' and '2023-12-31'.

Select * from passport where issue_date between '2023-06-01' and '2023-12-31';

--Order by

SELECT * FROM Person
ORDER BY Name;

--Retrieve the top 3 most recently issued passports.

select  * from passport 
order by 2 desc
fetch First 3 rows only;

---Show passport records 4–6 by applying ORDER BY with LIMIT and OFFSET.

Select * from passport
order by 1
limit 2 offset 3;


---List the Name and Issue_date of individuals who have a Person_id of 3 or 4, and their passport was issued either before '2023-03-01' or after '2023-06-01'.

SELECT p.Name, ps.Issue_date
FROM Person p, Passport ps
WHERE p.Person_id = ps.Person_id
  AND (p.Person_id = 3 OR p.Person_id = 4)
  AND (ps.Issue_date < '2023-03-01' OR ps.Issue_date > '2023-06-01');

