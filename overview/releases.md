---
title: Release Notes
description: 
published: true
date: 2020-11-07T11:00:11.461Z
tags: releasenotes, releases
editor: markdown
dateCreated: 2020-11-07T10:17:06.074Z
---

# Releases

>  **1.9.1**
Released Nov. 5th 2020 
{.is-info}


#### New Features
- Promise management, and Promises returned and resolved for: 
	- addPhotoDome
  - add2DText
  - add2DImage
  - addVideoPlayer
  - add3DText
  - addModelToScene
  - addLight
- Added Get Camera Position to ActionMenu
- Added ability to dynamically add lights 
- Point, spot, directional, and hemispheric along with colors and intensity.

#### New APIs:
- addLight
- updateLight
- highlightComponent
- clearAllHighlights


#### Enhancements and Bugfixes

- Fixed Layout bug in AdvancedRenderer component with the sometimes lack of display of sidebar
- Fixed issue with generated background-plane being selectable
- Added Scene optimization for weaker hardware
- Started the explosions from the largest element (area-wise) for single Drawing/component scenes
- Updated algorithm for camera position finding the element to focus on 
- Fixed getCameraPosition to return the appropriate decimal values observed in scene debugger
- Updated getHierarchy to return all elements in the scene, not just the base loaded element
- Fixed issue while attempting to position the camera and setting the alpha and beta setting. These now accept decimal values
- Update remove element to deselect the elements in the scene and also remove any attached GUI behavior (2d attached text) 
- Fixed rotation issue on loading additional components
- Corrected rotation on import of additional components (decimal input now works appropriately)
- Fixed the height of any imported model based on the ground height (y axis)
- Improved loading and applying a texture to now work with 3D photo domes (swapping background images)
- Improved spacing distance for added 2D text to be relatively closer to the cursor
- Increased photodome resolution without degradation
- Improved default 2D text action, autohiding text after highlighting and fixing a bug when scene context was lost but 2D text was displayed 
---

>  **1.9**
Released October. 21st 2020 
{.is-info}

### This release includes 
1 new component,
7 new events raised
14 different APIs added 
And a boatload of bug fixes and improvements to existing functionality. 

Here are some highlights of the new functionality:
For those unfamiliar all of our components of an active APIs if you can hear a few examples of the new APIs added to our components which you can do a custom apps on top of:
### Added API elements

- 	add2DImage
		Specify an 2D image, its size and add that image, floating, in 3D space 
- 	add2DText
		Adding text to a 3D scene and relating it to a given component within a 3D model- this can also be displayed only if a user is hovering over a specific component within a 3D model. 
- 	add3DTextToScene
		Display floating 3D text anywhere within your 3D scene
- 	addModelToScene
		With 1.9, you are no longer limited to a single 3-D model in a given scene, the ability to asynchronously add additional 3-D models as you see fit anywhere within your 3-D scene
- 	addPhotoDome
		Have a degree camera or access to photos from a 360° camera? Now can build a universe inside of your salesforce scene based off of a photo I follow that provides a interactive background that moves as you move around with the camera and three dimensional space.
- 	addVideoPlayer
		Add a floating Video player that is activated on click to display additional information as it relates to 
-    Add texture to model
		Instead of just swapping out colors for individual components inside of a 3-D element you now can dynamically load textures right onto your 3-D components. This is extremely useful for configuration
- 	setupGround
		In reality we take ground in gravity for granted, with 101.9 we have the ability to add a ground base that ground off of a height man so instead of just a flat image we can actually add dynamic grounds to our scene based off of real life textures, like grass, concrete, sand or anything else
- 	updateBackgroundImage
		Want to add a better background to your 3-D scene but don't have a 360° camera you can utilize any to the image as a background for your 3-D scene now with this with this functionality
- 	removeComponent
		Given we now have the ability to dynamically add additional components to the 3-D saying we obviously need the ability to remove components for the 3-D see it is extremely useful for configuration and other dynamics scenes that are based off of data within salesforce.

