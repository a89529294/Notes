There are three `Rails.env` values *'development'*, *'test'*, *'production'*.

```erb
<%= debug(params) if Rails.env.development? %>
```

You can also pass in `--environment production` or test/development
```bash
rails console --environment production
rails server --environment test
```
