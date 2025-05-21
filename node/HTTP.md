# 🌐 HTTP (HyperText Transfer Protocol)

## 🔍 What is HTTP?

- HTTP stands for HyperText Transfer Protocol.
- It defines how messages are formatted and transmitted over the web.
- It is the foundation of data communication for the World Wide Web.
- HTTP is a **stateless** protocol: each request is independent.

## 📄 HTTP Communication Model

1. Client (web browser or app) sends an HTTP request.
2. Server processes the request.
3. Server sends back an HTTP response with the requested resource.


## ⚙️ Core Components

• HTTP Request:
  - **Methods/Verbs**: GET, POST, PUT, DELETE, PATCH, OPTIONS, HEAD
  - **URL**: Specifies the resource location
  - **Headers**: Provide metadata (e.g., Content-Type, Authorization)
  - **Body**: Data payload for POST/PUT (optional)

• HTTP Response:
  - **Status Code**: Indicates the result (e.g., 200 OK, 404 Not Found)
  - **Headers**: Include server info, content type, caching info
  - **Body**: Contains the requested resource or error message

## 🔹 Example of an HTTP GET Request

GET /index.html HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0
Accept: text/html

## 🔹 Example of an HTTP Response

HTTP/1.1 200 OK
Content-Type: text/html; charset=UTF-8
Content-Length: 3425

<html>
  <head><title>Example</title></head>
  <body>
    <h1>Welcome to Example.com</h1>
    <!-- page content here -->
  </body>
</html>

## 🛠️ Common HTTP Methods

| Method  | Purpose                                                           |
|---------|-------------------------------------------------------------------|
| GET     | Retrieve data from the server.                                  |
| POST    | Submit data to be processed (e.g., form submission).            |
| PUT     | Replace the entire resource with the payload provided.          |
| PATCH   | Partially update an existing resource.                          |
| DELETE  | Remove a resource from the server.                              |
| OPTIONS | Request permitted methods and other options for a resource.     |
| HEAD    | Similar to GET, but only returns headers, no body.              |

## 📊 HTTP Status Codes (Common Examples)

• 1xx Informational:
   - 100 Continue: Initial part of request received, continue.

• 2xx Success:
   - 200 OK: Request succeeded.
   - 201 Created: Resource successfully created.

• 3xx Redirection:
   - 301 Moved Permanently: Resource has new URL.
   - 302 Found: Temporary redirection.

• 4xx Client Error:
   - 400 Bad Request: The server could not understand the request.
   - 401 Unauthorized: Authentication required.
   - 403 Forbidden: The server refused to fulfill the request.
   - 404 Not Found: Resource not found.

• 5xx Server Error:
   - 500 Internal Server Error: Generic server error.
   - 503 Service Unavailable: Server is overloaded or under maintenance.

## 💡 Real-Life Examples & Usage

- **Web Browsing**: Browsers send HTTP requests to load websites.
- **APIs**: RESTful APIs use HTTP methods to perform CRUD operations.
- **Microservices**: HTTP is often used for inter-service communication.
- **IoT Devices**: Many devices communicate with servers via HTTP.


## ✅ Advantages of HTTP

- Simple and widely adopted protocol.
- Flexible: works with a variety of content types.
- Statelessness simplifies scaling (each request is independent).

## ⚠️ Considerations

- Lack of built-in security (addressed by HTTPS).
- Being stateless requires additional management for sessions (like cookies, JWT).

## 📌 Summary

- HTTP is the protocol that powers the web.
- It operates on a request-response model.
- It supports different methods, each serving a specific purpose.
- Understanding HTTP is crucial for web development and API design.

