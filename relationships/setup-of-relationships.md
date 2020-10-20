---
title: Setup of Relationships between Salesforce Objects and 3D files
description: 
published: true
date: 2020-10-20T10:54:24.509Z
tags: relationships, metadata
editor: markdown
dateCreated: 2020-09-21T19:00:18.444Z
---


Prior to starting, let's ensure we understand a couple of topics:
- [What is a RenderDraw Relationship](/relationships/what-is-a-relationship)
- [Why use Relationships](/relationships/why-relationships)

If comfortable of why you'd want a relationship-based schema setup, let's create a relationship 
# Create a Relationship
Think of a RenderDraw relationship like a formula. This formula determines, by object, how we are going to fetch your 3D files and related resources for a given Salesforce Object record. At the end of the day, we are looking for a file in a remote destination, from the example above, we can break down the URL into its composite parts.


![filepathbreakdown.png](/filepathbreakdown.png)

Based on a set of fields mapped with the relationship objects, we can compose a URL for every product record that exists for any company. The relationships are maintained alongside the data in Salesforce, so as the records in the Salesforce org gradually grow in number, the most up-to-date drawing is updated on each record by convention, ensuring a scalable experience for every record of that type.    

![filepathbreakdown_relationship_example.png](/filepathbreakdown_relationship_example.png)

Lets prove this by adding a 3D interaction onto multiple record types Lightning pages. Then we'll update the filename reference and display the results on all references.  

## Add 3D Drawing Field to objects
Our primary purpose for this exercise is to visualize products, so we will start there. Lets add a text field named "3D Drawing" to the Product object. 

![productmetadatacreate.png](/productmetadatacreate.png)

Since all of our intended visualizations are going to be product-focused, it makes sense to create a controlling field on the product object that will be referenced from our other intended visualization targets
- Opportunity Product
- Asset
- Product
### The power of Salesforce lookups 
Creating fields in each individual linked object is a good way to reduce maintenance, so long as the same drawing will be used in each use case. 
Lets add a lookup to this field we just created on the product record to the Opportunity Product Object

Start by adding a custom field to our object. It will be a Formula
![order_productcustomfield.png](/order_productcustomfield.png)
Our return type will be text, remember we are attempting to build a URL
![order_productcustomfield2.png](/order_productcustomfield2.png)
For the formula value, locate the Product relationship and the 3D Drawing field that we created as the return value. This was done in the advanced formula field
![order_productcustomfield3.png](/order_productcustomfield3.png)
![orderproductrelationship_create.png](/orderproductrelationship_create.png)

Now follow the same process for the Asset object type as well as any other related object you might want to display 3D drawings on.

 
```plantuml
@startuml
skinparam backgroundColor White
skinparam state {

  BackgroundColor LightBlue
  BackgroundColor<<Warning>> LightYellow
  BorderColor Gray
  FontName Impact
}
skinparam arrow{
	color white
}

hide empty description
State Product as "Product"
State OLI as "Opportunity Item"
State QLI as "Quote Item"
State OI as "Order Item"
State Asset as "Asset"


OLI --> Product
QLI --> Product
Asset --> Product
OI --> Product
@enduml
  
```

## Create a RenderDraw Setting
Lets jump in and create the needed relationships so we can link those fields we created to the Lightning components on each page. 
### Setup
> Go to setup by clicking the gear in the top right of the screen. Click Setup, and go to the search on the far left of the screen. Type in Metadata
{.is-info}

### Search for Metadata
![custommetadata_types_search.png](/custommetadata_types_search.png)
> From there, we are creating a RenderDraw Setting, so lets select manage records for that type 
{.is-info}

![custom_metadata_typesrenderdrawsettings.png](/custom_metadata_typesrenderdrawsettings.png)
### Manage the relationships 
>  We can either manage any current setting, or create a new one. Lets create a new setting for the file server we saw above. Note we selected defaults for control and light settings, and provided the label **File Server** and the Base URL **https://files.renderdraw.us/** which was common among all of the files we looked at earlier.
{.is-info}

