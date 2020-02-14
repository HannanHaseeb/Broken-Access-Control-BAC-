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

* **Veritcal Privilage Escalation**
If a user can gain access to functionality that they are not allowed to access then this is vertical privilege escalation. For example, if a standerd user can gain access to an admin page where they can delete user accounts, then this is vertical privilege escalation.

* **Unprotected Functionality**
At its most basic, vertical privilege escalation arises where an application does not implement any protection over sensitive functionality.

For example, a website might host sensitive functionality at the following URL:
```
 https://exapmle.com/admin
 ```
In some cases, the sensitive functionality URL might be disclosed in other locations, such as the `robots.txt` file: 
```
 https://example.com/robots.txt
 ```

