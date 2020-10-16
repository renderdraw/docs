---
title: Setup Ground
description: 
published: true
date: 2020-10-16T19:47:48.153Z
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
- Ground elements will move with the scene when interacting
## Base Ground
To setup a base ground element, you'll need an imageURL, and the size of the ground you are going to uss. Remember, the image you will be loading in will be downloaded every time a user visits your scene, with that in mind, we'd reccomend keeping the image as small as possible. Take a look at our example grass image we use here (1000x1000):
<img src="https://files.renderdraw.us/public/images/demoassets/customer%20demos/clubcar/Grass_001_COLOR2.jpg" />

##### Let's add this to our default scene at a size of 12 x 12
Your Aura Component will wrap our AdvancedRenderer componoent with an id of 'renderer' so we can reference it later.
```
<RDraw:AdvancedRenderer aura:id="renderer" displayContext="true"
                                 loadingImage="{!v.loadingImage}" displaySidebar="{!v.showSidebar}" spitShine="True"
                                 allowSelection="true" recordId="{!v.recordId}" size="Large">
               ...                                                   
</RDraw:AdvancedRenderer>
```

We can bind to the [EVT_Renderer_Loaded](/events/EVT_Renderer_Loaded) event to set this up on load, or we can use a button that fires the function to add the ground to the scene. Either way, ensure the renderer has loaded prior to calling the method, otherwise nothing will occur. 

From our controller method:
```
  handleTestAddGround: function (component, event, helper) {
  let renderer = component.find('renderer');
  renderer.setupGround('https://files.renderdraw.us/public/images/demoassets/customer%20demos/clubcar/Grass_001_COLOR2.jpg', undefined, 12, 12,
             undefined, undefined, 1000
         );
 }
```

and the result should look something like this:
![groundwith_golfcartflatgrass.png](/groundwith_golfcartflatgrass.png)
with the image displayed as a flat texturem, in this case grass. 

> Sampling is how many times an the image is repeated over the space of the ground.  
{.is-info}

## Advanced Ground with Heightmap

What happens when we want to provide a better experience than a flat image? When is the last time you have seen a completely flat texture on the ground? Even the best concrete has subtle waves, so we have to be able to accomodate that.

Enter, heightmaps. 

From the <a href="https://en.wikipedia.org/wiki/Heightmap">Wikipedia entry:</a>
> In computer graphics, a heightmap or heightfield is a raster image used mainly as Discrete Global Grid in secondary elevation modeling. Each pixel store values, such as surface elevation data, for display in 3D computer graphics. A heightmap can be used in bump mapping to calculate where this 3D data would create shadow in a material, in displacement mapping to displace the actual geometric position of points over the textured surface, or for terrain where the heightmap is converted into a 3D mesh.

in laymens terms, this just means we will use an image to determine where our grass should be tall versus where it should remain flat. The heightmap image we will be using for this example looks like this: 
<img src="https://files.renderdraw.us/public/images/demoassets/customer%20demos/clubcar/Grass_001_ROUGH.jpg" />
The heightmap is black and white representation of where our image should be tall or short based on how dark or light that pixel is, relative to the texture we are rendering over it. 

Now our same function can be invoked, using the height map's URL and a few additional parameters for height. 

From our (updated) controller method:
```
  handleTestAddGround: function (component, event, helper) {
  let renderer = component.find('renderer');
  renderer.setupGround('https://files.renderdraw.us/public/images/demoassets/customer%20demos/clubcar/Grass_001_COLOR2.jpg', 'https://files.renderdraw.us/public/images/demoassets/customer%20demos/clubcar/Grass_001_ROUGH.jpg', 12, 12,
             0.105, 0.05, 1000
         );
 }
```
we can now see some grass that looks more realistic:
![groundwith_golfcartmediumgrass.png](/groundwith_golfcartmediumgrass.png)

Notice the edges? No longer a straight rectangle, but a subtle grass that proovides depth to our rendering. To fine tune this, we can modify our **maxheight** & **minheight** parameters, let's try it to provide even more depth
```
  handleTestAddGround: function (component, event, helper) {
  let renderer = component.find('renderer');
  renderer.setupGround('https://files.renderdraw.us/public/images/demoassets/customer%20demos/clubcar/Grass_001_COLOR2.jpg', 'https://files.renderdraw.us/public/images/demoassets/customer%20demos/clubcar/Grass_001_ROUGH.jpg', 12, 12,
             0.45, 0.095, 1000
         );
 }
```
![groundwith_golfcarttallgrass.png](/groundwith_golfcarttallgrass.png)
Ah, more depth- but notice how un-natural it looks? Based on how tall your heightmap parameters, you might want to modify your **samplesize** parameter so it looks more realistic

```
  handleTestAddGround: function (component, event, helper) {
  let renderer = component.find('renderer');
  renderer.setupGround('https://files.renderdraw.us/public/images/demoassets/customer%20demos/clubcar/Grass_001_COLOR2.jpg', 'https://files.renderdraw.us/public/images/demoassets/customer%20demos/clubcar/Grass_001_ROUGH.jpg', 12, 12,
             0.45, 0.095, 2500
         );
 }
```
a samplesize of 2500 provides a much more realistic grass for our scene
![rd-snapshot_(9).png](/rd-snapshot_(9).png)
> Performance consideration:
More edges in 3D space requires more performance from your computer's graphics card. Consider your average user when deciding how tall your heightmaps are rendered using the setupGround method.
{.is-warning}

Providing a ground element is a great start to creating a better experience for our users. Like many things, there are some compromises that have to be made, and that is up to you, the developer/ admin to find the happy medium for your clients and users.

We provide the tools to build the experience, but the experience is yours to create. 

