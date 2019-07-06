---
title: References
type: docs
draft: false
weight: 3
---


# **References**

A reference is the primary data entity. It can hold custom arbitrary data in the form of a JSON object. The reference can be located using the `GET /:ref` endpoint.

## **Create**

`POST https://lemma-chain.thehonestscoop.com/ref`


### **owner**  (optional)

The **owner** parameter sets the account name of the prospective reference. If unset, the reference will be &lsquo;unowned&rsquo; by an account. If set, the account owner must be currently [authenticated]({{< relref "authentication.md" >}}).

### **parents**  (optional)

**parents** are other references that the prospective reference links to. It accepts an array of strings where the first part is the `ref type`. This can be an arbitrary tag that does not contain `"`, `@` or `/`. It is followed by a `:` and then the identifier of the other reference.

Each reference can have up to 250 parent refs.

### **data**  (required)

The **data** parameter is used to store arbitrary custom data associated with the reference. Each reference must contain some data - even if it is an empty JSON object. It must be a string containing a JSON payload. It can contain at most **12kB** of data.

### **searchable**  (optional)

When **searchable** is set, the reference can be discovered by the [search]({{< relref "search.md" >}}) endpoint. The default value is false.


### **search_title** and  **search_synopsis** (optional)

The **search_title** and **search_synopsis** are used to provide extra details to help the [search]({{< relref "search.md" >}}) endpoint understand the content of the reference. When **searchable** is set to true, **search_title** and/or **search_synopsis** is required.

The **search_title** must be a title containing less than **100** characters. The **search_synopsis** is more descriptive and must contain less than **800** characters.

An example request:

```json
{
	"owner": "@alpha",
	"parents": ["required:@alpha/redsss242", "recommended:mnn2sdew76"],
	"data": "{\"custom_data\": \"abcdef\"}",
	"searchable": true,
	"search_title": "A book title",
	"search_synopsis": "The blurb of the book",
	"recaptcha_code": ""
}
```

An example response:

```json
{
  "link": "fjyvs4c2jk"
}
```

## **Find a ref and all its parents**

`GET https://lemma-chain.thehonestscoop.com/:ref?depth=x&types=a,b`

This endpoint has a max query duration of 300ms. If the query takes longer, then a 408 Status code is returned. The results of this endpoint are cached for 15 minutes.


### **depth**  (optional)

Since each reference can link to multiple other parent references, which can each link to multiple other parent references, the **depth** parameter sets a limit to the recursion.

In most cases, the **depth** parameter should be unset since you want the full chain of references returned.

### **types**  (optional)

The **types** parameter is a comma-delimited list of `ref types` that you want to filter for. In common use cases, you want all `ref types` returned.

**NOTE:** The custom JSON data is expanded out in the response. In all other endpoints, the response returns the data as a JSON-encoded string.

An example response:

`GET https://lemma-chain.thehonestscoop.com/23js45tbtl4?types=required,recommended`

```json
{
  "id": "23js45tbtl4",
  "data": {
    "custom_data": "abcdef"
  },
  "refs": [
    {
      "data": {
      },
      "id": "y2zsbpt8tdd",
      "ref_type": "recommended"
    },
    {
      "data": {
        "Title": "required reading"
      },
      "id": "@beta/p8rsy7tjt7y",
      "ref_type": "required",
      "refs": [
        {
          "data": {
            "title": "Dictionary"
          },
          "id": "@alpha/9v7s4gtgt9",
          "ref_type": "required"
        },
        {
          "data": {
            "title": "The Bible"
          },
          "id": "@alpha/43rsyjtzt8",
          "ref_type": "recommended"
        }
      ]
    }
  ]
}
```