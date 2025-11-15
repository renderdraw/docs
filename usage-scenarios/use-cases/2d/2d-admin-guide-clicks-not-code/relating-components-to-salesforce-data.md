---
description: >-
  Using our Record Lookup component, you can relate images that are draggable on
  the screen to Salesforce Data Records.
---

# Relating Components to Salesforce Data

Here's a visual look at how to relate subcomponents to Salesforce Data elements

{% embed url="https://app.tango.us/app/workflow/Relating-Components-to-your-Salesforce-Data-c37165782c1545d7af7c344595424975" %}

RenderDraw allows for the relating of:

* Droppable Areas
* DropZones
* Draggable Items
* Rooms (Layouts)

To Salesforce records. Previously, relating these objects was done by copying and pasting record Ids into a text field associated with each visual element. This was combersome, and led to issues when it came to migrating visuals from one org to another. Enter our Record Picker component. Easily search and relate elements to their appropriate Salesforce Records. From there, setup fallback unique fields to plan ahead for migrations. Let's take a closer look at this component in action: &#x20;

![](<../../../../.gitbook/assets/RenderDraw Architecture - Record Picker UI walkthrough.png>)

{% hint style="info" %}
Any object you hope to search for needs to be set up for searching in the object manager. Simply edit the object and check the "Allow Search" field and your object will be displayed while searching using the Record Picker component within RenderDraw
{% endhint %}

