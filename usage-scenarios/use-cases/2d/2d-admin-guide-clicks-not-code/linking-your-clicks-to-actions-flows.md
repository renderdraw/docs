---
description: >-
  Visuals are nice, but without interactions, they are just pretty. Let's take a
  look at how we can add interactions
---

# Linking your clicks to Actions / Flows

By default, we don't call any flows, but we allow you to map your Screen flows to a set of interaction events within our 2D Canvas Component. Remember to include input parameters in your **active** flows. Select the appropriate flow under the **Environment Options - Default Related Objects & Actions** tab.

<figure><img src="../../../../.gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>

### Canvas Changed Event&#x20;

This event is called any time the canvas is changed. This includes if the canvas has items loading on start. We pass a CanvasScene object named **canvas**  and can accept menubarText errorText successText as output depending on what happens in your flow. This can either be displayed or hidden based on the checkbox "visual display in popup"

### List Item Clicked Event&#x20;

When displaying the list of Draggable items or Droppable areas, this flow will be displayed when a list item is clicked. This is typically great for displaying information for items before their being added to the canvas. We pass **recordId,** which is required on your flow.&#x20;

### Droppable Area Clicked Event&#x20;

When a Droppable Area is clicked, the flow displays in a popup. We pass **recordId,** which is required on your flow.&#x20;

### Draggable Item Clicked Event&#x20;

When a Draggable Item is clicked, the flow displays in a popup. We pass **recordId,** which is required on your flow.&#x20;

### Selectable Shape Clicked Event&#x20;

When a Selectable Shape is clicked, the flow displays in a popup. We pass **recordId,** which is required on your flow.&#x20;

### Clickable Image Clicked Event

When a Clickable Image is clicked, the flow displays in a popup. We pass **recordId,** which is required on your flow.&#x20;
