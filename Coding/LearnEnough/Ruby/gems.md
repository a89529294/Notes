- `gen install sinatra` to install *sinatra*
- `ls ~/.rbenv/versions/2.7.4/lib/ruby/gems/2.7.0/gems` *lists* all gems installed for ruby version *2.7.4*
- `gem list | grep -E 'rails'` *lists* all gems that include *rails* in the name, `-E` enables regex

## Gemfile
- `gem "rails"` installs the latest gem version
- `gem "rails" ">= 3.26"` installs the latest gem version as long as it is greater than *3.26*
- `gem "rails" "~> 3.26"` installs the lastest version *LESS THAN*  `4.0` 
- 