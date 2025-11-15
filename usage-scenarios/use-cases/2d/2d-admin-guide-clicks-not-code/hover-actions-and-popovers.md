# Hover Actions and Popovers

RenderDraw's 2D scene editor component enhances your visual representation by offering dynamic hover information display functionalities. These features are designed to provide immediate, contextual information, improving user experience and interaction with 2D layouts or entities.

### Overview

RenderDraw integrates seamlessly with Salesforce, allowing users to link 2D entities to Salesforce records. Through intuitive hover actions, users can access a variety of information and navigate Salesforce records directly from the 2D scene editor. This document outlines the capabilities and configuration options available for hover information displays.

#### Key Features

* **Hover-Over Information**: Displays the name of the element or linked Salesforce record details on hover.
* **Salesforce Record Component Display**: Shows default record components from Salesforce for linked entities.
* **Navigation to Records**: Enables navigation to the linked Salesforce record, supporting both digital experiences and internal Salesforce navigation.
* **Custom Lightning Flow**: Administrators can select a Lightning flow to display information in a popover linked to the element's location on hover.

#### Setting Up Hover Actions

<figure><img src="../../../../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>

Hover actions are additional to click actions and can be configured in the 2D scene editor's environment options. Here's how to set them up:

1. **Access the 2D Scene Editor**: Open your environment with RenderDraw installed and navigate to the 2D scene editor component.
2. **Configure Environment Options**: Locate the environment options panel. Here, you will find settings for enabling or customizing hover and click actions.
3. **Hover Information Settings**: Within the environment options, you can specify what information is displayed on hover. Options include:
   * Displaying the element's name.
   * Showing Salesforce record components for linked entities.
   * Configuring navigation to the Salesforce record or digital experience.
4. **Custom Lightning Flow**: To set up a custom Lightning flow, select the desired flow from the available options. Ensure you specify the `recordId` to pass to the flow, facilitating a contextual information display on hover.
5. **Save Your Configuration**: After configuring the hover information settings, save your changes. Ensure to test the hover functionality to confirm that the information displays correctly and as expected.

<figure><img src="../../../../.gitbook/assets/image (60).png" alt=""><figcaption></figcaption></figure>

### Additional Notes

* **Popover Location**: The information popover is dynamically positioned based on the element's location in the 2D scene, ensuring optimal visibility and user experience.
* **Admin Focus**: These features are designed with an administrative focus, allowing for easy setup and customization without the need for extensive 3D visual expertise.
* **Compatibility**: The hover information display features are compatible with standard Salesforce records and custom Lightning flows, offering flexibility in how information is presented.

For more detailed guidance on configuring and utilizing these features, please refer to the specific sections in the RenderDraw documentation or contact our support team for personalized assistance.

\
