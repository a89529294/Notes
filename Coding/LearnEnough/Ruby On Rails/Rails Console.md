`rails console`
`rails console --sandbox`  so changes to db are reverted once the session ends

For the following *User* is the model. *user* is just one instance of `User`.
- `User.find(1)` find by id 1
- `User.find_by(name:'Albert')` find by name attribute, can pass in multiple attrs
- `User.all` find all users
- `user.name` get name of user
- `user.reload` refresh user using data from db