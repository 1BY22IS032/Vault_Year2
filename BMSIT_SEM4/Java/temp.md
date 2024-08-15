### Servlets

#### Describe core interfaces that are provided in `javax.servlet.http` package

The `javax.servlet.http` package provides several core interfaces, including:

1. **HttpServletRequest**:
   - **Description**: Provides request information for HTTP servlets.
   - **Core Methods**:
     - `String getAuthType()`
     - `Cookie[] getCookies()`
     - `long getDateHeader(String name)`
     - `String getHeader(String name)`
     - `Enumeration<String> getHeaders(String name)`
     - `Enumeration<String> getHeaderNames()`
     - `int getIntHeader(String name)`
     - `String getMethod()`
     - `String getPathInfo()`
     - `String getPathTranslated()`
     - `String getContextPath()`
     - `String getQueryString()`
     - `String getRemoteUser()`
     - `boolean isUserInRole(String role)`
     - `Principal getUserPrincipal()`
     - `String getRequestedSessionId()`
     - `String getRequestURI()`
     - `StringBuffer getRequestURL()`
     - `String getServletPath()`
     - `HttpSession getSession(boolean create)`
     - `HttpSession getSession()`
     - `boolean isRequestedSessionIdValid()`
     - `boolean isRequestedSessionIdFromCookie()`
     - `boolean isRequestedSessionIdFromURL()`
     - `boolean isRequestedSessionIdFromUrl()`

2. **HttpServletResponse**:
   - **Description**: Assists a servlet in sending a response to a client.
   - **Core Methods**:
     - `void addCookie(Cookie cookie)`
     - `boolean containsHeader(String name)`
     - `String encodeURL(String url)`
     - `String encodeRedirectURL(String url)`
     - `String encodeUrl(String url)`
     - `String encodeRedirectUrl(String url)`
     - `void sendError(int sc, String msg)`
     - `void sendError(int sc)`
     - `void sendRedirect(String location)`
     - `void setDateHeader(String name, long date)`
     - `void addDateHeader(String name, long date)`
     - `void setHeader(String name, String value)`
     - `void addHeader(String name, String value)`
     - `void setIntHeader(String name, int value)`
     - `void addIntHeader(String name, int value)`
     - `void setStatus(int sc)`
     - `void setStatus(int sc, String sm)`

3. **HttpSession**:
   - **Description**: Provides a way to identify a user across multiple page requests or visits to a Web site and store information about that user.
   - **Core Methods**:
     - `long getCreationTime()`
     - `String getId()`
     - `long getLastAccessedTime()`
     - `ServletContext getServletContext()`
     - `void setMaxInactiveInterval(int interval)`
     - `int getMaxInactiveInterval()`
     - `HttpSessionContext getSessionContext()`
     - `Object getAttribute(String name)`
     - `Object getValue(String name)`
     - `Enumeration<String> getAttributeNames()`
     - `String[] getValueNames()`
     - `void setAttribute(String name, Object value)`
     - `void putValue(String name, Object value)`
     - `void removeAttribute(String name)`
     - `void removeValue(String name)`
     - `void invalidate()`
     - `boolean isNew()`

4. **HttpSessionContext**:
   - **Description**: Provides a way to identify all the sessions in a web application and to identify the session IDs of all the sessions.
   - **Core Methods**:
     - `HttpSession getSession(String sessionId)`
     - `Enumeration<String> getIds()`

#### Write a Java servlet program to accept two parameters from a webpage, find the sum of them and display the result on a webpage. Also, give the necessary HTML script to create the webpage.

**HTML script (index.html):**
```html
<!DOCTYPE html>
<html>
<head>
    <title>Sum Calculator</title>
</head>
<body>
    <h2>Enter Two Numbers</h2>
    <form action="SumServlet" method="GET">
        Number 1: <input type="text" name="num1"><br>
        Number 2: <input type="text" name="num2"><br>
        <input type="submit" value="Calculate Sum">
    </form>
</body>
</html>
```

**Java servlet (SumServlet.java):**
```java
import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

public class SumServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        
        try {
            int num1 = Integer.parseInt(request.getParameter("num1"));
            int num2 = Integer.parseInt(request.getParameter("num2"));
            int sum = num1 + num2;
            
            out.println("<html><body>");
            out.println("<h2>The sum of " + num1 + " and " + num2 + " is: " + sum + "</h2>");
            out.println("</body></html>");
        } catch (NumberFormatException e) {
            out.println("<html><body>");
            out.println("<h2>Invalid input, please enter numeric values.</h2>");
            out.println("</body></html>");
        } finally {
            out.close();
        }
    }
}
```

#### Explain the role of Tomcat in servlets

