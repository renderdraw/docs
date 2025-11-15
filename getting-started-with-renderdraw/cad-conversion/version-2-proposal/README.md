# Version 2 (proposal)

<figure><img src="../../../.gitbook/assets/image (27).png" alt="" width="127"><figcaption></figcaption></figure>

{% hint style="info" %}
RenderDraw API conversion only accepts POST requests
{% endhint %}

### Request

This API will primarily convert input CAD files into a specified output format with various options for customization and data extraction.

#### API Overview

**Purpose:** Convert CAD files to different formats with options for screenshots, assembly modes, compression, and additional data extraction.

#### Input Parameters

1. **CADFile** (`binary` or `Zip`): The input CAD file. Accepts either a binary CAD file or a Zip file containing a CAD assembly with its parts or subassemblies.
2. **DimensionType** (`string`): Indicates whether the CAD file is 3D or 2D. Accepted values: "3D", "2D".
3. **OutputFileType** (`string`): The desired output file type. Typically a GLB file. Other formats can be specified as needed.
4. **TakeScreenshot** (`boolean`): Specifies whether to take a 2D screenshot of the CAD model. Default is `false`.
5. **AssemblyMode** (`string`): Determines the level of detail in the assembly conversion. Options are:
   * "full": Includes all components.
   * "subassembliesOnly": Includes only subassemblies.
   * "unimodel": Consolidates into a single top-level model.
6. **CompressionLevel** (`integer`): Sets the compression level for the output 3D model. Range is 0-10, with 7 as default.
7. **OutputModel** (`boolean`): Whether to output the converted 3D CAD model. Default is `true`.
8. **OutputAssemblyInformation** (`boolean`): If `true`, outputs the JSON structure of the CAD model, including Product Manufacturing Information (PMI). Default is `true`.

#### Sample API Calls

**Call 1: Basic Conversion**

```json
{
  "CADFile": "[Binary CAD File]",
  "DimensionType": "3D",
  "OutputFileType": "GLB",
  "TakeScreenshot": false,
  "AssemblyMode": "full",
  "CompressionLevel": 7,
  "OutputModel": true,
  "OutputAssemblyInformation": true
}
```

**Response 1:**

```json
{
  "status": "success",
  "convertedFile": "[URL to GLB File]",
  "assemblyInformation": "[JSON Structure]",
  "screenshot": null
}
```

**Call 2: Subassembly with Screenshot**

```json
{
  "CADFile": "[Zip File with Subassemblies]",
  "DimensionType": "3D",
  "OutputFileType": "GLB",
  "TakeScreenshot": true,
  "AssemblyMode": "subassembliesOnly",
  "CompressionLevel": 5,
  "OutputModel": true,
  "OutputAssemblyInformation": false
}
```

**Response 2:**

```json
{
  "status": "success",
  "convertedFile": "[URL to GLB File]",
  "assemblyInformation": null,
  "screenshot": "[URL to Screenshot Image]"
}
```

#### Additional Notes

* The API should handle various CAD file formats and be robust enough to process complex assemblies.
* Error handling must be implemented, especially for unsupported file formats, corrupted files, or conversion errors.
* Performance optimization is crucial, especially for large and complex CAD files.
* Security considerations should include secure handling and storage of the input CAD files.
* Consider providing a progress endpoint for monitoring the status of long-running conversions.
* Documentation should be clear, comprehensive, and include examples for various use cases.
* Optional features could include batch processing, additional output formats, and advanced compression options.

This structure provides a comprehensive foundation for the v2 CAD Conversion API, catering to a range of needs from basic file conversions to complex assembly processing with additional data extraction capabilities.

### Response&#x20;

This approach ensures that the response is easily consumable by JavaScript applications. Here's the structure:

#### Sample Response for Web API Service

**Response Format:**

```json
{
  "status": "success",
  "convertedFile": {
    "type": "GLB",
    "content": "[Base64 Encoded GLB File Data]",
    "fileName": "model.glb"
  },
  "assemblyInformation": {
    "content": "[Serialized JSON Object with Assembly Information]"
  },
  "screenshot": {
    "type": "Image",
    "content": "[Base64 Encoded Image Data]", // Only if TakeScreenshot is true
    "fileName": "screenshot.png"
  }
}
```

#### Explanation:

1. **Status**: Indicates the success or failure of the API call.
2. **ConvertedFile**:
   * **Type**: Specifies the file type, GLB in this case.
   * **Content**: The GLB file data encoded in Base64 format, which JavaScript can easily decode.
   * **FileName**: Suggested name for the file when saved or processed by the client.
3. **AssemblyInformation**:
   * **Content**: The assembly information provided as a serialized JSON object. This format is native to JavaScript and can be easily parsed and manipulated.
4. **Screenshot** (Optional):
   * **Type**: Specifies the image format.
   * **Content**: The image data encoded in Base64, provided only if `TakeScreenshot` is set to true.
   * **FileName**: Suggested name for the screenshot file.

#### Considerations:

* **Serialization**: All components of the response are serialized, allowing for easy parsing and processing in JavaScript.
* **Base64 Encoding**: While Base64 increases data size, it's a standard method for embedding binary data in JSON responses. JavaScript can handle Base64 encoding/decoding efficiently.
* **File Names**: Including suggested file names can help clients manage downloaded data.
* **Error Handling**: The API should include robust error handling and return meaningful error messages in a similar JSON structure.
* **Documentation**: Detailed documentation should accompany the API, explaining the response structure and providing examples of how to handle the data in JavaScript.

This approach aligns with the requirements of a web API service, ensuring that all data is returned in a format that can be serialized and utilized effectively in JavaScript-based applications.



