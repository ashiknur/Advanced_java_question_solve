### <div align = center> Answer to Question No 1</div>

#### a) Is Java a pure OOP? Explain your opinion?
  - Java is not considered a pure Object-Oriented Programming (OOP) language. While it embodies many OOP concepts such as inheritance, encapsulation, polymorphism, and abstraction, Java does not strictly adhere to all OOP principles. For instance, it supports primitive data types (like int, char, etc.) that are not objects, which is a deviation from the pure OOP paradigm where everything is supposed to be an object.

#### b) What is ‘DAO’, Why do we need DAO in web applications?
  - **DAO (Data Access Object):** DAO is a design pattern used in software engineering to provide an abstract interface to some type of database or other persistence mechanism. It separates the application's business logic from the data access code, making the code more modular and maintainable. 
  - **Why we need DAO in web applications:** 
    - **Abstraction:** DAO provides an abstraction layer, allowing the application to interact with the data access layer without being concerned with the specific details of the underlying database. 
    - **Maintainability:** By separating data access logic from business logic, changes to the database schema or technology can be isolated within the DAO implementation. 
    - **Testability:** DAOs can be easily mocked or replaced with test implementations during unit testing, facilitating testing of the business logic independently of the database. 

#### c) How Do You Trigger Garbage Collection From Java Code?
  - In Java, garbage collection cannot be triggered directly. The System.gc() method suggests that the JVM performs garbage collection, but it is not guaranteed. Garbage collection is managed by the JVM itself, which decides when to perform it based on its own algorithms and heuristics.

#### d) What are the JDBC API components?
  - JDBC (Java Database Connectivity) API components include:
    - **DriverManager:** Manages a list of database drivers.
    - **Connection:** Represents a connection with a database.
    - **Statement:** Used for executing a static SQL statement.
    - **PreparedStatement:** Inherits from Statement, used for executing pre-compiled SQL statements.
    - **ResultSet:** Represents the result set of a query.
    - **SQLException:** Handles any SQL errors that occur in the database communication process.


#### e) In a web application "**StringBuilder**" or “**StringBuffer**” which item should we use, why?
- In a web application, it's generally recommended to use **StringBuilder** over **StringBuffer** for performance reasons unless synchronization is explicitly needed. 
- **StringBuilder** is not synchronized, making it more efficient in a single-threaded environment. In a web application, where multiple threads may be handling different requests concurrently, synchronization might not be necessary in most cases. 
- **StringBuffer** is synchronized, which means it is thread-safe. If you are working in a multithreaded environment and need thread safety, you might choose **StringBuffer**. 
- However, if thread safety is not a concern, **StringBuilder** is preferred due to its 
better performance. 

### <div align = center><br/><br/><br/>Answer to Question No 2</div>

#### a) What is the difference between Get and Post method?
Both GET and POST are HTTP methods used to submit data to a web server, but they 
differ in how they do it: 
- **GET Method:** 
  - Parameters are included in the URL. 
  - Limited data can be sent, as the data is part of the URL. 
  - Data is visible to the user (in the URL). 
  - It is less secure for sensitive information. 
  - Cached by the browser. 
  - Generally used for requests that do not change server state. 
- **POST Method:** 
  - Parameters are included in the request body. 
  - Can send a larger amount of data. 
  - Data is not visible in the URL. 
  - More secure for sensitive information. 
  - Not cached by the browser. 
  - Generally used for requests that may change server state. 

#### b) Write a Java code to connect with MySQL database.

  - Here is a basic example of Java code to connect to a MySQL database:
    ```Java
    import java.sql.Connection;
    import java.sql.DriverManager;
    import java.sql.SQLException;
    
    public class Main {
        public static void main(String[] args) {
            String url = "jdbc:mysql://localhost:3306/myDatabase";
            String user = "username";
            String password = "password";
    
            try {
                Connection conn = DriverManager.getConnection(url, user, password);
                System.out.println("Connected to the database!");
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
    }
    ```
  

#### c) Why should we use JDBC?
Java Database Connectivity (JDBC) is a standard Java API that provides a way to interact with relational databases. Here are some reasons to use JDBC: 
- **Database Connectivity:** JDBC provides a standard interface for connecting Java 
applications with relational databases. 
- **Database Independence:** It allows the development of database-independent applications. You can switch databases by changing the JDBC driver without changing the application code. 
- **Transaction Management:** JDBC supports transaction management, allowing you to group multiple SQL statements into a single transaction. 
- **Dynamic SQL Generation:** JDBC allows the generation of SQL statements dynamically, which is useful for building flexible database applications. 
- **Portability:** JDBC is a part of the Java Standard Edition (SE) platform, making it a portable solution for database access in Java applications. 


