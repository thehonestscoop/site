---
title: The Gutter
type: docs
draft: false
weight: 1
---


# **The Gutter**



## **Usage**

A gutter is denoted by using a `div` tag with a class of `ths-gutter`. Multiple gutters can co-exist on the same page as long as there is no ancestral relationship (eg. parent-child).

Each gutter will operate independently to each other.

A gutter contains at least 1 strip but may contain more.


**You must prefix** each parameter below with `data-` in the HTML.

### **tags** (required)

A **tag** is used to create a strip. At least 1 `tag` is required.

Multiple tags can be defined by separating using a comma. When inserting [a marker,]({{< relref "markers.md" >}}) you must specify which strip the marker belongs to by using the `tag` parameter.


### **resolution** (default: 1)

The **resolution** sets how smoothly the gutter is rendered. The higher the resolution (denoted by a smaller value), the more processing time is required for each render.

The default of 1 pixel means the gutter is split into vertical sections of 1 pixel high for rendering purposes.

### **merge** (default: false)

The **merge** parameter sets whether or not the strips are combined into 1. If combined, then the first color is used.

### **width** (default: 2.5)

The **width** sets the width (in pixels) of each strip.

### **gap** (default: 0)

The **gap** sets the width (in pixels) of the space in between each strip.

### **placement** (default: &lsquo;left&rsquo;)

The **placement** parameter sets whether the gutter is positioned to the `left` or `right` of the passage of text.

### **margin** (default: 0)

The **margin** sets the left-most margin of the gutter (when `placement` is `left`) or the right-most margin of the gutter otherwise.

The `margin` does not influence the positioning of the passage of text. It merely shifts the gutter in the x-direction for aesthetic reasons.

### **padding** (default: 0)

The **padding** sets the padding of the passage of text.

Although the default `padding` is 0, for aesthetic reasons it may be wise to make adjustments.

### ~~**labels**~~


### **baseline** (default: 0's)

The **baseline** is used to calibrate the shading values of each strip. It is a comma-separated list of decimals (or percentages). Each value in the list corresponds to the `tags`.

Mathematically, it subtracts from the shading value prior to eventual rendering.

This is an advanced feature that should not be used in ordinary circumstances.

### **color** (default: black)

The **color** parameter is used to set the colors of the strips. It can be a single value or a comma-separated list corresponding to the `tags`.

If a single value is provided, then all strips will be that color.

The color value can be a predefined HTML color or in `#RRGGBB` format.

### **debug**

**debug** is not intended to be used by content creators. It is used by software developers wanting to make modifications to the library.

By enabling `debug` mode, the results of the sentence detection algorithm will be clearly demonstrated. Further diagnostic information will also be printed to the browser console.

Add the following `css` code inside the `head` tag:

```html
<style>
span.ths-sentence:nth-child(even){background-color:LightYellow}.ths-sentence:nth-child(odd){background-color:Salmon}.ths-sentence-start{background-color:Lime}.ths-sentence-end{background-color:Aqua}
</style>
```

## **Dynamic Fitting**

Obviously, the gutter's positioning needs to be adjusted if the structure of the page changes. For a smooth user experience, the gutter will rerender under these circumstances:

* When the DOM content is loaded
* 500ms after the DOM content is loaded
* After each image on the page loads
* 5 seconds after the DOM content is loaded
* 50ms after each window resize

If you discover a scenario that you feel should be catered for, please send us [an email](mailto:thehonestscoop@gmail.com) as soon as possible.


## **Example**

<p>
<strong style="background-color: yellow">&lt;div class="ths-gutter" data-placement='right' data-color="red,blue" data-width="5" data-resolution="1" data-margin="4" data-baseline="0,50%" data-debug=true data-gap="0" data-tags="xxx,zzz"&gt;&lt;/div></strong>
</p>
