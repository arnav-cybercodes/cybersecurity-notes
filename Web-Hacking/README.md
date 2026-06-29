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
````
# 06. HTTP Responses

## What is an HTTP Response?

An HTTP Response is sent by the **server** to the **client (browser)** after processing an HTTP request.

---

## Structure of an HTTP Response

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

Common response headers:

### Content-Type

Specifies the type of content returned.

Example:

```
Content-Type: text/html
```

---

### Server

Specifies the web server software.

Example:

```
Server: nginx
```

---

### Set-Cookie

Creates a cookie in the browser.

Example:

```
Set-Cookie: session=abc123
```

---

### Content-Length

Specifies the response size.

Example:

```
Content-Length: 250
```

---

### Location

Redirects the client to another page.

Example:

```
Location: /login
```

---

## Response Body

Contains the actual data returned by the server.

Examples:
- HTML
- CSS
- JavaScript
- JSON
- Images

---

## HTTP Status Codes

### 1xx – Informational

```
100 Continue
```

---

### 2xx – Success

```
200 OK
201 Created
204 No Content
```

---

### 3xx – Redirection

```
301 Moved Permanently
302 Found
304 Not Modified
```

---

### 4xx – Client Errors

```
400 Bad Request
401 Unauthorized
403 Forbidden
404 Not Found
405 Method Not Allowed
```

---

### 5xx – Server Errors

```
500 Internal Server Error
502 Bad Gateway
503 Service Unavailable
504 Gateway Timeout
```

---

## Quick Revision

✔ 2xx → Success

✔ 3xx → Redirect

✔ 4xx → Client Error

✔ 5xx → Server Error
````
````
# 07. HTTP Security Headers

## What are Security Headers?

Security headers are HTTP response headers that improve the security of a web application.

---

## Strict-Transport-Security (HSTS)

Forces browsers to use HTTPS.

Example:

```
Strict-Transport-Security
```

Protects against:
- Protocol Downgrade
- SSL Stripping

---

## Content-Security-Policy (CSP)

Controls which resources the browser can load.

Protects against:
- Cross-Site Scripting (XSS)

---

## X-Content-Type-Options

Value:

```
nosniff
```

Prevents MIME-type sniffing.

---

## X-Frame-Options

Prevents Clickjacking attacks.

Values:

```
DENY
```

```
SAMEORIGIN
```

---

## Referrer-Policy

Controls how much referrer information is shared with other websites.

---

## Permissions-Policy

Controls browser permissions like:

- Camera
- Microphone
- Geolocation
- Fullscreen

---

## Why are Security Headers Important?

They help protect web applications from:

- Cross-Site Scripting (XSS)
- Clickjacking
- MIME Sniffing
- Information Leakage

---

## Quick Revision

✔ HSTS → Force HTTPS

✔ CSP → Prevent XSS

✔ X-Frame-Options → Prevent Clickjacking

✔ X-Content-Type-Options → Prevent MIME Sniffing

✔ Referrer-Policy → Control Referrer Information

✔ Permissions-Policy → Control Browser Features
````
````
# 08. Cookies & Sessions

## Cookies

Cookies are small pieces of data stored in the user's browser.

Common Uses:
- Authentication
- User Preferences
- Tracking
- Shopping Cart

Example:

```
session=abc123
```

---

## Sessions

A session stores user information on the server.

Flow:

```
User Logs In
      ↓
Server Creates Session
      ↓
Session ID Sent as Cookie
      ↓
Browser Sends Cookie with Every Request
      ↓
Server Identifies the User
```

---

## Cookies vs Sessions

| Cookies | Sessions |
|----------|----------|
| Stored in Browser | Stored on Server |
| Small Amount of Data | Larger Data |
| Can Be Modified by User | Managed by Server |

---

## Cookie Attributes

### HttpOnly

Prevents JavaScript from accessing the cookie.

---

### Secure

Cookie is sent only over HTTPS.

---

### SameSite

