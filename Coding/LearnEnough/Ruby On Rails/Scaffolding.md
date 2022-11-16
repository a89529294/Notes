- `rails generate controller StaticPages home help` controller name `StaticPages` shoule be *PascalCased* and action names `home, help` should be in lowercase.
- `rails destroy controller StaticPages home help` cancel the above command.
- `rails generate model User name:string email:string`
- `rails db:migrate` 
	- to negate above use `rails db:rollback`
	- to go back to the beginning use `rails db:migrate VERSION=0`


## Notes
- controller names are *plural*, model names are *singular*.
- *migration* simply means modifying db schema according to files in `db/migrate`.