Tomcat, an open-source implementation of the Java Servlet, JavaServer Pages (JSP), and Java Expression Language technologies, acts as a servlet container, providing several key functionalities:

1. **Servlet Container**: Manages the lifecycle of servlets, from initialization to processing requests and responses.
2. **Web Server**: Serves static content such as HTML, CSS, and JavaScript files.
3. **JSP Engine**: Converts JSP files into servlets for execution.
4. **Configuration Management**: Handles configuration settings for web applications via `web.xml` and other context configurations.
5. **Security**: Provides authentication, authorization, and SSL support.
6. **Session Management**: Manages user sessions, ensuring consistent user state across multiple requests.
7. **Resource Management**: Manages resources like JDBC data sources, ensuring efficient connection pooling and resource allocation.

#### List and explain core classes and interfaces in `javax.servlet` package

The `javax.servlet` package provides several core classes and interfaces, including:

1. **Servlet**:
   - **Description**: Defines methods that all servlets must implement.
   - **Core Methods**:
     - `void init(ServletConfig config) throws ServletException`
     - `ServletConfig getServletConfig()`
     - `void service(ServletRequest req, ServletResponse res) throws ServletException, IOException`
     - `String getServletInfo()`
     - `void destroy()`

2. **GenericServlet**:
   - **Description**: An abstract class implementing the Servlet and ServletConfig interfaces, providing simple versions of the lifecycle methods.
   - **Core Methods**:
     - `void init(ServletConfig config) throws ServletException`
     - `ServletConfig getServletConfig()`
     - `void service(ServletRequest req, ServletResponse res) throws ServletException, IOException`
     - `String getServletInfo()`
     - `void destroy()`
     - `void init() throws ServletException`
     - `ServletContext getServletContext()`
     - `Enumeration<String> getInitParameterNames()`
     - `String getInitParameter(String name)`

3. **HttpServlet**:
   - **Description**: Provides an abstract class to be subclassed to create an HTTP servlet.
   - **Core Methods**:
     - `void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException`
     - `void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException`
     - `void doPut(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException`
     - `void doDelete(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException`
     - `void doHead(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException`
     - `void doOptions(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException`
     - `void doTrace(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException`

4. **ServletRequest**:
   - **Description**: Provides a way to retrieve information about the request.
   - **Core Methods**:
     - `Object getAttribute(String name)`
     - `Enumeration<String> getAttributeNames()`
     - `String getCharacterEncoding()`
     - `void setCharacterEncoding(String env) throws UnsupportedEncodingException`
     - `int getContentLength()`
     - `long getContentLengthLong()`
     - `String getContentType()`
     - `ServletInputStream getInputStream() throws IOException`
     - `String getParameter(String name)`
     - `Enumeration<String> getParameterNames()`
     - `String[] getParameterValues(String name)`
     - `Map<String, String[]> getParameterMap()`
     - `String getProtocol()`
     - `String getScheme()`
     - `String getServerName()`
     - `int getServerPort()`
     - `BufferedReader getReader() throws IOException`
    

 - `String getRemoteAddr()`
     - `String getRemoteHost()`
     - `void setAttribute(String name, Object o)`
     - `void removeAttribute(String name)`
     - `Locale getLocale()`
     - `Enumeration<Locale> getLocales()`
     - `boolean isSecure()`
     - `RequestDispatcher getRequestDispatcher(String path)`
     - `String getRealPath(String path)`
     - `int getRemotePort()`
     - `String getLocalName()`
     - `String getLocalAddr()`
     - `int getLocalPort()`

5. **ServletResponse**:
   - **Description**: Provides a way to send data back to the client.
   - **Core Methods**:
     - `String getCharacterEncoding()`
     - `String getContentType()`
     - `ServletOutputStream getOutputStream() throws IOException`
     - `PrintWriter getWriter() throws IOException`
     - `void setCharacterEncoding(String charset)`
     - `void setContentLength(int len)`
     - `void setContentLengthLong(long len)`
     - `void setContentType(String type)`
     - `void setBufferSize(int size)`
     - `int getBufferSize()`
     - `void flushBuffer() throws IOException`
     - `void resetBuffer()`
     - `boolean isCommitted()`
     - `void reset()`
     - `void setLocale(Locale loc)`
     - `Locale getLocale()`

