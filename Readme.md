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
    "email": "admin@admin.com",
    "name": "Admin",
    "password": "password123",
    "passwordConfirm": "password123"
  }
  ```
- Response:
  ```json
  {
    "data": {
        "user": {
        "id": "<user_id>",
        "name": "Admin",
        "email": "admin@admin.com",
        "role": "user",
        "provider": "local",
        "created_at": "2023-08-11T13:12:30.5741+07:00",
        "updated_at": "2023-08-11T13:12:30.5741+07:00"
        }
    },
    "status": "success"
  }
  ```

2. **Login User**
- Method: `POST`
- URL: `/api/auth/login`
- Request Body:
  ```json
  {
    "email": "admin@admin.com",
    "password": "password123"
  }
  ```
- Response:
  ```json
  {
    "status": "success",
    "token": "<jwt_token>"
  }
  ```

3. **Logout User**
- Method: `GET`
- URL: `/api/auth/logout`
- Headers: `Authorization: Bearer <jwt_token>`
- Response:
  ```json
  {
    "status": "success"
  }
  ```

4. **Get Current User**
- Method: `GET`
- URL: `/api/users/me`
- Headers: `Authorization: Bearer <jwt_token>`
- Response:
  ```json
  {
    "data": {
        "user": {
        "id": "<user_id>",
        "name": "Admin",
        "email": "admin@admin.com",
        "role": "user",
        "provider": "local",
        "created_at": "2023-08-11T13:12:30.5741+07:00",
        "updated_at": "2023-08-11T13:12:30.5741+07:00"
        }
    },
    "status": "success"
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

