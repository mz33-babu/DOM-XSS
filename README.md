# Document Object Model-XSS
This write-up will explain how DOM based XSS works and provide examples of how to detect and prevent it.

# DOM Based XSS
Cross-Site Scripting (XSS) is a type of vulnerability that allows attackers to inject client-side scripts into web pages viewed by other users. There are several types of XSS attacks, and one of them is DOM based XSS. This write-up will explain how DOM based XSS works and provide examples of how to detect and prevent it.

# How DOM Based XSS Works
DOM (Document Object Model) based XSS occurs when an attacker injects a script into a web page, which is then executed by the victim's browser. Unlike other types of XSS attacks, where the server is responsible for rendering the page, DOM based XSS is caused by the client-side code.

In DOM based XSS, the vulnerable code receives input from the user, and the input is then used to dynamically generate a portion of the web page. The attacker can then inject a script into the input field that is not properly sanitized by the application.

Here is an example of how DOM based XSS can be exploited:

```javascript
<script>
  var username = document.getElementById("username").value;
  document.write("Hello, " + username);
</script>
```

In this example, the attacker can inject a script that will be executed by the victim's browser. For example, the attacker can inject the following script:

```javascript
<script>alert("You have been hacked!");</script>
```

If the input field is not properly sanitized by the application, the injected script will be executed by the victim's browser, and the user will be presented with an alert message that says "You have been hacked!".

# Detecting DOM Based XSS
Detecting DOM based XSS can be challenging because it does not involve server-side code. One way to detect DOM based XSS is by using a web application scanner, such as OWASP ZAP or Burp Suite. These tools can scan web pages and identify potential vulnerabilities, including DOM based XSS.

Another way to detect DOM based XSS is by manually inspecting the JavaScript code on the page. Look for input fields that are used to dynamically generate content on the page, and make sure that the input is properly sanitized.

# Preventing DOM Based XSS
Preventing DOM based XSS involves properly sanitizing input fields on the page. Here are some tips for preventing DOM based XSS:

1. Use a Content Security Policy (CSP) to restrict the sources of scripts that can be executed on the page.

2. Sanitize all input fields to remove any scripts that may be injected by an attacker.

3. Use an HTML encoding library, such as OWASP Java Encoder or PHP's htmlspecialchars function, to encode any user input that is displayed on the page.

4. Use a JavaScript library, such as jQuery, that provides built-in protection against DOM based XSS.

Here is an example of how to sanitize input fields using JavaScript:

```javascript
function sanitizeInput(input) 
{
  return input.replace(/<script.*?>.*?<\/script>/gi, "");
}
```

This function will remove any script tags from the input, preventing an attacker from injecting a script into the page.

In summary, DOM based XSS is a type of vulnerability that allows attackers to inject client-side scripts into web pages viewed by other users. Detecting and preventing DOM based XSS involves properly sanitizing input fields on the page and using a Content Security Policy to restrict the sources of scripts that can be executed on the page.

