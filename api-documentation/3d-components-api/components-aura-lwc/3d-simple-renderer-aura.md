# 3D Simple Renderer (Aura)

SimpleRenderer is our first component made strictly for natively rendering a 3D drawing file within Salesforce. Once loaded, the drawing takes center stage while allowing for users to interact by mouse.

Use the SimpleRenderer wherever you would use a product or component image. SimpleRenderer has no supported global methods, Although the SimpleRenderer is a global component, you likely want to develop with our AdvancedRenderer.

SimpleRenderer requires one of the following attributes in order to render a drawing on the screen:

| **NAME**                  | **TYPE** | **DEFAULT** | **DESCRIPTION**                                                                                                                                                                                             |
| ------------------------- | -------- | ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <h3>brandImageURL</h3>    | string   |             | URL for brand image to be displayed in the bottom right of the rendering canvas. This will be displayed at a width of 120px                                                                                 |
| <h3>contentVersionId</h3> | string   |             | Id of the Salesforce Content Version where the binary rendering is stored                                                                                                                                   |
| <h3>environmentColor</h3> | string   | #e1f5fc     | Hex code for the background color of the 3D scene in #xxxxxx format (including #)                                                                                                                           |
| <h3>overrideURL</h3>      | string   |             | URL where your drawing can be fetched (ignores underlying relationships)                                                                                                                                    |
| <h3>recordId</h3>         | string   |             | <p><a href="https://ability-ruby-6013-dev-ed.lightning.force.com/docs/component-library/bundle/force:hasRecordId">Inherited from force:hasRecordId</a><br>The record Id</p>                                 |
| <h3>showActionMenu</h3>   | boolean  | TRUE        | Display the action menu to users, allowing for screenshots, changing of scene elements and more                                                                                                             |
| <h3>showUserMessages</h3> | boolean  | FALSE       | Display messages during the rendering loop to the user. These display in the bottom left corner of the component and automatically disappear as new messages are displayed, or after 2 seconds has passed   |
| <h3>size</h3>             | string   | Medium      | The size of the component on the page                                                                                                                                                                       |
| <h3>useCommunities</h3>   | boolean  |             | If you are using the SimpleRenderer within a Community, this is required to fetch resources based on the current community url path                                                                         |
| <h3>userInteracted</h3>   | boolean  | FALSE       | Is set to true when a user drags, points, scrolls or clicks on the rendering                                                                                                                                |
| <h3>showUserMessages</h3> | boolean  | FALSE       | `Display messages during the rendering loop to the user. These display in the bottom left corner of the component and automatically disappear as new messages are displayed, or after 2 seconds has passed` |
| <h3>size</h3>             | string   | Medium      | `The size of the component on the page`                                                                                                                                                                     |
| <h3>useCommunities</h3>   | boolean  |             | `If you are using the SimpleRenderer within a Community, this is required to fetch resources based on the current community url path`                                                                       |
| <h3>userInteracted</h3>   | boolean  | FALSE       | `Is set to true when a user drags, points, scrolls or clicks on the rendering`                                                                                                                              |
