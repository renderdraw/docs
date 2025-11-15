---
description: >-
  RenderDraw is a Salesforce application that enables visual interaction across
  many digital mediums for any object or app in Salesforce.
cover: >-
  https://images.unsplash.com/photo-1555371363-27a37f8e8c46?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHwzfHxTYWxlc2ZvcmNlfGVufDB8fHx8MTY4NzI2NjE0MXww&ixlib=rb-4.0.3&q=85
coverY: 0
---

# Getting Started with RenderDraw

To get started with RenderDraw, consult with our architects for a personalized guide or follow the guide below

### 1 - Installation

RenderDraw is a native Salesforce application, requiring a standard installation using the install link provided with your welcome email. Follow the guide to install in your Sandbox environment to setup RenderDraw, then repeat for other environments such as production.&#x20;

<figure><img src="../.gitbook/assets/RenderDraw Architecture - Install Flow.png" alt=""><figcaption></figcaption></figure>

{% content-ref url="installation.md" %}
[installation.md](installation.md)
{% endcontent-ref %}

### 2 - Define your visual interaction use case

RenderDraw provides several components to enhance the Salesforce experience by adding interactive visual aids. Now it's time to decide where to start with your first interaction. If you are already aware of your direct use case e.g. 3D Visualization for a CPQ configuration, this section can serve as inspiration for other potential use cases for your Salesforce orgs to ensure you get the most value out of your RenderDraw experience.&#x20;

#### Logical flow&#x20;

In order to plan out your use of RenderDraw, it would make sense to understand what components we have to offer. Follow this flow to understand which components and use cases you should focus on during your setup of RenderDraw.

<figure><img src="../.gitbook/assets/Plan your UseCase 2025.png" alt=""><figcaption></figcaption></figure>

#### General information for setup of RenderDraw

{% content-ref url="../diving-deeper/relationships/" %}
[relationships](../diving-deeper/relationships/)
{% endcontent-ref %}

{% content-ref url="../diving-deeper/renderdraw-architecture/supported-formats.md" %}
[supported-formats.md](../diving-deeper/renderdraw-architecture/supported-formats.md)
{% endcontent-ref %}

{% content-ref url="../diving-deeper/performance-considerations.md" %}
[performance-considerations.md](../diving-deeper/performance-considerations.md)
{% endcontent-ref %}

{% content-ref url="../diving-deeper/development-resources.md" %}
[development-resources.md](../diving-deeper/development-resources.md)
{% endcontent-ref %}

#### 3D Use Cases

{% content-ref url="../diving-deeper/renderdraw-architecture/supported-formats.md" %}
[supported-formats.md](../diving-deeper/renderdraw-architecture/supported-formats.md)
{% endcontent-ref %}

{% content-ref url="../usage-scenarios/use-cases/3d/admin/setup-3d-scene/visual-scene-setup/" %}
[visual-scene-setup](../usage-scenarios/use-cases/3d/admin/setup-3d-scene/visual-scene-setup/)
{% endcontent-ref %}

{% content-ref url="../usage-scenarios/use-cases/3d/admin/examples/product-visualization.md" %}
[product-visualization.md](../usage-scenarios/use-cases/3d/admin/examples/product-visualization.md)
{% endcontent-ref %}

{% content-ref url="cad-conversion/setup-of-cad-conversion.md" %}
[setup-of-cad-conversion.md](cad-conversion/setup-of-cad-conversion.md)
{% endcontent-ref %}

#### 2D Use Cases

{% content-ref url="../usage-scenarios/use-cases/2d/" %}
[2d](../usage-scenarios/use-cases/2d/)
{% endcontent-ref %}

{% content-ref url="../usage-scenarios/use-cases/2d/2d-admin-guide-clicks-not-code/" %}
[2d-admin-guide-clicks-not-code](../usage-scenarios/use-cases/2d/2d-admin-guide-clicks-not-code/)
{% endcontent-ref %}

### 3 - Configure and Setup

{% content-ref url="../usage-scenarios/use-cases/3d/admin/adding-components-to-your-lightning-pages.md" %}
[adding-components-to-your-lightning-pages.md](../usage-scenarios/use-cases/3d/admin/adding-components-to-your-lightning-pages.md)
{% endcontent-ref %}

{% content-ref url="../diving-deeper/relationships/why-metadata-matters/" %}
[why-metadata-matters](../diving-deeper/relationships/why-metadata-matters/)
{% endcontent-ref %}

### 4 - Replicate and Maintain&#x20;

Setup Metadata Relationships for your drawings

Copy your settings from one record to another by setting up relationships and fallbacks based on unique ids. Look at this migration guide and the Record Lookup component documentation for more information

<figure><img src="../.gitbook/assets/RenderDraw Architecture - Migration.png" alt=""><figcaption></figcaption></figure>

