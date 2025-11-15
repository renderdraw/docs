# QR Code Scanner

Meet the "QR Code Scanner" component, a versatile tool designed to decode QR codes within your Salesforce Lightning Flows. This highly functional component offers a seamless way to capture and interpret QR codes, simplifying data entry and reducing manual work.

How does it work? It starts with a click on the 'Scan QR Code' button, triggering the camera to scan any available QR code. If you want to customize the button label, you have the flexibility to do so using the 'instructionText' property.

Our QR Code Scanner is built to handle a variety of barcode types. Whether it's the common 'qr' or 'pdf417' type or something less usual like 'code39' or 'code128', this component has you covered.

Once a QR code is scanned, the resulting string is stored in the 'scannedCode' property, making it easy to retrieve and use this information later.

What if you're using Salesforce Flow? Well, the QR Code Scanner is equipped to handle that too. If the 'useWithFlow' property is activated, the scanner will automatically trigger the next step in the Flow upon completing a scan. This seamless integration provides an efficient way to streamline your workflows.

Last but not least, the component checks if a camera device is available before starting the scanning process. If a camera isn't available, it triggers an error message, ensuring you are kept informed.

In short, the QR Code Scanner is a capable and user-friendly tool that adds a layer of efficiency and automation to your Salesforce platform. It's all about making your work easier and more productive.