#### d) Write a Java program to illustrate "Constructor Overloading”.
  - Example of constructor overloading in Java:
    ```Java
    public class MyClass {
        private int x;
        private int y;
    
        // Constructor with one parameter
        public MyClass(int x) {
            this.x = x;
        }
    
        // Constructor with two parameters
        public MyClass(int x, int y) {
            this.x = x;
            this.y = y;
        }
    
        public static void main(String[] args) {
            MyClass obj1 = new MyClass(5);
            MyClass obj2 = new MyClass(5, 10);
        }
    }
    ```


#### e) Describe Strong, Weak, Soft, and Phantom References and Their Role in Garbage Collection?
  - **Strong Reference:** The default type of reference in Java. An object with a strong reference is not eligible for garbage collection.
  - **Weak Reference:** An object is weakly referenced when it is referenced only by weak references. It can be garbage collected at any time when there are no strong or soft references.
  - **Soft Reference:** An object with soft references is collected only if the JVM needs memory. Soft references are kept more aggressively than weak references but less than strong references.
  - **Phantom Reference:** The weakest level of reference. An object is phantomly referenced after it has been finalized and before its allocated memory is reclaimed. Phantom references are useful for scheduling pre-mortem cleanup actions in a more flexible way than is possible with finalization.




### <div align = center><br/><br/><br/>Answer to Question No 3</div>

#### a) What is multithreading? In how many ways Java implements multithreading? Explain one of these ways with a suitable example.
  - Multithreading is a Java feature that allows concurrent execution of two or more parts of a program for maximum utilization of CPU. Java implements multithreading primarily in two ways: by extending the Thread class or by implementing the Runnable interface.
    Example using Runnable:
    ```Java
    public class MyRunnable implements Runnable {
        public void run() {
            System.out.println("Thread is running.");
        }
    
        public static void main(String args[]) {
            MyRunnable myRunnable = new MyRunnable();
            Thread thread = new Thread(myRunnable);
            thread.start();
        }
    }
    ```


#### b) “A Java class can be used both as an applet as well as an application” - Support this statement with an example.
  - A Java class can indeed be structured to serve both as an applet and an application. This is achieved by defining both a main method (for application use) and an init method (for applet use). For example:
    ```Java
    import java.applet.Applet;
    import java.awt.Graphics;
    
    public class DualPurposeClass extends Applet {
        public void init() {
            // Applet initialization code
        }
    
        public void paint(Graphics g) {
            // Applet display code
            g.drawString("This is an Applet or an Application", 20, 20);
        }
    
        public static void main(String[] args) {
            // Application execution code
            System.out.println("Running as an Application");
        }
    }
    ```


#### c) What do you mean by static class and static method? Can we make an instance of an abstract class? Justify your answer with an example?
  - **Static Class:** A static class is a class that is nested inside another class and marked with the static keyword. It can be instantiated without creating an instance of the outer class.
  - **Static Method:** A static method belongs to the class rather than the instance of a class. It can be invoked without creating an instance of the class.
  - **Abstract Class Instance:** You cannot instantiate an abstract class directly. However, you can instantiate a subclass that implements the abstract methods of the abstract class. For example:
  ```Java
  abstract class AbstractExample {
      abstract void display();
  }
  
  public class SubClass extends AbstractExample {
      void display() {
          System.out.println("Abstract method implemented");
      }
  
      public static void main(String args[]) {
          AbstractExample obj = new SubClass();
          obj.display();
      }
  }
  ```

### <div align = center><br/><br/><br/>Answer to Question No 4</div>

#### a) Design an Interface Called Shape
- **Interface**: `Shape`
  - **Method**:
    - `getArea()`: A method to calculate the area of the shape.

- **Implementation**:
  - **Classes**: `Circle` and `Rectangle` implement `Shape`.
  - **Circle**: Computes the area using the formula πr².
  - **Rectangle**: Computes the area using the formula length × breadth.

- **Java Program**:
  ```java
  interface Shape {
      double getArea();
  }

  class Circle implements Shape {
      private double radius;

      public Circle(double radius) {
          this.radius = radius;
      }

      public double getArea() {
          return Math.PI * radius * radius;
      }
  }

  class Rectangle implements Shape {
      private double length;
      private double breadth;

      public Rectangle(double length, double breadth) {
          this.length = length;
          this.breadth = breadth;
      }

      public double getArea() {
          return length * breadth;
      }
  }

  public class ShapeDemo {
      public static void main(String[] args) {
          Shape circle = new Circle(5);
          System.out.println("Area of Circle: " + circle.getArea());

          Shape rectangle = new Rectangle(4, 5);
          System.out.println("Area of Rectangle: " + rectangle.getArea());
      }
  }
  ```



#### b) Access Modifiers in Java
**Java has four access modifiers:**
- **public:**
  - Scope: Everywhere.
  - Result: Classes, methods, or fields accessible from any other class.
