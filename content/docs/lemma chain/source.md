---
title: Source Code
type: docs
draft: false
weight: 7
---

# **Source Code**

The source code is openly available. It is programmed in Go 1.11+.

## **Dependencies**

[DGraph 1.1+](https://github.com/dgraph-io/dgraph) is a performant, developer-friendly graph database.

## **Repository**

[https://github.com/thehonestscoop/lemma-chain](https://github.com/thehonestscoop/lemma-chain)

## **Docker**

A Docker image can be created using the [Dockerfile](https://github.com/thehonestscoop/lemma-chain/tree/master/docker).

It is designed to store DGraph data in an s3-compatible bucket.

You can run it with a command like this:

```
docker run --name lemma-chain -e AWS_ACCESS_KEY_ID=xxx_key -e AWS_SECRET_ACCESS_KEY=xxx_secret -e BUCKET_NAME=xxx_bucket_name --privileged -p 1323:1323 thehonestscoop/lemma-chain
```

## **Configuration**

All configuration values are set via Environment Variables.

### HASHID_SALT

A random string used to create unique identifiers. Once set in production, it must not be modified.


### MAX_PAYLOAD_KB (default: 12)

Each reference can store associated custom JSON data. This parameter sets the maximum size of the payload in kilobytes.

### BEHIND_PROXY (default: 0)

If the application sits behind a proxy, set to 1.

### PORT (default: 1323)

The port used to listen for connections.

### QUERY_TIMEOUT (default: 300ms)

To prevent abuse of the service, a timeout (in ms) can be set. 

### CACHE_DURATION (default: 15)

Results of `GET` endpoints are cached for a duration (in minutes) based on this setting.

### RATE_LIMIT (default 4.0)

To prevent abuse of the service, a maximum number of requests per second per IP address can be set.

### RECAPTCHA_SECRET

All `POST` requests require passing [Google recaptcha](https://www.google.com/recaptcha/intro/v3.html) validation. You can set your recaptcha secret here. The default value allows all requests to pass validation.

### ACCOUNT VERIFICATION

If both `GMAIL_ACCOUNT` and `GMAIL_PASSWORD` are not set, all accounts will be created in a verified state.

WEBSITE_URL 

The website url (if you create references and accounts via a website).

HOST_URL 

The url of the lemma chain server application.

GMAIL_ACCOUNT

Gmail email address for account verification emails to be sent from. 

GMAIL_PASSWORD 

Gmail password for the above gmail account.

SMTP_HOST (default: "smtp.gmail.com")

SMTP Host domain of your email server.

SMTP_PORT (default: 587)

SMTP Port of your email server.



