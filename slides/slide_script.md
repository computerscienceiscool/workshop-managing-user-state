
### **Client-Side Web State Persistence**

Hi everyone! I want to talk about something invisible but essential to your experience online: how web apps remember who you are, what you’ve done, and even your preferences.

Every time you log into a site, click around, refresh a page, or close the browser and come back later, there’s a system working quietly to keep your experience smooth.

We’ll explore how browsers and websites use cookies, sessions, tokens, local storage, IndexedDB, and more to persist your state. Let’s make this simple and clear.

---

### **The Big Question – How does a website remember you?**

Let’s begin with this: when you log into a site, how does it remember you across pages or even days later?

Here’s the thing: websites run on systems called HTTPand HTTP.  Those have NO memory and it forgets everything between each click.

So developers had to come up with clever ways to give websites a memory. That’s where cookies, sessions, and tokens come in.

---

### **Cookie-Based Authentication – Cloakroom Ticket**

Let’s start with cookies.

Imagine you’re at a coat check. You hand in your coat and receive a little ticket. That ticket doesn’t store the coat; it simply tells the attendant, "Hey, this person checked something in."

A cookie works the same way. When you log into a website, it gives your browser a small identifier. Every time you do something on the site, your browser sends that identifier back so the site remembers you.

So cookies are like that little ticket — simple and automatic.

---

### **Cookies in Real Life**

You’ve seen cookies in action:

* Staying logged into Facebook
* Amazon remembering your cart
* Websites remembering your dark mode preference
* That "Remember me" checkbox

These are all made possible by cookies. Behind the scenes, your browser is quietly saying, "Hey, I’m still me," each time you click.

---

### **Cookie Security & Limitations**

Of course, cookies have limits and safety features.

Good websites make cookies safer by adding rules:

* Some cookies can’t be read by JavaScript, which blocks certain attacks
* Others only get sent over secure, encrypted connections
* Some are restricted so they’re not sent between unrelated sites

Still, cookies can only hold a small amount of data, and the site has to check them constantly. They’re helpful but not a perfect solution.

---

### **Server-Side Sessions – Library Card**

Now let’s talk about **sessions**.

Think of it like a **library card**. Your card doesn’t hold all the info about you. It just points to your file in the library’s computer.

A session works the same way. When you log in, the server creates a session—a record about you. Your browser only carries a little ID, like a barcode, to look it up.

---

### **Sessions in Real Life**

You’ll see sessions behind the scenes on:

* Banking websites
* University portals
* Insurance sites
* Online checkout pages

Why? Because the actual data stays on the server, not in your browser. It’s more secure that way.

---

### **Session Management Details**

So what’s the benefit?

With sessions, the server is in charge. It can kick you out, log you out from everywhere, and keep your data safe.

But this also means it has to store that session somewhere. And if it crashes, that session could vanish. Also, for big sites with lots of users, managing all those sessions can be tricky.

---

### **Token-Based Authentication – Hotel Keycard**

Now let’s look at **tokens**, especially a popular kind called JWTs.

Imagine checking into a hotel. You get a **keycard**. That card doesn’t just say your name. It *knows* what room you can access, for how long, and maybe even which floor.

Tokens work like that keycard. When you log in, the server gives you a digital card — a token — that contains everything needed to prove who you are.

---

### **JWT Structure & Examples**

These tokens, called JWTs, come in three parts:

1. A label saying what type it is
2. The info it holds — like your user ID and permissions
3. A digital signature to prevent forgery

You’ll see them when you:

* Log into a site using your Google account
* Use a mobile app
* Or when two systems talk to each other automatically

---

### **Token Advantages & Challenges**

Tokens are powerful because they don’t rely on the server to remember anything. Once you have one, it works until it expires.

They’re perfect for mobile and APIs, and they scale well.

But… revoking them requires additional planning. If a token gets stolen, it’s like losing your hotel keycard — you need systems in place to handle it.

---

### **Token Revocation Solutions**

To deal with that, developers use a few tricks:

* Make tokens expire quickly
* Give you a "refresh token" to get a new one when the old one expires
* Keep a list of bad tokens
* Or change a version number to invalidate older tokens

