# ToDo List API

ToDo List is a Java 17 Spring Boot REST API for creating users and managing
their tasks. Task requests use HTTP Basic Authentication, and task data is
stored through Spring Data JPA in an in-memory H2 database.

## Features

- Create users with unique usernames.
- Hash user passwords with BCrypt before persistence.
- Create tasks with a title, description, priority, start time, and end time.
- List the authenticated user's tasks.
- Update an existing task when it belongs to the authenticated user.
- Validate that task start and end times are in the future and ordered
  correctly.
- Return bad-request responses for malformed request bodies and common task
  errors.

This API currently exposes task creation, listing, and updating. It does not
expose a task deletion endpoint.

## Technology Stack

- Java 17
- Spring Boot 3.0.11
- Spring Web
- Spring Data JPA
- H2 Database
- Maven Wrapper (Maven 3.8.7)
- Lombok
- BCrypt
- Optional Docker image build

## Prerequisites

- JDK 17 or newer.
- Internet access on the first Maven build so the wrapper and project
  dependencies can be downloaded.
- Docker, only if you want to use the container workflow.

The repository includes `mvnw`, but it is not executable in the current
checkout. Use `sh mvnw ...` on Unix-like systems, or `mvnw.cmd ...` on Windows.

## Clone

```bash
git clone https://github.com/xfelipealves/todolist.git
cd todolist
```

## Build, Test, and Run

Build and install the application locally:

```bash
sh mvnw clean install
```

Run the automated tests:

```bash
sh mvnw test
```

Start the application from the project source:

```bash
sh mvnw spring-boot:run
```

The API listens on `http://localhost:8080` by default.

After a package build, the Spring Boot executable JAR is written to
`target/todolist-1.0.0.jar` and can be started with:

```bash
java -jar target/todolist-1.0.0.jar
```

### Docker

The repository includes a Dockerfile that builds and runs the same JAR:

```bash
docker build -t todolist .
docker run --rm -p 8080:8080 todolist
```

## API Overview

| Method | Endpoint | Authentication | Purpose |
| --- | --- | --- | --- |
| `POST` | `/users/` | None | Create a user. |
| `POST` | `/tasks/` | HTTP Basic | Create a task for the authenticated user. |
| `GET` | `/tasks/` | HTTP Basic | List tasks owned by the authenticated user. |
| `PUT` | `/tasks/{id}` | HTTP Basic | Update a task owned by the authenticated user. |

For task endpoints, send credentials using the standard HTTP Basic header,
for example:

```text
Authorization: Basic <base64(username:password)>
```

The H2 console is enabled at `http://localhost:8080/h2-console` during local
runs. The configured in-memory connection is `jdbc:h2:mem:todolist` with
username `admin` and password `admin`.

## Project Structure

```text
.
|-- .mvn/wrapper/              Maven Wrapper configuration and JAR
|-- src/main/java/             Application, controllers, models, filters, and repositories
|-- src/main/resources/        Runtime configuration
|-- src/test/java/             Spring Boot test source
|-- Dockerfile                 Container build definition
|-- mvnw, mvnw.cmd              Maven Wrapper launchers
`-- pom.xml                    Maven project and dependency configuration
```

The main Java packages are organized by responsibility:

- `user`: user model, repository, and registration controller.
- `task`: task model, repository, and task controller.
- `filter`: Basic Authentication filter for `/tasks/` requests.
- `errors`: controller advice for malformed request bodies.
- `utils`: helper used for partial task updates.

## Status and Testing

The repository is a runnable baseline application. Automated coverage is
currently limited to one `@SpringBootTest` context-load test. In this
checkout, `sh mvnw test` completes successfully with one test run and no
failures.

There is no CI configuration, API specification, migration setup, or production
database configuration in the repository.

## Limitations

- H2 is configured as an in-memory database, so data is lost when the
  application stops.
- The H2 console is enabled by default and should be reviewed before any
  externally reachable deployment.
- Task authentication is implemented with HTTP Basic Authentication; use HTTPS
  and review the authentication filter before production use.
- Task management has no delete endpoint.
- Automated tests cover application startup only, not the endpoint workflows.
- The Maven wrapper does not have the executable bit in the current checkout,
  so Unix users should invoke it through `sh` unless they set the bit locally.

## Contributing

Contributions are welcome through pull requests. Before opening a pull request,
run `sh mvnw test` and describe the behavior that changed. The repository does
not currently define a separate contribution guide or code of conduct.

## License

No `LICENSE` file or license declaration is present in this repository. Until a
license is added, reuse and distribution rights should be treated as
unspecified and should be clarified with the project owner.
