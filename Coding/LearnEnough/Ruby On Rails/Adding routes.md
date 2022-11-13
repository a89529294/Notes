1. update routes in `config/routes.rb`
2. add an action to a controller file in `app/controllers` dir
3. create view in `app/views`

`config/routes.rb`
```ruby
Rails.application.routes.draw do
	root 'static_pages#home'
	get '/help', to: 'static_pages#help'
	get '/about', to: 'static_pages#about'
	get '/contact', to: 'static_pages#contact'
end
```
- `root`  is a method that routes *GET* requests on path `/` to `static_pages` controller's `home` action. It also generates `root_path('/')` & `root_url('http://www.example.com/')`
- the first `get` is a method that routes *GET* requests on `/help` to `static_pages` controller's `help` action. It also generates `help_path('/help')` & `help_url('http://www.example.com/help')`
- Note that the *named path* e.g. `help_path` is based on the *route path* not the action name. 
