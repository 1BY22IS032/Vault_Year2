<!--markdownlint-disable MD033-->
# Servlets and JSP

## What is a Servlet

- Tech used to create web apps
- javax.servlet is an api and an interface

1. Used to handle client requests
2. Then Process the requests
3. Generate Dynamic response

### Common Gateway Interface CGI

- CGI allows the web server to call an external program and pass HTTP req info to the external program to process the request
- CGI calls a new process for every request
  
![CGI](https://cdn.imgchest.com/files/k46ac256wb7.png#thumbnail)

**Disadvantages of CGI**:

- Increase in number of clients increases time
- with large number of process, the server starts to struggle
- uses platform dependent language

### Servlets

- The Web-container creates threads for handling each request
- Threads share common memory area, are lightweight and the cost of communication between the threads are low

![Servlet](https://cdn.imgchest.com/files/my2pcgxwop7.png)

**Advantages of Servlets**:

- Beter performance : Creating threads rather than processes
- Not platform dependent : Java isn't platform dependent
- Robust : servlets are managed by JVM so we dont need to worry about memory leak, garbage collection etc

## Anatomy Of a Servlet

<div style="display: flex;">
    <div style="flex: 1;padding: 10px">
        <ul>Init()</ul>
        <ul>Destroy()</ul>
        <ul>Service()</ul>
        In Service:
        <ul>doGet()</ul>
        <ul>doPost()</ul>
    </div>
    <div style="flex: 2;padding: 10px">
        <li><b>Loading and Initialisation</b>: when server is started, servlet is loaded into memory and servlet obj is created</li><br>
        <li><b>Init method</b>: Servlet object is invoked using Init()</li><br>
        <li><b>Request handling</b>: service() method is called  which will handle the client request</li><br>
        <li><b>Destroy()</b>: when the server is shutdown, the destroy method is invoked and the servlet object will be deleted </li><br>
    </div>
</div>

### Life Cycle of a servlet

![LifeCycleServlet](https://cdn.imgchest.com/files/p7bwczvq627.jpg)

1. **Loading a Servlet**:
   1. Involves loading and initialising the servlet by servlet container
   2. Performs two operations
      1. Loading the servlet
      2. Creating instance of the servlet using the constructor
2. **Initializing the servlet**:
   1. Initializes important resources such as databases
3. **Request Handling**:
   1. creates the ServletRequest and ServletResponse objects
4. **Destorying a servlet**:
   1. It allows all the threads currently running in the service method of the Servlet instance to complete their jobs and get released
   2. After currently running threads have completed their jobs, the Servlet container calls the destroy() method on the Servlet instance

### Role of tomcat in sevlets

Servlet Container

- 

## JavaServletPages (JSP)
