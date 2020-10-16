---
title: Setup Ground
description: 
published: true
date: 2020-10-16T15:22:45.120Z
tags: advancedrenderer, ground, scene
editor: markdown
dateCreated: 2020-10-16T13:08:47.498Z
---

# Setting up a ground
A ground is a nice way to provide some depth to your 3D scene by adding a foundation for your drawings to be displayed on. We construct grounds based on a plane (think of this like a rectangle) in three-dimensional space with an image texture provided for its look and feel. The size and image are provided by you, the developer or admin, and the interaction is rendered by RenderDraw. 

Some notes about grounds elements,
- Ground elements are not pickable by the user, they cannot be clicked
- Ground elements, when added, ensure your loaded elements are not displayed below the ground, meaning if an element is loaded at 1,-4, 1 that element's position will be fixed by moving it above 0 on the y-axis, calculated by multiplying -1 * the lowest negative y point in three dimensions
- Ground elements are always loaded at the point of origin, 0,0,0 and their dimensions are based on the width and height paramenter you pass in. 
## Base Ground
To setup a base ground element, you'll need an imageURL, and the size of the ground you are going to uss. Remember, the image you will be loading in will be downloaded every time a user visits your scene, with that in mind, we'd reccomend keeping the image as small as possible. Take a look at our example grass image we use here (1000x1000):
<img src="https://files.renderdraw.us/public/images/demoassets/customer%20demos/clubcar/Grass_001_COLOR2.jpg" />

##### Let's add this to our default scene at a size of 12 x 12
Your Aura Componnt will wrap our AdvancedRenderer an element with an id of 'renderer' soo we can reference it later.
> <RDraw:AdvancedRenderer aura:id="renderer" displayContext="true"
>                                 loadingImage="{!v.loadingImage}" displaySidebar="{!v.showSidebar}" spitShine="True"
>                                 allowSelection="true" recordId="{!v.recordId}" size="Large">
>               ...                  
>                                 
></RDraw:AdvancedRenderer>

We can bind to the [EVT_Renderer_Loaded](/events/EVT_Renderer_Loaded) event to set this up on load, or we can use a button that fires the function to add the ground to the scene. Either way, ensure the renderer has loaded prior to calling the method, otherwise nothing will occur. 

From our controller method:
>  handleTestAddGround: function (component, event, helper) {
> 
> 	 let renderer = component.find('renderer');
> 	 renderer.setupGround(
> 'https://files.renderdraw.us/public/images/demoassets/customer%20demos/clubcar/Grass_001_COLOR2.jpg', undefined, 12, 12,
>             undefined, undefined, 1000
>         );
> }


and the result should look something like this:
![groundwith_golfcartflatgrass.png](/groundwith_golfcartflatgrass.png)
with flat grass. 

> Sampling is how many times an the image is repeated over the space of the ground.  
{.is-info}

## Advanced Ground with Heightmap
> Performance consideration:
More edges in 3D space requires more performance from your computer's graphics card. Consider your average user when deciding how tall your heightmaps are rendered using the setupGround method.
{.is-warning}
