# To-Do List Project

---
### Project Overview
Create a simple application to manage tasks (To-Do List). The application will have the following features:

1. **Create a new task.**
    
2. **List all tasks.**
    
3. **Find a task by ID.**
    
4. **Update an existing task.**
    
5. **Delete a task.**

---
### Spring Initializr Settings
The project was created by adding the dependencies `Spring Web`, `H2 Database`, and `Spring Data JPA`. The first dependency helps create [^1]*REST Endpoints*, the second dependency allows managing an in-memory database, while the third provides operations for manipulating this data.

---
### Project Packages and Layers
The following packages divide the project at its root (`com.example.todolist`):
###### `controller`:
This package encapsulates the classes that directly handle client requests to the system via the HTTP protocol. Therefore, the `controller` interacts directly with the classes in the `service` or `repository` packages, which in turn encapsulate the business logic of the system. The `controller` receives client requests through the HTTP protocol, which can come in the form of URLs, request bodies, or HTTP headers. The `controller` then maps these requests and determines which `service` or `repository` method is most appropriate to handle the client's request. After the selected method is executed, the response from that method is returned to the client via the HTTP protocol, where the response can be in JSON or XML format (serialization of the returned object). It can also include HTTP *status codes*.
###### `service`:
In summary, the `service` is an **intermediate layer** between the `controller` and the `repository`. The `service` layer receives HTTP requests sent by the `controller` layer. These requests are processed and validated by the methods in this layer. These methods, in turn, interact directly with the `repository` layer (which has direct access to the database). The response from the `repository` layer is passed through the `service`, encapsulated via the HTTP protocol, and then returned to the `controller` layer, which handles communication with the client. Therefore, we conclude that the `service` layer encapsulates the business logic, acting as an intermediary between the layer that manages the database (`repository`) and the layer that receives client requests (`controller`).
###### `repository`:
This package contains classes that extend the `JpaRepository` interfaces, which are implemented using the JPA dependency. The JPA interfaces provide methods for CRUD operations on the database.
###### `model`:
These are the classes that map the tables in the database and, therefore, represent the database entities. The `model` layer is used to transfer ORM data between other layers of the application and to define rules for the attributes of the entities (such as `@NotNull`).


[^1]: REST Endpoints consist of URLs that reference methods contained in controller classes (`controller`), allowing HTTP operations such as GET, POST, PUT, DELETE... and simplifying the serialization of objects into JSON and XML files via the HTTP protocol.