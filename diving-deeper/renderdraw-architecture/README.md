# RenderDraw Architecture

RenderDraw is native to the Salesforce platform. With a single install, you have access to all of our components, which are then licensed by feature. Understanding your use case is critical to the success of your project with RenderDraw.

<figure><img src="../../.gitbook/assets/RenderDraw Architecture - Architecture (1).png" alt=""><figcaption></figcaption></figure>

&#x20;Simply put, RenderDraw can be used anywhere in Salesforce in any case.&#x20;

### Answer these questions before beginning with RenderDraw

To understand what we are attempting to add interactions to, we need to answer a few things:

1. Where are we going to store the media associated with our interaction?
   1. By default, RenderDraw utilizes the Salesforce Files storage system, but it may make sense to host your files elsewhere, such as a CDN. Check out [storage-of-your-drawings](storage-of-your-drawings/ "mention")
2. What is the initial underlying use case?
   1. Start small and work outwards. Pick a cloud and add visuals, expand as needed to other objects using metadata relationships for reference or by adding new interactions. Check out [use-cases](../../usage-scenarios/use-cases/ "mention")
3. Who will be using the interaction?
   1. Permission Sets are delivered based on Licensed features, each user will need to be assigned a license and the appropriate level of permission sets to utilize the interaction. Check out [permissions-authorization.md](../../usage-scenarios/use-cases/other-apps/renderdraw-data-utilities/standard/annotateit-images/permissions-authorization.md "mention")

RenderDraw is meant to be additive across the entire Salesforce Landscape, and our components&#x20;
