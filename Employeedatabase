CREATE TABLE Department (
    dept_id INT PRIMARY KEY,
    dept_name VARCHAR(50),
    location VARCHAR(50)
);

CREATE TABLE Project (
    project_id INT PRIMARY KEY,
    project_name VARCHAR(50),
    location VARCHAR(50)
);

CREATE TABLE Employee (
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(50),
    dept_id INT,
    job_role VARCHAR(50),
    FOREIGN KEY (dept_id) REFERENCES Department(dept_id)
);

CREATE TABLE Incentives (
    emp_id INT,
    incentive_amt DECIMAL(10, 2),
    FOREIGN KEY (emp_id) REFERENCES Employee(emp_id)
);

CREATE TABLE Works_On (
    emp_id INT,
    project_id INT,
    FOREIGN KEY (emp_id) REFERENCES Employee(emp_id),
    FOREIGN KEY (project_id) REFERENCES Project(project_id)
);

INSERT INTO Department (dept_id, dept_name, location) VALUES (1, 'HR', 'Bengaluru');
INSERT INTO Department (dept_id, dept_name, location) VALUES (2, 'IT', 'Hyderabad');
-- Add more entries as needed for each table

INSERT INTO Project (project_id, project_name, location) VALUES (1, 'ProjA', 'Bengaluru');
INSERT INTO Project (project_id, project_name, location) VALUES (2, 'ProjB', 'Mysuru');
-- Continue with similar entries

INSERT INTO Employee (emp_id, emp_name, dept_id, job_role) VALUES (101, 'Alice', 1, 'Manager');
INSERT INTO Employee (emp_id, emp_name, dept_id, job_role) VALUES (102, 'Bob', 2, 'Developer');
-- Insert additional records as required

INSERT INTO Incentives (emp_id, incentive_amt) VALUES (101, 500.00);
-- More incentive records as appropriate

SELECT E.emp_id
FROM Employee E
JOIN Works_On W ON E.emp_id = W.emp_id
JOIN Project P ON W.project_id = P.project_id
WHERE P.location IN ('Bengaluru', 'Hyderabad', 'Mysuru');

SELECT E.emp_id
FROM Employee E
LEFT JOIN Incentives I ON E.emp_id = I.emp_id
WHERE I.emp_id IS NULL;

SELECT E.emp_name, E.emp_id, D.dept_name, E.job_role, D.location AS dept_location, P.location AS project_location
FROM Employee E
JOIN Department D ON E.dept_id = D.dept_id
JOIN Works_On W ON E.emp_id = W.emp_id
JOIN Project P ON W.project_id = P.project_id
WHERE D.location = P.location;
