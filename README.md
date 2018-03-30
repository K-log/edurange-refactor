#### Developer Installation

##  I. Clone the git repository:
```
git clone https://github.com/edurange/edurange-refactor.git
```

##  II. Install RVM (Ruby Version Manager), rails, rubygems, and bundler

  Note: If you have Ruby installed through your package manager, it might conflict with this installation. If necessary perge it first.
```
sudo apt-get remove --purge ruby
```

  Follow this guide to install RVM: (https://rvm.io/rvm/install#installation). Single-user instructions recommended.
  This project uses Ruby 2.5.0 so use RVM to install and select the correct version of Ruby:
```
rvm install [ruby version number eg 2.5.0]  - rvm install 2.5.0
rvm use [ruby version number eg 2.5.0]      - rvm use 2.5.0
```

You may have to do something like: `bin/bash --login` in order to set the RVM ruby version (which doens't refer to the system ruby version).

Also, install bundler (to take care of gem dependencies) and the rails framework:
```
gem install bundler
```
In the edurange-server directory, yank and update all the gem dependencies:
```
bundle update
bundle install
```


*ANYTHING BELOW THIS POINT HAS NOT BEEN FULLY TESTED AND IS STILL A WORK IN PROGRESS*

## II. (*Optional*) Install and setup MySql 

  Below is a link with full instructions for setting up the database but not populating it with data.
  Make sure to ignore the section about creating a new rails application.
  Some of the steps make not work such as running: ``` sudo mysql_install_db ``` So the information in this is only meant to be supplementary and not a fully tutorial for setting up the database.
  https://www.digitalocean.com/community/tutorials/how-to-use-mysql-with-your-ruby-on-rails-application-on-ubuntu-14-04

  First the Mysql server and client needs to be installed.
```
sudo apt-get install mysql-server mysql-client libmysqlclient-dev
```
  
  Next the mysql gem needs to be installed.
```
gem install mysql2
```
  or 
  Add this line to the Gemfile in the edurange-refactor home directory
  
  Sqllite3 needs to be removed. Comment out gem 'sqllite3' from the Gemfile.
  
  
  The config/database.yml file needs to be replaced with the inclued mysqldatabase.yml
  
  Rename the current database so it will not be used by the rails app. Then rename the mysqldatabase.yml so it will be used by the rails app. 
```
mv database.yml sqllite3database.yml
mv mysqldatabase.yml database.yml
```
  
  Create the development and test databases in the mysql server
 ```
rake db:create 
```
  
  
  
  
  
  



