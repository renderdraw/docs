---
description: >-
  When you need to update an intertaction within a 2D screen, often it is wise
  to use a Salesforce Lightning Flow
---

# Data interaction within a Flow

### From the Configuration of the scene, make sure you setup the scene for use within a Lightning flow

<figure><img src="../../../../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>

1.  Ensure you have the show next option selected; this will allow the user to see the proceed button (shown as save)

    **a.** Optionally set the text and the icon for the next button. The icons are available at [https://www.lightningdesignsystem.com/icons/ ](https://www.lightningdesignsystem.com/icons/)
2. Check the "Use with Lightning flow" option to ensure that when a user presses proceed, the Canvas object is generated and sent to the next step of the lightning flow
3. The Next button has been displayed to the user for interaction.

{% hint style="info" %}
You can redirect the user flow to the 2D canvas within a flow if you modify the Canvas object properties. The canvas will redraw based on the properties passed
{% endhint %}

Our interactions pass a apex object back and forth, and this object is detailed here:

[canvas.md](../../../../api-documentation/data-objects-used-throughout-the-suite/canvas.md "mention")

This Canvas object contains the latest information from the canvas directly.&#x20;

The standard data flow goes something like this:

<img src="../../../../.gitbook/assets/image (44).png" alt="" data-size="original">

Where we are using the Canvas object as a variable and mapping properties from it's sub-objects (in this case, draggable items) into products in a custom configuration scenario.

Setting up a Canvas object is as simple as defining the variable:

![](<../../../../.gitbook/assets/image (48).png>)

and then mapping before and after the canvas interaction

![](<../../../../.gitbook/assets/image (42).png>)

