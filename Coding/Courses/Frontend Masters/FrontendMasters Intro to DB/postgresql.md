```bash
docker run --name my-postgres -e POSTGRES_PASSWORD=mysecretpassword -p 5432:5432 -d --rm postgres:latest
```

```bash
docker exec -it -u postgres my-postgres psql
```

Once connected, created a database `CREATE DATABASE message_boards;`
To use it `\c message_boards`
To see _all databases_ `\l`
To see _all tables in a database_ `\d`

## create table example
```sql
CREATE TABLE users (
user_id INTEGER PRIMARY KEY GENERATED ALWAYS AS IDENTITY, user_name VARCHAR (25) UNIQUE NOT NULL, 
email VARCHAR (50) UNIQUE NOT NULL, 
full_name VARCHAR (100) NOT NULL, 
last_login TIMESTAMP, created_on TIMESTAMP NOT NULL
);
```

## insert example
```sql
INSERT INTO users (user_name, email, full_name, created_on) VALUES ('achang', 'lol@example.com', 'Albert Chang', NOW());
```
Note: strings _MUST_ be enclosed in single quotes `''`.  If you use double quotes, it means whatever's enclosed must be a identifier, like a column name.