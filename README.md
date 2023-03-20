# DOM-XSS
This write-up will explain how DOM based XSS works and provide examples of how to detect and prevent it.

# DOM Based XSS
Cross-Site Scripting (XSS) is a type of vulnerability that allows attackers to inject client-side scripts into web pages viewed by other users. There are several types of XSS attacks, and one of them is DOM based XSS. This write-up will explain how DOM based XSS works and provide examples of how to detect and prevent it.

# How DOM Based XSS Works
DOM (Document Object Model) based XSS occurs when an attacker injects a script into a web page, which is then executed by the victim's browser. Unlike other types of XSS attacks, where the server is responsible for rendering the page, DOM based XSS is caused by the client-side code.

In DOM based XSS, the vulnerable code receives input from the user, and the input is then used to dynamically generate a portion of the web page. The attacker can then inject a script into the input field that is not properly sanitized by the application.

Here is an example of how DOM based XSS can be exploited:

<script>
  var username = document.getElementById("username").value;
  document.write("Hello, " + username);
</script>
