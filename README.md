# TodoList API

This is an Express API for managing users and todo lists, with MySQL as the database. (Workshop CodeCamp15)

## Table of Contents

- [TodoList API](#todolist-api)
  - [Table of Contents](#table-of-contents)
  - [Features](#features)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Environment Variables](#environment-variables)
  - [API Endpoints](#api-endpoints)

## Features

- User registration and authentication
- JWT authentication
- CRUD operations for todo lists

## Prerequisites

- [Node.js](https://nodejs.org/)
- [MySQL](https://www.mysql.com/)

## Installation

1. Clone the repository:

    ```sh
    git clone https://github.com/your-username/todolist-api.git
    cd todolist-api
    ```

2. Install dependencies:

    ```sh
    npm install
    npm install sequelize-cli -g
    ```
3. Create Database
  
   ```sh
   sequelize-cli db:create
   ```

## Environment Variables

Create a `.env` file in the root directory and add the following environment variables:

```plaintext
PORT = 8000
SECRET_OR_KEY = your_jwt_secret
```


## API Endpoints

### User Endpoints
  - Register User
    #### POST /users/register
    - Request Body:
    ```json
        {
          "username": "exampleUser",
          "password": "examplePassword",
          "name": "Example Name"
        }
    ```
  - Login User
    #### POST /users/login
    - Request Body:
    ```json
        {
          "username": "exampleUser",
          "password": "examplePassword",
        }
    ```

    ### TodoList Endpoints
  - Get Todo List
    #### GET /todo-list
    - Headers: **`Authorization: Bearer jwt_token`**
    - Responses:
      - **`200 OK`**: Returns the list of todo items.
  - Get Todo List
    #### POST /todo-list
    - Headers: **`Authorization: Bearer jwt_token`**
    - Request Body:
    ```json
        {
          "task": "New Task"
        }
    ```
  - Delete Todo List
    #### POST /todo-list/:id
    - Headers: **`Authorization: Bearer jwt_token`**
    - Responses:
      - **`204 No Content`**
      - **`404 Not Found`**: Todo list not found.
  - Update Todo List
    #### PUT /todo-list/:id
    - Headers: **`Authorization: Bearer jwt_token`**
    - Request Body:
    ```json
        {
          "task": "Update new task"
        }
    ```
    - Responses:
      - **`200 OK`**: Updating is success.
      - **`404 Not Found`**: Todo list not found.
