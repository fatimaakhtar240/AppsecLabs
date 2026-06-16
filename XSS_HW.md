# Security Findings Report

## Finding 1

| Field                             | Details                                                                                                                                                                                                   |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Name**                          | XSS Vulnerability Found in Search Bar                                                                                                                                                                     |
| **Severity**                      | High                                                                                                                                                                                                      |
| **CVSS Score**                    | 9.8                                                                                                                                                                                                       |
| **Description**                   | The search functionality does not properly validate or encode user input before displaying it in the browser. An attacker can inject malicious JavaScript code that executes in a victim's browser.       |
| **Evidence / Steps to Reproduce** | 1. Click the search bar.<br>2. Enter `<script>alert(1)</script>` in the search field.<br>3. Click the search button.<br>4. An alert popup appears, confirming that JavaScript is executed by the browser. |
| **Impact**                        | An attacker could execute arbitrary JavaScript in a victim's browser, steal session cookies, perform actions on behalf of the user, modify page content, or redirect users to malicious websites.         |
| **Recommendation**                | Reject code such as `<script>alert("XSS")</script>`. Only allow JavaScript from trusted sources. Apply output encoding so user input is treated as text instead of executable code.                       |

**Screenshot Evidence**

```html
<img width="1788" height="509" alt="image" src="https://github.com/user-attachments/assets/4891708b-9eba-4d6a-aaab-8f4299b3bae6" />
```

---

## Finding 2

| Field                             | Details                                                                                                                                                                                                  |
| --------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Name**                          | Stored XSS Vulnerability Found in Comment Bar                                                                                                                                                            |
| **Severity**                      | Medium                                                                                                                                                                                                   |
| **CVSS Score**                    | 7.5                                                                                                                                                                                                      |
| **Description**                   | The comment field accepts malicious JavaScript and stores it. When users view the comment, the script executes in their browser.                                                                         |
| **Evidence / Steps to Reproduce** | 1. Click the comment bar.<br>2. Enter a malicious JavaScript payload.<br>3. Submit the comment.<br>4. Reload or revisit the page.<br>5. The script executes automatically when the comment is displayed. |
| **Impact**                        | An attacker could execute JavaScript in a user's browser, steal session information, modify page content, or perform actions on behalf of the user.                                                      |
| **Recommendation**                | Validate and sanitize user input before storing it. Apply output encoding when displaying comments so they are treated as text instead of executable code.                                               |

**Screenshot Evidence**

```html
<img width="812" height="311" alt="image" src="https://github.com/user-attachments/assets/7a67f954-c266-490d-8066-1fcfbbdace0a" />
```

---

## Finding 3

| Field                | Details                                                                                                                                                                                                                                                                          |
| -------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Name**             | DOM-Based XSS Vulnerability Found in Search Bar                                                                                                                                                                                                                                  |
| **Severity**         | Medium                                                                                                                                                                                                                                                                           |
| **CVSS Score**       | 7.5                                                                                                                                                                                                                                                                              |
| **Description**      | The search bar is vulnerable to DOM-based XSS. User input from the URL or search field is written directly into the page using `document.write()` without proper encoding. By entering `"><svg onload=alert(1)>`, JavaScript executes in the browser, proving the vulnerability. |
| **Proof of Concept** | 1. Click the search bar.<br>2. Enter: `"><svg onload=alert(1)>`<br>3. Submit the search.<br>4. An alert box appears, confirming XSS execution.                                                                                                                                   |
| **Impact**           | An attacker can execute malicious JavaScript, steal session data, impersonate users, modify page content, or redirect victims to malicious websites.                                                                                                                             |
| **Recommendation**   | Use safe DOM methods such as `textContent` instead of `innerHTML` or `document.write()`. Apply context-aware output encoding and sanitize user input before displaying it on the page.                                                                                           |

**Screenshot Evidence**

```html
<img width="836" height="257" alt="image" src="https://github.com/user-attachments/assets/b6302b2c-fa9f-4837-8e3b-7567877c6212" />
```

---

## Finding 4

| Field                     | Details                                                                                                                                                                                                                                                                                                                                               |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Name**                  | Reflected XSS into Attribute with Angle Brackets HTML-Encoded                                                                                                                                                                                                                                                                                         |
| **Severity**              | Medium                                                                                                                                                                                                                                                                                                                                                |
| **CVSS Score**            | 7.5                                                                                                                                                                                                                                                                                                                                                   |
| **Description**           | The search bar is vulnerable to Reflected XSS within an HTML attribute context. Although angle brackets (`<` and `>`) are encoded, user input can still break out of the attribute and inject malicious event handlers. By entering `"onmouseover="alert(1)`, the browser interprets the input as executable HTML, resulting in JavaScript execution. |
| **Proof of Concept**      | 1. Click the search bar.<br>2. Enter: `"onmouseover="alert(1)`<br>3. Submit the search.<br>4. Trigger the mouseover event.<br>5. An alert box appears, confirming XSS execution.                                                                                                                                                                      |
| **Impact**                | An attacker could execute arbitrary JavaScript in a victim's browser, steal session tokens, modify page content, perform actions as the victim, or redirect users to malicious websites.                                                                                                                                                              |
| **Recommendation**        | Apply context-aware output encoding for HTML attributes. User input should never be inserted directly into HTML attributes without proper encoding. Use secure templating frameworks that automatically escape output and validate user input where appropriate.                                                                                      |
| **Secure Coding Concept** | Output Encoding for HTML Attributes                                                                                                                                                                                                                                                                                                                   |

**Screenshot Evidence**

```html
<img width="782" height="669" alt="image" src="https://github.com/user-attachments/assets/4982c961-9d04-4007-9aac-abb1c15c88d7" />
```
