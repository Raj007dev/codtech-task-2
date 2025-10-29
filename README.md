NAME:  RAJKUMAR ATTRI
COMPANY: CODTECH IT SOLUTIONS
ID: CT04DR203
DOMAIN: CYBER SECURITY AND ETHICAL HACKING 
DURATION: OCTOBER TO NOVEMBER 2025
MENTOR: NEELA SANTOSH KUMAR


Web Application Vulnerability Scanner (Educational Overview)
​The web_scanner.py script is a highly simplified, educational Python tool designed to demonstrate the basic principles used by sophisticated vulnerability scanners. Its primary goal is to identify common structural elements and simple reflection patterns that can indicate potential vulnerabilities like Cross-Site Scripting (XSS).
​⚠️ ETHICAL AND EDUCATIONAL DISCLAIMER
​This tool is for educational use only. Real-world vulnerability scanners are highly complex. This script is not a robust security tool. You must only run this scanner against web applications you own or have explicit, written authorization to test. Unauthorized scanning is illegal and unethical.
​Core Technologies
​The script relies on two fundamental Python libraries for its operation:
​requests: Used to make HTTP GET and POST requests to the target web server. It handles fetching the HTML content of the target URL.
​BeautifulSoup (bs4): Used for parsing the received HTML content. It allows the script to easily navigate the HTML structure, find specific tags (like <form> and <input>), and extract their attributes.
​Key Functionalities
​The scanner performs two main conceptual checks on the provided URL:
​1. Form Discovery (Structural Analysis)
​This functionality is the first step in testing for vulnerabilities like SQL Injection (SQLi) or Cross-Site Scripting (XSS) that occur via user input.
​Action: The script scans the page for all <form> tags.
​Extraction: For each form found, it extracts crucial details:
​Action URL: Where the form data is sent.
​Method: Whether the form submits data using GET (via URL parameters) or POST (in the request body).
​Input Fields: The names of all relevant <input>, <textarea>, and <select> fields, which would later be the targets for injecting malicious payloads.
​2. Basic Reflection Check (XSS Principle)
​This check demonstrates the core idea behind detecting Reflective Cross-Site Scripting (XSS) vulnerabilities.
​Test Payload: A unique, harmless string (VULN_TEST_STRING_12345) is used as a test payload.
​Injection: The script takes the initial URL (if it has query parameters like ?id=1) and injects the test payload into those parameters.
​Verification: It fetches the web page with the injected parameters and checks the raw HTML response content.
​Vulnerability: If the TEST_PAYLOAD is found reflected in the HTML output, it indicates that the application is likely not sanitizing input correctly, marking a high potential for an XSS attack.
​Safe: If the payload is not found, the application may be sanitizing the input (or the reflection point is more complex).
​Limitations
​As an educational tool, the scanner has significant limitations compared to industry-standard tools like OWASP ZAP or Burp Suite:
​No Payload Library: It only tests with a single, simple reflection string, not a library of complex XSS or SQLi attack payloads.
​No POST Handling: It does not attempt to submit found forms using the POST method, focusing only on structural discovery and GET parameter reflection.
​No Crawling/State Management: It only analyzes a single, static page and does not follow links, manage cookies, or handle complex session states.
