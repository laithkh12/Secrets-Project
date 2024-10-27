
# Secret Sharing App

This is a Node.js application for sharing secrets, built with Express, Passport for authentication (including local and Google OAuth strategies), PostgreSQL for the database, and bcrypt for password hashing. It includes user registration, login, and Google OAuth-based authentication, allowing users to store and view "secrets."

## Features

- User registration and login using email and password.
- Google OAuth 2.0 authentication for user login.
- Secrets can be submitted and retrieved by authenticated users.
- Passwords are securely hashed using bcrypt.
- User sessions maintained with express-session.

## Prerequisites

- Node.js and npm
- PostgreSQL database
- Google OAuth 2.0 credentials
- `.env` file with the following environment variables:

```bash
PG_USER=<your_db_user>
PG_HOST=<your_db_host>
PG_DATABASE=<your_db_name>
PG_PASSWORD=<your_db_password>
PG_PORT=<your_db_port>
SESSION_SECRET=<your_session_secret>
GOOGLE_CLIENT_ID=<your_google_client_id>
GOOGLE_CLIENT_SECRET=<your_google_client_secret>
```

## Installation

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Set up PostgreSQL**:
   - Create a PostgreSQL database.
   - Run the following command to set up a `users` table:
     ```sql
     CREATE TABLE users (
       id SERIAL PRIMARY KEY,
       email VARCHAR(255) UNIQUE NOT NULL,
       password VARCHAR(255),
       secret TEXT
     );
     ```

4. **Configure environment variables**:
   - Create a `.env` file in the root directory with the values mentioned above.

## Usage

1. **Start the server**:
   ```bash
   npm start
   ```
2. **Access the application**:
   Open your browser and go to `http://localhost:3000`.

## Project Structure

- `app.js`: Main application file where routes, middleware, and Passport strategies are defined.
- `views/`: Directory containing EJS templates for pages like `home.ejs`, `login.ejs`, `register.ejs`, `secrets.ejs`, and `submit.ejs`.
- `public/`: Directory for static assets like CSS, JavaScript, and images.

## Routes

- `GET /`: Home page.
- `GET /login`: Login page.
- `GET /register`: Registration page.
- `POST /login`: Handle user login.
- `POST /register`: Handle new user registration.
- `GET /secrets`: Authenticated users' secret page.
- `POST /submit`: Submit a secret (authenticated users only).
- `GET /auth/google`: Initiates Google OAuth login.
- `GET /auth/google/secrets`: Redirect after successful Google login.

## License

This project is licensed under the MIT License.
