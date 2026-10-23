# Intrusion-Detector-

A web application that detects unauthorised logins using keystroke dynamics. Along with the password, it checks how the user types it. A correct password typed in the wrong rhythm is flagged as an intrusion.

Project Description:

Passwords alone can be stolen, guessed or shared. This project adds a second, passive layer of protection that needs no extra hardware or user action.

At sign-up, the user types their password three times. The time gaps between key presses are recorded and used to build a typing profile.
At login, the password and a fresh set of key-press timings are sent to the server.
The server compares the new timings with the stored profile using a T-distribution test (statistical anomaly detection).
If the password matches but the typing pattern does not, the app shows "Intrusion Detected". Otherwise it shows "OK".
Dataset

No external dataset is used. Typing samples are collected live by the application itself: each user provides three password samples at sign-up, and these form that user's reference profile (stored in MySQL).

Technologies Used:
Area	Technology
Language	Python 3.6
Web framework	Flask 1.0.2
Database	MySQL (via PyMySQL 0.8.0)
Statistics	SciPy (T-distribution test)
Front end	HTML templates, JavaScript (captures key-press timestamps)

Project Structure:
├── main.py            # Flask app and routes (/, /login, /signup)
├── views/             # UserView: registration and login logic
├── models/            # Database models
├── templates/         # index.html, Login.html, SignUp.html
├── static/            # CSS / JS / assets
└── requirements.txt   # Python dependencies

Setup and Run Instructions:
Clone the repository
bash
   git clone https://github.com/anjalit-gif/Intrusion-Detector-.git
   cd Intrusion-Detector-
Create and activate a virtual environment (Python 3.6+ recommended)
bash
   python -m venv venv
   source venv/bin/activate        # Windows: venv\Scripts\activate
Install dependencies
bash
   pip install -r requirements.txt
Set up MySQL: install MySQL, create a database, and enter your credentials in the database configuration inside models/. (add the exact file name and table-creation steps here)
Run the app
bash
   python main.py
Open http://127.0.0.1:8080 in your browser.

How to Use:
Go to Sign Up and create an account (type the password three times, naturally).
Go to Log In and sign in as yourself. You should see "OK".
Ask a friend to log in with your username and password. You should see "Intrusion Detected", because the password is right but the typing pattern is different.

Key Information:
Routes: GET /, GET/POST /login, GET/POST /signup
Local server: runs on 127.0.0.1:8080 with Flask debug mode on. Turn debug off before any real deployment.
Limitations: typing rhythm varies with mood, device and keyboard, and the profile is built from only three samples.
Future work: password hashing, HTTPS, rate limiting and account lockout, session handling, and evaluation on a public keystroke dataset.

Author:

Your Name, Computer Engineering, Thapar Institute of Engineering and Technology
