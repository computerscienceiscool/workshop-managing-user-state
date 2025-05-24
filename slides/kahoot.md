# Kahoot! Questions: Managing User State  
**Topic**: Cookies, Sessions & Tokens  
**Author**: JJ Salley

---

## Part 1: Scenario-Based Questions (20)

3. At a hotel, you check in and receive a keycard programmed with your room access and valid only during your stay.  
   - A) Cookie-based authentication  
   - B) Server-side sessions  
   - C) Token-based authentication*  
   - D) API keys  

4. You check out books at a library by presenting a membership card that the librarian scans to look up your account.  
   - A) Cookie-based authentication  
   - B) Server-side sessions*  
   - C) Token-based authentication  
   - D) Biometric authentication  

5. Your transit day pass has the expiry date printed on it; validation is offline at each turnstile.  
   - A) Cookie-based authentication  
   - B) Server-side sessions  
   - C) Token-based authentication*  
   - D) RFID badge  


7. You buy a movie ticket with a barcode encoding your seat number; the scanner reads it to admit you.  
   - A) Cookie-based authentication  
   - B) Server-side sessions  
   - C) Token-based authentication*  
   - D) Paper ticket  

8. Your gym membership card is swiped and checked against the gym’s database before you enter.  
   - A) Cookie-based authentication  
   - B) Server-side sessions*  
   - C) Token-based authentication  
   - D) PIN code  


10. You pay for parking and get a printed receipt showing your paid-until time; the parking attendant checks it visually.  
    - A) Cookie-based authentication  
    - B) Server-side sessions  
    - C) Token-based authentication*  
    - D) Mobile app  

11. An airline boarding pass QR code encodes flight and seat details that are validated at the gate.  
    - A) Cookie-based authentication  
    - B) Server-side sessions  
    - C) Token-based authentication*  
    - D) Paper boarding pass  

12. At an amusement park, you wear a wristband that’s scanned at each ride and checked against a backend system.  
    - A) Cookie-based authentication  
    - B) Server-side sessions*  
    - C) Token-based authentication  
    - D) RFID implant  

13. An e-commerce site stores a small file in your browser so you stay logged in as you browse.  
    - A) Cookie-based authentication*  
    - B) Server-side sessions  
    - C) Token-based authentication  
    - D) LocalStorage  

14. A bank website sets a random identifier in your browser and keeps all account state on its servers.  
    - A) Cookie-based authentication  
    - B) Server-side sessions*  
    - C) Token-based authentication  
    - D) API key  

15. A single-page app stores a JSON Web Token in localStorage and sends it with each API call.  
    - A) Cookie-based authentication  
    - B) Server-side sessions  
    - C) Token-based authentication*  
    - D) Form-based authentication  

16. Facebook sets a small file in your browser to remember your login across pages.  
    - A) Cookie-based authentication*  
    - B) Server-side sessions  
    - C) Token-based authentication  
    - D) OAuth  


19. Amazon uses a small browser file to keep track of your shopping cart between visits.  
    - A) Cookie-based authentication*  
    - B) Server-side sessions  
    - C) Token-based authentication  
    - D) WebSockets  

20. A RESTful API requires clients to include a signed token in an Authorization header for every request.  
    - A) Cookie-based authentication  
    - B) Server-side sessions  
    - C) Token-based authentication*  
    - D) Basic authentication  

---

## Part 2: Method-Specific Pros & Cons

### A. Cookie-Based Authentication (5 Questions)

1. Which is a unique security risk for cookie-based authentication?  
   - A) Susceptibility to cross-site request forgery (CSRF) attacks*
   - B) Need for a session database  
   - C) Token expiry complexity  
   - D) Lack of browser support  

2. What is a size limitation drawback of cookies?  
   - A) Maximum ~4 KB per cookie*  
   - B) Unlimited size  
   - C) Must be ASCII only  
   - D) Requires encryption  

3. Which header automatically sends all cookies back to the server?  
   - A) Cookie*  
   - B) Authorization  
   - C) Set-Cookie  
   - D) Content-Type  

4. What is an advantage of cookie-based auth?  
   - A) Built-in browser support without extra code*  
   - B) No need for HTTPS  
   - C) Stateless server logic  
   - D) Works without headers  

5. Which scenario highlights a drawback of cookies?  
   - A) Every request carries cookie data, adding overhead*  
   - B) Tokens can’t expire  
   - C) Sessions require no cleanup  
   - D) Cookies never get deleted  

### B. Server-Side Sessions (5 Questions)

1. Which is a key benefit of server-side sessions?  
   - A) Centralized invalidation of user state*  
   - B) No server storage needed  
   - C) Works without cookies  
   - D) Stateless design  

2. What scalability concern arises with server-side sessions?  
   - A) Need to replicate or shard session storage*  
   - B) Vulnerability to token leaks  
   - C) Browser compatibility issues  
   - D) Lack of standardization  

3. Which is a con of server-side sessions?  
   - A) Storage overhead on the server*  
   - B) Cannot expire automatically  
   - C) No way to revoke instantly  
   - D) Always stateless  

4. What must you implement to avoid stale server sessions?  
   - A) Periodic session cleanup or eviction*  
   - B) Client-side token introspection  
   - C) Larger cookie limits  
   - D) Cookie encryption  

5. Which scenario shows a security advantage of sessions over cookies?  
   - A) Sensitive data never travels to the client*  
   - B) Client holds full user data  
   - C) Tokens get stored in localStorage  
   - D) No need to validate requests  

### C. Token-Based Authentication (5 Questions)

1. What is a primary advantage of token-based authentication?  
   - A) No server-side session store required*  
   - B) Built-in browser cookie support  
   - C) Limited to web browsers  
   - D) Always encrypted  

2. Which is a common challenge with token revocation?  
   - A) Tokens often remain valid until expiry unless a blacklist is used*  
   - B) Tokens cannot expire  
   - C) Require server-side database for every request  
   - D) Always insecure  

3. Why are tokens ideal for third-party integrations?  
   - A) They follow open standards (OAuth, JWT)*  
   - B) They require no headers  
   - C) They never expire  
   - D) They use cookies by default  

4. What is a client-side storage risk for tokens?  
   - A) Storing in localStorage exposes them to XSS attacks*  
   - B) They cannot be encrypted  
   - C) They require server cleanup  
   - D) They must be <4 KB  

5. Which advantage comes from embedding claims inside a token?  
   - A) Faster validation without a database lookup*  
   - B) You must call back to the server each time  
   - C) No revocation mechanism  
   - D) Standard browser handling  

---

## Part 3: General Multiple-Choice Questions (4)

1. Which HTTP header does the server use to send a cookie to the client?  
   - A) Set-Cookie*  
   - B) Cookie  
   - C) Authorization  
   - D) Content-Type  

2. In a JSON Web Token (JWT), which field in the header specifies the signing algorithm?  
   - A) `alg`*  
   - B) `typ`  
   - C) `exp`  
   - D) `aud`  

3. Which protocol is most commonly associated with token-based authentication in web apps?  
   - A) OAuth 2.0*  
   - B) FTP  
   - C) SMTP  
   - D) SOAP  

4. Which user state method typically does **not** require any server-side session storage?  
   - A) Token-based authentication*  
   - B) Cookie-based authentication  
   - C) Server-side sessions  
   - D) Basic authentication  
