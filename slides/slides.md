 

# Managing User State: Cookies, Sessions & Tokens Explained  
**Author**: JJ Salley

---

## Introduction  
When you log in to a website or use a mobile app, the system needs a way to remember “who you are” as you move around pages or features. That’s called **managing user state**. In this talk, we’ll explore three common methods—cookies, sessions, and tokens—using everyday analogies so you can explain them to friends and family.

By the end of this session, you’ll be able to:
- Describe each method in simple terms.  
- Use analogies from non-technical life to make the ideas stick.  
- Understand how PromiseGrid manages user state in its web and agent components.

---

## 1. Cookie-Based Authentication  
### How it works  
1. You log in with a username and password.  
2. The server verifies your credentials and then sends you a small file called a **cookie**.  
3. Your browser stores that cookie and automatically sends it with every request.

### Real-world analogy: Cloakroom ticket  
- **You** hand over your coat at a cloakroom (enter credentials).  
- You receive a numbered ticket (cookie).  
- Whenever you want your coat back (access a protected page), you hand in the ticket—no need to show ID again.  
- When you leave, you return the ticket and the cloakroom deletes your record (logout or session expiry).

### Pros & Cons  
- **Pros**: Transparent to the user; works in any browser.  
- **Cons**: Cookies can be stolen or manipulated, so the server must validate each request.

---

## 2. Server-Side Sessions  
### How it works  
1. After login, the server creates a **session record** in its database.  
2. You still get a cookie, but it only contains a random **session ID**.  
3. Each time you interact, the server looks up your session ID in its database for details (permissions, last activity).

### Real-world analogy: Library membership  
- You join a library and get a paper membership card with a barcode (session ID).  
- The library’s computer stores your borrowing history and permissions.  
- When you check out books, the librarian scans your card to look up your account.  
- When your membership expires, the card still looks valid but the library system rejects it.

### Pros & Cons  
- **Pros**: Server controls all data; you never expose sensitive info in the browser.  
- **Cons**: Requires storage and cleanup on the server; scaling can be more complex.

---

## 3. Token-Based Authentication  
### How it works  
1. You authorize an app (e.g., a finance tracker) to access your account without giving it your password.  
2. The server issues a **token** (often a JSON Web Token, or JWT) that encodes who you are, what you can do, and when it expires.  
3. The app sends the token in an `Authorization` header with each request—no cookies needed.

### Real-world analogy: Hotel keycard  
- You check in at a hotel (authenticate) and receive a keycard programmed with your room access and valid only for your stay.  
- You can use the card everywhere in the hotel (room, gym, pool) but only within the permissions granted.  
- When you check out, the card deactivates automatically.

### Pros & Cons  
- **Pros**: Stateless on the server (no session store needed); ideal for mobile and third-party integrations.  
- **Cons**: Token revocation can be tricky; tokens must be stored securely on the client.

---

## 4. Comparing the Approaches

| Feature            | Cookies Only           | Server Sessions       | Tokens (JWT)           |
|--------------------|------------------------|-----------------------|------------------------|
| Server storage     | No                     | Yes                   | Optional               |
| Client transport   | Cookie header          | Cookie header         | Authorization header   |
| Scalability        | Easy                   | Needs session cleanup | Very easy              |
| Third-party apps   | Hard                   | Hard                  | Designed for it        |
| Revocation         | Server-driven          | Server-driven         | Requires extra mechanism |

---

## 5. Managing User State in PromiseGrid  
Steve (“stevegt”) and the PromiseGrid community have built a decentralized agent framework where each user or agent needs a reliable way to maintain context. In PromiseGrid’s web UI and MCP-based services, state management can be implemented via:

- **JWTs stored in browser localStorage**  
  Agents include their token in each request to the PromiseGrid registry, carrying identity and permissions without server-side sessions.

- **Ephemeral session store**  
  For high-security endpoints, PromiseGrid can issue short-lived session IDs backed by an in-memory store, ensuring rapid cleanup and minimal persistence.

- **Agent context promises**  
  Within the MCP protocol, context headers act like tokens—each message carries a “promise” of who the sender is and when the context expires, enabling stateless verification by any compliant server.

---

## Conclusion  
By using the cloakroom, library, and hotel analogies, you now have memorable hooks to explain how cookies, sessions, and tokens keep track of users. Whether you’re building a traditional web app or a decentralized PromiseGrid service, choosing the right method ensures both security and a smooth user experience.

Thank you

---
 

