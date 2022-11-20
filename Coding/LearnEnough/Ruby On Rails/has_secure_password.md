1. Add `password_digest` to users schema, `db/schema.rb`. 
	- `rails generate model User name:string email:string password_digest:string`
2. In User model `app/models/user.rb`
```ruby
class User < ApplicationRecord
	has_secure_password
end
```
3. Add bycrypt to `Gemfile`
```
gem 'bcrypt-ruby', '~> 3.1.2'
```
4. Now in order for a user to be valid it needs to meet one of the following
	1. has a `password` attribute 
	2. has a matching `password` and `password_confirmation` attributes.
```ruby
user = User.new(name:'Albert', email:'a@gmail.com', password:'123321')
user.valid? #true

user = User.new(name:'Albert', email:'a@gmail.com', password:'123321', password_confirmation:'123321')
user.valid? #true
```
5. user object now has `authenticate` method. 
	- Same as the bycrpt `compare` method, compares *plain pw* and *hashed pw*. 
	- *hashed pw* aka *password_digest* is in user object itself.
```ruby
user.authenticate('wrong password') # false
user.authenticate('123321') # returns the user object if pw is correct
```