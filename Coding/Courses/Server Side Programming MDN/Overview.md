## Web Server
1. On the *hardware* side, a web server is *a computer that stores web server software and a website's component files* (for example, HTML documents, images, CSS stylesheets, and JavaScript files). A web server connects to the Internet and supports physical data interchange with other devices connected to the web.
2. On the *software* side, a web server includes several parts that control how web users access hosted files. At a minimum, this is an _HTTP server_. An HTTP server is software that understands [URLs](https://developer.mozilla.org/en-US/docs/Glossary/URL) (web addresses) and [HTTP](https://developer.mozilla.org/en-US/docs/Glossary/HTTP) (the protocol your browser uses to view webpages). An HTTP server can be accessed through the domain names of the websites it stores, and it delivers the content of these hosted websites to the end user's device.

To publish a website, you need either a *static or a dynamic web server*.
A **static web server**, or stack, consists of a computer (hardware) with an HTTP server (software). We call it "static" because the server sends its hosted files as-is to your browser.
A **dynamic web server** consists of a static web server plus extra software, most commonly an _application server_ and a _database_. We call it "dynamic" because the application server updates the hosted files before sending content to your browser via the HTTP server.

## Server Side Code
server-side code is run on a web server and that its main role is to control _what_ information is sent to the user (while client-side code mainly handles the structure and presentation of that data to the user)

## Scale
- _vertical scaling_ (running your web application on more powerful hardware). 
- _scale horizontally_ (share the load by distributing your site across a number of web servers and databases) 
- _scale geographically_ because some of your customers are based a long way away from your server.

## Website Security
### Cross Site Scripting (XSS)
XSS is a term used to describe a class of attacks that allow an attacker to inject *client-side scripts through the website into the browsers* of other users.
Because the injected code comes to the browser from the site, the code is _trusted_ and can do things like send the user's site authorization cookie to the attacker.

#### Two Types of XSS
- *Reflected XSS*: when user content that is passed to the server is returned _immediately_ and _unmodified_ for display in the browser. For example, consider a site search function where the search terms are encoded as URL parameters, and these terms are displayed along with the results. An attacker can construct a search link that contains a malicious script as a parameter (e.g., `http://developer.mozilla.org?q=beer<script%20src="http://example.com/tricky.js"></script>`) and email it to another user. If the target user clicks this "interesting link", the script will be executed when the search results are displayed.
- _Persistent XSS_: occurs when the malicious script is _stored_ on the website and then later redisplayed unmodified for other users to execute unwittingly. For example, a discussion board that accepts comments that contain unmodified HTML could store a malicious script from an attacker. When the comments are displayed, the script is executed and can send to the attacker the information required to access the user's account.

#### Solution
The best defense against XSS vulnerabilities is to *remove or disable any markup that can potentially contain instructions to run the code*. For HTML this includes elements, such as `<script>`, `<object>`, `<embed>`, and `<link>`.

### SQL Injection
*SQL injection* vulnerabilities enable malicious users to *execute arbitrary SQL code on a database*, allowing data to be accessed, modified, or deleted irrespective of the user's permissions.

### Cross Site Request Forgery (CSRF)
CSRF attacks allow a *malicious user to execute actions using the credentials of another user without that user's knowledge or consent*.

A malicious user creates a form with hidden fields containing their bank details and an amount of money, then emails it to users of a particular site. The form is designed to look like a link to a "get rich quick" site, and if a user clicks on it, an HTTP POST request is sent to the server containing the transaction details and any client-side cookies associated with the site. The server checks the cookies to determine if the user is logged in and has permission to make the transaction.

One way to prevent this type of attack is for the server to require that `POST` requests include a *user-specific site-generated secret*. The secret would be supplied by the server when sending the web form used to make transfers. This approach prevents Josh from creating his own form, because he would have to know the secret that the server is providing for the user.


### Click Jacking
A malicious user *hijacks clicks meant for a visible top-level site and routes them to a hidden page beneath*.
As a *defense*, your site can prevent itself from being embedded in an iframe in another site by setting the appropriate HTTP headers. For example set `X-Frame-Options: DENY`.

### Denial of Service (DoS)
DoS is usually achieved by *flooding a target site with fake requests* so that access to a site is disrupted for legitimate users. The requests may be *numerous*, or they may *individually consume large amounts of resource* (e.g., slow reads or uploading of large files). 
DoS *defenses* usually work by identifying and *blocking "bad" traffic while allowing legitimate messages through*. These defenses are typically located before or in the web server (they are not part of the web application itself).


### Summary
Almost all of the security *exploits in the previous sections are successful when the web application trusts data from the browser*. Whatever else you do to improve the security of your website, you should *sanitize all user-originating data* before it is displayed in the browser, used in SQL queries, or passed to an operating system or file system call.
_User-originating data_ includes, but is not limited to data in URL parameters of `GET` requests, `POST` requests, HTTP headers and cookies, and user-uploaded files. **Always check and sanitize all incoming data**. Always assume the worst.