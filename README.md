This guide provides an overview of the codebase, the functionality of the app, and detailed instructions on how to set up and run the app. Make sure to follow all steps carefully, especially regarding Node.js version requirements.

Overview
This is an authentication-protected Todo App using Node.js, Express.js, bcrypt, JWT authentication, and SQLite. The app allows users to:

Register: Create a new account.
Login: Authenticate and receive a JWT token.
Manage Todos: Perform auth protected CRUD operations on their own todo tasks after logging in.
Project Structure
Here’s the corrected and complete project structure diagram for the auth-protected Todo App:

backend-todo-app/
│
├── public/
│   └── index.html              # The frontend HTML file for authentication and todo management
│
├── src/
│   ├── controllers/            # (Optional) For future separation of concerns
│   └── middlewares/
│       └── authMiddleware.js    # Middleware for verifying JWT and protecting routes
│   └── routes/
│       └── authRoutes.js        # Routes for user registration and login
│       └── todoRoutes.js        # Routes for authenticated CRUD operations on todos
│   └── db.js                    # SQLite database setup and table creation
│   └── server.js                # Main server entry point that sets up routing and middleware
│
├── .env                         # Environment variables for the project
├── package.json                 # Project dependencies and scripts
├── package-lock.json            # Lockfile for exact dependency versions
└── todo-app.rest                # REST client file for emulating API requests
This complete structure reflects all important directories and files, allowing for easy navigation of the project.

Key Directories and Files
public/index.html: Frontend HTML for authentication and todo management.
src/middlewares/authMiddleware.js: Middleware to protect routes using JWT.
src/routes/authRoutes.js: Handles user registration and login.
src/routes/todoRoutes.js: Handles CRUD operations for todos, protected by authentication.
src/db.js: Initializes SQLite database and creates tables.
src/server.js: Sets up the Express server, middleware, and routing.
todo-app.rest: REST client file for emulating HTTP requests (registration, login, CRUD).
Node.js Version and Flags
The app requires Node.js version 22 or higher and uses experimental features. If you're using a lower version, you will need to upgrade.

Checking and Modifying Node.js Version
To check your current Node.js version:

node -v
To install or switch Node versions, use nvm (Node Version Manager). If you don’t have nvm installed, follow the instructions here.

nvm install 22
nvm use 22
Once the appropriate version is installed, start the app with the following flags:

node --env-file=.env --experimental-sqlite ./src/server.js
Changing the Localhost Port to 3000
By default, the app runs on port 5000. If you want to run it on localhost:3000, you can modify the .env file:

Open .env and change the PORT variable to 3000:
PORT=3000
Restart the server using the updated environment configuration:
npm start
Now the app will be accessible at http://localhost:3000.

Getting Started
Clone the Repository:
git clone https://github.com/your-username/backend-todo-app.git
cd backend-todo-app
Install Dependencies:
Install all the required packages:

npm install express bcryptjs jsonwebtoken
Install Developer Dependencies
npm install --save-dev nodemon
Update The package.json Description
A Node.js To-do app with Express, Prisma, and JWT authentication.
Update The package.json Scripts
 "scripts": {
    "dev": "nodemon --env-file=.env --experimental-sqlite ./src/server.js",
  },
Set Up Environment Variables:
In the .env file, define your environment variables:

JWT_SECRET=your_jwt_secret_here
PORT=5000 # Or change to 3000 if preferred
Run the Server:
Ensure you are using Node.js v22 or higher with experimental flags:

npm run dev
Access the App:
Open http://localhost:5000 (or localhost:3000 if changed) in your browser to see the frontend. You can register, log in, and manage your todo list from there.

Emulating HTTP Requests (REST Client)
The REST Client file (todo-app.rest) is provided to help you test the API using HTTP requests directly. You can run these requests using the REST Client extension for VS Code or other compatible tools.

todo-app.rest
The todo-app.rest file includes requests for:

Registering a user: Sends a POST request to create a new user.
Logging in: Sends a POST request to authenticate a user and retrieve a JWT token.
Fetching todos: Sends a GET request to fetch the authenticated user's todos (JWT required).
Adding a todo: Sends a POST request to create a new todo (JWT required).
Updating a todo: Sends a PUT request to update an existing todo (JWT required).
Deleting a todo: Sends a DELETE request to remove a todo (JWT required).
How to Use the REST Client
Install the REST Client extension for VS Code.
Open todo-app.rest.
Run the requests by clicking on the "Send Request" link above each block of HTTP code.
Make sure to copy the token from the login response and replace {{token}} with the actual JWT token for protected routes.
Conclusion
This guide covers the main components of the app and how to get it up and running on your local machine. It highlights key considerations for Node.js version compatibility and provides a ready-to-use todo-app.rest file for testing. You can now explore the app's functionality, including authentication and CRUD operations on todos!
