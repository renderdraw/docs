---
title: Scene Settings & Setup
description: 
published: true
date: 2020-10-21T00:27:22.635Z
tags: scenesetup
editor: markdown
dateCreated: 2020-10-21T00:27:22.635Z
---

# Header

```
{
    "version": 1,
    "lastSaved": "",
    "sceneName": "Visualization",
    "attributes": {},
    "actions": [{
        "name": "onSceneLoaded",
        "steps": []
    }],
    "text": []
}
```

```
{
  "version": 1,
  "lastSaved": "2020-10-14T20:08:51.893Z",
  "sceneName": "Visualization",
  "attributes": {
    "brandImageURL": "https://files.renderdraw.us/public/images/2020RDLogo.png",
    "spitShine": true
  },
  "actions": [
    {
      "name": "onSceneLoaded",
      "steps": [
        {
          "method": "setupGround",
          "parameters": {
            "imageURL": "https://files.renderdraw.us/public/images/demoassets/customer%20demos/clubcar/Grass_001_COLOR2.jpg",
            "heightMapURL": "https://files.renderdraw.us/public/images/demoassets/customer%20demos/clubcar/Grass_001_ROUGH.jpg",
            "width": "12",
            "height": "12",
            "maxheight": "0.105",
            "minheight": "0.05",
            "subdivisions": "1000"
          }
        },
        {
          "method": "addPhotoDome",
          "parameters": {
            "name": "defaultPhotoDome",
            "photoURL": "https://files.renderdraw.us/public/images/demoassets/customer%20demos/clubcar/pexels-philippe-perruchot-4298805.jpg",
            "size": "15",
            "limitCamera": true
          }
        }
      ]
    }
  ],
  "text": [
    {
      "label": "XRT Body",
      "componentName": "Golf_Car_XRT_Body"
    },
    {
      "label": "Replacable XRT Seat",
      "componentName": "Golf_Car_XRT_Seat"
    }
  ]
}
```