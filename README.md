# Flask-with-CRUD

To install necessary packages:
  1. Create a file named "requirements.txt"
  2. Copy and paste the contents of the "requirements.txt" file in this repository into your own
  3. Open your terminal and type: pip install -r requirements.txt

Completed Replit Application @ https://replit.com/@TeoHean1/personalwebsite just need to add your database link
Launched application on render @ https://flask-with-crud-prv.onrender.com/
     
Some simple explanation:

1. app = Flask(__name__)
Imagine you're building a house. To build it, you need to know where to find different materials like bricks, wood, and paint. In the same way, when you're building a web application with Flask, you need to tell Flask where to find things like HTML templates (like the blueprints for rooms in a house) and static files (like the paint and decorations).
Now, when you're building your house, you need to know where you are to find the materials. Similarly, Flask needs to know where it is in your project to find the web page templates and static files. This is where the __name__ variable comes in.
In Python, __name__ tells you the name of the current file. So when you create a Flask app, you use __name__ to tell Flask the name of the file where it's being used. This way, Flask knows where to look for templates and static files because it knows where it is in your project.
In simpler terms, using __name__ in Flask is like giving directions to someone building your house. You tell them where they are so they can find the right materials in the right place.

2. app.secret_key = 'your-defined-secret-key
Signing Data: When Flask stores session data or other sensitive information in cookies (or elsewhere), it first signs the data using cryptographic techniques. This involves generating a unique signature based on the data and the secret key.
Verification: When the data is later retrieved, Flask verifies the signature to ensure that it has not been tampered with. It does this by recalculating the signature using the secret key and comparing it to the signature stored with the data.
Protection: By using this signature-based approach, Flask can ensure that the data has not been altered since it was signed. Even if a user tries to modify the data in the cookie, the signature won't match, indicating that the data has been tampered with.
Note: Never store your secret_key in your source code, store it as an environment variable or store it in another file that you are sure that no one will have access to it.

3. app.config['SQLALCHEMY_DATABASE_URI'] = 'your-database-connection-string'
This is to establish a connection with your chosen database so that you can read, write and append data on it.

4. db = SQLAlchemy(app)
Think of SQLAlchemy as a tool that helps your Flask web application talk to a database.
Imagine your database as a big library with lots of books (data). SQLAlchemy helps you manage this library.
db: This is like a librarian you hire to organize and handle all the tasks related to the library (database).
SQLAlchemy(app): You're telling SQLAlchemy that it's going to work inside your Flask application (app). It's like introducing your librarian to the library and telling them, "This is where you'll be working."

5. login_manager = LoginManager()
Imagine that the context is still a library, but a private one, people need to prove that they are allowed to enter.
LoginManager() is someone that controls who enters the library, basically it will authenticate the person.
Creating an object with is like hiring a librarian to control who comes in the library

6. db.Column is the columns of a table.
   db.Column(data_type, options)
   Data Types:
   - db.Integer --> 1, 2, 3, 4
   - db.String(length)
   - db.Boolean --> True or False
   - db.Float --> 0.9398593
   - db.Date
   - db.ForeignKey(Column) --> Represents a foreign key relationship with another column in a different table
   Note: Foreign key is a way of linking of two tables through the use of a unique ID, etc. For example, our project needs to assign the 'tasks' created by the user to the specific user_id so that when we load the task page, the user can see what he or she has uploaded.
  Options:
- primary_key: Indicates whether the column is a primary key for the table.
- unique: Specifies that the values in the column must be unique across all rows in the table.
- nullable: Indicates whether the column can contain null values (i.e., empty or missing values).
- default: Specifies a default value for the column if no value is provided during insertion.
- index: Creates an index on the column, which can improve query performance.
- autoincrement: Indicates whether the column should automatically increment its value for each new row added to the table. This is typically used with integer primary key columns.
- foreign_key: Defines a foreign key constraint for the column, linking it to a column in another table.
- ondelete: Specifies the action to take when the referenced row in the parent table is deleted. Common options include 'CASCADE', 'SET NULL', and 'RESTRICT'.
- onupdate: Specifies the action to take when the referenced row in the parent table is updated.
- comment: Adds a comment to the column, which can be helpful for documenting the purpose of the column.

  What about lazy=True?
  - Setting lazy=True in SQLAlchemy means data related to a particular object is loaded from the database only when you specifically ask for it, not automatically when you retrieve the main object. This saves time and resources by fetching data only when needed.

  7. @login_manager.user_loader
     def load_user(user_id):
      return User.query.get(int(user_id))
     @login_manager.user_loader is a decorator used to tell Flask-Login how to load a user from the database based on their unique identifier, in this case the user_id.

  8. @app.route('/')
     Flask creates a route for the root URL '/'. When a user visits this URL, the associated function is called to handle the request. Your functioos can be like return redirect(url_for('login')) --> Means that when you go to the root it will redirect you to the login page.

  9. Why url_for('') do not need to include things like where is the .html file located at and the name, instead just the name of the .html file without the .html?
     In Flask, the url_for() function is used to generate URLs for routes defined in your application. When you provide the name of the function that corresponds to a route, Flask automatically determines the URL associated with that route based on the route's name.

  10. Why can I not include the file location and the render_template function still works?
      In Flask, the render_template() function is used to render HTML templates. When you call render_template() and provide the name of the template file, Flask automatically looks for the template file within a predefined directory structure.

  11. Database functions
   - db.session.add()
   - db.session.delete()
   - db.session.commit()
   - tableName.query.get()
 
  12. with app.app_context():
      You are in a library filled with books
      Each bookshelf represents a different part of the library each book on the shelf contains valuable information
      
      Let's say you want to consult a specific book
      Before you can do that, you need to enter the library and locate the bookshelf where the book is located
      Once you're in the right section of the library
      You can easily find and access the book you need
      
      The library represents the Flask application
      Each bookshelf represents a different component of the application such as routes, models or templates
      The books on the shelf represent the resources or functionalitites 
      Entering the library and locating the correct bookshelf corresponds to using app.app_context()
      Once inside the application context you have access to all the components and easily find and interact with resources you need
