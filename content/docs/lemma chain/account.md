---
title: Accounts
type: docs
draft: false
weight: 2
---


# **Accounts**

A reference can be owned by a registered account or unowned. The advantage of creating a registered account is that all references created under the account can be listed together.

Each account must have a unique name. Once created, the name will be prepended with a `@`. Each account must also be registered with a unique non-disposable email address.


## **Create**

`POST https://lemma-chain.thehonestscoop.com/accounts`

An account name must not contain `@`, `/` and white-spaces. It must also be less than 50 characters long.

An example request:

```json
{
	"name": "alpha",
	"email": "test@gmail.com",
	"password_1": "password123",
	"password_2": "password123",
	"recaptcha_code": ""
}
```

There are various validation rules in place. The HTML form used for account creation must submit 2 identical passwords to satisfy validation.


If any validation fails, an error message will be returned.
If account creation is successful, a 200 Status code is returned.


## **List References**

`GET https://lemma-chain.thehonestscoop.com/accounts/:name`

All references owned by the `:name` will be listed provided that account owner is currently [authenticated]({{< relref "authentication.md" >}}) for the request. If the owner is not authenticated, the `email` information will not be revealed.  Only `searchable` references will be listed.


An example response:

`GET https://lemma-chain.thehonestscoop.com/accounts/alpha`

```json
{
  "name": "@alpha",
  "email": "alpha@gmail.com",
  "refs": [
    {
      "id": "@alpha/43rsyjtzt8",
      "data": "{\"title\":\"The Bible\"}",
      "searchable": true,
      "search_title": "Bible",
      "search_synopsis": "most popular religious text",
      "created_at": "2019-03-25T07:40:30.284795+11:00"
    },
    {
      "id": "@alpha/9v7s4gtgt9",
      "data": "{\"title\":\"Dictionary\"}",
      "searchable": true,
      "search_title": "common book",
      "search_synopsis": "you can check definitions",
      "created_at": "2019-03-25T07:39:45.714502+11:00"
    }
  ]
}
```

