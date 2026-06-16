
Finding table 
Name XSS vulnerability found in search bar
Severity High
Cvss score 9.8
Description 
Evidence/steps to reproduce 
click on search bar
Enter <script>alert(1)</script> in field and click on search button. alert popu[ is rendered by browser.
<img width="1788" height="509" alt="image" src="https://github.com/user-attachments/assets/4891708b-9eba-4d6a-aaab-8f4299b3bae6" />


Recommendation: Reject coode like <script>alert("XSS")</script>, Only run JavaScript from trusted locations,  Encode the input so it is treated as text instead of code




Finding table 
Name **Stored** XSS vulnerability found in comment bar
Severity Medium
Cvss score 7.5
Description: The comment field accepts malicious JavaScript and stores it. When users view the comment, the script executes in their browser.
Evidence/steps to reproduce 
click on comment bar
<img width="812" height="311" alt="image" src="https://github.com/user-attachments/assets/7a67f954-c266-490d-8066-1fcfbbdace0a" />
Impact:An attacker could execute JavaScript in a user's browser, steal session information, modify page content, or perform actions on behalf of the user.
Recommendation:  Validate and sanitize user input before storing it. Apply output encoding when displaying comments so they are treated as text instead of executable code.


Finding table 
Name **DOM ** XSS vulnerability found in the search bar
Severity Medium
Cvss score 7.5
Description: The search bar is vulnerable to DOM-based XSS. User input from the URL/search field is written directly into the page using document.write() without proper encoding. By entering "><svg onload=alert(1)>, JavaScript executes in the browser, proving the vulnerability.
Proof of concept: 1. Click the search bar. 2. Enter: "><svg onload=alert(1)> 3. Submit the search. 4. An alert box appears, confirming XSS execution.
Impact: An attacker can steal user cookies,steal session data to perform as a victim.
<img width="836" height="257" alt="image" src="https://github.com/user-attachments/assets/b6302b2c-fa9f-4837-8e3b-7567877c6212" />
Recommendation:. Use safe DOM methods like textContent instead of innerHTML or document.write(). Also apply context-aware output encoding and sanitize user input before displaying it on the page.


Finding Name	**Reflected** XSS into attribute with angle brackets HTML-encoded
Severity:Medium
CVSS Score: 7.5
Description:	The search bar is vulnerable to Reflected XSS. User HTML tags <> is getting encoded into the page. By entering "onmouseover="alert(1), browser is still compiling and treating input as HTML
Proof of concept: 1. Click the search bar. 2. Enter:"onmouseover="alert(1) . Submit the search. 4. An alert box appears, confirming XSS execution.
Impact: An attacker can steal user cookies,steal session data to perform as a victim.
<img width="782" height="669" alt="image" src="https://github.com/user-attachments/assets/4982c961-9d04-4007-9aac-abb1c15c88d7" />
Impact: An attacker could execute arbitrary JavaScript in a victim's browser, steal session tokens, modify page content, perform actions as the victim, or redirect users to malicious websites.
Recommendation:Apply context-aware output encoding for HTML attributes. User input should never be inserted directly into HTML attributes without proper encoding. Use secure templating frameworks that automatically escape output and validate user input where appropriate.
Secure Coding Concept: Output Encoding for HTML Attributes






