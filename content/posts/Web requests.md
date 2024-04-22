---
title: 'Web requests'
date: 2024-04-21
tags: ["network", "web", "security"]
TocOpen: true
---

## HyperText Transfer Protocol (HTTP)

- **Definition**: HTTP is an application-level protocol used for accessing World Wide Web resources. It facilitates communication between a client and a server.
    
- **Components of a URL**:
    
    - **Scheme**: Identifies the protocol (`http://`, `https://`).
    - **User Info**: Optional credentials (`admin:password@`).
    - **Host**: Resource location (hostname or IP address).
    - **Port**: Separated by a colon (`:80` if not specified).
    - **Path**: Points to the resource being accessed (`/dashboard.php`)
    - **Query String**: Parameters and values separated by `&`  (`?login=true`).
    - **Fragments**: Processed by browsers on the client-side (``#status``)
- **HTTP Flow**:
    
    - User enters URL.
    - Browser sends request to DNS server.
    - DNS server resolves domain to IP.
    - Browser sends GET request to server.
    - Server processes request and returns response.
    - Browser renders response.
- **cURL**:
    
    - Command-line tool for sending HTTP requests.
    - Can be used for scripting and automation.
    - Doesn't render HTML/CSS/JS, prints raw format.
    - Useful for penetration testing.
    - Common flags:
        - `-o`: Write output to a file.
        - `-s`: Silent mode.
        - `-u`: Specify user and password.
        - `-A`: Set User-Agent.
        - `-i`: Include protocol response headers.
        - `-d`: HTTP POST data.
        - `-h`: Help menu.


## Hypertext Transfer Protocol Secure (HTTPS)

- **Definition**: HTTPS (HTTP Secure) encrypts communications between a web browser and a web application, preventing interception of sensitive data.
  
- **Clear-text vs. Encrypted**: HTTP sends data in clear-text, making it vulnerable to interception. HTTPS encrypts data, making it unreadable to unauthorized parties.

- **Identification**:

    - HTTPS URLs start with `https://`.
    - Browsers show a lock icon for HTTPS sites.

**2. HTTPS Flow**

- **Operation**:

    - User enters URL (`http://` or `https://`).
    - Browser resolves domain and connects to server.
    - Initial connection attempts HTTP on port 80.
    - Server redirects to HTTPS on port 443.
    - Client and server exchange encryption keys.
    - Encrypted communication begins.

- **Security Considerations**:

    - Encrypted data can still reveal visited URLs if DNS resolution is not encrypted.
    - Downgrade attacks can revert HTTPS to HTTP; modern browsers and servers mitigate this risk.

**3. cURL for HTTPS**

- **Usage**:

    - cURL handles HTTPS by default.
    - May encounter issues with invalid or outdated SSL certificates.

- **Handling Invalid Certificates**:

    - By default, cURL rejects communication with sites having invalid certificates.
    - Use `-k` flag to skip certificate validation.


## HTTP Requests and Responses

**1. HTTP Request**

- **Overview**:
    - Made by client (e.g., cURL/browser).
    - Contains request details like method, path, headers, and data.
    - Headers separated by new lines.

- **Example**:
    ```
    GET /users/login.html HTTP/1.1
    Host: inlanefreight.com
    User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/96.0.4664.110 Safari/537.36
    ```

**2. HTTP Response**

- **Overview**:
    - Sent by server after processing request.
    - Contains response code, headers, and optional response body.

- **Example**:
    ```
    HTTP/1.1 200 OK
    Date: Tue, 21 Jul 2020 05:20:15 GMT
    Server: Apache/X.Y.ZZ (Ubuntu)
    Content-Length: 464
    Content-Type: text/html; charset=iso-8859-1
    ```

**3. cURL**

- **Usage**:
    - Use `-v` flag to view verbose output with both request and response details.
    - Helpful for debugging and penetration testing.

- **Example**:
    ```
    curl inlanefreight.com -v
    ```

**4. Browser DevTools**

- **Overview**:
    - Built-in tools for web developers.
    - Accessible via [CTRL+SHIFT+I] or [F12] in most browsers.

- **Network Tab**:
    - Displays all web requests made by the browser.
    - Shows response status, method, URL, and path.

- **Usage**:
    - Useful for monitoring network activity and debugging web requests.
    - Can inspect request and response details, including headers and raw response body.


## HTTP Headers 

HTTP headers play a crucial role in communication between clients and servers, providing essential information about requests and responses. 

### General Headers

General headers describe the message itself, independent of its content.
`common to both the request and response`

| **Header**     | **Example**                          | **Description**                                                                                                                                                                                              |
| -------------- | ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Date`         | `Date: Wed, 16 Feb 2022 10:38:44 GMT` | Holds the date and time when the message originated, preferably in UTC time zone.                                                                                                                            |
| `Connection`   | `Connection: close`                   | Indicates if the network connection should stay open (`keep-alive`) or be closed (`close`) after the request/response completes.                                                                           |


### Entity Headers

Entity headers describe the content being transferred.
`common to both the request and response`

| **Header**         | **Example**                   | **Description**                                                                              |
| ------------------ | ----------------------------- | -------------------------------------------------------------------------------------------- |
| `Content-Type`     | `Content-Type: text/html`     | Describes the type of resource being transferred, including the character encoding.          |
| `Media-Type`       | `Media-Type: application/pdf` | Indicates the type of media being transferred, such as PDF, image, etc.                      |
| `Boundary`         | `boundary="b4e4fbd93540"`     | Marks the boundary between different parts of the content, often used in multipart messages. |
| `Content-Length`   | `Content-Length: 385`         | Specifies the size of the content being transferred, in bytes.                               |
| `Content-Encoding` | `Content-Encoding: gzip`      | Indicates the encoding applied to the content to reduce its size, such as gzip compression.  |

### Request Headers

Request headers are sent by the client in an HTTP request.

| **Header**      | **Example**                         | **Description**                                                                                                                                                                                                                        |
| --------------- | ----------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Host`          | `Host: www.example.com`             | Specifies the host being queried for the resource.                                                                                                                                                                                     |
| `User-Agent`    | `User-Agent: Mozilla/5.0`           | Identifies the client making the request, typically including information about the browser, operating system, etc.                                                                                                                    |
| `Referer`       | `Referer: http://www.example.com/`  | Indicates the URL of the referring page from which the request originated. <br>(/!\ can be manipulated)                                                                                                                                |
| `Accept`        | `Accept: text/html`                 | Lists the media types that the client can handle, typically used by servers to determine the appropriate content type for the response.                                                                                                |
| `Cookie`        | `Cookie: sessionid=abc123`          | Contains cookies associated with the request, allowing for session management and tracking on the server-side.                                                                                                                         |
| `Authorization` | `Authorization: BASIC cGFzc3dvcmQK` | Another method for the server to identify clients. After successful authentication, the server returns a token unique to the client. Unlike cookies, tokens are stored only on the client-side and retrieved by the server per request |

### Response Headers

Response headers are sent by the server in an HTTP response.

| **Header**         | **Example**                                  | **Description**                                                                    |
| ------------------ | -------------------------------------------- | ---------------------------------------------------------------------------------- |
| `Server`           | `Server: Apache/2.4.41`                      | Specifies information about the server software handling the request.              |
| `Set-Cookie`       | `Set-Cookie: sessionid=abc123; Expires=...`  | Instructs the client to store a cookie for session management or other purposes.   |
| `WWW-Authenticate` | `WWW-Authenticate: Basic realm="Restricted"` | Specifies the authentication method required for accessing the requested resource. |

### Security Headers

Security headers enhance the security of web applications.

| **Header**                  | **Example**                                   | **Description**                                                                                                                        |
| --------------------------- | --------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| `Content-Security-Policy`   | `Content-Security-Policy: script-src 'self'`  | Defines the policy for executing scripts and other resources, helping prevent XSS attacks.                                             |
| `Strict-Transport-Security` | `Strict-Transport-Security: max-age=31536000` | Instructs the browser to only access the site over HTTPS, protecting against man-in-the-middle attacks and protocol downgrade attacks. |
| `Referrer-Policy`           | `Referrer-Policy: origin`                     | Controls how much referrer information is included with requests, helping protect user privacy.                                        |


### Displaying Headers

- Use `-I` flag to show only response headers: `curl -I https://www.example.com`
- Use `-i` flag to show both headers and response body: `curl -i https://www.example.com`

### Setting Headers

- Use `-H` flag to set request headers: `curl -H "Authorization: Bearer token123" https://www.example.com`
- Some headers have dedicated flags like `-A` for `User-Agent`: `curl -A "Mozilla/5.0" https://www.example.com`

### Browser DevTools

Browser DevTools provide insights into network requests.

- Navigate to `Network` tab to view requests.
- Click on a request to see headers in the `Headers` tab.
- Use the `Raw` button to view headers in raw format.



## HTTP Methods and Codes


The following are some of the commonly used methods:

| **Method** | **Description**                                                                                                                                                                                                                                                                                                                      |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `GET`      | Requests a specific resource. Additional data can be passed to the server via query strings in the URL (e.g. `?param=value`).                                                                                                                                                                                                        |
| `POST`     | Sends data to the server. It can handle multiple types of input, such as text, PDFs, and other forms of binary data. This data is appended in the request body present after the headers. The POST method is commonly used when sending information (e.g. forms/logins) or uploading data to a website, such as images or documents. |
| `HEAD`     | Requests the headers that would be returned if a GET request was made to the server. It doesn't return the request body and is usually made to check the response length before downloading resources.                                                                                                                               |
| `PUT`      | Creates new resources on the server. Allowing this method without proper controls can lead to uploading malicious resources.                                                                                                                                                                                                         |
| `DELETE`   | Deletes an existing resource on the webserver. If not properly secured, can lead to Denial of Service (DoS) by deleting critical files on the web server.                                                                                                                                                                            |
| `OPTIONS`  | Returns information about the server, such as the methods accepted by it.                                                                                                                                                                                                                                                            |
| `PATCH`    | Applies partial modifications to the resource at the specified location.                                                                                                                                                                                                                                                             |


### Informational responses (1xx):
- **100 Continue**: The server has received the initial part of the request and will continue processing it.

### Successful responses (2xx):
- **200 OK**: The request has succeeded. The response generally includes the requested information.
- **201 Created**: The request has been fulfilled, and a new resource is created.
- **204 No Content**: The server successfully processed the request but does not need to return any content.

### Redirection messages (3xx):
- **301 Moved Permanently**: The requested resource has been permanently moved to a new URL.
- **302 Found (Previously "Moved Temporarily")**: The requested resource temporarily resides under a different URL.
- **304 Not Modified**: The resource has not been modified since the last request.

### Client error responses (4xx):
- **400 Bad Request**: The server cannot process the request due to a client error.
- **401 Unauthorized**: The request requires user authentication.
- **403 Forbidden**: The server understood the request, but refuses to authorize it.
- **404 Not Found**: The server cannot find the requested resource.

### Server error responses (5xx):
- **500 Internal Server Error**: A generic error message indicating that the server encountered an unexpected condition.
- **502 Bad Gateway**: The server, while acting as a gateway or proxy, received an invalid response from the upstream server.
- **503 Service Unavailable**: The server is currently unable to handle the request due to temporary overload or maintenance.

### Unofficial codes:
- **418 I'm a teapot**: This code was defined in 1998 as one of the traditional IETF April Fools' jokes. It's not expected to be implemented by actual HTTP servers.

### Uncommon but noteworthy:
- **402 Payment Required**: Reserved for future use. It's not currently in use.



## Get & Post

1. **GET:**
    
    - GET method is used to request data from a specified resource.
    - When a client sends a GET request to a server, parameters are sent in the URL as query strings. For example, in `http://example.com/page?name=John&age=30`, "name" and "age" are parameters with values "John" and "30".
    - GET requests are often used to retrieve data, such as web pages or static resources (images, CSS files, etc.).
    - GET requests can be cached and are typically stored in the browser history, making them less secure for sending sensitive data.
2. **POST:**
    
    - POST method is used to send data to the server for processing.
    - Unlike GET, data sent via POST is included in the body of the HTTP request, rather than in the URL. This allows for sending larger and more complex data.
    - POST requests are often used to submit online forms, upload files, or perform actions that modify the server's state.
    - POST requests are typically not cached and are not stored in the browser history, making them more secure for sending sensitive data.

## cURL options 


- **X, --request [HTTP METHOD]**
    
    - Specifies the HTTP method to be used in the request (GET, POST, PUT, DELETE, etc.).
- **-d, --data [DATA]**
    
    - Sends data in the request body. Useful for POST requests or requests that require data.

```shell-session
curl -X POST -d 'username=admin&password=admin' http://<SERVER_IP>:<PORT>/`
```

- **-H, --header [HEADER]**
    
    - Adds a custom HTTP header to the request. Useful for setting headers like authentication tokens or content type.

```shell-session
curl -H 'Authorization: Basic YWRtaW46YWRtaW4=' http://<SERVER_IP>:<PORT>/
```

- **-i, --include**
    
    - Includes the HTTP response headers in the output. Helpful for debugging or analyzing responses.
- **-o, --output [FILE]**
    
    - Writes output to a specified file instead of standard output. Useful for saving responses to a file.
- **-L, --location**
    
    - Follows HTTP redirects. This is useful when accessing resources that have moved.
- **-u, --user [USER:PASSWORD]**
    
    - Specifies the username and password for HTTP authentication. Useful for accessing password-protected resources.
- **-k, --insecure**
    
    - Allows curl to perform "insecure" SSL connections. This is helpful when dealing with self-signed certificates or testing environments.
- **-v, --verbose**
    
    - Enables verbose output, showing detailed information about the request and response. Useful for debugging.
    - -vvv : ultra developped 
- **-XGET, -XPOST, etc.**
    
    - Shortcut for specifying the HTTP method. For example, `-XGET` is equivalent to `--request GET`.
- **-F, --form [KEY=VALUE]**
    
    - Sends form data in a multipart/form-data request. Useful for submitting HTML forms with file uploads.
- **-b, --cookie [COOKIE_STRING]**
    
    - Sends cookies in the request header. Helpful for maintaining session state.
- **--cookie-jar [FILE]**
    
    - Stores cookies from the response in a file for later use. Useful for maintaining session state across multiple requests.
- **--upload-file [FILE]**
    
    - Uploads a file to the server. Useful for sending files in POST requests.
- **-x, --proxy [PROTOCOL://HOST[:PORT]]**
    
    - Specifies a proxy server to be used for the request. Helpful for accessing resources behind a firewall.


```
curl -XPOST -b "PHPSESSID=1g8uj3f5ao4nkgu4b215v7egf4" -H "Content-type: application/json" -d '{"search":"flag"}' http://83.136.252.32:43390/search.php
```





