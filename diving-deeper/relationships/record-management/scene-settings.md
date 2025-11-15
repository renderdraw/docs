# Scene Settings

Scene Settings are the data description of the 3D scene as your users will see it. If you setup a custom component and call our component APIs to create a 3D experience, you are manually describing the scene through attributes, and a series of API calls based on events.

How does this scale?

Spoiler alert: it doesn't.

A custom component will most often describe a single scene, unless there is a custom data definition defined, in which case- godspeed\
For the majority of use cases, we will have more than one subject we should be

As of app version 1.8, we create Scene settings version 1.0. This can be added to your object by first creating a **Scene Settings** lookup on your Relationship. This settings data is structured like this:

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

Breaking this down a bit further, the version, lastSaved and sceneName are all internal, so setting those up is not needed by you.

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
      "label": "Replaceable XRT Seat",
      "componentName": "Golf_Car_XRT_Seat"
    }
  ]
}
```

## Parent Scene Settings

More often than not, you won't be utilizing a single object for all of your 3D scenes. Most frequently, we start with product visualization, using the Product2 object. From there, there are dozens of objects in the Salesforce world that represent instances of a given product, such as Assets, Opportunity Products, Quote Lines, and many more.

But setting up a scene for every Opportunity, Asset, or QuoteLine that uses your product and scene configuration would require an elaborate trigger system that no architect would approve, and no admin would want to maintain.

We cant use a formula field, as text lookups cannot use the required Long text / text area data type- the solution? A new metadata field that allows us to utilize lookup relationships between the data objects, and determine the metadata record that contains the Scene Setup information.

Sounds complex? It really isn't. Simply set up a Scene Settings field on your base object relationship, as we did in the steps above (In this case the Product relationship), and set up a child relationship object for a given object. For this example, we'll use Assets, as pretty much every Salesforce org has this object. For this relationship, we now have to populate