![createsettings.png](/createsettings.png)


## Create the relationship
>  Now that our RenderDraw Settings are created, we have the first part of the formula (URL Position 1) of the needed information to fetch a 3D file complete with the Base URL.
{.is-info}

![basesettingdetails.png](/basesettingdetails.png)

Lets work on creating URL Position 2. 
Start by Searching again for metadata relationships, and selecting “Manage Relationships” on the RenderDraw Relationship type
![custom_metadata_typesrenderdrawrelationshipsettings.png](/custom_metadata_typesrenderdrawrelationshipsettings.png)
We can create the Product Relationship with the following values: 

- Entity: Product (The object we will be looking up values on, e.g. where to render)
- Label: Something notable for when we have 20+ relationships later, typically this will have the object type in the Name.
- Rendering File: What field on the Object will have the File within the URL (e.g. URL Part 3)
- RenderDraw Setting: The reference to the Setting record we created last step (Think how are we going to create the full URL for the Product Record)
- For this record and how we have our renderings setup on this server, we are going to use the rendering path override 

> The rendering path is not required to successfully call out to other servers. In simpler setups, this can be ignored. For this example, we are using the **Relative Rendering Path Override** value of "renderings/public/" because that never changes between all of our files and likely never will. If we had several subfolders, we could add the value of those subfolders into another field on the related object and look that up by setting the **Rendering Relative Path** field on this setup.
{.is-info}

  ![productrelationship_create1.png](/productrelationship_create1.png)\

Save that relationship and follow the process for your additional related objects. 

## Render from your Relationship
### Add the product record
Ensure you have the last portion of your URL written down and add your product record. Note the last portion of our URL (URL Position 3) is what is populating the 3D Drawing field. This is what will change per each record of this type.
![club_car_xrt_850_x___salesforce.png](/club_car_xrt_850_x___salesforce.png)
### Add the Lightning Component
Add a component to the record detail screen and save it using the Lightning App Builder
![product_record_page_-_lightning_app_builder.png](/product_record_page_-_lightning_app_builder.png)

An in-depth view of this process can be seen [here](/getstarted/relationships/setup-of-relationships)

follow this for each of the additional record types you choose to render on. Each will appear exactly the same as
### View 
Our 3D Drawing can now be seen on every related page we added it to. This drawing should look something similar to this:

![large_robotics_sale_club_car_xrt_850_x___salesforce.png](/large_robotics_sale_club_car_xrt_850_x___salesforce.png)
# Relationship Strategies
Using the right tool for the job is of the utmost importance to scale your 3D interactions.   

## What are you visualizing?
If you are planning to render a single product or scene for your entire org, you likely do not need a relationship strategy or a relationship at all. Relationships are for scaling 3D over the size of a particular object type. 

Most frequently, you will likely be visualizing products in either sales or service scenarios. This will happen at scale- there might be some time when you only have drawings for a subset of your actual products, and thats okay. 

> Pro-tip: if you are rendering 5 or more diffent drawings that are represented by the same object in Salesforce, setup a relationship. If not, A Lightning flow and direct URLs would suffice  
{.is-success}


## Where are you going to want to render?
Our default strategy when setting up product-related 3D to scale is based on the Product Object as we did above.

With this in mind, we can potentially further re-utilize data to ensure when a new rendering path is available, we have a single source of truth for that product.

Think of your objects relationally. Where are you going to put the Lightning Component? 

```plantuml
@startuml
skinparam backgroundColor White
skinparam state {

  BackgroundColor LightBlue
  BackgroundColor<<Warning>> LightYellow
  BorderColor Gray
  FontName Impact
}
skinparam arrow{
	color white
}

hide empty description
State Product as "Product"
State OLI as "Opportunity Item"
State QLI as "Quote Item"
State OI as "Order Item"
State Asset as "Asset"


OLI --> Product
QLI --> Product
Asset --> Product
OI --> Product
@enduml
  
```
Could it be used elsewhere? This is important to consider because most frequently, this reference will be created and setup by an integration tool or an APEX script. 












