# HTTP Server 

## 🌟 Project Overview

> I developed the **REST API** – the entire server-side system – for a social media app (Chirpy), using **Node.js** and **TypeScript**. This backend makes sure users can securely sign up and log in, post short messages (called 'chirps') that are checked for length and bad words, view their feeds sorted by newest or oldest, and even delete their own posts. It also handles special premium upgrades for users and keeps all this information safely stored in a database, making the app fast and reliable.


## ✨ Core Features & Technical Demonstrations

*   **Secure Authentication System:** Implemented JSON Web Tokens (JWTs) with both Access and Refresh tokens for session management, coupled with Argon2 for secure password hashing.
*   **Comprehensive RESTful API:** Full suite of endpoints for user registration, login, and CRUD operations on "chirps" (short messages), utilizing Express.js for efficient routing.
*   **Relational Database Integration:** Persistent data storage and retrieval using PostgreSQL, managed with Drizzle ORM for type-safe and efficient queries.
*   **Scalable Backend Architecture:** Built on Node.js, leveraging its asynchronous capabilities, and structured with TypeScript for improved code quality and maintainability in larger applications.
*   **Webhooks for Monetization:** Integrated a secure endpoint to process external payment events for user upgrades (e.g., "Chirpy Red" status).
*   **Robust Data Validation:** Server-side input validation, including profanity filtering and character limits, to ensure data integrity and application stability.

## 🛠️ Tech Stack

*   **Runtime:** Node.js
*   **Language:** TypeScript
*   **Web Framework:** Express.js
*   **Database:** PostgreSQL
*   **ORM:** Drizzle ORM
*   **Security:** Argon2 (Password Hashing), JSON Web Tokens (JWT)
*   **Testing:** Vitest

## 🏃 Getting Started (Local Development)

To run the Chirpy backend on your local machine, follow these steps.

### Prerequisites

*   Node.js (v21.7.0 or higher)
*   npm (Node Package Manager)
*   A running PostgreSQL database instance

### Installation

1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/Archana38980609/HTTP_Server.git
    cd HTTP_Server
    ```

2.  **Install Dependencies:**
    ```bash
    npm install
    ```

3.  **Configure Environment Variables:**
    Create a `.env` file in the root directory and add:
    ```bash
    PORT=8080
    PLATFORM="dev"
    DB_URL="postgresql://user:password@localhost:5432/your_database_name"   # Update with your PostgreSQL connection string
    JWT_SECRET="your_super_secret_jwt_key"       # Generate a strong, unique key
    POLKA_KEY="your_webhook_api_key"      # Generate a strong, unique key
    ```

4.  **Database Setup:**
    Run migrations to create the necessary database schema:
    ```bash
    npm run migrate
    ```

5.  **Run the Server:**
    Start the development server with hot-reloading:
    ```bash
    npm run dev
    ```
    The API will be available at `http://localhost:8080`.

## 📜 Available Scripts

*   `npm run dev` - Starts the development server.
*   `npm run build` - Compiles TypeScript to JavaScript (`/dist`).
*   `npm run start` - Runs the compiled production server.
*   `npm run test` - Executes unit tests.
*   `npm run migrate` - Applies database schema changes.

## 🔌 API Endpoints

### Authentication
*   `POST /api/users` - Register a new user.
*   `POST /api/login` - Authenticate to receive Access and Refresh tokens.
*   `POST /api/refresh` - Exchange a refresh token for a new access token.
*   `POST /api/revoke` - Log out (revoke refresh token).

### Chirps (Posts)
*   `GET /api/chirps` - Retrieve all chirps (supports `?sort=asc|desc` and `?authorId=uuid`).
*   `POST /api/chirps` - Create a new chirp (authenticated, max 140 chars).
*   `GET /api/chirps/:id` - Fetch a specific chirp by ID.
*   `DELETE /api/chirps/:id` - Delete a chirp (authenticated, must be owner).

### Webhooks
*   `POST /api/polka/webhooks` - Endpoint for processing payment events (e.g., "Chirpy Red" upgrades).


## 📂 Project Structure

```text
http-server/
├── src/
│   ├── api/                # API Route Handlers & Middleware
│   │   ├── auth.ts         # Login, Refresh, & Revoke handlers
│   │   ├── chirps.ts       # Create, Read, Delete posts
│   │   ├── users.ts        # User registration & updates
│   │   ├── webhooks.ts     # Payment webhook logic
│   │   ├── middleware.ts   # Error handling & Logging
│   │   ├── metrics.ts      # Admin metrics endpoint
│   │   └── readiness.ts    # Health check endpoint
│   │
│   ├── app/                # Static Assets
│   │   ├── assets/         # Images (logo.png)
│   │   └── index.html      # Landing page
│   │
│   ├── db/                 # Database Layer
│   │   ├── migrations/     # SQL Migration files
│   │   ├── queries/        # Drizzle query functions
│   │   ├── schema.ts       # Database table definitions
│   │   └── index.ts        # Database connection setup
│   │
│   ├── auth.ts             # Core Security (JWT & Argon2 utils)
│   ├── auth.test.ts        # Unit tests for authentication
│   ├── config.ts           # Environment variable management
│   └── index.ts            # Main application entry point
│
├── .gitignore
├── .nvmrc                  # Node version config
├── package.json            # Dependencies & Scripts
├── package-lock.json       # Dependency lock file
└── tsconfig.json           # TypeScript configuration









































