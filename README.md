# Broken-Access-Control
### What is access control?
Access control (or authorization) is the application of constraints on who (or what) can perforn attempted actions or access resources that they have requested. In the context of web application, access control is dependent on authentication and session management:

Keep in mind that **Authentication** and **Authorizaion** are two different mechanism.
![Difference between Authentication & Authorization](https://user-images.githubusercontent.com/52100180/74501222-3fb0b000-4f0b-11ea-9c13-5f4e47d03363.png)
* **Authentication** Identifies the user and confirm thah they are who they say they are.
* **Authorization** Confirms that if you have rights to access specific resources.
* **Session Management** Session management refers to the process of securely handling multiple requests to a web-based application or service from a single user or entity. Websites and browsers use HTTP to communicate, and a session is a series of HTTP requests and transactions initiated by the same user. 
* **Access Control** Determines whether the user is allowed to carry out the action that they are attempting to perform.

Broken access controls are often critical security vulnerability.

**From user perspective, access controls can be divided into the following categories:**
* Vertical Access Controls**
* Horizontal Access Controls**
* Context-Dependent Access Controls**

## Vertical Access Control
Vertical access controls are mechanisms that restrict access to sensitive functionality that is not available to other types of users. For example **Vertical Access Control** restrict normal users to access admin level functionalities.

## Horizontal Access Control
Same role, but accessing the other user private data.

## Context-Dependent Access Control
Context-dependent access controls prevent a user performing actions in the wrong order.

## What is broken access control vulnerabilities?
Broken access control vulnerabilities exist when a user access some resource or perform some action that they are not supposed to be able to access. 

## Veritcal Privilage Escalation

If a user can gain access to functionality that they are not allowed to access then this is vertical privilege escalation. For example, if a standerd user can gain access to an admin page where they can delete user accounts, then this is vertical privilege escalation.

* **Unprotected Functionality**
At its most basic, vertical privilege escalation arises where an application does not implement any protection over sensitive functionality.

For example, a website might host sensitive functionality at the following URL:
```
 https://example.com/admin
 ```
In some cases, the sensitive functionality URL might be disclosed in other locations, such as the `robots.txt` file: 
```
 https://example.com/robots.txt
 ```
Even if the URL isn't disclosed anywhere, an attacker may be able to use a wordlist to brute-force the location of the sensitive functionality.

In some cases, sensitive functionality is not firmly protected but is invisible by giving it a less predictable URL. Merely hiding sensitive functionality does not provide effective access control since users might still discover the obfuscated URL in various ways. 

For example, consider an application that hosts sensitive functions at the following URL:
```
 https://example.com/administrator-panel-yb556 
 ```
This might not be directly guessable by an attacker. However, the application might still leak the URL to users. For example, the URL might be disclosed in JavaScript that constructs the user interface based on the user's role:
```
<script>
var isAdmin = false;
if (isAdmin) {
  ...
  var adminPanelTag = document.createElement('a');
  adminPanelTag.setAttribute('https://example.com/administrator-panel-yb556');
  adminPanelTag.innerText = 'Admin panel';
  ...
}
</script> 
```
This script adds a link to the user's UI if they are an admin user. However, the script containing the URL is visible to all users regardless of their role. 

* **Parameter-Based Access Control Methods**
Some applications determine the user's access rights or role at login, and then store this information in a user-controllable location, such as a hidden field, cookie, or preset query string parameter. After this application makes access control decisions based on the submitted value. For example
```
https://example.com/login/home.jsp?admin=true
https://example.com/login/home.jsp?role=1
```
This approach is basically insecure because a user can simply modify the value and gain access to functionality to which they are not authorized, such as administrative functions.

An alterantive attack can arise in relation to the HTTP method used in the request. If an attacker can use the GET (or another) method to perform actions on a restricted URL, then they can be bypass access control.

## Horizontal Privilege Escalation

Horizontal privilege escalation arises when a user is able to gain access to resources belonging to another user, instead of their own resources of that type this is also known as IDOR. For example, a user might ordinarily access their own account page using a URL like the following:
```
https://example.com/myaccount?id=123
```
Now, if an attacker modifies the id parameter value to that of another user, then the attacker might gain access to another user's account page, with associated data and functions.







