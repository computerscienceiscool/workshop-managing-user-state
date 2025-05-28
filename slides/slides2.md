# Client-Side Web State Persistence

---

## The Big Question – How does a website remember you?

- Websites use HTTP, which is stateless.
- Cookies, sessions, and tokens help "remember" users.
- These tools add memory to otherwise forgetful systems.

---

## Cookie-Based Authentication – Cloakroom Ticket

- Like a coat check ticket.
- Cookie = small identifier in your browser.
- Sent with every request to identify you.

---

## Cookies in Real Life

- Used for:
  - Staying logged in
  - Saving cart contents
  - Remembering preferences
- Browser sends them automatically.

---

## Cookie Security & Limitations

- Small in size.
- Can be secured:
  - HTTPOnly
  - Secure
  - SameSite
- Can’t store sensitive data directly.

---

## Server-Side Sessions – Library Card

- Like a library card pointing to your info.
- Server keeps the data.
- Browser has just a session ID.

---

## Sessions in Real Life

- Common in:
  - Banking
  - Schools
  - Checkouts
- Server maintains control and security.

---

## Session Management Details

- Server handles session lifetime.
- Can log users out or expire sessions.
- Need storage strategy for scaling.

---

## Token-Based Authentication – Hotel Keycard

- JWT = Digital keycard with info inside.
- Self-contained and portable.
- Doesn’t need server-side storage.

---

## JWT Structure & Examples

- Header: type + algorithm
- Payload: user info + permissions
- Signature: prevents tampering

---

## Token Advantages & Challenges

- Scales easily.
- Great for mobile & APIs.
- Needs strategy for revocation.

---

## Token Revocation Solutions

- Use short expiration times.
- Add refresh tokens.
- Track invalid tokens or version numbers.

---

## Updated Comparison Table

| Feature          | Cookies      | Sessions     | JWT Tokens   |
|------------------|--------------|--------------|--------------|
| Server storage   | Optional     | Required     | No           |
| Data location    | Browser      | Server       | Token        |
| Transport        | Cookie header| Cookie header| Auth header  |
| Scaling          | Easy         | Challenging  | Very easy    |
| 3rd-party APIs   | Limited      | Limited      | Excellent    |
| Revocation       | Easy         | Easy         | Complex      |
| Security         | Good         | Excellent    | Good         |

---

## When to Use Each Method

- **Cookies**: Basic websites.
- **Sessions**: High-security needs.
- **Tokens**: Mobile, APIs, flexibility.

---

## PromiseGrid’s Approach

- Mixes tokens and sessions.
- Agent headers add context.
- Short-lived sessions for sensitive tasks.

---

## Security Best Practices

- Always use HTTPS.
- Allow easy logout.
- Monitor and expire sessions.
- Store tokens carefully.

---

## Analogy Recap

- Cookies = Coat check tickets
- Sessions = Library cards
- Tokens = Hotel keycards

---

## Modern Trends

- Passwordless logins
- Zero-trust models
- Stronger standards
- Cookies making a comeback

---

## Distributed Environments

- Local storage = sticky notes
- Cloud state = shared notebook
- Client-only tools won’t sync across devices

---

## Final Thoughts

- Match the method to the context.
- Combine tools if needed.
- Prioritize user safety and experience.
