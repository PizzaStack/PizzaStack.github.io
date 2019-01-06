# HTTP/HTML
Hypertext Transfer Protocol & Hypertext Markup Language, the two main technologies for a web browser. HTML provides a structure for static content on web pages. HTML documents are organized by element tags, some with attributes. Browsers don't display the element tags, but instead parse them to render content.

<html>
    <body>
        <p>Hello there!</p>
        <a src="www.google.com">Google</a>
    </body>
</html>

HTTP is all about sending and receiving documents. A document is abstracted from HTTP packet that has information like metadata, contents, status codes.

# JavaEE
Java Enterprise Edition, this is a community driven collection of Specifications, APIs and Frameworks which provide enterprise functionality. We will start with Java Servlets, a JavaEE API for communicating between a Java code base and HTTP.

Found in `javax.servlet` and `javax.http` the Servlet API provides a Servlet Interface which is implemented by the GenericServlet Abstract Class, then the HTTPServlet Abstract Class, and then finally allows you to extend the HTTPServlet.

In a normal servlet process:
- The client sends an HTTP Request to a (Servlet) Web Container, which is a Java Server that is running your application. We will be using Apache Tomcat, which is Apache's lightweight implementation of the JavaEE Server and Servlet Container spec.
- Your Tomcat server will have your application in its webapps folder (as a war, usually), and this application will have the following:
    - *src/*: for the servlet and other business logic code
    - *webapp/*: for any hosted HTML-related files, as well as:
    - **Deployment Descriptor**: commonly a *web.xml* file that maps incoming requests to your Servlets.
- Java application on Tomcat will handle Request as well as the Response by creating Java objects to model the Request/Response.

## Servlet Lifecycle
The Tomcat server will handle the control flow of your application through a servlet lifecycle process.
1. When a request comes in, the container instantiates any appropriate servlets
1. Once instantiated the container initializes the servlet by invoking its `init()` method
1. After initialization (or existing servlet is found), the container invokes `service()` to process the request.
    1. public void service (ServletRequest req, ServletResponse resp) {...} ->
    1. protected void service (HttpServletRequest req, HttpServletResponse resp) {...} ->
    1. protected void doGet (HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {...} //You write this
1. Response object is returned to client
1. When the container shuts down or needs to conserve memory or just because a servlet's stated lifespan is reached, the container will call the `destroy()` method of your servlet.

tl;dr Container calls init() once, service() many times, and eventually destroy() once.

## HTTP Status Codes
- 100-199: INFO
- 200-299: OK/Success
- 300-399: Redirect
- 400-499: Error/Request Incomplete
- 500-599: Server Error

## HTTP Methods (Verbs)
 - GET: retrieves information, sends info in the URL itself, empty body
>localhost:8080/ExampleContext/example?name="bob"

 - POST: Send info as text or binary in a body
 - PUT
 - DELETE
 - PATCH
 - UPDATE
 - TRACE
 - HEAD
 - OPTIONS