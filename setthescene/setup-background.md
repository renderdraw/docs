---
title: Setup Background
description: Setup your scene's background using either an image or a photodome
published: true
date: 2020-10-17T16:24:48.548Z
tags: background, scene
editor: markdown
dateCreated: 2020-10-16T20:14:57.711Z
---

# Setup a background
When looking At a product in real life things tend to not float in front of a solid color background. With that in mind we've decided to provide two different methods to give your seems a bit of dimension. The first is providing a static photo as a background, and the second is providing What we consider a photo dome.

## Photo Background
The photo background is exactly what it sounds like a photograph to use his background instead of the static color that we provide. To provide a new photo for your background you must first host a photo somewhere that is probably accessible from your salesforce instance. This will be added to your scene by it's URL and one of our handy API methods, lets take a look.

Do you have a photo background first we need an instance of our advanced rendering component added to your custom component.

https://files.renderdraw.us/public/images/demoassets/customer%20demos/clubcar/golfcourse1.jpg

in action:
<video autoplay loop src="/bgphoto.mp4" />
## PhotoDome
In order to use the PhotoDome, we need a source image that is "Equirectangular", without an equirectangular source the method won't function correctly. Effectively, this is the output from a 350º camera, or application that can take a 360º photo with a standard camera, such as the <a href="https://www.amazon.com/Ricoh-Theta-360-Spherical-Camera/dp/B074W5BKYS"> Ricoh Thera 360º camera</a>. As a general rule, the smaller the output of the image, the better the load time for the user experience. 

to add a photodome, you have to call the 


Example of equirectangular image:
<video autoplay loop src="/photodome.mov" />

## Performance considerations
As with most things dealing with computer graphics, the more intense the experience is in terms of complexities 