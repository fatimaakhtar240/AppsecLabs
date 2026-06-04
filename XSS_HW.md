
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
Name XSS vulnerability found in comment bar
Severity Medium
Cvss score 7.5
Description 
Evidence/steps to reproduce 
click on comment bar
<img width="812" height="311" alt="image" src="https://github.com/user-attachments/assets/7a67f954-c266-490d-8066-1fcfbbdace0a" />
Recommendation:  Reject coode like <script>alert("XSS")</script>, Only run JavaScript from trusted locations, Encode the input so it is treated as text instead of code
