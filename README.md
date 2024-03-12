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