Additionally we have added the ability for what we're calling the playground. This basically means a scene without a base 3D model. This is extremely useful if you're not mapping every 3D scene to a given model in a 1-1 fashion. We realize not every 3-D interaction is going to start with a model and we have provided the functionality to setup a scene as a blank slate. This is also extremely important for what wee have planned for the product moving forward, so this is setting the foundation for future releases, which you should be excited about .

### Events raised:
If you're unfamiliar, renderdraw processes a lot of events during 3-D scene interaction and set up we were always raising events that you can subscribe to, but now we've added several additional events that allow for full customization of your 3d  environment based off of what's happening within during the render cycle and during user interaction. Here are a few examples of new events added 
- OnPhototaken: 
this is an event raised whenever a photo or snapshot a statement we will pass you the data of payload of the screenshot taken of the 3-D scene for processing on your side.
- Element Added to the scene:
Positional information along with unique identifier IDs extremely useful if you wanna modify seen at any time this was extremely useful for the 3-D configuration.

### Bug Fixes & Improvements:
- Loading of some models was happening backwards, corrected for all imported 3D models
- Decreased load time for many 3D models
- Scene settings for repeated scalability 
- Setting of a Parent Scene configuration, which we will break down in another release
- Quality of snapshots taken has increased 2x
- We are now adding an anti-aliasing post process that makes every scene sharper. 
- Further improving the spit shine feature 

>  1.7
 August 16th 2020
{.is-info}

---
> 1.6
 August 5th 2020
{.is-info}

---
> 1.5
 June 24th 2020 
{.is-info}


---
> 1.4
June 1st 2020
{.is-info}

--- 
> 1.3
> Jan. 7th 2020
{.is-info}

For our 1.3 release, we started with our stated goal for our app to allow 3D interactions "Anywhere in Salesforce". With this broadening of usage, our users get to utilize our app in any way they can conceive. A truly flexible approach, anywhere within Salesforce. Also, explosions.

#### New Components
**FileSelector**
FileSelector was created to allow the interaction with 3D files that exist within Salesforce Files. By passing in a recordId (through a Salesforce Flow or by placing on the Lightning Record Page), we fetch the latest versions of Attachments, and display the relevant 3D files as a list.

When Selecting, a 3D interaction pop-up displays and the drawing is loaded directly from Salesforce. There are no file limitation sizes to these files, and this component can be used dynamically in a Flow.  

#### Exceptional Features
**Explosions!**
Explode meshes with ease. Select "Show Explosion Bar" from the ActionMenu, and use the slider to explode your drawings to gain more perspective on your products / materials

**Screen Shots**
After you pan, zoom and explode you can take a screenshot of the rendering to include in your Sales or Service scenario.  

**ActionMenu**
Go beyond standard rendering by clicking the gear in your rendering, Actions include Debug, Take Screenshot and Explode

**Scene Debugging**
Break Down the complexities of a 3D scene with ease- Explore layers, lighting and effects applied to your drawings

**Communities Usage**
Ability to utilize a Communities URL structure for Partner or Customer Community. This is set within the Lightning component configuration by a checkbox

**Use Salesforce Files for Renderings** 
Pass a ContentVersion to the Renderer in order to fetch and render a 3D file hosted by Salesforce

**User Interaction indication**
Know when your users have actually reviewed your drawings, and utilize them. A flag (hasUserInteracted) is set once a user interacts with the 3D scene.

---

> **1.2** 
September 3rd 2019
{.is-info}


This version added:
* Internationalization
    * Translations have been added for every language that Salesforce supports 
* Custom development support
    * Simple render component can now be used in custom development scenarios beyond record pages. Add RenderDraw functionality to your lightning component/page
 
This version fixed:
* Loading additional resources 
    * The loading of any resources defined within your 3D renderings are now auto fetched based on relative urls
* Removal of an unused field on the product object 


