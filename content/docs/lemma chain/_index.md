---
title: Lemma Chain
type: docs
draft: false	
weight: 0
---


# **Lemma Chain**



## **Overview**

Lemma-Chain is a **free** online service that allows you to store a reference to an **article** or **body of work**, and signify its relationship to other articles or bodies of work.

It can store arbitrary amounts of custom data such as the article's title and author as well as an optional arbitrary tag (`ref type`) indicating how it relates to another article.

An example might be the novel &ldquo;The Prisoner of Azkaban&rdquo; in the Harry Potter series. This `ref` can hold arbitrary custom data which contains the &lsquo;title&rsquo; and &lsquo;author&rsquo; as a JSON object. It can also be related to the novel &ldquo;The Chamber of Secrets&rdquo; (another `ref`) with the `ref type`: &lsquo;required,&rsquo; signifying that &ldquo;The Chamber of Secrets&rdquo; is required reading to read &ldquo;The Prisoner of Azkaban.&rdquo;

The chain can continue with &ldquo;The Chamber of Secrets&rdquo; `ref` linking to the novel &ldquo;The Philosopher's Stone.&rdquo; This novel, being the first in the series, has no required reading, hence does not have a `ref type`.

Although the example above is with regards to novels and pre-requisite reading, there is actually no limitation to its context.

The service is designed to be simple for non-technical people to use.

## **References**

The primary data object that Lemma-Chain stores is a `ref`.

Each `ref` is given a unique identifier (`id`) which can be used to query for its chain of related `refs`.

The unique identifier takes one of two forms: `@alpha/43rsyjtzt8` or `9v7s4gtgt9`.

The first (as signified by `@alpha/`) was created by a registered account: `alpha`.
The second form was created without a registered account.

The advantage of a registered account is that users can search for all references &lsquo;owned&rsquo; by that account.



