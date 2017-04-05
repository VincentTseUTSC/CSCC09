## Lecture 1 - HTML & CSS
* Advantages of developing software as web applications as posed to stand alone dekstop application?
	* Easy to deploy and maintain
	* No installation required

	Trade off: Security (MITM, injections, etc)

* Differences between HTML, JavaScript and CSS, and what they're used for?
	* HTML - Content, JS - functionality, CSS - styling

* Beyond simply rendering HTML in the browser, why is CSS useful?
	* Aside from rendering, HTML and CSS are also used for outside screen rendering such as printing and accessibility.

* What are the 3 methods to add CSS and Javascript into HTML?
	* In-line
	* Link
	* Embedded

* What is a difference between an id attribute and a class attribute?
	* ID should be unique to 1 HTML element
	* Class can be applied to a list of HTML elements

* What are the differences between HTML and XHTML?
	* XHTML is eXtensible HTML
	* XHTML is more strictly typed than HTML and is defined as an XML application
	* XHTML elements must be properly nested, closed, in lower case and document must have one root

* What are the new features brought by HTML5?
	* Canvas
	* SVG
	* Audio
	* Video
	* Colour
	* Datetime

## Lecture 2 - JavaScript
* How does Java and Javascript compare?
	* JavaScript is not actually a part of the Java platform
	* JavaScript is loosely typed while Java is strictly typed

* What is the difference between console.log and document.write?
	* Different output streams, console.log writes to the developer console while document.write writes to the HTML document (DOM)

* What is the DOM?
	* Document Object Model
	* A tree with document being the root and every element in the HTML being rendered as nodes on the tree

* What can we do/don’t do programmatically with Javascript running in the browser?
	* JavaScript has no access to file systems, sockets, shell, cross origin sharing policy
	* JavaScript can access the DOM, parts of the browset, http request, web sockers and web workers

* What is event-based programming and why is it relevant for web development?
	* Events trigger on user inputs facilitated by event listeners and event handlers
	* Makes it very easy to develop due to predictable user interactions and non-invasive fixes dealing with specific events rather than core functionalities

## Lecture 3 - Web API
* What is HTTP?
	* HyperTextTransferProtocol
	* Application protocol for transfering files

* What are the different components of a URL?
	* Protocol
	* Server
	* Path
	* Resource
	* Query String
	* Parameters

* Components of HTTP Request
	* Command (Get, Post, etc)
	* Header
	* Query String
	* Body (optional)

* Components of HTTP Response
	* Header
	* Status
	* Body (optional)

* HTTP Response codes
	* 100 - Information
	* 200 - Ok
	* 300 Redirect
	* 400 Client error
	* 500 Server error

* Main HTTP requrest methods
	* GET
	* POST
	* PATCH
	* DELETE
	* PUT

* What is a safe method? What is a idempotent method?
	* A safe method if a call that does not alter the database
	* GET
	* Idempotent method - multiple requests have same effect as single request
	* PUT and DELETE

* What is RESTful API?
	* Representative State Transfer
	* Stateless client-server communication

* RESTful principles
	* CRUD

## Lecture 4 - Storing Data
* When do browsers perform HTTP requests? For each situation, what method is used or can be used?
	* When Ajax requests are made from the JavaScript
	* Follow CRUD

* What are the different ways to encode the HTTP request body? What are they used for? How does the browser tells the server which encoding is used?
	* Encode using Content-Type
	* multipart/form-data (Large payload)
	* application/x-www-form-urlencoded

* Can you read the content of a file stored locally in Javascript executed in the browser? In other words, is it possible to obtain a file handler in Javascript? If so, how?
	* It is possible through file metadata and FileReader

* How are uploaded files sent to the server? What is the best body encoding for that purpose? Why?
	* POST call
	* Through multipart form-data
	* Does not clog up bandwitdth by breaking up into packets, can handle large payload (compression)
	* Encrypted thus secure

* What is a mimetype? Why is it useful?
	* Multipurpose Internet Mail Extentsion
	* Defines the format of the document exchanged on the internet
	* text, HTML, image, JSON, etc

* What are the pros/cons of using SQL vs NoSQL databases?
	* SQL has tables and tuples, query using SQL, good for transactions (ACID), but inadequate for big data
	* NoSQL uses key/value pairs, uses API style querying, good for big data, but lacks consistency (non-ACID)

## Lecture 5 - Managing Users
* What is a cookie?
	* Key/Value pairs sent back and forth between client and server

* What can you store in a cookie?
	* Strings since cookie is a text file

* Can you read/write a cookie on the client? On the server?
	* Both client and server can read/write the cookie

* What is the difference between cookie and the HTML5 local storage?
	* Server has no access to local storage

* What does it mean for HTTP to be stateless?
	* The server does not care which socket they arrive from, the server does not keep information or status with each HTTP request

