CREATE TABLE ADDRESS(
	add_id INT PRIMARY KEY,
	country VARCHAR(100),
	state VARCHAR(100),
	city VARCHAR(100),
	street VARCHAR(100),
	zipcode INT,
	pre_known_add JSON,
	created_ts TIMESTAMP,
	last_update_ts TIMESTAMP
);


CREATE TABLE DEPARTMENT(
	department_id INT PRIMARY KEY,
	department_name VARCHAR(100),
	department_code VARCHAR(4) NOT NULL,
	address_id INT,
	dept_head_id INT NOT NULL,
	FOREIGN KEY (address_id) REFERENCES ADDRESS(add_id)
	
);


CREATE TABLE EMP(
	emp_id INT PRIMARY KEY,
	first_name VARCHAR(100) NOT NULL,
	last_name VARCHAR(100),
	email VARCHAR(100) NOT NULL,
	phone_number VARCHAR(20) NOT NULL,
	dept_id INT ,
	address_id INT,
	blood_group VARCHAR(10),
	dob DATE,
	doj DATE,
	dot DATE,
	created_ts TIMESTAMP,
	reference VARCHAR(100),
	role VARCHAR(100),
	salary FLOAT,
	band INT,
	reports_to INT,
	FOREIGN KEY (dept_id) REFERENCES DEPARTMENT(department_id),
	FOREIGN KEY (address_id) REFERENCES ADDRESS(add_id)
);
INSERT INTO ADDRESS(add_id, country,state,city,street,zipcode,pre_known_add,created_ts,last_update_ts)
VALUES 
    (111, 'United States', 'Florida', 'Delray Beach', 'Millitary Trail', 33484,NULL,CURRENT_TIMESTAMP,CURRENT_TIMESTAMP),
    (222, 'India', 'Tamil Nadu', 'Thanjavur', 'Arulanandha NAgar',613001,NULL,CURRENT_TIMESTAMP,CURRENT_TIMESTAMP);
INSERT INTO DEPARTMENT(department_id,department_name,department_code,address_id,dept_head_id)
VALUES 
    (1,'Math','Mat1','111','000'),
    (2,'Data Science','Dat2','222','001');
INSERT INTO EMP(emp_id, first_name, last_name, email, phone_number, dept_id, address_id, blood_group, dob, doj, dot, created_ts, reference, role, salary, band, reports_to)
VALUES
    (1, 'Laya', 'Yellanki', 'layayellanki@gmail.com', '+5617250869', 1, 111, 'O+', '2001-05-01', '2022-12-09', '2023-01-10', CURRENT_TIMESTAMP, 'Reference 1', 'Data Analyst', 25000, 1, NULL),
    (2, 'Aadharsh', 'Velu', 'aasharshvelu1@gmail.com', '+561223790', 2, 222, 'B+', '2003-05-12', '2021-03-05', '2022-04-21', CURRENT_TIMESTAMP, 'Reference_2', 'Software Engineer', 40000, 2, 1);
UPDATE ADDRESS
SET country = 'United States'
WHERE add_id = 222;
UPDATE DEPARTMENT 
SET department_name = 'Martin'
WHERE department_id = 2;
UPDATE EMP
SET first_name = 'Paul'
WHERE emp_id = 2;
DELETE FROM EMP
WHERE emp_id = 2;

DELETE FROM DEPARTMENT
WHERE department_id = 1;

DELETE FROM DEPARTMENT
WHERE department_id = 2;

DELETE FROM ADDRESS
WHERE add_id = 111;

DELETE FROM ADDRESS
WHERE add_id = 222;

ALTER TABLE EMP
DROP COLUMN reports_to;
ALTER TABLE DEPARTMENT
DROP COLUMN dept_head_id;

ALTER TABLE EMP
ALTER COLUMN band TYPE VARCHAR(10);
SELECT emp_id, DATE_PART('year', AGE(dob)) AS age
FROM EMP;

SELECT CURRENT_DATE AS "Today's Date";

SELECT emp_id, DATE_PART('year', AGE(doj)) AS experience
FROM EMP;
ALTER TABLE EMP
ADD COLUMN comment_col VARCHAR(255);

ALTER TABLE DEPARTMENT
ADD COLUMN comment_col VARCHAR(255);
ALTER TABLE ADDRESS
ADD COLUMN comment_col VARCHAR(255);
TRUNCATE TABLE EMP, DEPARTMENT, ADDRESS;
CREATE VIEW emp_department_address_view AS
SELECT 
    e.emp_id,
    CASE 
        WHEN e.last_name IS NOT NULL THEN CONCAT(e.first_name, ' ', e.last_name)
        ELSE e.first_name
    END AS name,
    CONCAT(a.street, ', ', a.city, ', ', a.state, ', ', a.country, ' ', a.zipcode) AS address,
    d.department_name AS dept_name,
    e.salary
FROM 
    EMP e
    JOIN DEPARTMENT d ON e.dept_id = d.department_id
    JOIN ADDRESS a ON e.address_id = a.add_id;
DROP TABLE IF EXISTS EMP, DEPARTMENT, ADDRESS CASCADE;

