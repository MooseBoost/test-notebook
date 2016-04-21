# test-notebook

Prep C9 (no hidden folders)
#########
###1. create git repo called sinatra-notebook
###2. clone, cd into dir
###3. bundle init
##4. Gems
```ruby
source "http://rubygems.org"

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

## 9.Rakefile
```ruby
touch Rakefile
```
```ruby
require 'sinatra/activerecord/rake'
require './config/environment'
```
### shotgun -> run app

#Part 2 Models

####New Branch - Models
```ruby
git checkout -b models
```

####Create teacher.rb, student.rb, lesson.rb
```ruby
class Teacher < ActiveRecord::Base
end

#TEACHER
  has_many :students
  has_many :lessons, through: :students
  
#STUDENT
  has_many :lessons
  belongs_to :teacher
  
#LESSON
  belongs_to :student
```

### New GEM
Gemfile -> `gem 'require_all'`

In envirnonment.rb
(fix development)
`require_all` 'app'

### Migrations
create three migrations
add columns according to form
add foreign keys

rake migrate
show schema

tux
Create a Teacher
Create a Student
Create a Lesson

