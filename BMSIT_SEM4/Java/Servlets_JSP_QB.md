# Servlets&JSP Questions

## Servlets

- Explain the lifecycle of servlet [Done]
- Explain difference between CGI programs and servlets [Done]
- Describe core interfaces that are provided in javax servlets.http package
- write java servlet program to accept two parameter from webpage, to find the sum of them and display the result in webpage,also give necessary html script to create webpage
- explain the role of tomcat in servlets
- List and explain core classes and interfaces in javax.servlets package
  
## JSP

1. What is JSp / define jsp
2. List diff between servlets and JSp
3. diff JSP tags with examples
4. Illustrate use of any two JSP tags with suitable code snippets
5. Explain sessions and cookies in JSP
6. Explain how arrays are defined in JSP
7. WHat is cookie, list diff methods defined by cookie. write a java program to add a cookie

## cookie

A cookie is a small piece of data that a server sends to a user's web browser.  Cookies are used for various purposes, such as session management, personalization, and tracking.

```java
public class AddCookieServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response) 
            throws ServletException, IOException {
        
        Cookie userCookie = new Cookie("username", "JohnDoe");
        
        
        userCookie.setMaxAge(60 * 60 * 24); 
        userCookie.setPath("/");
        userCookie.setHttpOnly(true);
        
        
        response.addCookie(userCookie);
        
        
        response.setContentType("text/html");
        response.getWriter().println("Cookie 'username' has been set.");
    }

```

## Scriplets 

```jsp
<%@ page language="java" %>
<html>
<head>
    <title>Array in JSP</title>
</head>
<body>
    <%
        // Define and initialize an array of integers
        int[] numbers = {1, 2, 3, 4, 5};

        // Define and initialize an array of strings
        String[] fruits = {"Apple", "Banana", "Cherry", "Date", "Elderberry"};

        // Loop through the integer array
        out.println("Numbers: ");
        for (int i = 0; i < numbers.length; i++) {
            out.println(numbers[i] + " ");
        }

        // Loop through the string array
        out.println("<br>Fruits: ");
        for (int i = 0; i < fruits.length; i++) {
            out.println(fruits[i] + " ");
        }
    %>
</body>
</html>
```

## JSP Action Tags

Sure! Here are different types of action tags in JSP that are not related to JavaBeans:

1. **`<jsp:include>`**: Includes another resource at request time.
   ```jsp
   <jsp:include page="includedPage.jsp" />
   ```

2. **`<jsp:forward>`**: Forwards the request to another resource.
   ```jsp
   <jsp:forward page="anotherPage.jsp" />
   ```

3. **`<jsp:param>`**: Used inside `<jsp:include>` or `<jsp:forward>` to pass parameters.
   ```jsp
   <jsp:include page="includedPage.jsp">
       <jsp:param name="paramName" value="paramValue" />
   </jsp:include>
   ```

4. **`<jsp:plugin>`**: Used to include a Java applet or a JavaBean in the JSP page.
   ```jsp
   <jsp:plugin type="applet" code="AppletClass" codebase="appletBase" width="300" height="300">
       <jsp:param name="paramName" value="paramValue" />
   </jsp:plugin>
   ```

5. **`<jsp:element>`**: Used to dynamically create XML elements.
   ```jsp
   <jsp:element name="elementName">
       <jsp:attribute name="attributeName" value="attributeValue" />
   </jsp:element>
   ```

6. **`<jsp:attribute>`**: Used to define attributes dynamically for XML elements created by `<jsp:element>`.
   ```jsp
   <jsp:element name="elementName">
       <jsp:attribute name="attributeName" value="attributeValue" />
   </jsp:element>
   ```

7. **`<jsp:body>`**: Used to define the body content of XML elements.
   ```jsp
   <jsp:element name="elementName">
       <jsp:attribute name="attributeName" value="attributeValue" />
       <jsp:body>
           Body content goes here.
       </jsp:body>
   </jsp:element>
   ```

8. **`<jsp:text>`**: Used to include text content within a JSP document.
   ```jsp
   <jsp:text>
       Some text content.
   </jsp:text>
   ```

These action tags help in including resources, forwarding requests, and dynamically generating XML content in JSP pages.