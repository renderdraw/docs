# Setup Logic for Interactions

The integration between RenderDraw and Salesforce RCA is powered by RenderDraw subscribing to RCA's Lightning Messaging Service (LMS) messages and taking action based on the content.

**Tasks:**

1. Within RenderDraw component on Product record, navigate to the "**Logic**" tab:
   1.

       <figure><img src="../../../../../../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>
2. Click "**Add Interaction Event**"
   1.

       <figure><img src="../../../../../../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>


3. Add "**Name**" for your event and select one of 3 event **Type**
   1. **Note**: The naming convention should mirror RCA Product "Attributes" and/or "Options"
   2. The event types perform the following:
      1. Focus: An event that highlights or maneuvers the scene to a specific area
      2. Change: An event that performs various actions that change a node, mesh, texture, material within the 3D model
      3. Focus Lost: An event that performs the inverse of Focus event
   3.

       <figure><img src="../../../../../../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>
4. For event type **Focus**:
   1. Create a new "**Action Item**" and optionally rename it
      1.

          <figure><img src="../../../../../../../.gitbook/assets/image (103).png" alt=""><figcaption></figcaption></figure>
   2. In the "**Steps**" section of the Action, click "**Add Step**" and select "Camera" tab, click "**Position and Aim Camera**", click "**Select**"
      1.

          <figure><img src="../../../../../../../.gitbook/assets/image (104).png" alt=""><figcaption></figcaption></figure>


   3. Click "**Set Visually**" and position camera to your desired location, click "**Get Camera Position & Aim**", and click "**Set Input Parameters"**:
      1.

          <figure><img src="../../../../../../../.gitbook/assets/image (105).png" alt=""><figcaption></figcaption></figure>


      2.

          <figure><img src="../../../../../../../.gitbook/assets/image (106).png" alt=""><figcaption></figcaption></figure>


   4. Click "**Save Changes**"
      1.

          <figure><img src="../../../../../../../.gitbook/assets/image (107).png" alt=""><figcaption></figcaption></figure>
5. For event type **Focus Lost:**&#x20;
   1. No need to create any actions, just ensure your event matches the naming convention of the **Product Attribute and/or Option**
   2.

       <figure><img src="../../../../../../../.gitbook/assets/image (108).png" alt=""><figcaption></figcaption></figure>


6. For event type **Change**:
   1. Create a new "**Action Item"** and name it to match the naming convention of the **Product Attribute and/or Option** you wish to target:
      1.

          <figure><img src="../../../../../../../.gitbook/assets/image (109).png" alt=""><figcaption></figcaption></figure>


   2. Under the **"Conditions"** section, create a condition, or multiple, that inform this action of what to look for to execute:
      1.

          <figure><img src="../../../../../../../.gitbook/assets/image (110).png" alt=""><figcaption></figcaption></figure>


   3. Under the **"Steps"** section, click **"Add Step"** to add the step(s) to take as a result of the condition(s) being met:
      1.

          <figure><img src="../../../../../../../.gitbook/assets/image (112).png" alt=""><figcaption></figcaption></figure>


7. Click **"Save Changes"**
   1.

       <figure><img src="../../../../../../../.gitbook/assets/image (113).png" alt=""><figcaption></figcaption></figure>
