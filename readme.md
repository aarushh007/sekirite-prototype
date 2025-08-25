# Sekirite Prototype

## Author

This program was written by **Aarush Hadimani** as part of a prototype project for a hackathon.

## Purpose

The purpose of this application is to provide a lightweight web platform where users can submit and view reports of violence and other crime in Haiti. It integrates a web frontend with a Flask backend and a **Firebase Realtime Database** for storing and retrieving reports. Real-time communication is supported through **Flask-SocketIO**.

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

4. Configure Firebase:

   * Go to [Firebase Console](https://console.firebase.google.com/) and create a new project (or use an existing one).
   * Enable **Realtime Database** and set the rules appropriately (for development you may allow read/write access, but in production configure proper security rules).
   * Go to project settings and create a web app
   * Copy your Firebase configuration (API key, database URL, etc.).
   * Update the configuration inside `models/report_model.py` with your Firebase project details.

## Running the Program

1. Start the Flask application:

   ```bash
   python app.py
   ```

2. Open your web browser and go to:

   ```
   http://127.0.0.1:5000/
   ```

### Rules / Inputs

* Users can submit reports through the web form on the homepage.
* Input data is validated and stored in Firebase.
* Real-time updates are broadcast via WebSockets.

## Outputs

* Submitted reports are saved in the Firebase Realtime Database.
* Reports are displayed dynamically on the webpage.
* Console logs in the terminal provide server-side feedback.

flowchart TD
    A[User opens web app] --> B[Frontend (HTML/CSS/JS)]
    B --> C[User submits report form]
    C --> D[Flask Backend (app.py)]
    D --> E[Firebase Realtime Database]
    E --> D
    D --> F[Flask-SocketIO]
    F --> G[Frontend Updates in Real-Time]
    G --> H[Users see reports displayed on webpage]
