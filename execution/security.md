# API Authentication
Every registered API MUST be assigned a unique Client ID and a Client Secret as a part of an HTTP header. The Client Secret MUST NOT be shared. DO NOT solely rely on a Client ID for authentication.

# Access Control
Not every user has a right to every web service. This is vital, as you don't want administrative web services to be misused. The API key SHOULD be sent along as a cookie, body parameter, or HTTP message header to ensure that privileged collections or actions are properly protected from unauthorized use. Every API MUST TO BE authenticated before it can be used.

# Masking HTTP Headers
Server versioning information or any other sensitive information from the HTTP headers SHOULD BE removed/masked according to industry best practices. This prevents any form of targeted attacks since the vulnerabilities are mostly specific to the vendors.

# Session Management
RESTful web services SHOULD use session-based authentication, either by establishing a session token via a POST or by using an API key (Client ID and a Client Secret) as a POST body argument or as a cookie. Usernames, passwords, session tokens, API keys, and sensitive information MUST NOT appear in the URL, as this can be captured in web server logs, which makes them intrinsically valuable.

# Protect HTTP Methods
RESTful API often use GET (read), POST (create), PUT (replace/update) and DELETE (to delete a record). Not all of these are valid choices for every single resource collection, user, or action. Make sure the incoming HTTP method is valid for the session token/API key and associated resource collection, action, and record.

# HTTP Status Codes
HTTP defines status code. While designing a REST API, DON'T just use 200 for success or 404 for error. Every error message needs to be customized as to NOT reveal any unnecessary information. Here are some guidelines to consider for each REST API status return code. Proper error handle may help to validate the incoming requests and better identify the potential security risks. 

* 200 OK - Response to a successful REST API action.
* 400 Bad Request - The request is malformed, such as message body format error.
* 401 Unauthorized - Wrong or no authentication ID/password provided.
* 403 Forbidden - It's used when the authentication succeeded but authenticated user doesn't have permission to the request resource
* 404 Not Found - When a non-existent resource is requested
* 405 Method Not Allowed - The error checking for unexpected HTTP method. For example, the RestAPI is expecting HTTP GET, but HTTP PUT is used.
* 429 Too Many Requests - The error is used when there may be DOS attack detected or the request is rejected due to rate limiting