The best combo? Use short-lived tokens with refresh tokens for longer access.

---

### **Comparison Table**

<!--  Let’s compare everything:

| **Feature**    | **Cookies**       | **Sessions**  | **JWT Tokens**          |
| -------------- | ----------------- | ------------- | ----------------------- |
| Server storage | Optional          | Required      | No                      |
| Data location  | Browser           | Server        | Token itself            |
| Transport      | Cookie header     | Cookie header | Authorization header\*  |
| Scaling        | Easy              | Challenging   | Very easy               |
| 3rd-party APIs | Limited           | Limited       | Excellent               |
| Revocation     | Easy              | Easy          | Requires planning       |
| Security       | Good (with flags) | Excellent     | Good (if stored safely) |

\*Tokens can also be sent in cookies for web apps

Each one has strengths and tradeoffs. There’s no universal winner—just tools for different jobs.

 -->

Now let’s stack these options side by side to see how they compare.

**First, server storage:**
- Cookies can store a little bit on your browser. Sometimes the server also uses them, but it’s optional.
- Sessions need a server to keep track of your data.
- Tokens like JWTs don’t require server storage at all — they carry the info with them.

**Where’s the data stored?**
- Cookies: in your browser.
- Sessions: on the server.
- Tokens: inside the token itself — it’s self-contained.

**How’s the data sent?**
- Cookies and sessions both use the cookie header.
- Tokens usually go in an `Authorization` header, which is handy for APIs and mobile apps.

**When it comes to scaling:**
- Cookies and tokens are easy — they don’t require much server memory.
- Sessions can be trickier for big apps, because the server has to keep everyone’s data organized.

**For third-party APIs:**
- Cookies and sessions don’t work so well.
- Tokens are the best here — they’re built for it.

**What about revoking access?**
- Cookies and sessions are easy to revoke — the server just deletes the session or ignores the cookie.
- Tokens are trickier. Once they’re out there, they stay valid until they expire unless you build extra systems to cancel them.

**And finally, security:**
- All of these can be secure — but only if used correctly.
- Sessions tend to be the safest because the data never leaves the server.
- Tokens need careful storage and short expiration times.

So there’s no clear winner — just different tools for different jobs.

---

### **When to Use Each Method**

So, when do you use what?

Use **cookies** for traditional websites. Simple needs, desktop users, nothing fancy.

Use **sessions** when security matters a lot, like in banking or healthcare.

Use **tokens** when you need something flexible, mobile-friendly, or you’re connecting multiple systems or apps.

---

## **Client-Side Data Persistence Techniques – Script**

 <!--  

Web apps don’t just need to remember *who* you are — they also need to remember *what* you were doing.

Here are some ways browsers store data beyond cookies:

| Feature         | Purpose                                            | Storage Location |
| --------------- | -------------------------------------------------- | ---------------- |
| Local Storage   | Simple key-value data                              | Browser          |
| Session Storage | Temporary data (per tab)                           | Browser          |
| IndexedDB       | Complex structured data (e.g. drafts, preferences) | Browser          |
| Cache API       | Offline access, faster loads                       | Browser          |

Each tool helps apps remember drafts, theme choices, carts, and more — not just logins. -->



So far we’ve talked a lot about how websites remember *who* you are — but they also need to remember *what* you’re doing.

Maybe you’re writing a long post, halfway through a checkout process, or switching between light mode and dark mode. For all that, websites use more than just cookies.

Here are a few client-side tools browsers offer:

- **Local Storage** is like a simple notepad. It saves small bits of data — like a theme preference — and it sticks around even after you close the tab.
- **Session Storage** is more temporary. It’s great for things like multi-step forms or wizards — and it disappears when you close the browser tab.
- **IndexedDB** is more powerful. It’s like a mini database in your browser — great for saving drafts, preferences, or other structured data.
- And then there’s the **Cache API**. This one helps with offline access and faster page loads. It lets the browser save parts of the site so they load quickly, even without internet.

Each of these helps the app feel responsive, smooth, and personal — even before the server gets involved.


