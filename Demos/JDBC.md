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

# SQL CLI program
A demonstration of various JDBC methods
```java
String url = "jdbc:postgresql://host:port/database";
String username = "databaseuser"
String password = "password"
String sql;

// Connect to a Postgres instance and set Scanner to stdin
try (Connection connection = DriverManager.getConnection(url, username, password);
        Scanner scanner = new Scanner(System.in);) {
    // Loop after each user input
    while (true) {
        Statement statement = connection.createStatement();
        System.out.print("sql> ");
        sql = scanner.nextLine();
        if (sql.equalsIgnoreCase("quit"))
            break;

        // Statement.execute(String query) returns true if ResultSet
        boolean isResultSet = statement.execute(sql);
        if (isResultSet) {
            // Get and print column names from metadata
            ResultSet resultSet = statement.getResultSet();
            ResultSetMetaData rsmd = resultSet.getMetaData();
            for (int j = 1; j <= rsmd.getColumnCount(); j++) {
                System.out.print(rsmd.getColumnLabel(j) + "\t");
            }
            System.out.println();

            // Get and print column values from ResultSet
            while (resultSet.next()) {
                for (int i = 1; i <= rsmd.getColumnCount(); i++) {
                    System.out.print(resultSet.getString(i) + "\t");
                }
                System.out.println();
            }
            resultSet.close();
        } else {
            // If other DML, return rows affection
            System.out.println(statement.getUpdateCount() + " rows affected");
        } 				
        statement.close();
    }

} catch (SQLException e) {
    e.printStackTrace();
}
```