6. **ServletContext**:
   - **Description**: Provides a way to communicate with the servlet container.
   - **Core Methods**:
     - `String getContextPath()`
     - `ServletContext getContext(String uripath)`
     - `int getMajorVersion()`
     - `int getMinorVersion()`
     - `int getEffectiveMajorVersion()`
     - `int getEffectiveMinorVersion()`
     - `String getMimeType(String file)`
     - `Set<String> getResourcePaths(String path)`
     - `URL getResource(String path) throws MalformedURLException`
     - `InputStream getResourceAsStream(String path)`
     - `RequestDispatcher getRequestDispatcher(String path)`
     - `RequestDispatcher getNamedDispatcher(String name)`
     - `Servlet getServlet(String name) throws ServletException`
     - `Enumeration<Servlet> getServlets()`
     - `Enumeration<String> getServletNames()`
     - `void log(String msg)`
     - `void log(Exception exception, String msg)`
     - `void log(String message, Throwable throwable)`
     - `String getRealPath(String path)`
     - `String getServerInfo()`
     - `String getInitParameter(String name)`
     - `Enumeration<String> getInitParameterNames()`
     - `boolean setInitParameter(String name, String value)`
     - `Object getAttribute(String name)`
     - `Enumeration<String> getAttributeNames()`
     - `void setAttribute(String name, Object object)`
     - `void removeAttribute(String name)`
     - `String getServletContextName()`
     - `ServletRegistration.Dynamic addServlet(String servletName, String className)`
     - `ServletRegistration.Dynamic addServlet(String servletName, Servlet servlet)`
     - `ServletRegistration.Dynamic addServlet(String servletName, Class<? extends Servlet> servletClass)`
     - `<T extends Servlet> T createServlet(Class<T> c) throws ServletException`
     - `ServletRegistration getServletRegistration(String servletName)`
     - `Map<String, ? extends ServletRegistration> getServletRegistrations()`
     - `FilterRegistration.Dynamic addFilter(String filterName, String className)`
     - `FilterRegistration.Dynamic addFilter(String filterName, Filter filter)`
     - `FilterRegistration.Dynamic addFilter(String filterName, Class<? extends Filter> filterClass)`
     - `<T extends Filter> T createFilter(Class<T> c) throws ServletException`
     - `FilterRegistration getFilterRegistration(String filterName)`
     - `Map<String, ? extends FilterRegistration> getFilterRegistrations()`
     - `SessionCookieConfig getSessionCookieConfig()`
     - `void setSessionTrackingModes(Set<SessionTrackingMode> sessionTrackingModes)`
     - `Set<SessionTrackingMode> getDefaultSessionTrackingModes()`
     - `Set<SessionTrackingMode> getEffectiveSessionTrackingModes()`
     - `void addListener(String className)`
     - `<T extends EventListener> void addListener(T t)`
     - `void addListener(Class<? extends EventListener> listenerClass)`
     - `<T extends EventListener> T createListener(Class<T> c) throws ServletException`
     - `JspConfigDescriptor getJspConfigDescriptor()`
     - `ClassLoader getClassLoader()`
     - `void declareRoles(String... roleNames)`
     - `String getVirtualServerName()`

### JSP

#### 1. What is JSP / Define JSP

JavaServer Pages (JSP) is a server-side technology that allows the creation of dynamic, platform-independent web content. JSPs are compiled into servlets by the server and are used to create web applications that leverage Java for business logic while embedding HTML and other markup for content presentation. JSPs simplify the creation of dynamic web pages by enabling the embedding of Java code directly within HTML.

#### 2. List differences between servlets and JSP

| **Aspect**           | **Servlets**                         | **JSP**                                    |
|----------------------|--------------------------------------|--------------------------------------------|
| **Syntax**           | Pure Java code                       | HTML with embedded Java code               |
| **Ease of Use**      | Requires more code to create HTML    | Easier to write and maintain for web pages |
| **Design**           | Controller-based                     | View-based                                 |
| **Compilation**      | Manually compiled                    | Automatically compiled into servlets       |
| **Modification**     | Requires recompilation for changes   | Changes are automatically recompiled       |
| **Separation of Concerns** | Less separation between logic and presentation | Better separation of logic and presentation |

#### 3. Different JSP tags with examples

1. **Directive Tags**: Provide global information about the entire JSP page.
   - **Example**:
     ```jsp
     <%@ page language="java" contentType="text/html; charset=UTF-8" %>
     <%@ include file="header.jsp" %>
     ```

2. **Declaration Tags**: Declare variables or methods to be used later in the JSP.
   - **Example**:
     ```jsp
     <%! int counter = 0; %>
     <%! public int getCounter() { return counter++; } %>
     ```

3. **Scriptlet Tags**: Embed Java code to be executed when the JSP is requested.
   - **Example**:
     ```jsp
     <% 
        String name = request.getParameter("name");
        out.println("Hello, " + name);
     %>
     ```

4. **Expression Tags**: Evaluate a Java expression and output the result.
   - **Example**:
     ```jsp
     <%= new java.util.Date() %>
     ```

