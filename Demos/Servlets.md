# Servlet

## WAR
JEE web applications are usually packaged as `.war` files, a web archive similar to a `.jar` but with some minor changes to folder heirarchy. A `src/main/webapp` folder becomes the root directory, and the archive is usually hosted on a Java web server such as **Apache Tomcat**. Be sure to set the `packaging` property in your `pom.xml` to `war`:
#### pom.xml
```xml
...
<packaging>war</packaging>
...
```

## Dependencies
To begin using Java Servlets, include the following dependency to your Maven `pom.xml`:
#### pom.xml
```xml
...
<groupId>javax.servlet</groupId>
<artifactId>servlet-api</artifactId>
<version>2.5</version>
...
```
`Servlet` is a JEE specification which is not included in Java's standard library, so it must be imported or the project must use a JDK with JEE libraries included already.

## Deployment Descriptor
A Java server like Tomcat will deploy a web archive and register all servlets according to the *deployment descriptor* found in `src/main/webapp/WEB-INF/web.xml`:
#### web.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://java.sun.com/xml/ns/javaee" xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd" version="2.5">

...

</web-app>
```
Servlets, Filters, Context parameters, and other configurations are declared and defined in the `web.xml` 

## Servlet Mapping
Servlet classes are registered in the `web.xml` by assigning a name to both a url mapping and the fully qualified class name of the Servlet:
#### web.xml
```xml
...
<servlet>
    <servlet-name>myServlet</servlet-name>
    <servlet-class>servlets.MyServlet</servlet-class>
</servlet>

<servlet-mapping>
    <servlet-name>myServlet</servlet-name>
    <url-pattern>/myServlet</url-pattern>
</servlet-mapping>
...
```
This will provide access to the servlet through its url mapping, in the above case at `http:[hostname]:[port]/[app-context]/myServlet`

## Servlet
The Servlet API provides the `HttpServlet` abstract class which can be extended to define your own custom behavior:
#### MyServlet.java
```java
package servlets;

import java.io.IOException;

import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

public class MyServlet extends HttpServlet {
	@Override
	protected void doGet(HttpServletRequest req, HttpServletResponse resp)
		throws ServletException, IOException {
            // Implements GET behavior
	}
	
	@Override
	protected void doPost(HttpServletRequest req, HttpServletResponse resp)
		throws ServletException, IOException {
            // Implements POST behavior
	}
}
```
The `HttpServletRequest` object provides useful methods such as `getParameter(String name)` which returns the value of a Query or post body parameter. `HttpServletResponse` provides a `getWriter()` method which returns a `PrintWriter` object to append data to the response body.

## Servlet 3+
More recent versions of the Servlet API offer convenience annotations that allows configuration in a decorator over the Servlet class itself, leaving the `web.xml` blank for the most part:

#### pom.xml
```xml
...
<groupId>javax.servlet</groupId>
<artifactId>javax.servlet-api</artifactId>
<version>3.0.1</version>
<scope>provided</scope>
...
```

#### MyServlet.java
```java
package servlets;

import java.io.IOException;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/myServlet")
public class MyServlet extends HttpServlet {
	protected void doGet(HttpServletRequest req, HttpServletResponse resp)
		throws ServletException, IOException {
            // Implements GET behavior
	}
}
```