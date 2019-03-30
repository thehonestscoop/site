---
title: Authentication
type: docs
draft: false
weight: 5
---

# **Authentication**

The request must be authenticated to:

* Create a reference owned by an account
* List **all** references owned by an account (instead of just [searchable]({{< relref "search.md" >}}) references)


## **Request Headers**

The HTTP request must contain these custom headers.

### **X-AUTH-ACCOUNT**

The account's name or associated email address.


### **X-AUTH-PASSWORD**

The account's password.


## **Response**

* If authentication fails, a 401 Status Code is returned with no accompanying error message.
* If the account's associated email address hasn't been verified, a 401 Status Code is returned along with an error message explaining the reason.