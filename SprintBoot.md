# Spring Boot Code 

1. New Spring Starter Project
```
Type: Maven Project
Packaging: War
Java version: 8
Add dependemcies: Spring Boot DevTools, Spring Data JPA, MySQL Driver, Spring Web 
```
2. Create DB Schema on MySQL Workbench using Charset: UTF-8

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
    public String index() {
        return "index.jsp";
    }
}
```
---------------------------------------------------

## *** Dependency: add to pom.xml
```
<!-- DEPENDENCIES FOR STARTING SPRING PROJECTS-->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-devtools</artifactId>
    <scope>runtime</scope>
    <optional>true</optional>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-tomcat</artifactId>
    <scope>provided</scope>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-test</artifactId>
    <scope>test</scope>
</dependency>
<!-- DEPENDENCIES FOR DISPLAYING JSPS AND USING JSTL TAGS -->
<dependency>
    <groupId>org.apache.tomcat.embed</groupId>
    <artifactId>tomcat-embed-jasper</artifactId>
</dependency>
<dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>jstl</artifactId>
</dependency>
<!-- DEPENDENCIES FOR INTEGRATING SQL DATABASE AND USING JPA -->
<!-- Note: Project will not run until a schema has been created and the 
    proper settings in application properties are present for 
    connecting to a database. -->
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <scope>runtime</scope>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
<!-- DEPENDENCY FOR USING VALIDATION ANNOTATIONS -->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-validation</artifactId>
</dependency>
<!-- DEPENDENCY FOR USING BCRYPT  -->
<dependency>
    <groupId>org.mindrot</groupId>
    <artifactId>jbcrypt</artifactId>
    <version>0.4</version>
</dependency>
<!-- DEPENDENCIES FOR BOOTSTRAP -->
<dependency>
    <groupId>org.webjars</groupId>
    <artifactId>webjars-locator</artifactId>
    <version>0.30</version>
</dependency>
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
spring.datasource.url=jdbc:mysql://localhost:3306/<<YOUR_SCHEMA_NAME>>
spring.datasource.username=root
spring.datasource.password=root
spring.jpa.hibernate.ddl-auto=update
spring.mvc.hiddenmethod.filter.enabled=true
```
---------------------------------------------------

## *** Create: src/main/webapp/WEB-INF/index.jsp
```
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c"%>                          <!-- c:out ; c:forEach etc. -->
<%@taglib uri="http://java.sun.com/jsp/jstl/fmt" prefix="fmt"%>                         <!-- Formatting (dates) -->
<%@ taglib prefix="form" uri="http://www.springframework.org/tags/form"%>               <!-- form:form -->
<%@ page isErrorPage="true" %>                                                          <!-- for rendering errors on PUT routes -->

<!--/////////////////////////////////////////////////////
//	INDEX JSP
///////////////////////////////////////////////////////// -->

<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- //// CSS LINKS //////////////////////////////////////// -->
    <link rel="stylesheet" href="/webjars/bootstrap/css/bootstrap.min.css">
	<link rel="stylesheet" type="text/css" href="/css/style.css">
	<title>TITLE</title>
</head>
<body>
    <!-- //// HEADER /////////////////////////////////////////// -->
	<header>
		<div class="navbar navbar-dark bg-dark box-shadow">
			<div class="container d-flex justify-content-between">
				<a href="/" class="navbar-brand d-flex align-items-center"> <strong
					class="text-warning">TITLE</strong>
				</a> <a class="btn btn-secondary " href="/">HOME</a>
			</div>
		</div>
	</header>

	<!-- //// MAIN AREA //////////////////////////////////////// -->
	<main role="main">
		<div class="container mt-4">

		</div>
	</main>


    <!-- //// JAVASCRIPT LINKS ///////////////////////////////// -->
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
```
---------------------------------------------------
## PROJECT: Run as Spring Boot App

Then check Local to see if index displayed

---------------------------------------------------
## Set Up Repository 
```
import java.util.List;

import org.springframework.data.repository.CrudRepository;
import org.springframework.stereotype.Repository;

import com.vcabading.dojosandninjas.models.Dojo;

////////////////////////////////////////////////////////////////
//	DOJO REPOSITORY
////////////////////////////////////////////////////////////////

@Repository
public interface DojoRepository extends CrudRepository<Dojo, Long> {

	//	---- Retrieves all books -------------------------------
	List<Dojo> findAll();
}
```

----------------------------------------------------
## Set Up Service
```
/////////////////////////////////////////////////////
// 	DOJO SERVICE
/////////////////////////////////////////////////////

@Service
public class DojoService {
	
	//	//// FIELDS /////////////////////////////////
	
	@Autowired
	DojoRepository dojoRepo;
	
	//	//// CREATE /////////////////////////////////
	
	//	---- Create a Dojo --------------------------
	public Dojo create(Dojo dojo) {
		return this.dojoRepo.save(dojo);
	}
	
	//	//// RETRIEVE ///////////////////////////////
	
	//	---- Retrieve All ---------------------------
	public List<Dojo> retrieveAll() {
		return this.dojoRepo.findAll();
	}
	
	//	---- Retrieve Dojo by ID --------------------
	public Dojo retrieveDojo(Long id) {
		Optional<Dojo> optDojo = this.dojoRepo.findById(id);
		if ( optDojo.isPresent() ) {
			return optDojo.get();			
		} else {
			return null;
		}
	}
	
	//	//// UPDATE /////////////////////////////////
	
	public Dojo update(Dojo dojo) {
		Optional<Dojo> optDojo = this.dojoRepo.findById(dojo.getId());
		if ( optDojo.isPresent() ) {
			return this.dojoRepo.save(dojo);
		} else {
			return null;
		}
	}
	
	//	//// DELETE /////////////////////////////////
	
	public void delete(Long id) {
		this.dojoRepo.deleteById(id);
	}
}
```