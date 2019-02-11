---
title: FAQ
type: docs
draft: false
weight: 4
---

# **Frequently Asked Questions**


## **How can I diagnose potential issues?**

You can enable `debug` mode for the gutter. This will clearly showcase the results of the sentence detection algorithm as well as print out various diagnostic details in the browser console. See more [info here]({{< relref "gutter.md#debug" >}}).

## **Can I implement other shading equations other than a standard Bell Curve?**

At this stage, only a standard Bell Curve is implemented. If there is sufficient demand in the future, it will definitely be possible.

## **Are other static site generators like Jekyll supported?**

The Gutter can be easily implemented for almost any standard website using the standard Javascript API. It can be easily implemented for Jekyll with minimal fuss.

However, for tight integration (such as the native support for Hugo) more detailed work is required. Pull Requests are greatly appreciated.

## **How accurately are sentences detected?**

Latin-based languages (such as English) are supported well. However, the sentence detection algorithm is not perfect and can be [improved further.]({{< relref "bounty.md" >}})

## **Can I add new abbreviations?**

Abbreviations (with periods inside) cause havoc to the sentence detection algorithm. The list of English abbreviations [can be found here.](https://github.com/thehonestscoop/gutter/blob/master/src/regex.js#L9)

Let us know if you want to add more.
