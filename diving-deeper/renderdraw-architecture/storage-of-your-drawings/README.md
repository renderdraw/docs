# Storage of your Drawings

RenderDraw is a versatile 3D rendering platform that seamlessly integrates with Salesforce, offering both 2D and 3D canvas interfaces for various visualization needs. One of the key features of RenderDraw is its flexibility in file storage and integration, allowing users to store and manage their files using different options.

### Salesforce Files Integration

RenderDraw provides direct integrations and components for storing files directly on Salesforce Files. This integration is particularly convenient for most users, as it allows them to keep their files within the Salesforce ecosystem, ensuring easy access and management.

Benefits of using Salesforce Files:

* Native integration with RenderDraw components
* Seamless access to files within the Salesforce environment
* Ideal for storing compressed 3D files and images

### Third-Party Storage Integration

In addition to Salesforce Files, RenderDraw also supports file storage in popular third-party platforms such as Amazon S3, Azure, and Google Cloud. This flexibility allows organizations to leverage their existing file storage infrastructure or choose the platform that best suits their needs.

Considerations for using third-party storage:

* Large volumes of 3D files: If your organization deals with a significant number of 3D files, third-party storage can provide scalability and cost-effectiveness.
* Existing drawing management systems: If you already have a drawing management system in place, integrating RenderDraw with your existing third-party storage can ensure a seamless workflow.

### File Compression and Optimization

When working with large CAD files, RenderDraw automatically compresses and optimizes them during the conversion process. Original CAD files, which can be around 100MB in size, are compressed to the size of a large image (typically 2-5MB) after conversion. This compression ensures efficient storage and faster loading times within the RenderDraw platform.

Images, on the other hand, are often better hosted directly in Salesforce Files. RenderDraw fetches these images natively, providing a smooth and integrated experience for users.

### Choosing the Right File Storage Option

When deciding on the file storage option for your RenderDraw implementation, consider the following factors:

* RenderDraw requires no setup for Salesforce Files option. There will be some setup required for storing files outside of the platform
* File types and sizes: Evaluate the types and sizes of files you'll be working with, such as CAD files, images, and PDFs.
* Storage capacity: Assess your storage requirements based on the volume of files you expect to manage.
* Existing infrastructure: Consider your organization's existing file storage infrastructure and whether integrating RenderDraw with your current setup would be beneficial.
* Access and collaboration: Determine the level of access and collaboration needed for your files within the RenderDraw platform.

By leveraging the file storage and integration capabilities of RenderDraw, organizations can optimize their visualization workflows, ensure efficient file management, and seamlessly collaborate within the Salesforce ecosystem.
