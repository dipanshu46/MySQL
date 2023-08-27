# Code with examples

To show the databases present -
- show databases;

To select a databases to start working on it - 
- use database_name;

To show the tables inside the current database -
- show tables;

To query all the records from a table - 
- select * from table_name;

To get thestructure of a table - 
- describe table_name;

    This shows the fields i.e. the columns of the table, Type i.e. datatype of each column, Null Yes if any value is null else no, Key is it a primary key or other type, Default and Extra.

To create a database in MySQL - 
- create database database_name;

To create a table in MySQL - 
- create table table_name (column_names datatype,)
    
    Eg. mysql> create table employee_details (Name varchar(30), Age int, Sex char(1), DOJ date, City varchar(15), salary float);

To insert records in your table - 
- insert into table_name values (records,)

    Eg. insert into employee_details values ("Jimmy", 35, "M", "2005-05-30", "Chicago", 70000), ("Shane", 30, "M", "1999-06-25", "Seattle", 55000), ("Marry", 28, "F", "2009-03-10", "Boston", 62000), ("Dwayne", 37, "M", "2011-07-12", "Austin", 57000), ("Sara", 32, "F", 2017-10-27, "New York", 72000), ("Ammy", 35, "F", "2014-12-20", "Seattle", 80000);

To display distinct rows for a particular column -
- select distinct column_name from table_name;

Note: Names for columns are not case sensitive.

To display the count of a column - 
- select count(column_name) from table_name;

To display the output with an alias name - 
- select query as alias_name from table_name;

To display sum of a column entries - 
- select sum(column_name) from table_name;

To display the average of a column entries - 
- select avg(column_name) from table_name;

To display only specific columns - 
- select column_name_1, column_name_2, ... column_name_n from table_name;

#### Where clause
To display rows that fulfil a condition -
- select * from table_name where condition;

You can play with these conditions and the columns which you want to display.

To display rows that fulfil or condition - 
- select * from table_name where condition_1 or condition_2;

To display rows that fulfil and condition - 
- select * from table_name where condition_1 and condition_2 and .... and condition_n

We can also use the in operator specify our clause -
- select * from table_name where column_name in (specific_value_1, specific_value2, ...., specific_value_n);

To select values between a given range - 
- select * from table_name where column_name between value_1 and value_2;


#### Order by clause
Sorts the result in ascending or descending order. Sorts in ascending order by default.
- select * from table_name order by column_name;
- select * from table_name order by column_name desc;

We can perform some basic operation as well - 
- select (10+20) as addition;
- select (10-20) as subtract;

### Basic Functions in SQL

Try using workbench to know more about functions through its auto suggestions.

To find the length of text or string -
- select length('your_string');
- select character_length('string');
- select char_length('string');

To repeat a string - 
- select repeat('string', n);
n is the number of times you want to repeat the string.

To uppercase every letter in a string - 
- select upper('string');
- select ucase('string');

To lowercase every letter in a string - 
- select lower('string');
- select lcase('string');

To reverse a string - 
- select reverse('string');

To concatenate two or more strings -
- select concat(string_1, string_2, ..., string_n);

To replace in a string - 
- select replace(string, string_1, string_2);
    
    where string is the main string, string_1 is the string to be replaced, string_2 is the string to be replaced with.  

To remove the leading whitespaces from a string - 
- select ltrim(string);

To remove the trailing whitespaces from a string -
- select rtrim(string);

To remove both leading and trailing whitespaces from a string -
- select trim(string);

To get the position of the first occurence of a substring in a string - 
- select position('sub_string' in 'string');
    
    returns 0 if not found

To get the ascii value of a character -
- select ascii(character);

To print the current date -
- select curdate();
- select current_date();

To print the day from the current date - 
- select day(curdate());

To print the current date and time -
- select now();
- select current_timestamp();

To print the length of the names from a table entry -
- select length(column_name) from table_name;

### Group by clause
Group By statement groups records into summary rows and returns one record for each group.

