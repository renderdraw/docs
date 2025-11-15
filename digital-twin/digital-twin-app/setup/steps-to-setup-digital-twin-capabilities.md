# Steps to Setup Digital Twin Capabilities

**Prerequisite Tasks:**

1. Install **both** the Main RenderDraw and Digital Twin Salesforce packages
   1. Install Main package first. Instructions found [here](../../../getting-started-with-renderdraw/installation.md)

**Tasks:**

1. Add two tabs (ex. 3D Visual and 3D Admin) to **Object Lightning Record Page** where your products are maintained and will be visualized
   1. Ex. Product Standard Object
   2.

       <figure><img src="../../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>
   3. On the first newly created tab, drag Custom Component **3D Interaction Canvas**
   4. On the second newly created tab, drag Custom Component **3D Scene Director**
   5. Activate and Save layout
2. Add tab (ex. Digital Twin) to **Object Lightning Record Page** where your assets are maintained and will be visualized
   1. Ex. Asset Standard Object
   2.

       <figure><img src="../../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>
   3. On the newly created tab, drag Custom Component **RenderDraw Digital Twin**
   4. Activate and Save layout
3. Add Flow to **Object Lightning Record Page** where your customer accounts are maintained named Digital Twin Search referenced [here](https://docs.renderdraw.us/digital-twin/digital-twin-app/setup/visualization)
   1. Ex. Account Standard Object
   2.

       <figure><img src="../../../.gitbook/assets/image (16).png" alt=""><figcaption><p><strong>Note</strong>: Out of the box actions available on the bottom right section</p></figcaption></figure>
4. Create **custom text field** (255 characters) on **Object** where your products are maintained and will be visualized named "**Drawing Reference**"
   1. Ex. Product Standard Object&#x20;
   2.

       <figure><img src="../../../.gitbook/assets/image (17).png" alt=""><figcaption><p><strong>Note:</strong> Set max character length at bottom of page to 255 characters</p></figcaption></figure>
5. Create **custom lookup field** on **Object** where your products are maintained and will be visualized named "**Parent Product**" that is **Related To = Product**
   1. Ex. Product Standard Object&#x20;
   2.

       <figure><img src="../../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>
6. Create a new **formula text field** on **Object** where your assets are maintained and will be visualized
   1. Ex. Asset Standard Object&#x20;
   2. Name = "Drawing Reference"&#x20;
   3. Forumla Return Type = "Text"
   4. Formula = _**Product2.Drawing\_Reference\_\_c**_
      1.

          <figure><img src="../../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>
   5. Save
7. Edit Custom Metadata Type
   1. Setup -> Custom Metadata Types -> RenderDraw Relationship -> Manage Records -> Edit "Product Relationship"&#x20;
      1.

          <figure><img src="../../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>
   2. Child Node Related Object = Product&#x20;
   3. Child Node Lookup Field = "Drawing Reference"&#x20;
      1.

          <figure><img src="../../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>
   4. Save
8. Add New Custom Metadata Record
   1. Setup -> Custom Metadata Types -> RenderDraw Relationship -> Manage Records -> New ->&#x20;
      1.

          <figure><img src="../../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>
   2. Name = Asset, Entity = Asset
   3. RenderDraw Setting = Default RenderDraw Settings&#x20;
   4. Parent Relationship Settings Lookup = Product ID&#x20;
      1.

          <figure><img src="../../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>
   5. Save
9. Edit Custom Metadata Type
   1. Setup -> Custom Metadata Types -> Digital Twin Settings -> Manage Records -> Edit "Asset Digital Twin"&#x20;
      1.

          <figure><img src="../../../.gitbook/assets/image (69).png" alt=""><figcaption></figcaption></figure>
   2. Value Field = "Drawing Reference"
      1.

          <figure><img src="../../../.gitbook/assets/image (67).png" alt=""><figcaption></figcaption></figure>
   3. Save
10. Ensure **both** page layouts used from above have **Drawing Reference** field **added**
11. Create Parent Product
    1. **Drawing Reference** field should be the **naming convention** used in the **visualization root object**
12. Create Children Products
    1. Relate Parent Product field
    2. **Drawing Reference** is the **naming convention** used in the **visualization file for given node**
13. Create Assets
    1. Parent and children products all need asset records
    2. Reference Products created in Steps 10-11, and Parent Asset accordingly
