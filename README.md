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
