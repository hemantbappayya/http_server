# Chirpy http_server

This project is a simple, Twitter-like social media backend called "Chirpy". It allows users to sign up, post short messages ("chirps"), and view chirps from others.

## Purpose

This project serves as a clear and practical example of a modern web backend built with TypeScript. It demonstrates a clean project structure and the integration of several popular technologies:

- **Express.js:** For handling HTTP requests and defining API endpoints.
- **PostgreSQL:** As the relational database for storing user and chirp data.
- **Drizzle ORM:** For type-safe database queries and schema management.
- **JWT (JSON Web Tokens):** For secure user authentication.
- **TypeScript:** For a strongly-typed and more maintainable codebase.

It's a great starting point for anyone looking to learn how these technologies can be combined to build a robust API.

## Installation and Setup

1.  **Clone the repository:**

    ```bash
    git clone <repository-url>
    cd http_server
    ```

2.  **Install dependencies:**

    ```bash
    npm install
    ```

3.  **Set up the database:**

    - Make sure you have PostgreSQL installed and running.
    - Create a new database for this project.
    - Create a `.env` file in the root of the project and add your database connection string:
      ```
      DATABASE_URL=postgresql://<user>:<password>@<host>:<port>/<database>
      ```

4.  **Run database migrations:**
    This will set up the necessary tables in your database.

    ```bash
    npm run migrate
    ```

5.  **Run the development server:**
    This command will compile the TypeScript code and start the server.
    ```bash
    npm run dev
    ```
    The server will be running at `http://localhost:8080` by default.

## Available API Endpoints

### Authentication

- `POST /api/login`: Authenticate a user and receive a JWT.
- `POST /api/refresh`: Obtain a new JWT using a refresh token.
- `POST /api/revoke`: Revoke a user's refresh token.

### Users

- `POST /api/users`: Create a new user account.
- `PUT /api/users`: Update an authenticated user's information.

### Chirps

- `POST /api/chirps`: Create a new chirp (requires authentication).
- `GET /api/chirps`: Retrieve all chirps. Can be filtered by `authorId`.
- `GET /api/chirps/:chirpId`: Retrieve a single chirp by its ID.
- `DELETE /api/chirps/:chirpId`: Delete a chirp (requires authentication and ownership).

### Webhooks

- `POST /api/polka/webhooks`: Webhook endpoint for external services (e.g., to handle user upgrades).

### Admin & Health

- `GET /api/healthz`: Health check endpoint.
- `GET /admin/metrics`: View application metrics.
- `POST /admin/reset`: Reset the database and metrics (for development purposes only).
