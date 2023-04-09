# SQL_Home_work_3
Отсортируйте данные по полю заработная плата (salary) в порядке: убывания; возрастания для каждой группы
   
    create table Employees
(
     Id_employee INT auto_increment primary key,
    Name_employee varchar(15) NOT NULL,
    Surname_employee varchar(15) NOT NULL,
    Specialty_employee varchar(15),
    Seniority_employee INT,
    Salary_employee INT,
    Age_employee TINYINT
);

  INSERT INTO Employees 
    (Name_employee, Surname_employee, Specialty_employee, Seniority_employee, Salary_employee, Age_employee)
VALUES
    
    ('Антон', 'Антонов', 'Рабочий', 8, 19000, 28),
    ('Юра', 'Юркин', 'Рабочий', 5, 15000, 25),
    ('Максим', 'Воронин', 'Рабочий', 2, 11000, 22),
    ('Юра', 'Галкин', 'Рабочий', 3, 12000, 24),
    ('Вася', 'Васькин', 'Начальник', 40, 100000, 60),
    ('Петя', 'Петькин', 'Начальник', 8, 70000, 30),
    ('Катя', 'Каткина', 'Инженер', 2, 70000, 25),
    ('Саша', 'Сашкин', 'Инженер', 12, 50000, 35),
    ('Иван', 'Иванов', 'Рабочий', 40, 30000, 59),
    ('Петр', 'Петров', 'Рабочий', 20, 25000, 40),
    ('Катя', 'Каткина', 'Инженер', 2, 70000, 25),
    ('Саша', 'Сашкин', 'Инженер', 12, 50000, 35),
    ('Иван', 'Иванов', 'Рабочий', 40, 30000, 59),
    ('Петр', 'Петров', 'Рабочий', 20, 25000, 40),
     
     SELECT * FROM Employees 
  ORDER BY Salary_employee DESC;

  SELECT * FROM Employees 
  ORDER BY Salary_employee;
    
Выведите 5 максимальных заработных плат (saraly)
 
   SELECT Surname_employee, Salary_employee  
   FROM Employees LIMIT 5;
  
Посчитайте суммарную зарплату (salary) по каждой специальности (роst)

SELECT Specialty_employee, SUM(Salary_employee) AS "Sum of salaries"
FROM Employees
GROUP BY Specialty_employee;

Найдите кол-во сотрудников с специальностью (post) «Рабочий» в возрасте от 24 до 49 лет включительно.
  
  SELECT Specialty_employee, COUNT(*)  AS "Number of employees"
  FROM Employees 
  WHERE Specialty_employee = 'Рабочий' && Age_employee >= 24 && Age_employee <= 49
  GROUP BY Specialty_employee;

Найдите количество специальностей
  
  SELECT  COUNT(distinct Specialty_employee) AS "Quantity of specialties"
  FROM Employees;

Выведите специальности, у которых средний возраст сотрудников меньше 30 лет

  SELECT Specialty_employee, AVG(Age_employee)
  FROM Employees 
  GROUP BY Specialty_employee
  HAVING AVG(Age_employee) < 30;
