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

    
    $rails server
    
    or 

     
    $rails s
     
    
    to start up a web server called Puma that will serve static files and the Rails app 

    * Autoloading in development: the Rails server will detect changes to code and auto reload every time one is made. Rails also rarely uses require statement explicitly because it uses naming conventions to require files automatically.

3: Creating a Database Model

    * Active Record is a feature of Rails that maps relational databases to Ruby code. It helps generate the SQL for interacting with the database like creating, updating, and deleting tables and records. Here, SQLite will be used, which is the default for Rails.

    - Run the command:
    
 
        $rails generate model Product name:string


    to add a database table to the Rails app to add products to this simple e-commerce store

    - this command tells Rails to generate a model named Product which has a name column and type of string in the database. It:
    
        * creates a migration in the db/migrate folder
        * an Active Record model in app/models/product.rb
        * tests and test fixtures for this model

    * Model names are singular, because an instantiated model represents a single record in the database(ie. you are creating a product to add to the database)


4: Database Migrations

    * A migration is a set of changes one wants to make to the database. By defining migrations, one is telling Rails how to change the database to add, remove, or change tables, columns, or any other attributes of our database. This helps keep track of changes one makes in development locally so they can be deployed to production live safely.

    - The migration just created for products(Create Products), is telling Rails to create a new database table named Products.

    - In contrast to the model just spoken of, Rails makes the database table names plural, because the database holds all of the instances of each model. (ie. one is creating a database of products)

    - The create_table block then defines which columns and types should be defined in thie database table. t.string :name tells Rails to create a column in the products table called name and set the type as string

    - t.timestamps is a shortcut for defining two columns on your models: created_at:datetime and updated_at:datetime. These are automatically set by Active Record when creating or updating records

5: Running Migrations

    - after determining what changes to make to the database, use the following command to run the migrations:

        $rails db:migrate

    which checks for any new migrations and applies them to your database

    - if you make a mistake, you can undo the last migration by running:

        $rails db:rollback

6: Rails Console

    - rails console is an interactive tool for testing our code in our Rails app

        $rails console or rails c

    - in the console, code will be executed when hitting enter

        $Rails.version
        => "8.0.1"


7: Active Record Basics

    - when we ran the Rails Model generator to create Product model, it created the model file in app/models/product.rb. the file creates a class that uses Active Record for interacting with our products table.

    - Q: how does Rails know with no code in the class what defines the model?
    - A: when the product model is used, Rails will query the database table for the column names and types and automatically generate code for these attributes. Rails saves us from writing this boilerplate code and instead takes care of it for us behind the scenes so we can focus on the app logic instead. 

    - checking to see what colummns Rails detects for the Product Model with the command: 

        $Product.column_names
        =>  ["id", "name", "created_at", "updated_at"]


    - Rails asked the database for column info above and used that info to define attributes on the Product class dynamically so you don't have to manually define each of them. 


8: Creating Records

    - instantiate a new product with the following:

        $product = Product.new(name: "T-Shirt")
    
    - the product variable is an instance of Product. It has not been saved to the db, so does not have an ID, created_at, or updated_at timestamps

    - call save to write the record to the db:

        $product.save

    - when save is called, Rails takes the attribute in memory and generates an INSERT SQL Query to insert this record into the database. Rails also updates the object in memory with the db record id along with the created_at and updated_at timestamps. which one can see by printing the product variable:

        $product

    - the new + save methods work in a similar way as the create method, doing both at once, instantiating and saving an Active Record object in a single call:

        $ Product.create(name: "Pants")


* ...
