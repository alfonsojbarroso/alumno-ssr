# Alumno SSR

A small server-side-rendered web application built with Spring Boot and Thymeleaf. The home page is rendered on the server and displays a list of technologies supplied by a Spring MVC controller. The project also includes a web app manifest and a basic service worker.

## Requirements

- Java 21
- No separate Maven installation is required; the project includes the Maven Wrapper.

## Run the application

From the project directory, use the wrapper for your operating system:

```bash
# macOS / Linux
./mvnw spring-boot:run
```

```powershell
# Windows PowerShell
.\mvnw.cmd spring-boot:run
```

The application starts at [http://localhost:8080](http://localhost:8080). The home page is served at `/`.

Alternatively, the included `run.sh` script starts the app on macOS or Linux:

```bash
./run.sh
```

## Build and test

Run the test suite:

```bash
./mvnw test
```

On Windows, use `.\mvnw.cmd test`.

Package the application as an executable JAR:

```bash
./mvnw package
```

The JAR is created in `target/` and can be run with:

```bash
java -jar target/alumno-ssr-0.0.1-SNAPSHOT.jar
```

## Application behavior

`HomeController` handles `GET /`, adds a page heading and a list of sample technologies to the model, and returns the `index` Thymeleaf template. The template renders the heading and list on the server.

The current sample list is Java, Spring Boot, PWA, SW, and Js. There are no student records, database integration, or create/update/delete endpoints in this project.

## Progressive web app files

- `src/main/resources/static/manifest.json` provides the web app name, display mode, start URL, and theme colors.
- `src/main/resources/static/sw.js` registers a service worker that caches `/` and `/css/styles.css` during installation and checks the cache before making a network request.
- The page registers the service worker when the browser supports it.

The manifest references `/images/icon-192.png`; add that image under `src/main/resources/static/images/` if you want the configured app icon to be available.

## Project structure

```text
src/
├── main/
│   ├── java/com/alumno/ssr/
│   │   ├── AlumnoSsrApplication.java
│   │   └── controller/HomeController.java
│   └── resources/
│       ├── application.properties
│       ├── static/
│       │   ├── css/styles.css
│       │   ├── manifest.json
│       │   └── sw.js
│       └── templates/index.html
└── test/java/com/alumno/ssr/
    └── AlumnoSsrApplicationTests.java
```

## Configuration

The application name is set to `alumno-ssr` in `src/main/resources/application.properties`. Spring Boot's default web server port is used (8080).


## Author

Dr. Alfonso José Barroso Barajas