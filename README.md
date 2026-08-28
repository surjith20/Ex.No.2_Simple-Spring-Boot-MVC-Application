# Exp_2_Simple-Spring-Boot-MVC-Application

## AIM:
To develop a Simple Spring Boot MVC (Model-View-Controller) Application that uses a Controller to handle HTTP requests, a Model to pass data, and a View (Thymeleaf) to render dynamic HTML pages.

## ALGORITHM:
Create a New Spring Boot Project:

Use Spring Initializr

Add dependencies:

Spring Web

Thymeleaf

Set Up Project Structure:

Create the main class annotated with @SpringBootApplication

Create a Controller class using @Controller

Add HTML templates under src/main/resources/templates

Create a Controller:

Define a method to handle HTTP GET requests using @GetMapping

Return a view name (HTML page name) from the controller

Pass data to the view using Model object

Create a Model (Optional):

Define a simple POJO class if you need to pass structured data to the view

Create View Pages (HTML using Thymeleaf):

Create an HTML file inside the templates folder

Use Thymeleaf syntax (e.g., ${name}) to render dynamic content

Run the Application:

Run the Spring Boot application from your IDE or command line

Access the Application:

Open a browser and navigate to http://localhost:8080/
## PROGRAM

```

spring-mvc-demo/
├── src/
│   └── main/
│       ├── java/
│       │   └── com.example.mvc/
│       │       ├── MvcApplication.java
│       │       └── HomeController.java
│       └── resources/
│           ├── templates/
│           │   └── Welcome.html
│           └── application.properties
├── pom.xml

```

### pom.xml :
```
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>spring-mvc-demo</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <name>Spring MVC Demo</name>

    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>3.1.2</version>
    </parent>

    <dependencies>
        <!-- Spring Web -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <!-- Thymeleaf for View Rendering -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-thymeleaf</artifactId>
        </dependency>
    </dependencies>
</project>
```

### MvcApplication.java (Main Class):
```
package com.example.mvc;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class MvcApplication {
    public static void main(String[] args) {
        SpringApplication.run(MvcApplication.class, args);
    }
}

```
### HomeController.java (Controller):

```
package com.example.mvc;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.ui.Model;

@Controller
public class demoController {

    @GetMapping("/")
    public String test(Model model) {
        model.addAttribute("Greeting", "Welcome to thymeleaf");
        return "Welcome";
    }
}
```

### Welcome.html (View – inside src/main/resources/templates/):

```
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
    <meta charset="UTF-8">
    <title>Home</title>
    <link rel="stylesheet" th:href="@{style.css}">
</head>
<body>
<p id="demo"> Original Text</p>

<button onclick="showMessage()">Click Me</button>
<button onclick = "changeText()"> Change Text</button>
<script th:src="@{script.js}"></script>
<h1 th:text="${Greeting}">Welcome</h1>
</body>
</html>
```
### styles.css
```
body {
    background-color: lightblue;
}

h1 {
    color: darkblue;
}
```

### Script.js
```
function showMessage() {
    alert("Hello from JavaScript!");
}

function changeText() {
    const element = document.getElementById("demo");

    if (element) {
        element.innerHTML = "Text Changed!";
    } else {
        console.log("Element not found");
    }
}
```
### application.properties:
server.port=8080

# Thymeleaf configuration
spring.thymeleaf.prefix=classpath:/templates/
spring.thymeleaf.suffix=.html
spring.thymeleaf.mode=HTML
spring.thymeleaf.encoding=UTF-8
spring.thymeleaf.servlet.content-type=text/html

## Output:
<img width="1623" height="862" alt="1234" src="https://github.com/user-attachments/assets/929e41f5-d054-4e3d-a8ff-e14453333427" />

## Result:
A Simple Spring Boot MVC (Model-View-Controller) Application that uses a Controller to handle HTTP requests, a Model to pass data, and a View (Thymeleaf) to render dynamic HTML pages is developed.
