# Spring Boot Code 

## *** Edit: src/main/java/com/vcabading/PROJECTNAME/PROJECTNAME.java
```
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

/////////////////////////////////////////////////////////////////
//	PROJECTNAME
/////////////////////////////////////////////////////////////////

@SpringBootApplication
 class PROJECTNAME {
	public static void main(String[] args) {
		SpringApplication.run(FirstspringprojectApplication.class, args);
	}
}

```
---------------------------------------------------
## *** Create: src/main/java/com.vcabading.PROJECTNAME/HomeController.java
```
/////////////////////////////////////////////////////////////////
//	HOME CONTROLLER
/////////////////////////////////////////////////////////////////

@Controller
public class HomeController {
    @GetMapping("/")
    public String index(Model model) {
    	model.addAttribute("dojoName", "San Jose");
        return "index.jsp";
    }
}
```
---------------------------------------------------

## *** Dependency: add to pom.xml
```
<!-- SPRING BOOT DEPENDENCIES -->
<dependency>
        <groupId>org.apache.tomcat.embed</groupId>
        <artifactId>tomcat-embed-jasper</artifactId>
</dependency>
<dependency>
        <groupId>javax.servlet</groupId>
        <artifactId>jstl</artifactId>
</dependency>
<dependency>
    <groupId>org.webjars</groupId>
    <artifactId>webjars-locator</artifactId>
    <version>0.30</version>
</dependency>

<!-- BOOTSTRAP DEPENDENCIES -->
<dependency>
    <groupId>org.webjars</groupId>
    <artifactId>bootstrap</artifactId>
    <version>5.0.1</version>
</dependency>
<dependency>
    <groupId>org.webjars</groupId>
    <artifactId>jquery</artifactId>
    <version>3.6.0</version>
</dependency>
```
---------------------------------------------------

## *** Edit: src/main/resources/applications.properties
```
spring.mvc.view.prefix=/WEB-INF/
```
---------------------------------------------------

## *** Create: src/main/webapp/WEB-INF/index.jsp
```
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core"%>

<!--/////////////////////////////////////////////////////
//	INDEX JSP
///////////////////////////////////////////////////////// -->

<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- ---- CSS LINKS --------------------------------- -->
    <link rel="stylesheet" href="/webjars/bootstrap/css/bootstrap.min.css">
	<link rel="stylesheet" type="text/css" href="css/style.css">
	<title>TITLE</title>
</head>
<body>
    	<!-- //// HEADER //////// -->
	<header>
		<div class="navbar navbar-dark bg-dark box-shadow">
			<div class="container d-flex justify-content-between">
				<a href="/" class="navbar-brand d-flex align-items-center"> <strong
					class="text-warning">TITLE</strong>
				</a> <a class="btn btn-secondary " href="/">HOME</a>
			</div>
		</div>
	</header>

	<!-- //// MAIN AREA //////// -->
	<main role="main">
		<div class="container mt-4">


		</div>
	</main>


    <!-- ---- JAVASCRIPT LINKS ---------------------------- -->
    <script src="/webjars/jquery/jquery.min.js"></script>
    <script src="/webjars/bootstrap/js/bootstrap.min.js"></script>
    <script type="text/javascript" src="js/app.js"></script>
</body>
```
---------------------------------------------------
## *** Create: src/main/resources/static/css/style.css
```
/*/////////////////////////////////////////////////////////
//	STYLE CSS
///////////////////////////////////////////////////////////*/

body {
    background-color: black;
}

* {
    color: white;
}
```
---------------------------------------------------
## *** Create: src/main/resources/static/js/app.js
```
///////////////////////////////////////////////////////////
//	APP JAVASCRIPT
///////////////////////////////////////////////////////////

alert("Hello World");
```
---------------------------------------------------
## PROJECT: Run as Spring Boot App

Then check Local to see if index displayed

---------------------------------------------------
