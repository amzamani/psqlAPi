## PSQL COMMANDS USED
```postgres=# CREATE ROLE me WITH LOGIN PASSWORD 'password';
postgres=# ALTER ROLE me CREATEDB;
\du
postgres=# \q
We’re back in our computer’s default Terminal connection. Now we’ll connect postgres with me.

psql -d postgres -U me
postgres=> CREATE DATABASE api;
Use the \list command to see the available databases.

Name    |    Owner    | Encoding |   Collate   |    Ctype    |
api     | me          | UTF8     | en_US.UTF-8 | en_US.UTF-8 |
postgres=> \c api
You are now connected to database "api" as user "me".
api=>
api=>
CREATE TABLE users (
  ID SERIAL PRIMARY KEY,
  name VARCHAR(30),
  email VARCHAR(30)
);
INSERT INTO users (name, email)
  VALUES ('Jerry', 'jerry@example.com'), ('George', 'george@example.com');
  api=> SELECT * FROM users;```
id |  name  |       email        
----+--------+--------------------
  1 | Jerry  | jerry@example.com
  2 | George | george@example.com

# create simple requests using curl in the terminal

POST
Add a new user with the name Elaine and email elaine@example.com.

curl --data "name=Elaine&email=elaine@example.com" 
http://localhost:3000/users
PUT
Update the user with id 1 to have the name Kramer and email kramer@example.com.

curl -X PUT -d "name=Kramer" -d "email=kramer@example.com" 
http://localhost:3000/users/1
DELETE
Delete the user with id 1.

curl -X "DELETE" http://localhost:3000/users/1