---

### **PromiseGrid’s Data Persistence Approach**
<!--
At PromiseGrid, user state isn’t just about logging in. We also persist:

* Agent identities
* Task history
* Decision trails
* Data artifacts (like generated plans, charts, or documents)

How?

* Auth state: token + optional session
* Agent state: stored via versioned records
* User data: saved to distributed stores (IPFS/Grid nodes)
* Resilience: state is portable between devices, because it lives in the mesh

This is more like giving each agent a **“travel journal”** it carries and syncs wherever it goes.
-->

## **PromiseGrid’s Data Persistence Approach**

Let’s talk about how we handle user state at PromiseGrid.

It’s not just about keeping someone logged in. Our system needs to remember a lot more — like what agents were doing, what decisions they made, and what data they’ve created or used.

Here’s how we break it down:

- **Authentication**: We use a mix of tokens and sessions. That tells us *who* you are.
- **Agent state**: Each agent has its own versioned history — like a logbook that records tasks, choices, and updates over time.
- **User data**: Whether it’s a generated chart or a saved plan, we store that data across a distributed network — so it’s not tied to just one device.
- **Resilience**: Everything is designed to be portable. If you switch devices, your state comes with you — because it lives in the mesh, not on just one machine.

Think of it like this: each agent carries a **travel journal** — a notebook it always has on hand. Wherever the agent goes, that notebook goes too, keeping track of the journey.


---

## **PromiseGrid Visual Analogy – Sticky Notes vs. Travel Journals**

Let’s make this visual.

Think of different ways to save state like different types of notes:

- **Cookies, LocalStorage, IndexedDB** — these are like **sticky notes** you put on your laptop. Super convenient, but only available on that one device. Close the laptop or switch to your phone? Those notes don’t come with you.

- **Sessions** — these are like **notes at the front desk**. You check in, and someone else keeps track of your details. But if you visit another building, your info doesn’t follow unless they talk to each other.

- **Tokens** — more like an **ID badge**. It tells systems who you are and what you’re allowed to do. Great for moving between places — but if you lose it, someone could use it unless you’ve got safeguards.

Now here’s where **PromiseGrid** is different.

It gives each agent a **travel journal** — a full notebook that goes everywhere they go. It holds identity, history, tasks, and data — and it syncs automatically.

That means your state doesn’t vanish when a page closes or a device changes. It lives and grows, just like the agent carrying it.

---

### **Security Best Practices**

No matter the method, the rules for safety stay the same:

* Use encrypted connections (always HTTPS)
* Let users log out easily
* Set time limits
* Watch for weird behavior

And if you're using tokens: store them carefully and rotate them when needed.

---

### **Analogy Recap**

Let’s bring back our metaphors:

* **Cookies**: coatroom tickets
* **Sessions**: library cards
* **Tokens**: hotel keycards
* **Hybrids**: use what fits your needs

Each one plays a role in helping sites remember who you are.

---

### **Modern Trends**

What’s new in this space?

* Passwordless logins, like magic links or face scans
* Zero-trust security, where every request must prove itself
* Better industry standards
* And yes, even cookies are making a comeback — with stronger protections

But no matter the trend, the core concepts of cookies, sessions, and tokens still matter.

---

### **Distributed Environments – A Visual Analogy**

So let’s talk about what happens in a distributed world — when users move across devices.

Think of local storage, cookies, or IndexedDB like sticky notes on your laptop. Helpful, quick, right there when you need them — but only on that device. If you open your phone? That sticky note’s not there.

Now compare that to writing in a shared notebook that lives in the cloud. Everyone sees the same info — no matter where they open it. That’s what happens when you sync state through the server.

So when your app needs to be remembered across devices or browsers, client-side tools aren’t enough. You need a strategy that connects the sticky note to the shared notebook.

---

### Final Thoughts

So how do you decide what to use?

* Ask how sensitive the data is
* Think about where people will log in from
* Consider how your system is built

There’s no one-size-fits-all. And most modern apps actually combine these tools to get the best results.

---

Thank You

Thanks so much for joining me today!

