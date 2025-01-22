**CWE-79:** Improper Neutralization of Input During Web Page Generation ('Cross-site Scripting')

### Definition

This vulnerability is commonly known as Cross-site Scripting (XSS) and is one of the most well-known security vulnerabilities in web applications. It occurs when a web application allows untrusted data (such as user inputs) to be included in the page content without applying sufficient sanitization or encoding. This can lead to the execution of malicious JavaScript code in the browsers of users interacting with the application.

### Key Reasons Behind CWE-79 Vulnerability:

1. Lack of Input Validation: The application does not enforce restrictions or sanitize data entered by users through form fields like ( payloads )
2. Absence of Proper Encoding: The failure to encode special characters like `<`, `>`, `&`, or `'`
5. Lack of Content Security Policy (CSP): Without a `Content-Security-Policy` header

### Find this vulnerability in wide scop:

> Collect all parameters (URL parameters, cookies, HTTP headers, form inputs, etc.) across the website and test them for potential XSS vulnerabilities.

##### Summary in line:
```
subdomains > urls > parameters > scanning < payloads
```

### Techniques Prevention:

CSP configuration
```
Content-Security-Policy: script-src 'self'; object-src 'none'; frame-ancestors 'none';
```
Sanitization
```php
htmlspecialchars("<script>alert('XSS')</script>"); // &lt;script&gt;alert(&#039;XSS&#039;)&lt;/script&gt;
```

### writeups:
- Self-XSS to ATO via Site Features: https://script.hashnode.dev/self-xss-to-ato-via-site-features
- Stored XSS in LibreOffice: https://bunny0417.medium.com/stored-xss-in-libreoffice-ed4ad22e0f56
- SSD Advisory – SonicWall SMA100 Stored XSS To RCE: https://ssd-disclosure.com/ssd-advisory-sonicwall-sma100-stored-xss-to-rce/
- How I found DOM XSS via postMessage on Bing.com - Microsoft Bug Bounty: https://namcoder.com/blog/how-i-found-dom-xss-on-bingcom-microsoft-bug-bounty-write-up/
- CVE-2023-26465 - Breaking Through XSS Filters in Pega Platform: https://www.secforce.com/blog/cve-2023-26465-breaking-through-xss-filters-in-pega-platform/

### sources:
- https://cwe.mitre.org/data/definitions/79.html
