# Spring Web MVC
Spring's web framework is built on the Servlet API and deployed on its own embedded Servlet container. Centered around its Dispatcher Servlet, Spring MVC handles much of the complexity of the request-response cycle.

## MVC Design Pattern
- Model: The data being passed, rendered, and manipulated
- View: What will be displayed, usually as html
- Controller: Handles logic, routing

## Spring MVC Request-Response Flow
1. Request sent to `DispatcherServlet`
1. `DispatcherServlet` calls `HandlerMapping` for help with request URI
1. `HandlerMapping` looks up the handler for the URI, a registered `Controller` which is returned to the `DispatcherServlet` and called
1. `Controller` is the entry-point for an event in and out of the rest of the program
1. `Controller` returns a `View` name & `Model` to the `DispatcherServlet`
1. `DispatcherServlet` consults `ViewResolver` to interpret `View` name as a template file and weave the `Model` into the response body
1. Response sent to client


## DispatcherServlet
Spring MVC's front controller has its own WebApplicationContext, allowing it to handle more bean scopes than singleton and prototype. It manages Controllers, HandlerMapping, ViewResolver, and all other components.

## HandlerMapping
While configurable using `RequestMappingHandlerMapping` objects, it can be simply enabled using a `<mvc:@annotation-driven/>` element tag in configuration, allowing for component scanning to automatically register all @Controller and similar beans along with their mappings. It is responsible for routing requests to specific methods within these controllers.

## Controllers
A `@Controller` stereotype annotation registers a class as a library of methods mapped to URI paths to handle requests. Several related annotations help to further specify these requests and their expected responses.

- `@RequestMapping` specifies the URI with attributes like value for the path and method for the HTTP verb, and can be defined at the class or method level.
- `@GetMapping` is a shorthand form of a `@RequestMapping` with GET assumed as its method. Also has siblings in `@PostMapping` and similar annotations.
- `@RequestParam` can be used on method parameters to bind form or query attributes to arguments.
- `@PathVariable` can be used on method parameters to bind URI path variables to arguments.
- `@ResponseBody` tags a method (or all methods of a class) to write their return objects directly to the response body, skipping the ViewResolver entirely.

## ViewResolver
ViewResolvers handle server-side view resolution for static HTML/CSS/JS files, or rendering for dynamic templates like JSPs or Thymeleaf files. 