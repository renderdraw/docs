# Example input for Conversion

When sending the request to our conversion server, ensure they match the following format:

```
curl --url https://api.renderdraw.us/CAD -h "x-api-key:YOUR_CONVERSION_API_KEY"  -F "files=@./test-files/TestArchive.zip" > test-result.zip
```

where the TestArchive.zip contains a CAD file of a supported format. This zip can also contain assemblies and their supporting component files, each file will be converted to the resulting format (GLB).   &#x20;

The API will return a compressed collection of the converted 3D file, the JSON structure of the CAD file, and a 2D Snapshot image of the 3D file.&#x20;

Calling this API is only supported with 3D files at this time.

{% hint style="info" %}
RenderDraw API conversion only accepts POST requests
{% endhint %}
