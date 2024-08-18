
**Backend API Documentation**

**Overview**

This project is a backend API for managing customers and laborers. It uses MongoDB for data storage and JWT for authentication.

**Installation**
Clone the repository:


git clone <repository-url>

Navigate to the project directory:


cd <project-directory>

Install dependencies:


npm install

Set up environment variables:

Create a .env file in the root directory and add your environment variables, such as database connection strings and JWT secret.

**Configuration**

Database: MongoDB

JWT Secret Key: mysecretkey (for generating and validating tokens)

**API Endpoints**

**Authentication Routes**

POST /auth/login

Description: Login endpoint for laborers and customers.

Request Body:

{
  "email": "string",
  
  "password": "string"
}
**Responses:**

200 OK: Login successful, returns user data and JWT token.

400 Bad Request: Missing fields or incorrect credentials.

404 Not Found: User not found.

500 Internal Server Error: Server error.

**POST /auth/createUser**

Description: Register a new customer.

Request Body:

{
  "name": "string",
  
  "email": "string",
  
  "phoneNumber": "string",
  
  "password": "string",
  
  "confirmPassword": "string",
  
  "image": "string"
}

**Responses:**

201 Created: User created successfully, returns user data and JWT token.

400 Bad Request: Missing fields or passwords do not match.

500 Internal Server Error: Server error.

**POST /auth/laborStats**

Description: Create labor statistics for a laborer.

Request Body:

{
  "price": "number",
  
  "experience": "number"
  
}
**Responses:**

201 Created: Labor statistics created successfully.

400 Bad Request: Invalid data.

404 Not Found: Labor user not found.

500 Internal Server Error: Server error.

**POST /auth/CLogin**


Description: Login endpoint for customers.

Request Body:

{
  "email": "string",
  
  "password": "string"
  
}
**Responses:**

200 OK: Login successful, returns user data and JWT token.

400 Bad Request: Missing fields or incorrect credentials.

404 Not Found: User not found.

500 Internal Server Error: Server error.

**GET /auth/getUser**


Description: Get a list of all laborers.

Responses:

200 OK: Returns list of laborers.

404 Not Found: No users found.

500 Internal Server Error: Server error.

**GET /auth/getCustomer**


Description: Get a list of all customers.

**Responses:**

200 OK: Returns list of customers.

404 Not Found: No customers found.

500 Internal Server Error: Server error.

**GET /auth/getAllUser**


Description: Get a list of all users (laborers and customers).

Responses:

200 OK: Returns list of all users.

404 Not Found: No users found.

500 Internal Server Error: Server error.

**Models**

**CustomerSignup**

Schema:


const LSchema = new mongoose.Schema({

    name: { type: String, required: true },
    
    email: { type: String, required: true, unique: true, lowercase: true },
    
    phoneNumber: { type: String, required: true },
    
    password: { type: String, required: true },
    
    image: { type: String }
    
}, { timestamps: true });

**LaborSignup**

Schema:

const LSchema = new mongoose.Schema({

    name: { type: String, required: true },
    
    email: { type: String, required: true, unique: true, lowercase: true },
    
    phoneNumber: { type: String, required: true },
    
    cnic: { type: String, required: true },
    
    password: { type: String, required: true },
    
    city: { type: String, required: true }
    
}, { timestamps: true });

**LaborStats**

Schema:


const userSchema = new mongoose.Schema({

    price: { type: String },
    
    experience: { type: String },
    
    laborEmail: { type: String, required: true }
    
});
**Middleware**

**Auth Middleware**

Purpose: Validates JWT tokens for protected routes.


**Routes**

Index

Purpose: Imports and aggregates all route handlers for easy routing setup.

**Running the Project**

Start the server:


npm start

Access the API: The server will be running at http://localhost:5000 (or your specified port).

**License**

This project is licensed under the MIT License.
