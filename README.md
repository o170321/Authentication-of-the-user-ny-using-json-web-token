# Authentication-of-the-user-ny-using-json-web-token

# Goodreads Clone

This is a simple Node.js application that serves as a basic clone of Goodreads, a popular platform for book lovers. It allows users to register, log in, and retrieve information about books. This README file provides an overview of the application and its functionality.

## Table of Contents

- [Features](#features)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [API Endpoints](#api-endpoints)
- [Security](#security)
- [Contributing](#contributing)
- [License](#license)

## Features

- User Registration: Users can create accounts by providing a username, name, password, gender, and location. Passwords are securely hashed before being stored in the database.
- User Login: Registered users can log in to the system using their username and password. Upon successful login, they receive a JSON Web Token (JWT) for authentication.
- Book Information: Users can access information about books, including their titles and other details.

## Prerequisites

Before running the application, you need to ensure that you have the following installed:

- Node.js
- SQLite
- Required Node modules (you can install them using `npm` or `yarn`)

## Getting Started

1. Clone the repository to your local machine:

   ```bash
   git clone https://github.com/your-username/goodreads-clone.git
   ```

2. Navigate to the project directory:

   ```bash
   cd goodreads-clone
   ```

3. Install the required Node modules:

   ```bash
   npm install
   ```

4. Initialize the SQLite database and start the server:

   ```bash
   node app.js
   ```

5. The server will start running at `http://localhost:3000/`. You can access the API endpoints as described in the next section.

## API Endpoints

### User Registration

- **URL:** `/users/`
- **Method:** `POST`
- **Description:** Register a new user by providing a username, name, password, gender, and location.
- **Request Body:**

```json
{
  "username": "your_username",
  "name": "Your Name",
  "password": "your_password",
  "gender": "Male/Female/Other",
  "location": "Your Location"
}
```

- **Response:** If registration is successful, it will return a message "User created successfully." If the user already exists, it returns a 400 status code and a message "User already exists."

### User Login

- **URL:** `/login/`
- **Method:** `POST`
- **Description:** Log in with your username and password to receive a JWT for authentication.
- **Request Body:**

```json
{
  "username": "your_username",
  "password": "your_password"
}
```

- **Response:** If login is successful, it returns a JWT token in the following format:

```json
{
  "jwtToken": "your_jwt_token"
}
```

### Get Books

- **URL:** `/books/`
- **Method:** `GET`
- **Description:** Retrieve information about all books in the system.
- **Authorization:** Include the JWT token obtained during login in the `Authorization` header.

- **Response:** Returns an array of book objects, each containing details about a book.

### Get Book by ID

- **URL:** `/books/:bookId/`
- **Method:** `GET`
- **Description:** Retrieve information about a specific book by providing its `bookId` in the URL.
- **Authorization:** Include the JWT token obtained during login in the `Authorization` header.

- **Response:** Returns details about the requested book.

## Security

This application uses JWT for user authentication, and passwords are securely hashed before being stored in the database. However, for production use, it is recommended to enhance security, implement HTTPS, and follow best practices.

## Contributing

Contributions to this project are welcome. Feel free to open issues, submit pull requests, and help improve the application.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