To display rows grouped to a summary row that have same value for a column - 
- select coulumn_name_1, sum/avg/count(column_name) from table_name group by column_name_1;

Example for the above commands :-

    mysql> show tables;
    +---------------------+
    | Tables_in_sql_intro |
    +---------------------+
    | employee_details    |
    +---------------------+
    1 row in set (0.00 sec)

    mysql> show tables
        -> ;
    +---------------------+
    | Tables_in_sql_intro |
    +---------------------+
    | employee_details    |
    +---------------------+
    1 row in set (0.00 sec)

    mysql> select * from employee_details
        -> ;
    Empty set (0.00 sec)

    mysql> insert into employee_details 
        -> values ("Jimmy", 35, "M", "2005-05-30", "Chicago", 70000),
        -> ("Shane", 30, "M", "1999-06-25", "Seattle", 55000),
        -> ("Marry", 28, "F", "2009-03-10", "Boston", 62000);
    Query OK, 3 rows affected (0.01 sec)
    Records: 3  Duplicates: 0  Warnings: 0

    mysql> select * from employee_details
        -> ;
    +-------+------+------+------------+---------+--------+
    | Name  | Age  | Sex  | DOJ        | City    | Salary |
    +-------+------+------+------------+---------+--------+
    | Jimmy |   35 | M    | 2005-05-30 | Chicago |  70000 |
    | Shane |   30 | M    | 1999-06-25 | Seattle |  55000 |
    | Marry |   28 | F    | 2009-03-10 | Boston  |  62000 |
    +-------+------+------+------------+---------+--------+
    3 rows in set (0.00 sec)

    mysql> insert into employee_details
        -> values ("Dwaye", 37, "M", "2011-07-12", "Austin", 57000),
        -> ("Sara", 32, "F", "2017-10-27", "New York", 72000),
        -> ("Ammy", 35, "F", "2014-12-20", "Seattle", 80000);
    Query OK, 3 rows affected (0.01 sec)
    Records: 3  Duplicates: 0  Warnings: 0

    mysql> select * from employee_details
        -> ;
    +-------+------+------+------------+----------+--------+
    | Name  | Age  | Sex  | DOJ        | City     | Salary |
    +-------+------+------+------------+----------+--------+
    | Jimmy |   35 | M    | 2005-05-30 | Chicago  |  70000 |
    | Shane |   30 | M    | 1999-06-25 | Seattle  |  55000 |
    | Marry |   28 | F    | 2009-03-10 | Boston   |  62000 |
    | Dwaye |   37 | M    | 2011-07-12 | Austin   |  57000 |
    | Sara  |   32 | F    | 2017-10-27 | New York |  72000 |
    | Ammy  |   35 | F    | 2014-12-20 | Seattle  |  80000 |
    +-------+------+------+------------+----------+--------+
    6 rows in set (0.00 sec)

    mysql> select * from employee_details
        -> ;
    +----------+------+------+------------+----------+--------+
    | Name     | Age  | Sex  | DOJ        | City     | Salary |
    +----------+------+------+------------+----------+--------+
    | Jimmy    |   35 | M    | 2005-05-30 | Chicago  |  70000 |
    | Shane    |   30 | M    | 1999-06-25 | Seattle  |  55000 |
    | Marry    |   28 | F    | 2009-03-10 | Boston   |  62000 |
    | Dwaye    |   37 | M    | 2011-07-12 | Austin   |  57000 |
    | Sara     |   32 | F    | 2017-10-27 | New York |  72000 |
    | Ammy     |   35 | F    | 2014-12-20 | Seattle  |  80000 |
    | Dipanshu |   21 | M    | 2023-09-01 | Pune     |  50000 |
    +----------+------+------+------------+----------+--------+
    7 rows in set (0.00 sec)

    mysql> select distinct city from employee_details
        -> ;
    +----------+
    | city     |
    +----------+
    | Chicago  |
    | Seattle  |
    | Boston   |
    | Austin   |
    | New York |
    | Pune     |
    +----------+
    6 rows in set (0.00 sec)

    mysql> select distinct sex from employee_details
        -> ;
    +------+
    | sex  |
    +------+
    | M    |
    | F    |
    +------+
    2 rows in set (0.00 sec)

    mysql> select distinct Sex from employee_details;
    +------+
    | Sex  |
    +------+
    | M    |
    | F    |
    +------+
    2 rows in set (0.00 sec)

    mysql> select distinct name from employee_details;
    +----------+
    | name     |
    +----------+
    | Jimmy    |
    | Shane    |
    | Marry    |
    | Dwaye    |
    | Sara     |
    | Ammy     |
    | Dipanshu |
    +----------+
    7 rows in set (0.00 sec)

    mysql> select distinct NAME from Employee_Details;
    ERROR 1146 (42S02): Table 'sql_intro.Employee_Details' doesn't exist
    mysql> select distinct NAME from employee_details;
    +----------+
    | NAME     |
    +----------+
    | Jimmy    |
    | Shane    |
    | Marry    |
    | Dwaye    |
    | Sara     |
    | Ammy     |
    | Dipanshu |
    +----------+
    7 rows in set (0.00 sec)

    mysql> select distinct city as ajube from employee_details
        -> ;
    +----------+
    | ajube    |
    +----------+
    | Chicago  |
    | Seattle  |
    | Boston   |
    | Austin   |
    | New York |
    | Pune     |
    +----------+
    6 rows in set (0.01 sec)

    mysql> select count(name) as Naam from employee_details;
    +------+
    | Naam |
    +------+
    |    7 |
    +------+
    1 row in set (0.00 sec)

    mysql> select sum(salary) from employee_details;
    +-------------+
    | sum(salary) |
    +-------------+
    |      446000 |
    +-------------+
    1 row in set (0.00 sec)

    mysql> select sum(salary) as sum_salary from employee_details;
    +------------+
    | sum_salary |
    +------------+
    |     446000 |
    +------------+
    1 row in set (0.01 sec)

    mysql> select avg(salary) as average_salary from employee_details;
    +-------------------+
    | average_salary    |
    +-------------------+
    | 63714.28571428572 |
    +-------------------+
    1 row in set (0.00 sec)

    mysql> select name, age, salary from employee_details
        -> ;
    +----------+------+--------+
    | name     | age  | salary |
    +----------+------+--------+
    | Jimmy    |   35 |  70000 |
    | Shane    |   30 |  55000 |
    | Marry    |   28 |  62000 |
    | Dwaye    |   37 |  57000 |
    | Sara     |   32 |  72000 |
    | Ammy     |   35 |  80000 |
    | Dipanshu |   21 |  50000 |
    +----------+------+--------+
    7 rows in set (0.00 sec)

    mysql> select * from employee_details where age < 30;
    +----------+------+------+------------+--------+--------+
    | Name     | Age  | Sex  | DOJ        | City   | Salary |
    +----------+------+------+------------+--------+--------+
    | Marry    |   28 | F    | 2009-03-10 | Boston |  62000 |
    | Dipanshu |   21 | M    | 2023-09-01 | Pune   |  50000 |
    +----------+------+------+------------+--------+--------+
    2 rows in set (0.00 sec)

    mysql> select name, age from employee_details where sex = 'F';
    +-------+------+
    | name  | age  |
    +-------+------+
    | Marry |   28 |
    | Sara  |   32 |
    | Ammy  |   35 |
    +-------+------+
    3 rows in set (0.00 sec)

    mysql> select name, age, salary from employee_details where 
        -> sex = 'F' or age < 30;
    +----------+------+--------+
    | name     | age  | salary |
    +----------+------+--------+
    | Marry    |   28 |  62000 |
    | Sara     |   32 |  72000 |
    | Ammy     |   35 |  80000 |
    | Dipanshu |   21 |  50000 |
    +----------+------+--------+
    4 rows in set (0.00 sec)

    mysql> select name, city, age from employee_details where  sex = 'F' or age < 30
    ;
    +----------+----------+------+
    | name     | city     | age  |
    +----------+----------+------+
    | Marry    | Boston   |   28 |
    | Sara     | New York |   32 |
    | Ammy     | Seattle  |   35 |
    | Dipanshu | Pune     |   21 |
    +----------+----------+------+
    4 rows in set (0.00 sec)

    mysql> select * from employee_details where age in (21, 28);
    +----------+------+------+------------+--------+--------+
    | Name     | Age  | Sex  | DOJ        | City   | Salary |
    +----------+------+------+------------+--------+--------+
    | Marry    |   28 | F    | 2009-03-10 | Boston |  62000 |
    | Dipanshu |   21 | M    | 2023-09-01 | Pune   |  50000 |
    +----------+------+------+------------+--------+--------+
    2 rows in set (0.01 sec)

    mysql> select * from employee_details where age between 20 and 30;
    +----------+------+------+------------+---------+--------+
    | Name     | Age  | Sex  | DOJ        | City    | Salary |
    +----------+------+------+------------+---------+--------+
    | Shane    |   30 | M    | 1999-06-25 | Seattle |  55000 |
    | Marry    |   28 | F    | 2009-03-10 | Boston  |  62000 |
    | Dipanshu |   21 | M    | 2023-09-01 | Pune    |  50000 |
    +----------+------+------+------------+---------+--------+
    3 rows in set (0.00 sec)

    mysql> select * from employee_details where age between 20 and 29;
    +----------+------+------+------------+--------+--------+
    | Name     | Age  | Sex  | DOJ        | City   | Salary |
    +----------+------+------+------------+--------+--------+
    | Marry    |   28 | F    | 2009-03-10 | Boston |  62000 |
    | Dipanshu |   21 | M    | 2023-09-01 | Pune   |  50000 |
    +----------+------+------+------------+--------+--------+
    2 rows in set (0.00 sec)

    mysql> select name, age, salary from employee_details where doj between '2008-01-01' and '2023-12-31';
    +----------+------+--------+
    | name     | age  | salary |
    +----------+------+--------+
    | Marry    |   28 |  62000 |
    | Dwaye    |   37 |  57000 |
    | Sara     |   32 |  72000 |
    | Ammy     |   35 |  80000 |
    | Dipanshu |   21 |  50000 |
    +----------+------+--------+
    5 rows in set (0.01 sec)

    mysql> select name, age, sex, doj from employee_details where doj between '2008-
    01-01' and '2023-12-31';
    +----------+------+------+------------+
    | name     | age  | sex  | doj        |
    +----------+------+------+------------+
    | Marry    |   28 | F    | 2009-03-10 |
    | Dwaye    |   37 | M    | 2011-07-12 |
    | Sara     |   32 | F    | 2017-10-27 |
    | Ammy     |   35 | F    | 2014-12-20 |
    | Dipanshu |   21 | M    | 2023-09-01 |
    +----------+------+------+------------+
    5 rows in set (0.00 sec)

    mysql> select name, age from employee_details where age<30 and salary>20000 and doj between '2003-02-02' and '2023-12-04';
    +----------+------+
    | name     | age  |
    +----------+------+
    | Marry    |   28 |
    | Dipanshu |   21 |
    +----------+------+
    2 rows in set (0.00 sec)

    mysql> select * from employee_details group by sex;
    ERROR 1055 (42000): Expression #1 of SELECT list is not in GROUP BY clause and contains nonaggregated column 'sql_intro.employee_details.Name' which is not functionally dependent on columns in GROUP BY clause; this is incompatible with sql_mode=only_full_group_by

    mysql> select sex, sum(salary) as total_salary from employee_details group by sex;
    +------+--------------+
    | sex  | total_salary |
    +------+--------------+
    | M    |       232000 |
    | F    |       214000 |
    +------+--------------+
    2 rows in set (0.00 sec)

    mysql> select name, sum(salary) as total_salary from employee_details group by sex;
    ERROR 1055 (42000): Expression #1 of SELECT list is not in GROUP BY clause and contains nonaggregated column 'sql_intro.employee_details.Name' which is not functionally dependent on columns in GROUP BY clause; this is incompatible with sql_mode=only_full_group_by

    mysql> select city, sum(salary) as total_salary from employee_details group by city;
    +----------+--------------+
    | city     | total_salary |
    +----------+--------------+
    | Chicago  |        70000 |
    | Seattle  |       135000 |
    | Boston   |        62000 |
    | Austin   |        57000 |
    | New York |        72000 |
    | Pune     |        50000 |
    +----------+--------------+
    6 rows in set (0.00 sec)

    mysql> select name, age, salary from employee_details order by salary;
    +----------+------+--------+
    | name     | age  | salary |
    +----------+------+--------+
    | Dipanshu |   21 |  50000 |
    | Shane    |   30 |  55000 |
    | Dwaye    |   37 |  57000 |
    | Marry    |   28 |  62000 |
    | Jimmy    |   35 |  70000 |
    | Sara     |   32 |  72000 |
    | Ammy     |   35 |  80000 |
    +----------+------+--------+
    7 rows in set (0.00 sec)

    mysql> select name, age, salary from employee_details order by salary desc;
    +----------+------+--------+
    | name     | age  | salary |
    +----------+------+--------+
    | Ammy     |   35 |  80000 |
    | Sara     |   32 |  72000 |
    | Jimmy    |   35 |  70000 |
    | Marry    |   28 |  62000 |
    | Dwaye    |   37 |  57000 |
    | Shane    |   30 |  55000 |
    | Dipanshu |   21 |  50000 |
    +----------+------+--------+
    7 rows in set (0.00 sec)

    mysql> select (10+20) as addition;
    +----------+
    | addition |
    +----------+
    |       30 |
    +----------+
    1 row in set (0.00 sec)

    mysql> select (10-20) as subtraction;
    +-------------+
    | subtraction |
    +-------------+
    |         -10 |
    +-------------+
    1 row in set (0.00 sec)

    mysql> select (10*3);
    +--------+
    | (10*3) |
    +--------+
    |     30 |
    +--------+
    1 row in set (0.00 sec)

    mysql> select length('India');
    +-----------------+
    | length('India') |
    +-----------------+
    |               5 |
    +-----------------+
    1 row in set (0.00 sec)

    mysql> select repeat('@', 10);
    +-----------------+
    | repeat('@', 10) |
    +-----------------+
    | @@@@@@@@@@      |
    +-----------------+
    1 row in set (0.00 sec)

    mysql> select upper('Dipanshu');
    +-------------------+
    | upper('Dipanshu') |
    +-------------------+
    | DIPANSHU          |
    +-------------------+
    1 row in set (0.00 sec)

    mysql> select lower('PIZZA');
    +----------------+
    | lower('PIZZA') |
    +----------------+
    | pizza          |
    +----------------+
    1 row in set (0.00 sec)

    mysql> select curdate();
    +------------+
    | curdate()  |
    +------------+
    | 2023-08-27 |
    +------------+
    1 row in set (0.00 sec)

    mysql> select day(curdate());
    +----------------+
    | day(curdate()) |
    +----------------+
    |             27 |
    +----------------+
    1 row in set (0.00 sec)

    mysql> select now();
    +---------------------+
    | now()               |
    +---------------------+
    | 2023-08-27 16:50:43 |
    +---------------------+
    1 row in set (0.00 sec)

    mysql> select current_timestamp();
    +---------------------+
    | current_timestamp() |
    +---------------------+
    | 2023-08-27 16:50:55 |
    +---------------------+
    1 row in set (0.00 sec)

    mysql> select ucase('Dipanshu');
    +-------------------+
    | ucase('Dipanshu') |
    +-------------------+
    | DIPANSHU          |
    +-------------------+
    1 row in set (0.00 sec)

    mysql> select length(name) as total_length from employee_details;
    +--------------+
    | total_length |
    +--------------+
    |            5 |
    |            5 |
    |            5 |
    |            5 |
    |            4 |
    |            4 |
    |            8 |
    +--------------+
    7 rows in set (0.00 sec)

    mysql> select Name, length(name) as total_length from employee_details;
    +----------+--------------+
    | Name     | total_length |
    +----------+--------------+
    | Jimmy    |            5 |
    | Shane    |            5 |
    | Marry    |            5 |
    | Dwaye    |            5 |
    | Sara     |            4 |
    | Ammy     |            4 |
    | Dipanshu |            8 |
    +----------+--------------+
    7 rows in set (0.00 sec)

    mysql> select age as Age, length(age) as total_length from employee_details;
    +------+--------------+
    | Age  | total_length |
    +------+--------------+
    |   35 |            2 |
    |   30 |            2 |
    |   28 |            2 |
    |   37 |            2 |
    |   32 |            2 |
    |   35 |            2 |
    |   21 |            2 |
    +------+--------------+
    7 rows in set (0.00 sec)

    mysql> select length(234) as length;
    +--------+
    | length |
    +--------+
    |      3 |
    +--------+
    1 row in set (0.00 sec)

    mysql> select concat('India', ' ', 'is', ' ', 'in Asia.') as Sentence;
    +-------------------+
    | Sentence          |
    +-------------------+
    | India is in Asia. |
    +-------------------+
    1 row in set (0.00 sec)

    mysql> select reverse('Yahoo');
    +------------------+
    | reverse('Yahoo') |
    +------------------+
    | oohaY            |
    +------------------+
    1 row in set (0.00 sec)

    mysql> select replace('Orange is a vegetable', 'vegetable', 'fruit');
    +--------------------------------------------------------+
    | replace('Orange is a vegetable', 'vegetable', 'fruit') |
    +--------------------------------------------------------+
    | Orange is a fruit                                      |
    +--------------------------------------------------------+
    1 row in set (0.00 sec)

    mysql> select ltrim('      Luggage');
    +------------------------+
    | ltrim('      Luggage') |
    +------------------------+
    | Luggage                |
    +------------------------+
    1 row in set (0.00 sec)

    mysql> select rtrim('Luggage        ');
    +--------------------------+
    | rtrim('Luggage        ') |
    +--------------------------+
    | Luggage                  |
    +--------------------------+
    1 row in set (0.00 sec)

    mysql> select trim('      Whitespaces        ');
    +-----------------------------------+
    | trim('      Whitespaces        ') |
    +-----------------------------------+
    | Whitespaces                       |
    +-----------------------------------+
    1 row in set (0.00 sec)

    mysql> select position('fruit' in 'Orange is a fruit');
    +------------------------------------------+
    | position('fruit' in 'Orange is a fruit') |
    +------------------------------------------+
    |                                       13 |
    +------------------------------------------+
    1 row in set (0.00 sec)

    mysql> select ascii('t');
    +------------+
    | ascii('t') |
    +------------+
    |        116 |
    +------------+
    1 row in set (0.00 sec)

    mysql> select sex as Genders from employee_details group by sex;
    +---------+
    | Genders |
    +---------+
    | M       |
    | F       |
    +---------+
    2 rows in set (0.00 sec)

    mysql> select sex as Genders, count(sex) as Count from employee_details group by sex;
    +---------+-------+
    | Genders | Count |
    +---------+-------+
    | M       |     4 |
    | F       |     3 |
    +---------+-------+
    2 rows in set (0.00 sec)

    mysql> select sex as Genders, count(name) as Count from employee_details group b
    y sex;
    +---------+-------+
    | Genders | Count |
    +---------+-------+
    | M       |     4 |
    | F       |     3 |
    +---------+-------+
    2 rows in set (0.00 sec)
