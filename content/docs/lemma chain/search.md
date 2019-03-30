---
title: Search
type: docs
draft: false
weight: 4
---

# **Search**

`GET https://lemma-chain.thehonestscoop.com/search/:terms`

All references that are set to &lsquo;searchable&rsquo; are potentially discoverable by the search endpoint. The `search_title` and `search_synopsis` fields are used to find relevant references.

This endpoint has a max query duration of 300ms. If the query takes longer, then a 408 Status code is returned. The results of this endpoint are cached for 15 minutes.

**NOTE:** Characters such as `?` require encoding to prevent interpretation as query parameters.


An example response:

`GET https://lemma-chain.thehonestscoop.com/search/popular`

```json
{
  "results": [
    {
      "created_at": "2019-03-25T07:40:30.284795+11:00",
      "data": "{\"title\":\"The Bible\"}",
      "id": "@alpha/43rsyjtzt8",
      "search_synopsis": "most popular religious text",
      "search_title": "Bible"
    }
  ]
}
```