- **protected:**
  - Scope: Within the same package and subclasses.
  - Result: Methods and fields are accessible within the same package and by subclasses.
- **default (no modifier):**
  - Scope: Within the same package.
  - Result: Classes, methods, or fields are accessible only within the same package.
- **private:**
  - Scope: Within the same class.
  - Result: Methods and fields are accessible only within the class they are declared.

#### c) Differentiate Between Components and Containers in AWT
- **Components:**
  - Components are the basic building blocks of a GUI application.
  - Examples include buttons, text fields, labels, etc.
  - They represent elements that a user interacts with.
- **Containers:**
  - Containers hold components and arrange them in a specific layout.
  - They are used to group related components together.
  - Examples include Panel, Frame, and Dialog.

### <div align = center><br/><br/><br/>Answer to Question No 5</div>

#### a) Java Program with Exception Handling
```Java
public class Main {
    public static void main(String[] args) {
        try {
            int a = 5, b = 0;
            int result = a / b;
            System.out.println("Result: " + result);
        } catch (ArithmeticException e) {
            System.out.println("Error: Division by zero.");
        }
    }
}
```
#### b) JDBC Program for Searching an Attribute
```Java
// This is a simplified version. Actual implementation may require more details.
import java.sql.*;

public class SearchStudent {
    public static void main(String[] args) {
        String url = "jdbc:mysql://localhost:3306/your_database";
        String user = "username";
        String password = "password";
        String rollNumber = "your_roll_number";

        try {
            Connection conn = DriverManager.getConnection(url, user, password);
            String query = "SELECT * FROM students WHERE roll_number = ?";
            PreparedStatement stmt = conn.prepareStatement(query);
            stmt.setString(1, rollNumber);
            ResultSet rs = stmt.executeQuery();
            
            while (rs.next()) {
                // Assuming the table has name, age, etc.
                System.out.println("Name: " + rs.getString("name"));
                System.out.println("Age: " + rs.getInt("age"));
                // More fields can be added as needed
            }
            stmt.close();
            conn.close();
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```
#### c) Lifecycle of an Applet
An Applet has the following lifecycle stages:
  - **Initialization (init):**
    - The applet is initialized. This method is called once.
  - **Starting (start):**
     - The applet is started. Called after the init method and each time the applet is restarted.
  - **Painting (paint):**
    - The applet paints its content. Called when the applet needs to display or refresh its output.
  - **Stopping (stop):**
    - The applet is stopped. Called when the browser moves away from the page containing the applet.
  - **Destruction (destroy):**
    - The applet is destroyed. This is the final stage, cleaning up resources. Called when the browser shuts down normally.

### <div align = center><br/><br/><br/>Answer to Question No 6</div>

#### a) MVC Design Pattern and HTTP as a Stateless Protocol
  1. **MVC Design Pattern:**
     MVC stands for Model-View-Controller. It's a design pattern widely used in software development for organizing code in a manner that separates concerns, thus making it more modular and manageable.
      - **Model:** Represents the data and the business logic of the application. It's responsible for retrieving, processing, and storing data.
      - **View:** Represents the UI components. The View displays data from the Model to the user and sends user commands (like button clicks) to the Controller.
      - **Controller:** Acts as an interface between Model and View. It processes all the business logic and incoming requests, manipulates data using the Model, and interacts with the View to render the final output.
  MVC allows for efficient code reuse and parallel development, enhancing scalability and maintainability of applications.
  
  2. **HTTP as a Stateless Protocol:**
  HTTP (HyperText Transfer Protocol) is the foundational protocol used by the World Wide Web. It is stateless, meaning each request from a client to a server is treated as new, with no memory of previous interactions.
      - This statelessness implies that every HTTP request happens in isolation. The server doesn't retain session information between different requests from the same user.
      - To manage state, mechanisms like cookies, sessions, and tokens are used. These are not part of the HTTP protocol itself but are built on top of it.
#### b) RMI in JAVA and Its Architecture
  1. **RMI in JAVA:**
    RMI stands for Remote Method Invocation. It's a Java API that allows an object to invoke methods on an object running in another Java Virtual Machine. RMI provides a simple and direct way to communicate between applications running on different machines in a network.
  
  2. **Architecture of an RMI:**
    The RMI architecture consists of several layers:
  
      - **Stub and Skeleton Layer:** The stub (client side) acts as a proxy for the remote object and sends the request to the server. The skeleton (server side) receives the request and passes it to the actual remote object.
      - **Remote Reference Layer:** Manages references made from clients to the server's remote objects.
      - **Transport Layer:** Manages the network connections between clients and servers.
