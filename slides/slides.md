 # Managing User State: Cookies, Sessions & Tokens  
**Author**: JJ Salley  

---

## Title Slide  
**Managing User State**  
*Cookies, Sessions & Tokens*  
How apps remember who you are

---

## The Big Question  
**How does a website remember you?**  
- You sign in once  
- Click around  
- Still logged in  
**Why?** HTTP is stateless - each request is independent. Let's explore how we add memory.

---

## Cookie-Based Authentication  
**Analogy**: Cloakroom Ticket  
- You hand in your coat (login)  
- Get a numbered ticket (cookie)  
- Show ticket to get coat (access protected content)

**How it works**: Browser automatically sends cookie with each request

---

## Cookies in Real Life  
**Examples**  
- Staying logged into Facebook  
- Shopping carts on Amazon  
- Remembering dark mode settings
- "Remember me" checkboxes

**Technical note**: Cookies can store session IDs or actual user data

---

## Cookie Security & Limitations  
**Modern Security Features**  
- **HttpOnly**: Prevents JavaScript access (XSS protection)
- **Secure**: Only sent over HTTPS
- **SameSite**: Prevents cross-site request forgery

**Limitations**  
- Size limit (~4KB)
- Domain restrictions
- Must be validated on each request

---

## Server-Side Sessions  
**Analogy**: Library Card  
- Get a card with a barcode (session ID)  
- Library (server) stores your info  
- Card just points to your record

**Key difference**: Only the session ID travels between browser and server

---

## Sessions in Real Life  
**Examples**  
- Online banking (auto-logout after inactivity)
- School portals  
- Insurance sites  
- Shopping checkout processes

**Security benefit**: Sensitive data stays on server, not in browser

---

## Session Management Details  
**Pros**  
- Server controls everything  
- Easy to invalidate (logout everywhere)
- Sensitive data never leaves server

**Cons**  
- Server must store session data (memory/database)
- Harder to scale across multiple servers
- Sessions can be lost if server restarts

---

## Token-Based Authentication  
**Analogy**: Hotel Keycard  
- Check in (login)  
- Get keycard with permissions (token)  
- Works until checkout (expiration)

**Key insight**: Token contains the information, not just a reference

---

## JWT Structure & Examples  
**JWT (JSON Web Token) Parts**:
- **Header**: Token type and signing algorithm
- **Payload**: User info and permissions  
- **Signature**: Verification that token hasn't been tampered with

**Real-world examples**:
- "Login with Google" on apps
- API access for mobile apps
- Microservices communication

---

## Token Advantages & Challenges  
**Pros**  
- Stateless on the server (no storage needed)
- Perfect for mobile and API access
- Easy to scale across multiple servers
- Self-contained (includes user info)

**Challenges**  
- Token revocation requires additional infrastructure
- Larger size than session IDs
- Sensitive to secure storage on client

---

## Token Revocation Solutions  
**Common approaches**:
- **Short expiration** + refresh tokens
- **Token blacklists** (defeats stateless benefit)
- **Token versioning** (increment user's token version on logout)
- **Logout endpoints** that notify all services

**Best practice**: Combine short-lived access tokens with longer refresh tokens

---

## Comparison Table  
| Feature            | Cookies           | Sessions         | JWT Tokens         |
|--------------------|------------------|------------------|--------------------|
| Server storage     | Optional         | Required         | No                 |
| Data location      | Browser          | Server           | Token itself       |
| Transport          | Cookie header    | Cookie header    | Authorization header* |
| Scaling            | Easy             | Challenging      | Very easy          |
| 3rd-party APIs    | Limited          | Limited          | Excellent          |
| Revocation         | Easy             | Easy             | Requires planning  |
| Security           | Good (with flags)| Excellent        | Good (if stored safely) |

*Tokens can also be sent in cookies for web apps

---

## When to Use Each Method  

**Choose Cookies when**:
- Traditional web applications
- Simple authentication needs
- Users primarily on desktop browsers

**Choose Sessions when**:
- High security requirements (banking, healthcare)
- Server-side rendered applications
- Need immediate logout capability

**Choose Tokens when**:
- Mobile applications
- API-first architecture
- Third-party integrations
- Microservices

---

## PromiseGrid's Approach  
**How does PromiseGrid manage user state?**  
- **JWTs in localStorage**  
  Agents send tokens with each request  
- **Ephemeral sessions**  
  Used for short-term, high-security operations  
- **Agent context headers**  
  Each message carries its own "identity badge"

**Why this hybrid approach?** Combines API flexibility with security for sensitive operations

---

## Security Best Practices  
**For all methods**:
- Always use HTTPS in production
- Implement proper logout functionality
- Set appropriate expiration times
- Monitor for suspicious activity

**Token-specific**:
- Store JWTs securely (avoid localStorage for sensitive apps)
- Use refresh token rotation
- Validate tokens on every request

---

## Analogy Recap  
- **Cookies** = Cloakroom ticket (simple, browser handles it)
- **Sessions** = Library card (server keeps the records)  
- **Tokens** = Hotel keycard (self-contained permissions)  
- **Hybrid approaches** = Different tools for different jobs

---


## Modern Trends  
**What's happening now**:
- **Passwordless authentication** (WebAuthn, magic links)
- **Zero-trust architecture** (verify every request)
- **OAuth 2.1** and **OpenID Connect** standardization
- **httpOnly + SameSite** cookies making a comeback for web apps

**The future**: Authentication methods will continue evolving, but these core concepts remain fundamental

---

## Final Thoughts  
Choose based on your specific needs:  
- **Security requirements** (how sensitive is the data?)
- **User experience** (mobile, web, or both?)  
- **Architecture** (monolith vs microservices?)
- **Team expertise** (what can you implement safely?)

**Remember**: You can mix approaches - many apps use multiple methods for different features

---

## Thank You  
Thanks for learning with me!  
Questions welcome.

--- 

 
