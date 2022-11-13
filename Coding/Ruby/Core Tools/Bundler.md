- A *gem* that serves as a **dependency manager**.
- Installing *Ruby* version `2.5` or higher automatically includes this gem.
- `bundle exec some_command` uses the version of the command found in your `Gemfile.lock`.
- use `bundle _2.3.14_ install` to specify bundler version.

## Steps
1. `Gemfile` in project root
 ```
source 'https://rubygems.org'

ruby "3.1.2"
gem 'nokogiri'
gem 'rack' '~> 2.2.4'
gem 'rspec'
```
2. `bundle install` in terminal. This creates `Gemfile.lock`
3. Add `require 'bundler/setup'` to the beginning of your app, before any other gems. (Not needed for *Rails*). This modifies `$LOAD_PATH` so Ruby finds the correct versions of gems listed in `Gemfile.lock`

