# test-notebook

Prep C9 (no hidden folders)
#########
###1. create git repo called sinatra-notebook
###2. clone, cd into dir
###3. bundle init
##4. Gems
```ruby
gem 'sinatra'
gem 'activerecord'
gem 'sinatra-activerecord'
gem 'rake'
gem 'bcrypt'

group :development do
gem 'pry'
gem 'pry-nav'
gem 'sqlite3'
gem 'tux'
gem 'shotgun'
end
```
## 5. Create directories + files
```ruby
mkdir app
mkdir app/controllers
mkdir app/models
mkdir app/views



mkdir db
mkdir public
mkdir public/css
mkdir public/js
mkdir public/images


touch Rakefile
```


##6. Environment
```ruby
mkdir config
touch config/environment.rb
```
```ruby
require 'bundler'
Bundler.require

configure :development do
  set :database, "sqlite3:db/notebook.db"
end
```

##7. create ApplicationController
```ruby
require './config/environment'

class ApplicationController < Sinatra::Base
  get '/'do
    "Hello, World."
  end
end
```
## 8. CONFIG
```ruby
touch config.ru
require './app/controllers/application_controller'

run ApplicationController
```
