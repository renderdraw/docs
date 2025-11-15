# Embedding Digital Twin Components



#### There are two main components that can be added to your Salesforce objects, flows, and/or digital experiences.

####

1. Digital Twin Search Flow Component&#x20;
   1. **Add** the flow called "**Digital Twin Search**" to your object record page (Ex. Account Record Page)
      1. Note: Check the "Pass record ID into this variable" box
      2.

          <figure><img src="../../../.gitbook/assets/image (57).png" alt=""><figcaption></figcaption></figure>
2. RenderDraw DigitalTwin Component
   1. Add "RenderDraw Digital Twin" component to your various record pages (Ex. Objects, Dashboard, etc.)
      1.

          <figure><img src="../../../.gitbook/assets/image (92).png" alt=""><figcaption></figcaption></figure>


   2. For **Digital Experiences**, please follow these steps:
      1. **Create** a new **flow** and create **2 new variables**
         1. Variable #1: Text variable with API Name "recordId" and both Available for Input and Output checked
            1.

                <figure><img src="../../../.gitbook/assets/image (95).png" alt=""><figcaption></figcaption></figure>


         2. Variable #2: Boolean variable with API Name "useInDigitalExperience" and Available for Input checked
            1.

                <figure><img src="../../../.gitbook/assets/image (96).png" alt=""><figcaption></figcaption></figure>


      2. **Add** a **Screen Element** to the flow and add the **RenderDraw Digital Twin component** and configure as follows
         1.

             <figure><img src="../../../.gitbook/assets/image (97).png" alt=""><figcaption></figcaption></figure>


      3. On Digital Experience page, add a Flow Component with the flow created above and the following boxes checked:
         1.

             <figure><img src="../../../.gitbook/assets/image (99).png" alt=""><figcaption></figcaption></figure>
