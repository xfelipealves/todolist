# ToDo List API

This project is a ToDo List API developed as part of an online Java course taught by Rocketseat.

## Features

- **Task Management**: Basic CRUD operations for managing tasks.
- **REST API**: API endpoints for creating, reading, updating, and deleting tasks.

## Technologies Used

- **Java**: Programming language.
- **Spring Boot**: Framework for building the API.
- **Maven**: Build automation tool.
- **Docker**: Containerization platform.
- **Lombok**: Reduces boilerplate code.
- **H2 Database Engine**: In-memory database for development and testing.

## Additional Implementations

- **User Data Security**: Implementing security measures for user data.
- **Exception Handling**: Robust error and exception management.
- **Backend Deployment**: Deploying the backend to a production environment.

## Folder Structure

- `.mvn/wrapper`: Maven wrapper files.
- `src`: Source code for the application.
- `.gitignore`: Git configuration file to ignore specific files.
- `Dockerfile`: Configuration file for Docker.
- `mvnw` and `mvnw.cmd`: Maven wrapper scripts.
- `pom.xml`: Maven project configuration file.

## How to Run

1. Clone the repository:
    ```bash
    git clone https://github.com/xfelipealves/todolist.git
    ```
2. Navigate to the project directory:
    ```bash
    cd todolist
    ```
3. Build the project using Maven:
    ```bash
    ./mvnw clean install
    ```
4. Run the application:
    ```bash
    ./mvnw spring-boot:run
    ```
5. The API will be accessible at:
    ```
    http://localhost:8080
    ```

## Status

This project was developed as part of an online Java course by Rocketseat, where the focus was on teaching how to create APIs in Java. The course credential can be found [here](https://app.rocketseat.com.br/certificates/6710f89f-566f-4c90-98de-3b9d37c2a52a).

## Contribution

Feel free to fork the project and submit pull requests. Suggestions and improvements are welcome!

## License

This project does not have a license.
