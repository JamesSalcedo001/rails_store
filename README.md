# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions


## Notes Section

1: Model-View-Controller Basics

    * Rails Code is organized using the MVC architecture. With MVC there are 3 main concepts where the majority of the code lives: 

        - Model: Manages the data in your app. Typically your database tables
        - View: Handles rendering responses in different formats like HTML, XML or JSON etc.
        - Controller: Handles user interactions and the logic for each request

2: Running the server

    * Run the command:

    `$rails server` 
     or 
    `rails s` 
    
    to start up a web server called Puma that will serve static files and the Rails app 

    * Autoloading in development: the Rails server will detect changes to code and auto reload every time one is made. Rails also rarely uses require statement explicitly because it uses naming conventions to require files automatically.

3: Creating a Database Model

    * Active Record is a feature of Rails that maps relational databases to Ruby code. It helps generate the SQL for interacting with the database like creating, updating, and deleting tables and records. Here, SQLite will be used, which is the default for Rails.

    - Run the command:
    
    `$rails generate model Product name:string`

        to add a database table to the Rails app to add products to this simple e-commerce store

    - this command tells Rails to generate a model named Product which has a name column and type of string in the database. It:
    
        * creates a migration in the db/migrate folder
        * an Active Record model in app/models/product.rb
        * tests and test fixtures for this model

    * Model names are singular, because an instantiated model represents a single record in the database(ie. you are creating a product to add to the database)
* ...