5. **Action Tags**: Use built-in functionalities such as including other resources or forwarding requests.
   - **Example**:
     ```jsp
     <jsp:include page="footer.jsp" />
     <jsp:forward page="anotherPage.jsp" />
     ```

#### 4. Illustrate the use of any two JSP tags with suitable code snippets

1. **Directive Tag Example**:
   ```jsp
   <%@ page language="java" contentType="text/html; charset=UTF-8" %>
   <html>
   <head><title>Directive Tag Example</title></head>
   <body>
       <%@ include file="header.jsp" %>
       <h2>Directive Tag Example</h2>
       <p>This is an example of using a directive tag to include another JSP file.</p>
       <%@ include file="footer.jsp" %>
   </body>
   </html>
   ```

2. **Scriptlet Tag Example**:
   ```jsp
   <html>
   <head><title>Scriptlet Tag Example</title></head>
   <body>
       <% 
           String name = request.getParameter("name");
           if (name == null) {
               name = "Guest";
           }
       %>
       <h2>Welcome, <%= name %>!</h2>
       <p>This is an example of using a scriptlet tag to process a request parameter.</p>
   </body>
   </html>
   ```

#### 5. Explain sessions and cookies in JSP

**Sessions**:
- **Description**: Sessions track user interactions with a web application across multiple requests. Each user is assigned a unique session ID.
- **Core Methods**:
  - `getSession()`: Retrieves the current session or creates one if it does not exist.
  - `getAttribute(String name)`: Retrieves an attribute from the session.
  - `setAttribute(String name, Object value)`: Sets an attribute in the session.
  - `removeAttribute(String name)`: Removes an attribute from the session.
  - `invalidate()`: Invalidates the session, removing all attributes.

**Cookies**:
- **Description**: Cookies are small pieces of data stored on the client's machine and sent with each request to the server. They are used to remember information between requests.
- **Core Methods**:
  - `getName()`: Retrieves the name of the cookie.
  - `getValue()`: Retrieves the value of the cookie.
  - `setValue(String value)`: Sets the value of the cookie.
  - `setMaxAge(int expiry)`: Sets the maximum age of the cookie in seconds.
  - `getMaxAge()`: Retrieves the maximum age of the cookie.
  - `setPath

(String uri)`: Sets the path for the cookie.
  - `getPath()`: Retrieves the path of the cookie.
  - `setDomain(String domain)`: Sets the domain for the cookie.
  - `getDomain()`: Retrieves the domain of the cookie.
  - `setSecure(boolean flag)`: Indicates whether the cookie should only be sent over secure connections.
  - `getSecure()`: Retrieves the secure flag of the cookie.
  - `setHttpOnly(boolean isHttpOnly)`: Sets whether the cookie is HTTP only.
  - `isHttpOnly()`: Checks if the cookie is HTTP only.

#### 6. Explain how arrays are defined in JSP

Arrays in JSP can be defined and used similarly to Java. They can be declared within scriptlets or expressions.

**Example**:
```jsp
<%
    int[] numbers = {1, 2, 3, 4, 5};
    String[] names = {"Alice", "Bob", "Charlie"};

    for (int i = 0; i < numbers.length; i++) {
        out.println("Number: " + numbers[i] + "<br>");
    }

    for (int i = 0; i < names.length; i++) {
        out.println("Name: " + names[i] + "<br>");
    }
%>
```

#### 7. What is a cookie? List different methods defined by the cookie. Write a Java program to add a cookie.

**Cookie**:
A cookie is a small piece of data sent from a website and stored on the user's computer by the user's web browser while the user is browsing. Cookies are used to remember information about the user.

**Different Methods Defined by Cookie**:
1. `getName()`
2. `getValue()`
3. `setValue(String value)`
4. `setMaxAge(int expiry)`
5. `getMaxAge()`
6. `setPath(String uri)`
7. `getPath()`
8. `setDomain(String domain)`
9. `getDomain()`
10. `setSecure(boolean flag)`
11. `getSecure()`
12. `setHttpOnly(boolean isHttpOnly)`
13. `isHttpOnly()`

**Java Program to Add a Cookie**:
```java
import java.io.IOException;
import javax.servlet.ServletException;
import javax.servlet.http.Cookie;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

public class AddCookieServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        // Create a cookie
        Cookie userCookie = new Cookie("username", "JohnDoe");
        
        // Set the maximum age to one day (24*60*60 seconds)
        userCookie.setMaxAge(24 * 60 * 60);
        
        // Add the cookie to the response
        response.addCookie(userCookie);
        
        // Notify the user
        response.setContentType("text/html");
        response.getWriter().println("Cookie has been set.");
    }
}
```