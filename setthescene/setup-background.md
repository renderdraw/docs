---
title: Setup Background
description: Setup your scene's background using either an image or a photodome
published: true
date: 2020-10-17T20:06:24.019Z
tags: background, scene
editor: markdown
dateCreated: 2020-10-16T20:14:57.711Z
---

# Setup a background
When looking At a product in real life things tend to not float in front of a solid color background. With that in mind we've decided to provide two different methods to give your seems a bit of dimension. The first is providing a static photo as a background, and the second is providing what we consider a photodome.

The simplistic breakdown of the two options are, do you want the background to move with the user's interaction? If so, you want a photodome, otherwise, a simple photo background is likely the more performant option that will still make your scene standout.

## Photo Background
The photo background is exactly what it sounds like a photograph to use his background instead of the static color that we provide. To provide a new photo for your background you must first host a photo somewhere that is probably accessible from your salesforce instance. This will be added to your scene by it's URL and one of our handy API methods, let's take a look.

Do you have a photo background first we need an instance of our advanced rendering component added to your custom component.
Using this image as a background:
https://files.renderdraw.us/public/images/demoassets/customer%20demos/clubcar/golfcourse1.jpg
<img src="https://files.renderdraw.us/public/images/demoassets/customer%20demos/clubcar/golfcourse1.jpg"/> we can provide a better user experience than a standard color for our 3D scene. 
Let's take a look at what it will take to add this to our 3D scene.

Starting from a custom component that wraps an instance of the [AdvancedRenderer](/components/AdvancedRenderer)  with an id of 'renderer'
```
<RDraw:AdvancedRenderer aura:id="renderer" displayContext="true"
                                 loadingImage="{!v.loadingImage}" displaySidebar="{!v.showSidebar}" spitShine="True"
                                 allowSelection="true" recordId="{!v.recordId}" size="Large">
               ...                                                   
</RDraw:AdvancedRenderer>
```
we can call the [updatebackgroundimage](/components/AdvancedRenderer#updatebackgroundimage)  method once the scene is loaded
```
   handleSetBackgroundImage: function (component, event, helper) {
        let renderer = component.find('renderer');
        let imageURL = "https://files.renderdraw.us/public/images/demoassets/customer%20demos/clubcar/golfcourse1.jpg";
        renderer.updateBackgroundImage(imageURL);
    }
```
we get the output of:
<video autoplay loop src="/bgphoto.mp4" />

To clear the background, we can call the same function with empty parameters to remove the background, which can be useful if you plan on swapping backgrounds during your user experience 

```
    handleClearBackgroundImage: function (component, event, helper) {
        let renderer = component.find('renderer');
        renderer.updateBackgroundImage(undefined);
    },
```
## PhotoDome
In order to use the PhotoDome, we need a source image that is "Equirectangular", without an equirectangular source the method won't function correctly. Effectively, this is the output from a 350º camera, or application that can take a 360º photo with a standard camera, such as the <a href="https://www.amazon.com/Ricoh-Theta-360-Spherical-Camera/dp/B074W5BKYS"> Ricoh Thera 360º camera</a>. As a general rule, the smaller the output of the image, the better the load time for the user experience. 

to add a photodome, you have to call the [addphotodome](/components/AdvancedRenderer#addphotodome)  method once the scene is loaded. The method 
takes four parameters:

| Name        | type        |  required   |  description|
| ----------- | ----------- | ----------- | ----------- |
| name        | Title       | true |The name of the component to add (For reference later)|
| photoURL    | Text        | true | The URL of the remote equirectangular image to use as the domes background |
| size        | Text        |false |The size of the photodome to add (defaults to 15)
 |
| limitCamera | boolean     |false | whether or not to limit the cameras radius to fit inside the dome |

for this example, we will use this 360º photo as a background:
<img src="https://files.renderdraw.us/public/images/demoassets/customer%20demos/clubcar/pexels-philippe-perruchot-4298805.jpg"/>
and after testing, it looks like a size of 12 is a perfect fit for our model. To test this, you can use the debug menu to dispose of added photodomes that don't really fit, but by default we set this to 15. 


**Let's add a photodome!**

Using the same instance of 'renderer' we used above, our controller function would look something like this:

```
    handleTestAddPhotoDome: function (component, event, helper) {
        let renderer = component.find('renderer');
        let domeName = 'testDome';
        let photoDomeURL = 'https://files.renderdraw.us/public/images/demoassets/customer%20demos/clubcar/pexels-philippe-perruchot-4298805.jpg';
        let photoDomeSize = 12;
        let limitCamera = true;
        renderer.addPhotoDome(domeName, photoDomeURL, photoDomeSize, limitCamera);
    },
```
And our output should look like this:
<video autoplay loop src="/photodome.mov" />

Notice the environment moving as the mouse moves? This is the big difference in experience.
## Performance considerations
As with most things dealing with computer graphics, the more intense the experience is in terms of complexities, the beefier the graphics card required. 

What is the average hardware your users will be using to access Salesforce? If this is standardized, go for it! otherwise, it may be wise (unless using more simplistic 3D drawings) to provide your users with a 2D image background or standard color for an improved interaction. 