Helps prevent Cross-Site Request Forgery (CSRF).

---

## Security Risks

Attackers may target cookies using:

- Session Hijacking
- Cookie Theft
- Cross-Site Scripting (XSS)
- Cross-Site Request Forgery (CSRF)

---

## Best Practices

- Use HttpOnly
- Use Secure
- Use SameSite
- Use HTTPS
- Avoid storing sensitive information in cookies

---

## Quick Revision

✔ Cookies → Stored in Browser

✔ Sessions → Stored on Server

✔ HttpOnly → Blocks JavaScript Access

✔ Secure → HTTPS Only

✔ SameSite → Helps Prevent CSRF
````
````
## SQL (Structured Query Language)

### What is SQL?

SQL (Structured Query Language) is the standard language used to interact with **Relational Database Management Systems (RDBMS)** such as MySQL, PostgreSQL, MariaDB, Oracle Database, and Microsoft SQL Server.

SQL allows us to:

* Create databases and tables
* Insert data
* Retrieve data
* Update records
* Delete records
* Filter and sort data
* Perform calculations and aggregation

---

# Databases

A **database** is an organized collection of information stored electronically.

Example:

Instead of storing user information in text files:

```
Arnav
123@gmail.com
Password123
```

A database stores it in a structured format.

Example Table:

| id | name  | email                                   |
| -- | ----- | --------------------------------------- |
| 1  | Arnav | [123@gmail.com](mailto:123@gmail.com)   |
| 2  | John  | [john@gmail.com](mailto:john@gmail.com) |

---

# Types of Databases

## Relational Databases (SQL)

* Store data in tables
* Data organized into rows and columns
* Relationships exist between tables
* Uses SQL

Examples:

* MySQL
* PostgreSQL
* MariaDB
* Oracle
* SQL Server

---

## Non-Relational Databases (NoSQL)

Store data as:

* JSON
* Documents
* Key-Value
* Graph
* Collections

Examples:

* MongoDB
* Cassandra
* Redis

---

# Tables, Rows and Columns

### Table

A collection of related data.

Example:

```
Books
```

---

### Row

One complete record.

```
1 | Android Security | 2021
```

---

### Column

A single attribute.

```
Name
Price
Category
```

---

# Primary Key

A Primary Key uniquely identifies every row.

Example

```
book_id
```

Properties

* Unique
* Cannot be NULL
* Only one Primary Key per table

Example

| book_id | name |
| ------- | ---- |
| 1       | Nmap |
| 2       | Burp |

---

# Foreign Key

A Foreign Key links two tables.

Books Table

| book_id | author_id |
| ------- | --------- |
| 1       | 5         |

Authors Table

| author_id | name  |
| --------- | ----- |
| 5         | Craig |

Foreign Keys create relationships between tables.

---

# SQL CRUD Operations

CRUD =

* Create
* Read
* Update
* Delete

---

## CREATE

Create Database

```sql
CREATE DATABASE tools_db;
```

Create Table

```sql
CREATE TABLE hacking_tools(
id INT,
name VARCHAR(50)
);
```

---

## READ (SELECT)

Select everything

```sql
SELECT * FROM hacking_tools;
```

Specific columns

```sql
SELECT name, category FROM hacking_tools;
```

---

## UPDATE

```sql
UPDATE hacking_tools
SET category='Network'
WHERE id=2;
```

---

## DELETE

```sql
DELETE FROM hacking_tools
WHERE id=5;
```

---

# Database Commands

Create Database

```sql
CREATE DATABASE tools_db;
```

Show Databases

```sql
SHOW DATABASES;
```

Use Database

```sql
USE tools_db;
```

Show Tables

```sql
SHOW TABLES;
```

Describe Table

```sql
DESCRIBE hacking_tools;
```

or

```sql
DESC hacking_tools;
```

Drop Table

```sql
DROP TABLE hacking_tools;
```

Drop Database

```sql
DROP DATABASE tools_db;
```

