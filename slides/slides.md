# Managing User State: Cookies, Sessions & Tokens  
**Author**: JJ Salley  

---

## Slide 1: Title Slide  
**Managing User State**  
_Cookies, Sessions & Tokens_  
How apps remember who you are

---

## Slide 2: The Big Question  
**How does a website remember you?**  
- You sign in once  
- Click around  
- Still logged in  
**Why?** Let’s find out.

---

## Slide 3: Cookie-Based Authentication  
**Analogy**: Cloakroom Ticket  
- You hand in your coat (login)  
- Get a numbered ticket (cookie)  
- Show ticket to get coat (access protected content)

---

## Slide 4: Cookies in Real Life  
**Examples**  
- Staying logged into Facebook  
- Shopping carts on Amazon  
- Remembering dark mode settings

---

## Slide 5: Cookie Pros & Cons  
**Pros**  
- Simple  
- Built into browsers  

**Cons**  
- Can be stolen or faked  
- Must be validated on each request

---

## Slide 6: Server-Side Sessions  
**Analogy**: Library Card  
- Get a card with a barcode (session ID)  
- Library (server) stores your info  
- Card just points to your record

---

## Slide 7: Sessions in Real Life  
**Examples**  
- Online banking  
- School portals  
- Insurance sites  

**Note**: Sessions expire for safety.

---

## Slide 8: Session Pros & Cons  
**Pros**  
- Server controls everything  
- Less risk in browser  

**Cons**  
- Server must store and manage session data  
- Harder to scale

---

## Slide 9: Token-Based Authentication  
**Analogy**: Hotel Keycard  
- Check in (login)  
- Get keycard with permissions (token)  
- Works until checkout (expiration)

---

## Slide 10: Tokens in Real Life  
**Examples**  
- “Login with Google” on apps  
- Budgeting apps accessing your bank  
- Mobile apps syncing health data

---

## Slide 11: Token Pros & Cons  
**Pros**  
- Stateless on the server  
- Easy for mobile and 3rd-party apps  

**Cons**  
- Hard to revoke  
- Needs secure storage on device

---

## Slide 12: Quick Comparison Table  

| Feature            | Cookies           | Sessions         | Tokens (JWT)       |
|--------------------|------------------|------------------|--------------------|
| Server storage     | No               | Yes              | No (usually)       |
| Transport          | Cookie header    | Cookie header    | Authorization header |
| Scaling            | Easy             | Medium           | Very easy          |
| 3rd-party use      | Poor             | Poor             | Excellent          |
| Revocation         | Easy             | Easy             | Tricky             |

---

## Slide 13: PromiseGrid’s Approach  
**How does PromiseGrid manage user state?**  

- **JWTs in localStorage**  
  Agents send tokens with each request  
- **Ephemeral sessions**  
  Used for short-term, high-security use  
- **Agent context headers**  
  Each message carries its own “identity badge”

---

## Slide 14: Analogy Recap  
- **Cookies** = Cloakroom ticket  
- **Sessions** = Library card  
- **Tokens** = Hotel keycard  
- **PromiseGrid** = Delivery driver with a digital badge

---

## Slide 15: Real-Life Quiz  
**Guess the Method:**  
- A website keeps you logged in = ?  
- Your bank logs you out after 10 minutes = ?  
- You use an app that connects to Google = ?  

Answers: Cookie, Session, Token

---

## Slide 16: Final Thoughts  
Choose the right method based on:  
- Who stores the data  
- How secure the context needs to be  
- Whether it’s just your site or 3rd-party tools

---

## Slide 17: Thank You  
Thanks for learning with me!  
Questions welcome.
