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
