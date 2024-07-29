# Api security checklist:

## Input validation checklist:

1. Do not trust input parameters/objects.
2. Validate input: length / range / format and type.
3. Achieve an implicit input validation by using strong types like numbers,booleans, dates, times or fixed data ranges in API parameters.
4. Constrain string inputs with regexps.
5. Reject unexpected/illegal content.
6. Make use of validation/sanitation libraries or frameworks.
7. Define an appropriate request size limit and reject requests exceedingthe limit with HTTP response status 413 Request Entity Too Large.
8. Use a secure parser for parsing the incoming messages. If you areusing XML, make sure to use a parser that is not vulnerable to XXE andsimilar attacks.
9. Use the proper HTTP method according to the operation: GET (read),POST (create), PUT/PATCH (replace/update), and DELETE (to delete arecord), and respond with 405 Method Not Allowed if the requestedmethod isn't appropriate for the requested resource.
10. Validate user input to avoid common vulnerabilities (e.g. XSS, SQL-Injection, Remote Code Execution, etc.).
11. Don't use any sensitive data (credentials, Passwords, security tokens,or API keys) in the URL, but use standard Authorization header.
12. Use an API Gateway service to enable caching, Rate Limit policies (e.g.Quota, Spike Arrest, or Concurrent Rate Limit) and deploy APIsresources dynamically.1.

## Content type validation

1. Reject requests containing unexpected or missing content typeheaders with HTTP response status 406 Unacceptable or 415Unsupported Media Type.
2. For XML content types ensure appropriate XML parser hardening, seethe XXE cheat sheet.
3. Avoid accidentally exposing unintended content types by explicitlydefining content types e.g. Jersey (Java)@consumes("application/json"); @produces("application/json"). Thisavoids XXE-attack vectors for example.
4. Do NOT simply copy the Accept header to the Content-type header ofthe response.
5. Reject the request (ideally with a 406 Not Acceptable response) if theAccept header does not specifically contain one of the allowable types.
6. Ensure sending intended content type headers in your responsematching your body content e.g. application/json and notapplication/javascript.

## Authentication

1. Don't use Basic Auth. Use standard authentication instead (e.g.JWT, OAuth).
2. Don't reinvent the wheel in Authentication, token generation,password storage. 
3. Use Max Retry and jail features in Login.
4. Use encryption on all sensitive data.

## JWT (JSON Web Token)

1. Use a random complicated key (JWT Secret) to make brute forcingthe token very hard.
2. Don't extract the algorithm from the header. 
3. Force the algorithm in the backend (HS256 or RS256).Make token expiration (TTL, RTTL) as short as possible.
4. Don't store sensitive data in the JWT payload, it can be decoded easily.
5. Ensure JWTs are integrity protected by either a signature or a MAC.
6. Do not allow the unsecured JWTs: {"alg":"none"}.
7. In general, signatures should be preferred over MACs for integrityprotection of JWTs.

## Management Endpoints

1. Avoid exposing management endpoints via Internet.
2. If management endpoints must be accessible via the Internet, makesure that users must use a strong authentication mechanism, e.g.multi-factor.
3. Expose management endpoints via different HTTP ports or hostspreferably on a different NIC and restricted subnet.
4. Restrict access to these endpoints by firewall rules or use of accesscontrol lists.

## API Keys

1. Enforce API keys for every request to the protected endpoint.
2. Return 429 Too Many Requests HTTP response code if requestsare coming in too quickly.
3. Revoke the API key if the client violates the usage agreement.
4. Do not rely exclusively on API keys to protect sensitive, critical orhigh-value resources.

## Error Handling

1. Respond with generic error messages - avoid revealing details of the failure unnecessarily.
2. Do not pass technical details (e.g. call stacks or other internal hints)to the client.

## Audit Logs

1. Write audit logs before and after security related events.
2. Consider logging token validation errors in order to detect attacks.
3. Take care of log injection attacks by sanitising log data beforehand.

## API Outpu Checks

1. Send X-Content-Type-Options: nosniff header.
2. Send X-Frame-Options: deny header.
3. Send Content-Security-Policy: default-src 'none' header
4. Remove fingerprinting headers - X-Powered-By, Server, X-AspNet-Version, etc.
5. Force content-type for your response. If you return application/json,then your content-type response is application/json.
6. Don't return sensitive data like credentials, Passwords, or securitytokens.
7. Return the proper status code according to the operationcompleted. (e.g. 200 OK, 400 Bad Request, 401 Unauthorized, 405Method Not Allowed, etc.).

## API Pentest Checklist

1. Observe each parameter in every module of API, understand how thedata is transferred from source to destination. Try to play with theparameter by tampering them
   
2. Identify if the API has any authorization token if it is having then remove that authorization token and see application response. Insome cases, if authorization is not implemented correctly then API might give you access to forbidden assets of application.
   
3. Analyze and check each module with a different access level of userex: admin, moderator, normal user

4. Check whether admin modules can be accessed via the restricted user

5. Identify the parameters which may vulnerable to IDOR typevulnerabilities such as id=1234 and also look at the cookies formanipulating the Ids.
   
6. Check injection vulnerabilities by inserting special characters in allparameters in a request and check the response from the server. Ifyou find any stack traces then use the information for further exploitation.
   
7. Insert greater than, less than (<,>) characters in all parameters and seeresponse whether the application encoding them as > and <. If anapplication doesn’t escape any special characters then the applicationmay be vulnerable to client-side attacks such as XSS (cross-sitescripting).
   
8. Modify the content-type server header for understanding the XMLentity injection attack. Example: change content Application/JSONto application/XML and insert the XML entity payload to find theXML entity injection.
   
9.  Test for API Input Fuzzing (for this you can use an open-source fuzzingtool called Fuzzapi
    
10. Test for API Injection Attacks:
    Test for SQL Injection (using a tool called SQLmap)
    Test for Command Injection (using a tool called Commix)
    Test for Parameter Tampering
    Test for Unhandled HTTP Methods

11. Test for File Upload vulnerability
12. Test for XML Bomb (DoS)
13. Test for Session fixation
14. Test for XML Signature wrapping
15. Test for Host Cipher Support/ Valid Certificate/ Protocol Support
16. Test for Authentication based attacks
17. Test for Replay attacks

## Tools
Fiddler, Burp Suite, Acunetix/IBM Security, AppScan, ZAPProxy, Curl, SOAP UI, etc.

## Practices
OWASP,  OSSTMM, WASC,CREST, NIST

