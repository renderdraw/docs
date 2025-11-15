# Sample File Input Conversion

#### HTML with Additional Pickers

```html
<form id="cadUploadForm">
    <input type="file" id="cadFilePicker" accept=".cad,.zip" />
    <br/>

    <label for="dimensionType">Dimension Type:</label>
    <select id="dimensionType">
        <option value="3D">3D</option>
        <option value="2D">2D</option>
    </select>
    <br/>

    <label for="outputFileType">Output File Type:</label>
    <select id="outputFileType">
        <option value="GLB">GLB</option>
        <!-- Add other file types as needed -->
    </select>
    <br/>

    <label for="takeScreenshot">Take Screenshot:</label>
    <input type="checkbox" id="takeScreenshot">
    <br/>

    <label for="assemblyMode">Assembly Mode:</label>
    <select id="assemblyMode">
        <option value="full">Full</option>
        <option value="subassembliesOnly">Subassemblies Only</option>
        <option value="unimodel">UniModel</option>
    </select>
    <br/>

    <button type="submit">Upload</button>
</form>
```

#### Updated JavaScript with Fetch Request

```javascript
document.getElementById('cadUploadForm').addEventListener('submit', function(event) {
    event.preventDefault(); // Prevents the form from submitting the traditional way

    let fileInput = document.getElementById('cadFilePicker');
    let file = fileInput.files[0];

    if (!file) {
        alert('Please select a CAD file.');
        return;
    }

    // Construct FormData
    let formData = new FormData();
    formData.append('CADFile', file);
    formData.append('DimensionType', document.getElementById('dimensionType').value);
    formData.append('OutputFileType', document.getElementById('outputFileType').value);
    formData.append('TakeScreenshot', document.getElementById('takeScreenshot').checked);
    formData.append('AssemblyMode', document.getElementById('assemblyMode').value);

    // Fetch request
    fetch('https://convert.renderdraw.us/CAD/2.0/', {
        method: 'POST',
        body: formData
    })
    .then(response => {
        if (!response.ok) {
            throw new Error('Network response was not ok');
        }
        return response.json();
    })
    .then(data => {
        console.log('Success:', data);
        // Handle the response data
    })
    .catch(error => {
        console.error('Error:', error);
    });
});
```

* The form (`<form id="cadUploadForm">`) now includes additional input elements for various options.
* Each option (Dimension Type, Output File Type, etc.) is represented by a dropdown or checkbox.
* The JavaScript listens for the 'submit' event on the form.
* It retrieves the values of all input elements and appends them to the `FormData`.
* The `fetch` request then sends this data to your API.
