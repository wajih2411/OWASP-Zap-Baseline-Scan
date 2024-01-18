# Bug Reports

## 1. Cross-Domain JavaScript Source File Inclusion

### Description
The application includes JavaScript files from different domains. This practice can introduce various security risks, particularly if these external sources are compromised or not entirely trustworthy.

### Steps to Recreate
1. Open the web page `https://juice-shop.herokuapp.com/`.
2. Use browser developer tools or a network analysis tool.
3. Inspect the `<script>` tags in the HTML source.
4. Observe that external JavaScript files are included from different domains.

### Impact
The impact ranges from minor to severe, depending on the external domains' security. Potential risks include execution of malicious scripts, leading to Cross-Site Scripting (XSS) attacks or data breaches.

### Possible Mitigation
- Prefer hosting all JavaScript files on the same domain.
- If external scripts must be included, ensure that the domains are secure and trusted.
- Implement Subresource Integrity (SRI) to prevent the execution of modified scripts.

---

## 2. Content Security Policy (CSP) Header Not Set

### Description
The server responses for the web application do not include the Content Security Policy (CSP) header. CSP is a security standard which helps to detect and mitigate certain types of attacks, like Cross-Site Scripting (XSS) and data injection attacks.

### Steps to Recreate
1. Send a request to `https://juice-shop.herokuapp.com/`.
2. Inspect the response headers using browser developer tools or `curl`.
3. Notice the absence of the `Content-Security-Policy` header in the response.

### Impact
Without CSP, the application is more susceptible to XSS attacks and other injection attacks. CSP helps restrict resources the browser is allowed to load, thereby enhancing security.

### Possible Mitigation
- Implement and configure a Content Security Policy header for the application.
- Define a policy that specifies which scripts, styles, and other resources are allowed to load.
