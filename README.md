# xss-cheatsheet
Educational XSS cheatsheet with vulnerable demos, payloads, mitigation techniques, and safe testing guidance for authorized use.
## **Purpose:** 
A beginner-to-intermediate GitHub repository to explain XSS, demonstrate all types (Reflected, Stored, DOM-based) with small vulnerable example apps, provide payloads, show realistic scenarios (how to capture screenshots), and list defenses and secure code examples. Use this repo for education, testing in safe labs, or pentest writeups. Do not use these on systems you don't own or are not authorized to test.

### ***What is XSS?***

Cross‑Site Scripting (XSS) is a class of web vulnerability where an attacker injects malicious scripts (commonly JavaScript) into web pages viewed by other users. When the victim's browser executes that script, the attacker may steal cookies, hijack sessions, perform actions on behalf of the user, or modify page content.

#### ***Types of XSS***
**⭐Reflected XSS (non‑persistent)**

- Input is reflected back in the HTTP response immediately (often via a query parameter or POST body) without proper encoding.

- Usually requires user interaction (clicking a crafted link or visiting a URL).

<img width="969" height="919" alt="2025-09-25 21_15_02-artists" src="https://github.com/user-attachments/assets/2b2914b0-6265-4a3f-a323-ec3311e926b0" /> 

<img width="1361" height="673" alt="2025-09-25 21_16_09-artists" src="https://github.com/user-attachments/assets/efff00ac-0106-4f93-a1a1-1ce51a3c3d2f" />


**⭐Stored XSS (persistent)**

- Malicious payload is stored on the server (database, message board, profile, comments) and served to multiple users later.

- More dangerous because it can affect every user who views the stored content.

<img width="1054" height="946" alt="2025-09-25 20_29_38-guestbook-3" src="https://github.com/user-attachments/assets/ce52f959-ee04-4698-a47f-618a781e4bcb" /> 

<img width="1252" height="944" alt="2025-09-25 20_34_48-guestbook-4" src="https://github.com/user-attachments/assets/22e26f7b-1738-4e4f-a2fb-dbad4ce165f1" />

Stored XSS occurs when an attacker’s malicious script is saved on a server (e.g., comments, profiles, or database). When other users load the affected page, the script executes in their browsers—potentially stealing cookies, hijacking sessions, or performing actions as the victim. This demo shows how stored XSS works and how to safely test and fix it in authorized environments only.


**⭐DOM‑based XSS (client‑side)**

- The vulnerability arises entirely in client‑side JavaScript: the script reads data from location.hash, location.search, document.referrer or other DOM sources and unsafely writes to the DOM (e.g., innerHTML, document.write, eval).

- The server response may be static and seemingly safe — the browser JS performs the insecure operation.

<img width="920" height="1034" alt="2025-09-25 20_31_05-guestbook-5" src="https://github.com/user-attachments/assets/4ae92cc8-f181-4f26-86f0-3e765d2fade7" />

<img width="1317" height="915" alt="2025-09-25 20_31_39-guestbook-6" src="https://github.com/user-attachments/assets/e8e3a0e4-56a3-4186-a33e-fe213a1857f2" />

DOM-based XSS happens entirely in the browser when client-side JavaScript reads untrusted data (e.g., location.hash, location.search, or document.referrer) and unsafely inserts it into the page (for example via innerHTML, document.write, or eval). Because the unsafe operation occurs in the DOM, the server may never see the malicious payload — the attack executes only when a user loads or interacts with the page, allowing an attacker to run scripts, steal data, or hijack sessions in the victim’s browser. This demo illustrates how DOM-based XSS works and shows safe testing and remediation techniques for authorized environments.

## Quick Protection Tips
- Escape output for correct context (HTML, JS, URL).  
- Use framework auto-escaping features.  
- Avoid unsafe functions like innerHTML, eval, document.write.  
- Sanitize trusted HTML with DOMPurify.  
- Apply strict Content Security Policy (CSP).  
- Set cookies with HttpOnly, Secure, SameSite flags.  


**Conclusion**
This repository provides a complete overview of XSS—covering reflected, stored, and DOM-based attacks with examples, payloads, and demos. It also includes real-world scenarios, screenshots, and mitigation techniques. By exploring these resources, developers and security learners can understand how XSS works and implement effective defenses to build safer applications.

#### ***Responsible disclosure & legal note***

Only test on systems you own or where you have explicit authorization. Do not run these demos on public production systems. Follow your organization's disclosure policy when you find vulnerabilities.
