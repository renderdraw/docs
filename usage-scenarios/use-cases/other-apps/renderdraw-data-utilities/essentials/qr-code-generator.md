# QR Code Generator

Think about all those times you've wished to share a website or a piece of information with someone without needing them to type a long, cumbersome URL. Enter the QR Code Generator, a component that's as simple to use as it is powerful!

To start, let's look at the heart of this generator: the QR Code itself. This is represented by an image in the center of the component. This isn't just any image - it's a specially generated QR Code based on a URL you provide. Just point a QR Code reader at it (like the one on your smartphone), and you'll be instantly directed to the specified URL.

When the QR Code is clicked, a user will be navigated to the URL posted

Optionally, Below the QR code image, you'll find two input fields: the URL Input and Label Input.

The URL Input field is where you get to specify the URL you want to be encoded in the QR Code. As you type, the `handleTextValueChanged` function is triggered. This updates the URL to be encoded, and the QR Code image is regenerated in real-time.

The Label Input field serves a different purpose. It provides a way to label the QR Code. This label appears in the title section of the card containing the QR code. As you input your label, the `handleTextLabelValueChanged` function is triggered, which updates the title above the QR code, giving your users some context about what the QR Code is for.

To summarize, the QR Code Generator is a handy tool that helps you create QR Codes for any URL, right within Salesforce. It's user-friendly and extremely versatile. So the next time you need to share a link with your users or need a QR Code for your marketing materials, you know which tool to use!

A handy QR code component you can use within Flows, or screen components

![](<../../../../../.gitbook/assets/image (43).png>)

Easily add the component to a Lightning flow, and put the URL you want the QR to point to in the urlToEncode Field.&#x20;

The title parameter will add a Header title to the QR code.&#x20;

If you want your users to be able to change the URL or label, set the showInput parameter to true.&#x20;
