# Sekirite Prototype

## Author

This program was written by **Aarush Hadimani** as part of a prototype project for a hackathon.

## Purpose

The purpose of this application is to provide a lightweight web platform where users can submit and view reports of violence and other crime in Haiti. It integrates a web frontend with a Flask backend and a PostgreSQL database. Real-time communication is supported through **Flask-SocketIO**.

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/aarushh007/sekirite-prototype.git
   cd sekirite-prototype
   ```

2. Create and activate a virtual environment:

   ```bash
   python3 -m venv venv
   source venv/bin/activate   # On Windows use: venv\Scripts\activate
   ```

3. Install required dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Install and configure PostgreSQL:

   * Download and install PostgreSQL from [https://www.postgresql.org/download/](https://www.postgresql.org/download/).
   * Start the PostgreSQL server.
   * Create a new database:

     ```bash
     psql -U postgres
     CREATE DATABASE sekirite;
     ```
   * (Optional) Create a dedicated user and grant privileges:

     ```sql
     CREATE USER sekirite_user WITH PASSWORD 'yourpassword';
     GRANT ALL PRIVILEGES ON DATABASE sekirite TO sekirite_user;
     ```
   * Update the connection string in the project (e.g., inside `db_setup.py` or the configuration file) to match your database credentials. Example:

     ```python
     DATABASE_URL = "postgresql+psycopg2://sekirite_user:yourpassword@localhost/sekirite"
     ```

## Running the Program

1. Initialize the database tables (if required):

   ```bash
   python db_setup.py
   ```

2. Start the Flask application:

   ```bash
   python app.py
   ```

3. Open your web browser and go to:

   ```
   http://127.0.0.1:5000/
   ```

### Rules / Inputs

* Users can submit reports through the web form on the homepage.
* Input data is validated and stored in the PostgreSQL database.
* Real-time updates are broadcast via WebSockets.

## Outputs

* Submitted reports are saved in the database.
* Reports are displayed dynamically on the webpage.
* Console logs in the terminal provide server-side feedback.

