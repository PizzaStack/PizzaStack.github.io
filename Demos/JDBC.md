# JDBC API
Java Database Connectivity (JDBC) is an API for connecting to a RDBMS such as Oracle, PostgreSQL, or MySQL. As a collection of interfaces it requires a driver from the database vendor on the classpath. Once added, a `java.sql.Connection` is used to send SQL queries with `java.sql.Statement`, `java.sql.PreparedStatement`, or `java.sql.CallableStatement` objects, and retrieve result sets in `java.sql.ResultSet` objects.

```java
// Loading the driver may not be necessary, but it's good to specify
try {
    Class.forName("org.postgresql.Driver");
} catch (java.lang.ClassNotFoundException e) {
    System.out.println(e.getMessage());
}

// Pay attention to the url pattern
String url = "jdbc:postgresql://host:port/database";
String username = "databaseuser"
String password = "password"

try (
    // Be sure to close all connections after use
    Connection connection = DriverManager.getConnection(url, username, password);
    Statement statement = connection.createStatement();
){
    // executeUpdate() returns the number of rows affected for DML
    int rowCount = statement.executeUpdate("insert into pizza values (1, 'cheese')");

    // executeQuery() returns a ResultSet object for queries
    ResultSet pizzas = statement.executeQuery("select * from pizza");

    // Loop through ResultSet for each row returned
    while(pizzas.next()) {
        System.out.println(pizzas.getInt("id"));
        System.out.println(pizzas.getString("flavor"));
    }

} catch (SQLException ex) {
    
} 
```

# Password credentials
Hardcoding url, username, and password is not secure, especially once your source code is pushed to public repositories online. An alternative is to save your information to a properties file:

### connection.properties
```
url = jdbc:postgresql://host:port/database
username = databaseuser
password = password
```

Then, in your Java application, load in the properties using `java.util.Properties`
```java
Properties properties = new Properties();
properties.load(new FileInputStream("connection.properties"));

String url = properties.getProperty("url");
String username = properties.getProperty("username");
String password = properties.getProperty("password");
```
Then simply remember to never add your `connection.properties` file to your git repository.