---

# Table Modification

Add Column

```sql
ALTER TABLE hacking_tools
ADD version VARCHAR(20);
```

---

# SQL Clauses

## WHERE

Filters rows.

```sql
SELECT *
FROM books
WHERE id=3;
```

---

## DISTINCT

Returns only unique values.

```sql
SELECT DISTINCT category
FROM hacking_tools;
```

---

## GROUP BY

Groups rows together.

```sql
SELECT category,
COUNT(*)
FROM hacking_tools
GROUP BY category;
```

---

## ORDER BY

Ascending

```sql
ORDER BY amount ASC;
```

Descending

```sql
ORDER BY amount DESC;
```

---

## HAVING

Filters grouped results.

```sql
SELECT category,
COUNT(*)
FROM hacking_tools
GROUP BY category
HAVING COUNT(*)>2;
```

Difference:

WHERE → before grouping

HAVING → after grouping

---

# SQL Operators

## LIKE

Pattern Matching

```
% = any number of characters

_ = one character
```

Examples

```sql
WHERE name LIKE "%Hack%"
```

```sql
WHERE name LIKE "A%"
```

---

## AND

Both conditions must be TRUE.

```sql
WHERE category="Network"
AND amount>200;
```

---

## OR

Either condition can be TRUE.

```sql
WHERE category="Network"
OR category="Web";
```

---

## NOT

Negates a condition.

```sql
WHERE NOT category="Web";
```

---

## BETWEEN

Checks a range.

```sql
WHERE amount BETWEEN 100 AND 500;
```

---

## Comparison Operators

Equal

```sql
=
```

Not Equal

```sql
!=
```

Greater Than

```sql
>
```

Less Than

```sql
<
```

Greater Than or Equal

```sql
>=
```

Less Than or Equal

```sql
<=
```

---

# SQL Functions

## CONCAT()

Joins strings.

```sql
SELECT CONCAT(name," - ",category)
FROM hacking_tools;
```

---

## GROUP_CONCAT()

Combines values from multiple rows.

```sql
SELECT GROUP_CONCAT(name SEPARATOR ", ")
FROM hacking_tools;
```

---

## SUBSTRING()

Extract part of a string.

```sql
SELECT SUBSTRING(name,1,4)
FROM hacking_tools;
```

---

## LENGTH()

Returns string length.

```sql
SELECT LENGTH(name)
FROM hacking_tools;
```

---

## COUNT()

Counts rows.

```sql
SELECT COUNT(*)
FROM hacking_tools;
```

---

## SUM()

Adds values.

```sql
SELECT SUM(amount)
FROM hacking_tools;
```

---

## MAX()

Maximum value.

```sql
SELECT MAX(amount)
FROM hacking_tools;
```

---

## MIN()

Minimum value.

```sql
SELECT MIN(amount)
FROM hacking_tools;
```

---

# Useful SQL Tips

Largest value with its name

```sql
SELECT name, amount
FROM hacking_tools
ORDER BY amount DESC
LIMIT 1;
```

Amount not ending in 0

```sql
WHERE amount % 10 != 0
```

Multiple names in one row

```sql
GROUP_CONCAT(name SEPARATOR " & ")
```

---

# Burp Suite Basics

## What is Burp Suite?

Burp Suite is a Java-based web application security testing framework used by penetration testers to intercept, inspect, modify, and analyze HTTP/HTTPS traffic between a browser and a web server.

It acts as a proxy between the client and the target application.

```
Browser
    │
    ▼
Burp Proxy
    │
    ▼
Target Website
```

---

# Burp Suite Editions

## Community Edition

* Free
* Manual testing
* Suitable for learning
* Limited Intruder speed

---

## Professional Edition

Includes:

* Automated Vulnerability Scanner
* Fast Intruder
* Burp Collaborator
* API Integration
* Advanced Reporting
* Unlimited Extensions

---

## Enterprise Edition

Designed for organizations.

Features:

