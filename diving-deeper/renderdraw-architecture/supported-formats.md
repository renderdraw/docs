# Supported Formats

#### 3D Formats:

Unfortunately, modern browsers cannot natively render CAD files from leading software vendors. Fortunately, most CAD files can be converted to modern web standard WebGL 3D without much being lost in between. By default, we support the native formats listed below.

<table><thead><tr><th width="196.9568393840621">Native</th><th width="471.96138642524267">Conversion Supported</th></tr></thead><tbody><tr><td><p></p><ul><li>OBJ</li></ul><ul><li>STL</li></ul><ul><li>glTF</li></ul><ul><li>glb</li></ul></td><td><p></p><table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><ul><li>3D PDF</li><li>Collada</li><li>glTF</li><li>OBJ</li><li>STEP</li><li>USD</li><li>3DS</li><li>DXF</li><li>IGES</li><li>PLY</li><li>STL</li><li>VRML</li><li>3MF</li><li>FBX</li><li>JT</li><li>PRC</li><li>U3D</li><li>X3D</li><li>ACIS</li></ul></td><td><ul><li>Open CASCADE</li><li>Parasolid </li><li>Rhino </li><li>CATIA V5 </li><li>CATIA V6 (3D XML)</li><li>DWG</li><li>Inventor </li><li>PTC Creo </li><li>Siemens NX</li><li>Solid Edge </li><li>Solidworks</li><li>DXF</li><li>FBX</li><li>Solidworks</li><li>PTC Creo</li><li>Siemens NX</li><li>X3D</li><li>3MF</li><li>IFC</li></ul></td></tr></tbody></table></td></tr></tbody></table>

For the best experience possible, utilize professional drawing tools such as Solidworks or Siemens NX and give your components and subcomponents meaningful names within the drawings. &#x20;

**\*Batch auto conversion** or **CAD Conversion** utilizes an API to convert files and associated materials and textures to GLB format. This requires an additional subscription, or alternatively, you can utilize these methods to export to the native format:

* [Solidworks convert to glb](https://help.solidworks.com/2019/english/SolidWorks/sldworks/t_export_using_extended_reality.htm)
* [3DSMax conversion to GLTF](https://doc.babylonjs.com/resources/3dsmax)
* [AutoDesk Inventor export (paid but reasonable)](https://apps.autodesk.com/INVNTOR/en/Detail/Index?id=6155426903769565235\&appLang=en\&os=Win64)
* [AutoDesk Fusion Convert to OBJ or STL ](https://knowledge.autodesk.com/support/fusion-360/learn-explore/caas/sfdcarticles/sfdcarticles/How-to-export-a-design-in-Fusion-360.html)

Our CAD Conversion UI lets you convert files right inside Salesforce! Take a look at the use case here:

{% content-ref url="../../usage-scenarios/use-cases/cad-conversion/cad-conversion-using-admin-ui/cad-conversion-ui-within-salesforce.md" %}
[cad-conversion-ui-within-salesforce.md](../../usage-scenarios/use-cases/cad-conversion/cad-conversion-using-admin-ui/cad-conversion-ui-within-salesforce.md)
{% endcontent-ref %}

#### 2D

Our 2D components can use most image formats, including png, jpg and SVG&#x20;
