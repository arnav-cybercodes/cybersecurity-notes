# 01. Web Applications

## What is a Web Application?

A **Web Application** is software that runs on a **web server** and is accessed through a **web browser** using HTTP/HTTPS.

### Examples
- Gmail
- YouTube
- Instagram
- Facebook
- Amazon
- TryHackMe

---

## Components of a Web Application

### Front End (Client Side)
Visible to users.

Technologies:
- HTML → Structure
- CSS → Design
- JavaScript → Interactivity

### Back End (Server Side)
Handles:
- Authentication
- Business Logic
- APIs
- Database Operations

Languages:
- Python
- PHP
- Java
- Node.js
- Go

### Database
Stores:
- Users
- Password Hashes
- Products
- Orders
- Messages

Examples:
- MySQL
- PostgreSQL
- MongoDB

### Web Server
Receives HTTP requests and returns HTTP responses.

Examples:
- Apache
- Nginx
- IIS

### WAF (Web Application Firewall)
Protects applications against:
- SQL Injection
- XSS
- Command Injection
- Malicious Bots

---

## Request Flow

Browser
→ Web Server
→ Application
→ Database
→ Application
→ Web Server
→ Browser

---

## Cybersecurity Importance

Understanding web applications helps identify attacks like:
- SQL Injection
- XSS
- CSRF
- IDOR
- File Inclusion
- RCE

---

## Quick Revision

✔ Front End = HTML + CSS + JavaScript

✔ Back End = Server Logic

✔ Database = Stores Data

✔ Web Server = Handles HTTP Requests

✔ WAF = Filters Malicious Traffic

# 02. URLs

## What is a URL?

A **URL (Uniform Resource Locator)** is the address of a resource on the Internet.

Example:

https://example.com/login?id=10#profile

---

## Anatomy of a URL

https://example.com:443/login?id=10#profile

| Part | Description |
|------|-------------|
| https | Protocol (Scheme) |
| example.com | Domain |
| 443 | Port |
| /login | Path |
| id=10 | Query String |
| #profile | Fragment |

---

## URL Components

### Scheme
Defines the protocol.

Examples:
- HTTP
- HTTPS
- FTP

### Host (Domain)
Identifies the website.

Example:
example.com

### Port
Default ports:
- HTTP → 80
- HTTPS → 443

### Path
Specifies the resource.

Example:
/login
/api/users

### Query String
Starts with ?

Example:

?id=5&role=admin

### Fragment
Starts with #

Example:

#about

---

## Cybersecurity Importance

Attackers often manipulate:
- Query Parameters
- URL Paths
- IDs

Possible attacks:
- IDOR
- SQL Injection
- Path Traversal

---

## Quick Revision

✔ URL = Web Address

✔ HTTP → 80

✔ HTTPS → 443

✔ Query starts with ?

✔ Fragment starts with #

# 03. HTTP & HTTPS

## HTTP

**HTTP (HyperText Transfer Protocol)** is used to transfer web data.

Characteristics:
- Plain text
- No encryption
- Port 80

---

## HTTPS

**HTTPS (HyperText Transfer Protocol Secure)** is HTTP + TLS/SSL Encryption.

Characteristics:
- Encrypted
- Secure
- Port 443

---

## HTTP vs HTTPS

| HTTP | HTTPS |
|-------|--------|
| Unencrypted | Encrypted |
| Port 80 | Port 443 |
| Less Secure | More Secure |
| Uses HTTP | Uses TLS/SSL |

---

## Why HTTPS?

Protects:
- Passwords
- Cookies
- Credit Card Details
- Personal Information

Prevents:
- Packet Sniffing
- MITM Attacks
- Session Hijacking

---

## SSL/TLS Handshake

Client
↓

Server

↓

Certificate Verification

↓

Session Key Generated

↓

Encrypted Communication

---

## Quick Revision

✔ HTTP = Port 80

✔ HTTPS = Port 443

✔ HTTPS uses TLS/SSL

✔ HTTPS encrypts communication

# 04. HTTP Messages

HTTP communication consists of two message types:

- HTTP Request
- HTTP Response

---

## HTTP Request

Sent by the client to the server.

Contains:
- Request Line
- Headers
- Blank Line
- Body (Optional)

---

## HTTP Response

Sent by the server.

Contains:
- Status Line
- Headers
- Blank Line
- Body

---

## Basic Structure

Request

METHOD /path HTTP/1.1

Headers

Body

---

Response

HTTP/1.1 200 OK

Headers

Body

---

## Why HTTP Messages Matter

Understanding HTTP helps:
- Analyze traffic
- Use Burp Suite
- Find vulnerabilities
- Debug APIs

---

## Quick Revision

✔ Client → Request

✔ Server → Response

✔ Messages contain:
- Start Line
- Headers
- Body

  ````markdown
# 05. HTTP Requests

## What is an HTTP Request?

An HTTP Request is sent by the **client (browser)** to the **web server** requesting a resource.

Example:

```
GET /index.html HTTP/1.1
Host: example.com
```

---

## Structure of an HTTP Request

```
Request Line

Headers

Blank Line

Body (Optional)
```

---

## Request Line

Contains:

- HTTP Method
- Path
- HTTP Version

Example:

```
GET /login HTTP/1.1
```

---

## HTTP Methods

### GET

Retrieves data.

Example:

```
GET /products
```

---

### POST

Sends data to the server.