* Continuous automated scanning
* Dashboard
* Scheduled scans
* Centralized vulnerability management
* 
---

# Features of Burp Community Edition

## Proxy

* Intercepts HTTP/HTTPS requests and responses.
* Allows modifying requests before sending them.
* Core feature used in web application testing.

## Repeater

* Sends the same request multiple times.
* Useful for manually testing parameters and vulnerabilities.

## Intruder

* Automates sending multiple payloads.
* Used for fuzzing and brute-force attacks.
* Community Edition has limited speed.

## Decoder

* Encodes and decodes data.
* Supports URL, Base64, Hex and other formats.

## Comparer

* Compares two requests or responses.
* Highlights differences between them.

## Sequencer

* Analyzes randomness of session tokens and cookies.

## Extensions

* Burp supports extensions written in Java, Python (Jython), and Ruby.
* Additional extensions can be installed from the BApp Store.

---

# Burp Dashboard

The dashboard is divided into four sections:

### 1. Tasks

Displays background tasks such as passive crawling.

### 2. Event Log

Shows Burp events, warnings and errors.

### 3. Issue Activity

Shows vulnerabilities detected by automated scanning (Professional Edition).

### 4. Advisory

Displays detailed information about identified issues.

---

# Navigation

Burp is divided into modules:

* Dashboard
* Target
* Proxy
* Intruder
* Repeater
* Collaborator
* Sequencer
* Decoder
* Comparer
* Logger
* Organizer
* Extensions

Each module contains its own sub-tabs.

Useful shortcuts:

* Ctrl + Shift + D → Dashboard
* Ctrl + Shift + T → Target
* Ctrl + Shift + P → Proxy
* Ctrl + Shift + I → Intruder
* Ctrl + Shift + R → Repeater

---

# Settings

Burp has two types of settings.

## Global Settings

* Applied every time Burp starts.
* Affect the entire Burp installation.

## Project Settings

* Apply only to the current project.
* Not saved permanently in Community Edition.

Settings can be searched using the search bar.

---

# Burp Proxy

The Proxy sits between the browser and the target website.

Browser
↓
Burp Proxy
↓
Web Server

Functions:

* Intercept requests
* Forward requests
* Drop requests
* Modify requests
* Capture HTTP history
* Capture WebSocket traffic

Even with Intercept OFF, Burp still records traffic in HTTP History.

---

# HTTP History

Stores every captured request and response.

Useful for:

* Reviewing previous requests
* Finding hidden endpoints
* Sending requests to Repeater or Intruder

---

# Match and Replace

Automatically modifies requests or responses using predefined rules.

Useful for:

* Replacing headers
* Replacing cookies
* Modifying request values automatically

---

# Site Map

Target → Site Map

Displays every discovered page and endpoint.

Useful for:

* Mapping web applications
* Finding hidden pages
* Discovering APIs
* Finding unusual endpoints

Example:

/about/
/contact/
/products/
/admin/
/randomHiddenPage

---

# Scope

Scope tells Burp which websites belong to the assessment.

Advantages:

* Filters unrelated websites
* Reduces unnecessary traffic
* Makes testing easier

Add Scope:

Target
→ Right Click Host
→ Add To Scope

---

# Proxy Interception Rules

Rules determine which requests Burp should intercept.

Examples:

* Ignore images
* Ignore CSS
* Ignore JavaScript
* Ignore requests outside target scope

This keeps interception clean and focused.

---

# Burp Browser

Burp includes its own Chromium browser.

Advantages:

* Already configured with Burp Proxy
* No FoxyProxy setup required
* Automatically captures all traffic

Can be opened from:

Proxy
→ Open Browser

---

# Practical Lab

While exploring the Site Map, Burp can reveal endpoints that are not easily visible while browsing manually.

Example:

/5yjR2GLcoGoij2ZK

This hidden endpoint contained the room flag, demonstrating how Site Map helps discover hidden resources during web application testing.

---


