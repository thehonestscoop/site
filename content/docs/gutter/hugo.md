---
title: Hugo shortcodes
type: docs
draft: false
weight: 3
---


# **Hugo shortcodes**

## **What is Hugo?**

[Hugo](https://gohugo.io/) is a leading static site generator which allows you to generate websites with minimal coding expertise. It is extremely popular for creating high-quality blogs and documentation.

**The Gutter** can be easily integrated to Hugo sites, but it does require you to make some minor *coding* adjustments.


## **Usage**

### **HTML Template**

1. Add the Gutter library to the bottom of the HTML template
2. Make sure it is somewhere below the closing `</body>` tag.

The HTML template files can be found in the `layouts` directory.


```html
<script src="https://unpkg.com/@thehonestscoop/gutter@latest" defer></script>
```

* [See Single Page Templates](https://gohugo.io/templates/single-page-templates/)

### **Create Shortcodes**

1. Create shortcodes in `layouts/shortcodes` directory

```html

gutter.html: 

<script>
var parentTag = document.scripts[document.scripts.length - 1].parentNode;parentTag.classList.add("ths-gutter");
{{ with .Get "tags"}} parentTag.setAttribute('data-tags', '{{.}}'); {{ end }}{{ with .Get "debug"}} parentTag.setAttribute('data-debug', '{{.}}'); {{ end }}{{ with .Get "placement"}} parentTag.setAttribute('data-placement', '{{.}}'); {{ end }}{{ with .Get "width"}} parentTag.setAttribute('data-width', '{{.}}'); {{ end }}{{ with .Get "color"}} parentTag.setAttribute('data-color', '{{.}}'); {{ end }}{{ with .Get "margin"}} parentTag.setAttribute('data-margin', '{{.}}'); {{ end }}{{ with .Get "resolution"}} parentTag.setAttribute('data-resolution', '{{.}}'); {{ end }}{{ with .Get "gap"}} parentTag.setAttribute('data-gap', '{{.}}'); {{ end }}{{ with .Get "labels"}} parentTag.setAttribute('data-labels', '{{.}}'); {{ end }}{{ with .Get "baseline"}} parentTag.setAttribute('data-baseline', '{{.}}'); {{ end }}{{ with .Get "padding"}} parentTag.setAttribute('data-padding', '{{.}}'); {{ end }}{{ with .Get "merge"}} parentTag.setAttribute('data-merge', '{{.}}'); {{ end }}
</script>

marker.html:

<span class="ths-marker"
{{ with .Get "tag"}} data-tag="{{.}}" {{ end }}
{{ with .Get "max"}} data-max="{{.}}" {{ end }}
{{ with .Get "limit"}} data-limit="{{.}}" {{ end }}
{{ with .Get "spread"}} data-spread="{{.}}" {{ end }}
></span>

```


* [See Shortcodes](https://gohugo.io/content-management/shortcodes/)


### **Add Gutter**


In your content file (`*.md`) insert something like this at the top:

```html

{\{< gutter placement="left" color="red,green" width="5" margin="1" padding="5" resolution="1" gap="0" tags="xxx,zzz" >}}

```

Read the documentation for more information on the various parameters. You must not prepend the parameters with `data-*`. 

Also remove the `\` inside the `{\{<` above.

### **Add markers**

In your content file (`*.md`) insert something like this at various points where you want markers:

```html

{\{< marker tag="xxx" max="100%"  >}}

```

Read the documentation for more information on the various parameters. You must not prepend the parameters with `data-*`. 

Also remove the `\` inside the `{\{<` above.


## **Known Issues**

If the gutter is affecting your page summary, then either place it lower down or set the summary manually using the front-matter.
