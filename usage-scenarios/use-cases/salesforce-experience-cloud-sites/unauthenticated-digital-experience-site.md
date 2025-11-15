---
description: Ex. Public facing website
---

# Unauthenticated Digital Experience Site

1. Ensure that you have setup RenderDraw for use on Salesforce LWR templates by following the directions [here](../../../diving-deeper/using-components-on-lwr-digital-experiences.md)
2. Any uploaded assets need to be shared beyond the Admin user or they **will not** render on a Digital Experience site
   1.

       <figure><img src="../../../.gitbook/assets/image (117).png" alt=""><figcaption></figcaption></figure>
3. The Lightning Flow and/or LWC setup to show the RenderDraw component needs to have a **boolean flag input** parameter for **useInDigitalExperience**
   1.

       <figure><img src="../../../.gitbook/assets/image (65).png" alt=""><figcaption></figcaption></figure>
4. In the Digital Experience Site Builder, ensure that the Flow and./or LWC using RenderDraw has both **{!recordId}** in the Record ID field and **Use In Digital Experience** checked
   1.

       <figure><img src="../../../.gitbook/assets/image (119).png" alt="" width="268"><figcaption></figcaption></figure>
5. In the Digital Experience Site Builder Settings (under General), ensure that **Public Access** and a **Guest User Profile** are checked and setup
   1.

       <figure><img src="../../../.gitbook/assets/image (118).png" alt=""><figcaption></figcaption></figure>
6. The underlying **User** that is assigned to that **Guest User Profile,** must have a **RenderDraw License** assigned to them as well as any relevant **RenderDraw** **Permission Sets**.
   1. This user has a "**Guest License**" User License type
