- **One Time Setup** `gem install bundler`
- In project folder `touch Gemfile`
- In gemfile put: 
```
source 'https://rubygems.org'

gem 'jekyll', '4.2.1'
```
- Install dependencies `bundle install`
- Tell Jekyll to create static files and serve them `bundle exec jekyll serve --port 4001` port is optional

## bundle exec with or without
- `bundle exec jekyll serve` runs the exact jekyll server version that is specified in your Gemfile
- `jekyll servce` runs _some_ version of jekyll server

## Four types of magic Jekyll files
1. layouts, any files in the *_layouts* directory
2. includes, any files in the *_includes* directory
3. pages
4. posts