# Intput Validation
Everything you know about [input validation](https://www.owasp.org/index.php/Data_Validation)  applies to RESTful web services, but add 10% because automated tools can easily fuzz your interfaces for hours on end at high velocity. Help the user input high quality data into your web services, such as ensuring a Zip code makes sense for the supplied address, or the date makes sense. If not, reject that input. Also make sure that the output encoding is very strong for your application. Some other specific forms of input validations need to be implemented:

* Secure parsing: Use a secure parser for parsing the incoming messages. If you are using XML, make sure to use a parser that is NOT VULNERABLE to XXE and similar attacks.

* Strong typing: It's difficult to perform most attacks if the only allowed values are true or false, or a number, or one of a small number of acceptable values. Strongly type incoming data as quickly as possible.

* Validate incoming content-types: When POSTing or PUTting new data, the client will specify the Content-Type (e.g. application/xml or application/json) of the incoming data. The server SHOULD NEVER assume the Content-Type; it SHOULD ALWAYS check that the Content-Type header and the content are the same type. A lack of Content-Type header or an unexpected Content-Type header SHOULD result in the server rejecting the content with a 406 Not Acceptable response.

* Validate response types: It is common for REST services to allow multiple response types (e.g. application/xml or application/json, and the client specifies the preferred order of response types by the Accept header in the request. DO NOT simply copy the Accept header to the Content-type header of the response. Reject the request (ideally with a 406 Not Acceptable response) if the Accept header does not specifically contain one of the allowable types. Because there are many MIME types for the typical response types, it's important to document for clients specifically which MIME types should be used.

* XML input validation: XML-based services MUST ensure that they are protected against common XML based attacks by using secure XML-parsing. This typically means protecting against XML External Entity attacks, XML-signature wrapping etc.

#  Escape Content
This means removing any executable code that would cause the browser to do something you don’t want it to. Typically this means removing // &lt;![CDATA[ tags and HTML attributes that cause JavaScript to be evaluated. If you use standard data formats like JSON, you can use standard libraries which have been thoroughly checked by many professionals. However, DO NOT TRY TO DO THIS YOURSELF. Use a known library, or the auto-escaping features of your favorite template library. This needs to be done in the browser and on your server, if you allow users to submit data that is saved into a database.

# Restrict Testing Environment
THUMB Rule. No production data or any form of sensitive data to be used while testing the APIs in the testing environment.

#  Storing Tokens at Client Side
There are two ways to save authentication information in the browser:

* Cookies
* HTML5 Web Storage

In each case, you have to trust that browsers are implemented correctly, and that Website A can't somehow access the authentication information for Website B. In that sense, both storage mechanisms are equally secure. Problems can arise in terms of how you use them though.

- If you use cookies: The browser will automatically send the authentication information with every request to the API. This can be convenient so long as you know it's happening. Prevention against CSRF is a must while using this technique. It is also strongly recommended to use cookies with HTTPOnly and Secure flags set. This will allow the browser to send along the token for authentication purposes, but won’t expose it to the JavaScript environment.

- If you use HTML5 Web Storage: You have to write JavaScript that manages exactly when and what authentication information is sent.

# Protect against Cross-Site Request Forgery
For resources exposed by RESTful web services, it's important to make sure any PUT, POST, and DELETE request is protected from Cross Site Request Forgery. Typically, one would use a token-based approach. See Cross-Site Request Forgery (CSRF) Prevention Cheat Sheet for more information on how to implement CSRF-protection: 
https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF)_Prevention_Cheat_Sheet
CSRF is easily achieved even using random tokens if any XSS exists within your application, so PLEASE MAKE SURE you understand how to prevent XSS:
https://www.owasp.org/index.php/XSS_(Cross_Site_Scripting)_Prevention_Cheat_Sheet

# 12	Insecure direct object references:
A URL or even a POSTed form should NEVER contain an access control "key" or similar that provides automatic verification. A data contextual check needs to be done, server side, with each request.

# 13	Enable CORS for all APIs:
When your API's resources receive requests from a domain other than the API's own domain, you MUST enable cross-origin resource sharing (CORS) for selected methods on the resource. This amounts to having your API respond to the OPTIONS preflight request with at least the following CORS-required response headers:
*	Access-Control-Allow-Methods
*	Access-Control-Allow-Headers
*	Access-Control-Allow-Origin

# 14	Data in transit:
Unless the public information is completely read-only, the use of TLS v1.2 should be MANDATED, particularly where credentials, updates, deletions, and any value transactions are performed. The overhead of TLS is negligible on modern hardware, with a minor latency increase that is more than compensated by safety for the end user.

# 15	Message Integrity:
In addition to HTTPS/TLS, JSON Web Token (JWT) is an open standard that defines a compact and self-contained way for securely transmitting information between parties as a JSON object. JWT can not only be used to ensure the message integrity but also authentication of both message sender/receiver. The JWT includes the digital signature hash value of the message body to ensure the message integrity during the transmission.

# 16	Weak SSL/TLS Ciphers Support:
The encryption ciphers supported by the server may allow an attacker to eavesdrop on the connection. Verify the following guidelines:
*	When serving up content to your users, ONLY strong ciphers are enabled (128 bits and above).
*	When connecting to other remote systems ensure that your client DOES NOT connect using a weak cipher if the server supports it.
*	Renegotiation MUST be properly configured (e.g. Insecure Renegotiation MUST be disabled, due to MiTM attacks and Client-initiated Renegotiation MUST be disabled, due to Denial of Service vulnerability).
*	MD5 MUST NOT be used, due to known collision attacks.
*	RC4 MUST NOT be used, due to crypto-analytical attacks
*	Server SHOULD be protected from BEAST Attack 
*	Server SHOULD be protected from CRIME attack, TLS compression MUST be disabled 
*	Server SHOULD support Forward Secrecy

# 17	Mixed Content:
When serving up content to your users over SSL, it’s important that you DO NOT include content served over HTTP such as Images, JavaScript, Flash, or CSS. By mixing HTTP content with HTTPS content, you expose your users to man in the middle attacks and eliminate the security benefits that SSL/TLS provides.

# 18	SSL certificate validity – client and server:
In order for the communication to be set up, a number of checks on the certificates MUST be passed:	
*	Checking if the Certificate Authority (CA) is a known one (meaning one considered trusted);
*	Checking that the certificate is currently valid;
*	Checking that the name of the site and the name reported in the certificate match.

# 19	Certificate Requirements:
The following checklist NEEDS TO BE followed while using an SSL certificate:
*	X.509 certificates key length MUST be strong (e.g. if RSA or DSA is used the key MUST be at least 1024 bits).
*	X.509 certificates MUST be signed only with secure hashing algorithms (e.g. not signed using MD5 hash, due to known collision attacks on this hash).
*	Fully Qualified Domain Name (FQDN) certificates is a MANDATE. This is a certificate that has been issued with a name registered with an entity that manages a top-level domain (TLD). The differentiating characteristic about an FQDN is that it is unique. There is one controller and that controller determines who can have any name under that root.
*	NO USGAE of Wildcard SSL Certificate.
*	SHA-1 (or MD5) certificates SHOULD NOT BE used. The problem isn't the security of the server's real certificate, it's the client policy that allows the client to trust low-security certificates.

# 20	Penetration Testing:
An exhaustive penetration testing needs to be performed against all the developed APIs exposed to the public internet and within adidas internal network. For detailed understanding of the process, please contact the adidas Global IT Security Team.