* How can we make HTTP stateful using sessions?
	* Assign session IDs to each user

* How are sessions generated?
	* Unique session ID generated from server and passed to client
	* Stored in cookie
	* Session key/value pair stored in server

* What are the properties of the session id?
	* Unique
	* Stored in cookie
	* Unforgable
	* Bound to key/value pair

* Can you read/write a session on the client? On the server?
	* Both server and client can read the sessionID
	* Client does not have access to session key/value pairs

* How does basic authentication work exactly? How does it compared to using a POST request to send the login and password?
	* Stateless authentication
	* Sent in clear base64-encoding in the header
	* Versus POST, the password is stored in different areas (body vs header)

* How does third-party authentication like OAuth work?
	* User goes to login page of resource X
	* User is redirected to Authorization server
	* User authenticates and logs in
	* Authorization server gives token
	* User is redirected to resource X
	* Resource X accepts token
	* Resource X returns resources

* How are sessions useful for authentication?
	* Allows user to stay logged in and authenticate using third party authentication

* When signin up, how is the username and password sent from the browser to the server?
	* via HTTPS/SSL and the username and password is encrypted

* What is the correct way to store user passwords? What is stored in the database exactly?
	* Salted hash

* How are passwords verified?
	* The server adds the salt and checks if it matches the salted hash

## Lecture 7 - Security
* What is the same-origin policy? When is it violated? How does the browser handle such a violation?
	* Resources must come from the same domain, host, port
	* Elements under same-origin policy: Ajax, Forms
	* It is violated when the new domain is different than the current
	* Browser default blocks it

* What is an iframe? How does it work? How is it related to the same-origin policy?
	* Opens a viewport for third party HTML/JS to be loaded
	* It is allowed within same-origin policy because things in the iframe has no access to the DOM of the host

* What is JSON with padding (JSON-P)? How does it work? How is it related to the same-origin policy?
	* JSON-P is a way to get around the same-origin policy. The Ajax requests are not made usint XHTTP request, but rather put into a script tag into the header.

* What is cross-origin ressource sharing (CORS)? How does it work? How is it related to the same-origin policy?
	* A mechanism that allows resource sharing from different domains by describing new HTTP headers

* What is an insufficient transport layer protection? Why is it bad?
	* Insufficient security on web flow where SSL is not used everywhere within the application, resulting in leaked session IDs

* What is HTTPS? What does it provide terms of security?
	* HTTP-Secured, requires a Certified Authenticate certificate for API calls to be made on the website. This means that the website is trusted by browsers and is secure

* What is a certificate? What does it contain? Who generates this certificate? Who uses it?
	* Certificate is an electronic document used to prove ownership of a public key. It includes information about the public key, owner and a digital signature from an entity that has verified the contents. Anyone can make an self-signed certificate, only CA can issue signed certificate. The browser uses the certificate to verify the identity of a website.

* What does it mean when the browser says that the website is secure (green lock)?
	* The certificate for the website is verified by a Certificate Authority. Condifentiality and Integrity.

* What does it mean when the browser says that the website is not secure (red cross)?
	* The website's certificate is not signed or it is self signed, meaning that the contents are not verified and potentially expose the client to risks

* What is a mixed-content vulnerability? Why is it bad?
	* When a secure HTTPS website makes HTTP ajax requests. It is bad because it exposes sensitive information in the cookies such as session ID.

* How can it be mitigated?
	* ALWAYS HTTPS

* What is an SQL injection vulnerability (SQLi)? What could be the consequences if such a vulnerability is exploited?
	* Attack can inject SQL or noSQL code and bypass authentication and  retrieve, add, modify or elete information. Example: password = "1 == 1"

* How can SQLi vulnerabilities be mitigated?
	* Validate inputs, use a query API

* Is using a NoSQL database a good way to mitigate SQL injection vulnerabilities?
	* No, still need to do validation

* What is a content spoofing vulnerability (CSRF)? What could be the consequences if such a vulnerability is exploited?
	* Content spoofing - Attackers can inject HTML tags that leads to illegitimate websites

* How can content spoofing vulnerabilities be mitigated?
	* Protect legitimate requests with a CSRF token

* What is a cross-site scripting vulnerability (XSS)? What could be the consequences if such a vulnerability is exploited?
	* Attacker injects JavaScript code that will be executed by the browser
	* Inject illegitimate content - same as content spoofing
	* Inject illegitimate HTTP request - same as CSRF
	* Steal sessionID from cookie
	* Steal user's username and password

* How can content spoofing vulnerabilities be mitigated?
	* Sanitize input

* What is a cross-site request forgery vulnerability (CSRF)? What could be the consequences if such a vulnerability is exploited?
	* CSRF - attacker injects URL based HTML tags into website that the browser will retreive normally, causes the victim to perform unwanted things.

* How can content spoofing vulnerabilities be mitigated?
	* Protect legitimate requests with a CSRF token