#### c) WAR File and Its Creation
  1. WAR File:
    WAR (Web Application Archive) file is a file format used to distribute and deploy web applications in a Java environment.
  
      - It's essentially a JAR file (Java Archive) but specifically used for web applications.
      - It contains JSPs, servlets, Java classes, XML, and other resources for web applications.
  2. Creating a WAR File:
    WAR files are typically created using a build tool like Maven or Gradle or even manually.
  
      - Using Maven: Define your web application in a pom.xml file and use the mvn package command. Maven will compile your code and package it into a WAR file.
      - Manually: Structure your application in the required directory format (WEB-INF, etc.) and use the jar command-line tool to create a WAR file.

#### d) Marshalling and Unmarshalling in Java RMI & Goals of Java RMI
  1. **Marshalling and Unmarshalling:**
  
      - **Marshalling:** The process of converting an object into a format that can be sent over the network. In Java RMI, objects are marshalled to be transmitted to a remote machine.
      - **Unmarshalling:** The reverse process, where the received data is converted back into an object.
  2. **Goals of Java RMI:**
      - **Simplify the complexity of network communication:** Abstract the network communication layer, allowing developers to invoke methods on remote objects seamlessly.
      - **Provide object-level abstraction for Java objects:** Allow objects to be passed between JVMs.
      - **Security:** Ensure secure communication between clients and servers.
      - **Performance:** Offer efficient data transfer between remote objects.
      - **Scalability and Robustness:** Facilitate the development of scalable and robust networked applications.

### <div align = center><br/><br/><br/>Answer to Question No 7</div>

#### a) Stack and Heap in Memory Structures
1. **Stack:**

    - The stack is a region of memory that stores temporary variables created by each function (including the main() function).
    - When a function is called, a block of memory (stack frame) is allocated on the top of the stack for local variables and some bookkeeping data.
    - On function exit, this memory is automatically deallocated.
    - The stack is very fast and managed by the CPU.
    - It's primarily used for static memory allocation.
2. **Heap:**

    - The heap is a region of memory used for dynamic memory allocation. Unlike the stack, memory on the heap is not automatically managed.
    - Variables allocated on the heap are accessible by any function, anywhere in your program.
    - Heap variables are managed using pointers in C or C++ and references in languages like Java.
    - Memory allocation and deallocation are manual and more flexible, but also more prone to errors like memory leaks.
3. **Interrelation:**

    - Stack and heap are distinct, but they both serve the purpose of storing data required by a program.
    - They complement each other; the stack is used for static memory allocation and function call management, while the heap is used for dynamic memory allocation, allowing more flexibility.
  
#### b) Servlets Thread Safety and Achieving It
- **Thread Safety in Servlets:**

  - Servlets are not inherently thread-safe. This means that when a servlet instance is accessed by multiple threads simultaneously, there is a potential for data inconsistency or corruption if the servlet modifies shared data (like instance variables).
- **Achieving Thread Safety:**

    - **Synchronization:** Use synchronized blocks or methods to protect critical sections of code.
    - **Avoid Shared Data:** Don't use instance variables that may be modified by servlet methods. Instead, use local variables or pass data with method parameters.
    - **SingleThreadModel Interface:** Although deprecated, this interface ensures that servlets handle only one request at a time. It's not recommended due to performance drawbacks.
#### c) Advantages of Servlet over CGI
- **Performance:** Servlets are more efficient than CGI scripts as they run within the web server's JVM. This eliminates the need to create a new process for each request.
- **Scalability:** Servlets can handle multiple requests concurrently by spawning new threads rather than processes, which is more resource-efficient.
- **Portability:** Servlets are written in Java, making them platform-independent.
- **Integration with Java:** Being a Java component, a servlet can easily integrate with other Java technologies like JSP, JDBC, and EJB.
- **Powerful:** Servlets offer a wide range of functionalities, including session management, request dispatching, and direct communication with the web server.

#### d) Two Ways to Include Results of Another Page in JSP
1. **The <jsp:include> Action:**
    - This action includes content at request time. It's processed each time the JSP is executed. Changes in the included page are reflected in the output, as the inclusion happens dynamically.
2. **The <%@ include %> Directive:**
    - This directive includes content at the translation time of the JSP. It's akin to a copy-paste at the source code level. Once the JSP is translated, changes in the included file won't affect the JSP unless it's recompiled.
#### e) Necessity of Collection Framework in Java
- **Efficiency:** The Collection Framework provides highly efficient implementations of various data structures and algorithms, which helps in writing efficient code.
- **Standardization:** It standardizes the way in which collections of data are handled in Java, making code more readable and maintainable.
- **Reduced Effort for Developers:** Developers don't need to implement common data structures from scratch.
- **Enhanced Functionality:** Provides a wide range of functions like searching, sorting, manipulation, etc., which are essential for working with collections of data.
- **Interoperability:** Different parts of an application can exchange data in a standardized format.
- **Type Safety:** Generics in collections help in ensuring type safety at compile time, reducing runtime errors.





