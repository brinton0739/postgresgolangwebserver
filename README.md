# Golang CRUD Web Server with PostgreSQL

## Introduction

This project is a simple CRUD (Create, Read, Update, Delete) web server implemented in Golang, with a PostgreSQL database for storage. It demonstrates how to build a RESTful API using Go and Gorilla Mux, and how to interact with a PostgreSQL database. The server supports basic CRUD operations on a `users` table.

## Table of Contents

1. [Features](#features)
2. [Prerequisites](#prerequisites)
3. [Installation](#installation)
4. [Usage](#usage)
5. [API Endpoints](#api-endpoints)
6. [Running Tests](#running-tests)
7. [Contributing](#contributing)
8. [License](#license)

## Features

- **Create User**: Add a new user to the database.
- **Read User**: Retrieve user details by ID.
- **Update User**: Modify existing user details by ID.
- **Delete User**: Remove a user from the database by ID.

## Prerequisites

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Installation

1. **Clone the repository:**

    ```sh
    git clone https://github.com/yourusername/golang-crud-webserver.git
    cd golang-crud-webserver
    ```

2. **Create the `init.sql` file:**

    ```sql
    CREATE TABLE users (
        id SERIAL PRIMARY KEY,
        name VARCHAR(100),
        email VARCHAR(100)
    );
    ```

3. **Ensure the project directory structure is as follows:**

    ```
    golang-crud-webserver/
    ├── Dockerfile
    ├── docker-compose.yml
    ├── go.mod
    ├── go.sum
    ├── init.sql
    └── main.go
    ```

4. **Build and run the containers:**

    ```sh
    docker-compose up --build
    ```

    This command will build the Docker images and start the containers for the application and PostgreSQL database.

## Usage

### Accessing the API

The web server runs on `http://localhost:8080`. You can interact with the API using tools like `curl` or [Postman](https://www.postman.com/).

### Example `curl` Commands

1. **Create a User:**

    ```sh
    curl -X POST -H "Content-Type: application/json" -d '{"name":"John Doe", "email":"john@example.com"}' http://localhost:8080/users
    ```

2. **Get a User:**

    ```sh
    curl http://localhost:8080/users/1
    ```

3. **Update a User:**

    ```sh
    curl -X PUT -H "Content-Type: application/json" -d '{"name":"Jane Doe", "email":"jane@example.com"}' http://localhost:8080/users/1
    ```

4. **Delete a User:**

    ```sh
    curl -X DELETE http://localhost:8080/users/1
    ```

## API Endpoints

### 1. Create a User

- **URL:** `/users`
- **Method:** `POST`
- **Body:**
    ```json
    {
        "name": "John Doe",
        "email": "john@example.com"
    }
    ```
- **Response:**
    ```json
    {
        "id": 1,
        "name": "John Doe",
        "email": "john@example.com"
    }
    ```

### 2. Get a User

- **URL:** `/users/{id}`
- **Method:** `GET`
- **Response:**
    ```json
    {
        "id": 1,
        "name": "John Doe",
        "email": "john@example.com"
    }
    ```

### 3. Update a User

- **URL:** `/users/{id}`
- **Method:** `PUT`
- **Body:**
    ```json
    {
        "name": "Jane Doe",
        "email": "jane@example.com"
    }
    ```
- **Response:**
    ```json
    {
        "id": 1,
        "name": "Jane Doe",
        "email": "jane@example.com"
    }
    ```

### 4. Delete a User

- **URL:** `/users/{id}`
- **Method:** `DELETE`
- **Response:** `204 No Content`

## Running Tests

Currently, this project does not include automated tests. You can test the API manually using `curl` commands or Postman as described in the [Usage](#usage) section.

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request with your changes. Ensure your code adheres to the existing style and includes appropriate documentation.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
