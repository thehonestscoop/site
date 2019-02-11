---
title: Markers
type: docs
draft: false
weight: 2
---


# **Markers**

## **Usage**

A marker is denoted by using a `span` tag with a class of `ths-marker`. You can place markers within the boundary of any sentence. 

**You must prefix** each parameter below with `data-` in the HTML.

### **tag** (required)

The **tag** denotes to which strip in the gutter the marker belongs to.

### **max** (default: 1.0)

The **max** signifies the maximum shade in the strip. The maximum shade is **always** at the position of the marker and is usually 100% unless reduced by the `max` parameter.

The value can be a decimal ranging from `0.0` to `1.0` or a percentage. A value of `0.5` indicates that the shade is at 50% darkness compared to the default.

### **limit** (default: no limit)

The **limit** specifies the range of the shading on either side of the marker.

A `limit` of `"3s"` means the shading will apply from `±3 (inclusive)` sentences on either side of the location of the marker. The shading will abruptly end at the limit.


### **spread** (default: no spread)

The **spread** is used to apply a gradient to the strip's shade based on the equation for a bell curve. 

The `spread` parameter requires 2 numbers separated by a comma. The first number represents the sentences away from the marker and the second decimal represents what the shade value should be at that position.

A spread of `3,95%` indicates that the shading of the strip should be at 95% darkness when it is 3 sentences away from the location of the marker.

The `max` value is independent of the spread. A spread of `95%` at 3 sentences away does not necessarily render to a `95%` shade. The `max` will get multiplied to further reduce the shade.

## **Overlapping Markers**

When multiple markers overlap, the darkest marker gets rendered. This is also the case when multiple markers have different spread values. At any given sentence, the darkest shade is used.

## **Example**

<p>
In viverra nunc et commodo finibus. Sed id molestie sapien. Cras eu leo non augue vulputate posuere ac sed justo <strong style="background-color: yellow">&lt;span class="ths-marker" data-tag="xxx" data-max="75%" data-spread="3,95%">&lt;/span&gt;</strong> nullam ac dolor ut nisl molestie fringilla. Phasellus nec risus eu leo aliquam ornare. Etiam mi neque, <strong style="background-color: yellow">&lt;span class="ths-marker" data-tag="yyy" data-max="100%" data-limit="1s">&lt;/span></strong> iaculis at sapien in, vestibulum euismod felis.
</p>

