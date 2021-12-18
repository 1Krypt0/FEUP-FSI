# Task 1 - Knowing the basics about SQL Statements

The objective of the task is to get familiar with the most common SQL commands. First, we need to start up the Docker containers with `docker-compose up`. Then, we create a shell in it and launch mySQL to interact with the database. After that, we must use the table given by the Lab, and make a query to select a row that belongs to Alice. A screenshot of this query is provided below:

![./SQL-Statement.png](The SQL statement selecting Alice's information) 

# Task 2 - SQL Injection Attack on SELECT Statement

This task reveals some of the greatest and most common mistakes frequently made by developers on SELECT Statements.

## Task 2.1 - Injection from the Webpage

The objective is to try and login as an admin to the web application from the login page. To do this, the name of the admin account is given, which is admin. Then, we need to manipulate the input given in the username and password to gain access.

The solution comes from the fact that the query needs only the admin username to gain access. As such, all that is necessary is supply the query with the admin name "admin" and a comment symbol to ignore the remaining input.

More concretely, we give to the username field the "admin '#" input, which effectively makes the SELECT query act like  `SELECT Password FROM credential WHERE name = "admin"`.

## Task 2.2 - Injection from the Command Line

Since we already figured out the correct input, all we need to do here is translate it into the correct format for the HTTP request. In this case, all we need to change is the whitespace, which will become %20, the hash symbol which will be %23, and the single quote, which will be %27. Everything else will be correctly parsed.

To execute, we run `curl 'www.seed-server.com/unsafe_home.php?username=admin%20%27%23&Password=admin'`

Once again, the admin password is just filler, we could have put anything in there.

## Task 2.3 - Append a new SQL Statements

Besides simply accessing the information, we might want to maybe alter the password to have complete access, adding new users as a backdoor or simply deleting other users to cause some damage.

To do this, we can add a semicolon at the end of the input, and then try and inject a new SQL statement after it. Something like `admin'; UPDATE TABLE credential SET Name='Tiago' WHERE Name='Alice';#`.

The problem with this is that PHP itself doesn't allow multiple SQL statements in one query (as a safety measure). As such, it is impossible to inject more than one command at a time, and the attack will be always unsuccessfull.

# Task 3 - SQL Injection on UPDATE Statement

This task reveals some of the biggest mistakes, and the consequences they mght have, of misusing UPDATE Statements.

## Task 3.1 - Modifying your own salary.

In order to update your own salary, we can abuse the fact that this is an update statement running. Even though we don't have access to the form edit statement, we can inject some SQL code that allows to access the table, which we know is the salary one.

To do this, we can do it in the last input (the one that will be executed before the WHERE part of the Statement), which is the Phone number one, and inject something like `123', salary = 650000 WHERE name = 'Alice' #`. The hash symbol in the end is there to comment out the rest of the code.

After submitting the form, we can see that the salary has been updated and that Alice is now receiving 650000 dollars.

## Task 3.2 - Modifying other people's salaries

To update our Boss Boby's salary, we need to run the exact same statement in the form, changing only the value of the name referenced in the where clause. So, if we want to reduce it to say, 1 dollar, we can do it by running (in the exact same place as the other one, in the Phone number input), the statement `123' salary = 1 WHERE name = 'Boby' #`.

In order to check if it worked, we can access the Boby profile page by using the same exploit we used in task 2.1, and check that in fact, Boby's salary has been reduced to 1 dollar.