Commonly used for:

- Login
- Registration
- File Upload

Example:

```
POST /login
```

---

### PUT

Updates an existing resource.

Example:

```
PUT /users/1
```

---

### DELETE

Deletes a resource.

Example:

```
DELETE /users/1
```

---

### PATCH

Updates only part of a resource.

Example:

```
PATCH /users/1
```

---

## HTTP Versions

HTTP/1.0
- One request per connection

HTTP/1.1
- Persistent connections

HTTP/2
- Faster
- Multiplexing
- Header Compression

HTTP/3
- Uses QUIC
- Faster and more secure

---

## Query Parameters

Used to send extra information.

Example:

```
?id=10&role=admin
```

Multiple parameters are separated using:

```
&
```

---

## Request Headers

Headers provide additional information.

Common Headers:

Host

```
Host: example.com
```

User-Agent

```
User-Agent: Chrome
```

Accept

```
Accept: text/html
```

Cookie

```
Cookie: session=abc123
```

Authorization

```
Authorization: Bearer token
```

Content-Type

```
Content-Type: application/json
```

---

## Request Body

Used mainly with:

- POST
- PUT
- PATCH

Common Formats:

### Form Data

```
username=admin
password=123
```

### JSON

```json
{
"name":"Arnav",
"age":20
}
```

### XML

```xml
<user>
<name>Arnav</name>
</user>
```

---

## Quick Revision

✔ GET → Read

✔ POST → Create

✔ PUT → Update

✔ PATCH → Partial Update

✔ DELETE → Delete

✔ Body mainly used in POST, PUT & PATCH
````

---

````markdown
# 06. HTTP Responses

## What is an HTTP Response?

An HTTP Response is sent by the **server** back to the **client** after processing a request.

---

## Structure

```
Status Line

Headers

Blank Line

Body
```

---

## Status Line

Contains:

- HTTP Version
- Status Code
- Status Message

Example:

```
HTTP/1.1 200 OK
```

---

## Response Headers

Common Headers:

Content-Type

```
Content-Type: text/html
```

Server

```
Server: nginx
```

Set-Cookie

```
Set-Cookie: session=abc123
```

Content-Length

```
Content-Length: 250
```

Location

```
Location: /login
```

---

## Response Body

Contains:

- HTML
- CSS
- JavaScript
- JSON
- Images

Example:

```html
<h1>Hello World</h1>
```

---

## Common Status Codes

### 1xx

Informational

Example:

```
100 Continue
```

---

### 2xx

Success

```
200 OK
201 Created
204 No Content
```

---

### 3xx

Redirection

```
301 Moved Permanently
302 Found
304 Not Modified
```

---

### 4xx

Client Errors

```
400 Bad Request
401 Unauthorized
403 Forbidden
404 Not Found
405 Method Not Allowed
```

---

### 5xx

Server Errors

```
500 Internal Server Error
502 Bad Gateway
503 Service Unavailable
504 Gateway Timeout
```

---

## Quick Revision

2xx → Success

3xx → Redirect

4xx → Client Error

5xx → Server Error
````

---

````markdown
# 07. HTTP Security Headers

Security headers improve web application security.

---

## Strict-Transport-Security (HSTS)

Forces HTTPS connections.

Example:

```
Strict-Transport-Security
```

---

## Content-Security-Policy (CSP)

Restricts what content the browser can load.

Helps prevent:

- Cross-Site Scripting (XSS)

---

## X-Content-Type-Options

```
nosniff
```

Prevents MIME-type sniffing.

---

## X-Frame-Options

Protects against:

- Clickjacking

Values:

```
DENY

SAMEORIGIN
```

---

## Referrer-Policy

Controls how much referrer information is shared.

---

## Permissions-Policy

Controls browser features such as:

- Camera
- Microphone
- Geolocation

---

## Why Security Headers Matter

They help defend against:

- XSS
- Clickjacking
- MIME Sniffing
- Information Leakage

---

## Quick Revision

HSTS → HTTPS Only

CSP → Prevent XSS

X-Frame-Options → Prevent Clickjacking

X-Content-Type-Options → Prevent MIME Sniffing
````

---

````markdown
# 08. Cookies & Sessions

## Cookies

Cookies are small pieces of data stored in the user's browser.

Uses:

- Authentication
- User Preferences
- Tracking
- Shopping Cart

Example:

```
session=abc123
```

---

## Session

A session stores user information on the server.

Flow:

```
User Logs In

↓

Server Creates Session

↓

Session ID Sent as Cookie

↓

Browser Sends Cookie in Every Request

↓

Server Identifies User
```

---

## Difference

| Cookies | Sessions |
|----------|----------|
| Stored in Browser | Stored on Server |
| Small Data | Larger Data |
| Can be Modified by User | Managed by Server |

---

## Cookie Attributes

HttpOnly

- JavaScript cannot access the cookie.

Secure

- Sent only over HTTPS.

SameSite

- Helps prevent CSRF attacks.

---

## Cybersecurity Importance

Attackers may target cookies through:

- Session Hijacking
- Cookie Theft
- XSS
- CSRF

Protect cookies using:

- HttpOnly
- Secure
- SameSite

---

## Quick Revision

✔ Cookies → Browser

✔ Sessions → Server

✔ HttpOnly → Prevent JS Access

✔ Secure → HTTPS Only

✔ SameSite → CSRF Protection
````

