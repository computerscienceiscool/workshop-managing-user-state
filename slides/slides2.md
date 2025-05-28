
# Client-Side Web State Persistence  
*Cookies, Sessions, Tokens & Data*

How apps remember who you are  
**JJ Salley**

---

## The Big Question  
**How does a website remember you?**  
- You log in  
- Click around  
- Come back tomorrow — you're still you

But HTTP, the system websites use, is *stateless*.  
It forgets between every click.  
So how do we add memory? Let's find out.

---

## Cookies = Cloakroom Ticket  
- You check your coat and get a small ticket  
- The website gives your browser a cookie  
- On each visit, your browser says: "Hey, I’ve got this ticket!"

It’s simple, automatic, and works well for many cases.

---

## Cookies in Real Life  
- Staying logged into Facebook  
- Amazon cart memory  
- Remembering dark mode  
- "Remember me" checkboxes

Cookies help your browser remind the site who you are.

---

## Cookie Security & Limits  
✅ HttpOnly, Secure, SameSite — safety flags  
❌ Small size (~4KB), domain-limited, must be validated

Cookies are helpful, but they have boundaries.

---

## Sessions = Library Card  
- Your card has an ID  
- The library keeps your record  
- The card just points to your account

Only the ID travels. The rest stays on the server.

---

## Sessions in Real Life  
- Banking sites  
- School portals  
- Health & insurance  
- Checkout processes

Sessions keep sensitive info *off* your browser.

---

## Session Pros & Cons  
✅ Server control  
✅ Easy to log out everywhere  
❌ Needs server memory  
❌ Harder to scale  
❌ Lost on crash

---

## Tokens = Hotel Keycard  
- You check in, get a digital key  
- The key *contains* your access info  
- No need to check a guestbook

This is a **JWT** — JSON Web Token.

---

## What’s Inside a JWT  
- Header (type, algorithm)  
- Payload (your data)  
- Signature (proof it’s valid)

Used for:  
- Google logins  
- Mobile apps  
- Microservices

---

## Token Pros & Cons  
✅ No server memory needed  
✅ Great for mobile & scaling  
❌ Can’t be revoked easily  
❌ Needs careful client storage

If a token gets stolen, you need systems in place.

---

## Token Revocation Options  
- Short expirations  
- Refresh tokens  
- Blacklists  
- Token versioning  
- Logout endpoints

**Best Practice**: Short-lived access + rotating refresh tokens.

---

## Updated Comparison Table

| Feature         | Cookies          | Sessions         | JWT Tokens         |
|-----------------|------------------|------------------|--------------------|
| Server storage  | Optional         | Required         | No                 |
| Data location   | Browser          | Server           | Token itself       |
| Transport       | Cookie header    | Cookie header    | Auth header*       |
| Scaling         | Easy             | Challenging      | Very easy          |
| 3rd-party APIs  | Limited          | Limited          | Excellent          |
| Revocation      | Easy             | Easy             | Requires planning  |
| Security        | Good (with flags)| Excellent        | Good (stored safely)|

*Can also send tokens in cookies for web apps

---

## When to Use What  
**Cookies**: Simple sites, desktop-first  
**Sessions**: High-security, server-side rendered  
**Tokens**: Mobile apps, APIs, third-party integrations

Choose what fits your user and your system.

---

## What About Multiple Devices?  
- Cookies & localStorage stay on one device  
- No sync across phone and laptop  
- IndexedDB is local-only

---

## Visual Analogy: Sticky Notes vs Shared Notebook  
- **Sticky Note** = localStorage, cookie, IndexedDB  
  → Just on this device  
- **Shared Notebook** = Synced to server  
  → Accessible everywhere

Want a seamless experience? You need to sync your state.

---

## Modern Trends  
- Passwordless login (magic links, WebAuthn)  
- Zero-trust architecture  
- OAuth 2.1 + OpenID Connect  
- Cookies making a secure comeback

But at the core? Still cookies, sessions, tokens.

---

## Final Thoughts  
Pick based on:  
- Security needs  
- UX goals  
- Architecture  
- Team skills

And remember — most apps use a mix. That’s okay.

---

## Thank You  
Thanks for learning with me.  
Questions welcome!
