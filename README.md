# Todo App

A secure, full-stack Todo application built with Node.js, Express, JWT authentication, bcrypt, and SQLite.

This project allows users to register, log in, and manage their own todo items behind protected routes.

## Overview

The app includes:

- User registration
- Login with JWT authentication
- Protected todo CRUD operations
- SQLite persistence
- A simple frontend served from `public/index.html`

## Features

- Create a new account
- Sign in securely with a username/password
- Receive and store a JWT token
- Create, read, update, and delete todos
- Restrict todo access to the authenticated user only

## Project Structure

```text
backend-todo-app/
├── public/
│   └── index.html               # Frontend UI for authentication and todo management
├── src/
│   ├── db.js                    # SQLite database setup and table creation
│   ├── server.js                # Express app setup and route registration
│   ├── middlewares/
│   │   └── authMiddleware.js    # Verifies JWT and protects routes
│   └── routes/
│       ├── authRoutes.js        # Registration and login routes
│       └── todoRoutes.js        # Authenticated CRUD routes for todos
├── .env                         # Environment variables
├── package.json                 # Dependencies and scripts
├── package-lock.json            # Lockfile
├── todo-app.rest                # REST client requests for testing the API
└── README.md                    # Project documentation
```

## Requirements

- Node.js 22 or higher
- npm
- SQLite support via Node's experimental SQLite mode

## Getting Started

### 1) Clone the repository

```bash
git clone https://github.com/your-username/backend-todo-app.git
cd backend-todo-app
```

### 2) Install dependencies

```bash
npm install express bcryptjs jsonwebtoken
npm install --save-dev nodemon
```

### 3) Configure environment variables

Create a `.env` file:

```env
JWT_SECRET=your_jwt_secret_here
PORT=5000
```

If you want the app to run on port `3000`, set:

```env
PORT=3000
```

### 4) Start the app

Use a compatible Node.js version and enable the experimental SQLite flag:

```bash
node --env-file=.env --experimental-sqlite ./src/server.js
```

Or run it in development mode with nodemon:

```bash
npm run dev
```

Make sure your `package.json` includes a script like this:

```json
{
  "scripts": {
    "dev": "nodemon --env-file=.env --experimental-sqlite ./src/server.js"
  }
}
```

## Access the App

Open the app in your browser:

- http://localhost:5000
- or http://localhost:3000 if you changed the port

You can register, log in, and manage your todo list from the frontend.

## API Endpoints

### Authentication routes

#### Register user

```http
POST /api/auth/register
```

Request body:

```json
{
  "username": "alice",
  "password": "secret123"
}
```

#### Login user

```http
POST /api/auth/login
```

Request body:

```json
{
  "username": "alice",
  "password": "secret123"
}
```

This returns a JWT token for future requests.

### Todo routes

All todo routes require a valid JWT token in the `Authorization` header:

```http
Authorization: Bearer <token>
```

#### Get todos

```http
GET /api/todos
```

#### Create todo

```http
POST /api/todos
```

Request body:

```json
{
  "title": "Finish project proposal",
  "completed": false
}
```

#### Update todo

```http
PUT /api/todos/:id
```

#### Delete todo

```http
DELETE /api/todos/:id
```

## Testing with the REST Client

A `todo-app.rest` file is included to help test the API directly.

### How to use it

1. Install the REST Client extension for VS Code.
2. Open `todo-app.rest`.
3. Click `Send Request` above each request block.
4. Copy the token from the login response and replace `{{token}}` with the actual JWT token.

This file includes requests for:

- Registering a user
- Logging in
- Fetching todos
- Creating a todo
- Updating a todo
- Deleting a todo

## Notes

- The app requires Node.js v22+.
- It uses `--experimental-sqlite` for SQLite support.
- JWT tokens are required for all protected todo operations.

## Conclusion

This project demonstrates a simple, secure Todo application using Node.js, JWT authentication, and SQLite persistence.

It is a strong starting point for building authenticated APIs and adding more features later.
