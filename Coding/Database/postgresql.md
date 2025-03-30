### setup
1. `psql --version` to make sure you have brew installed
2. `brew list | grep postgresql` to check how many versions of postgresql you have installed
3. `brew update` then `brew doctor` 
4. upgrade everything, including postgresql using `brew upgrade`
5.  Note above command will only upgrade versions you already installed. If you want to install a new version you need to run `brew install _postgresql_@16` 
6. `brew services start postgresql@16`
7. Run `psql` to connect to db
8. If above command gives you `psql: error: connection to server on socket "/tmp/.s.PGSQL.5432" failed: FATAL:  database "albert" does not exist`, run `createdb`.
9. when quitting run `brew services stop postgresql@16`

## useful commands 
After running `psql`
- `\l` list all dbs
- `\dt` list all tables in a db
- `CREATE DATABASE mydatabase;` create new db
- `\c mydatabase` switch to another db

