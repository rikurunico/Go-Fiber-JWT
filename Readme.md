# Go-Fiber-JWT API

This project is a Go-based API built using the Fiber framework with JWT authentication. It provides various endpoints for user authentication and interaction.

## Installation

1. Clone the repository: `git clone <repository_url>`
2. Navigate to the project directory: `cd go-fiber-jwt`
4. Run Docker Compose: `docker-compose up -d`

## Running the Application

1. Install the required dependencies: `go mod tidy`
2. Run the application: `go run main.go` or `air .` (for hot reloading)

## Endpoints

1. **Register User**
- Method: `POST`
- URL: `/api/auth/register`
- Request Body:
  ```json
  {
    "username": "your_username",
    "email": "your_email@example.com",
    "password": "your_password"
  }
  ```
- Response:
  ```json
  {
    "status": "success",
    "message": "User registered successfully"
  }
  ```

2. **Login User**
- Method: `POST`
- URL: `/api/auth/login`
- Request Body:
  ```json
  {
    "email": "your_email@example.com",
    "password": "your_password"
  }
  ```
- Response:
  ```json
  {
    "status": "success",
    "message": "Login successful",
    "data": {
      "token": "<jwt_token>"
    }
  }
  ```

3. **Logout User**
- Method: `GET`
- URL: `/api/auth/logout`
- Headers: `Authorization: Bearer <jwt_token>`
- Response:
  ```json
  {
    "status": "success",
    "message": "Logout successful"
  }
  ```

4. **Get Current User**
- Method: `GET`
- URL: `/api/users/me`
- Headers: `Authorization: Bearer <jwt_token>`
- Response:
  ```json
  {
    "status": "success",
    "data": {
      "user": {
        "id": 1,
        "username": "your_username",
        "email": "your_email@example.com"
      }
    }
  }
  ```

5. **Health Checker**
- Method: `GET`
- URL: `/api/healthchecker`
- Response:
  ```json
  {
    "status": "success",
    "message": "Welcome to Golang, Fiber, and GORM"
  }
  ```

6. **Fallback (Not Found)**
- Method: `ALL`
- URL: `/*`
- Response:
  ```json
  {
    "status": "fail",
    "message": "Path: <requested_path> does not exist on this server"
  }
  ```

## Note

- Replace `<your_database_url>` with your actual database connection URL.
- Replace `<your_secret_key>` with a secure secret key for JWT authentication.
- Replace `<jwt_token>` with the actual JWT token received after successful login.

Make sure to adjust the documentation as needed for your project's actual implementation and requirements.

