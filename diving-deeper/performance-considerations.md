# Performance Considerations

RenderDraw uses the latest in web technologies to provide an in-browser rendering experience. In order for interactive 3D to be possible, we have to ensure both **WebGL** and **Hardware Acceleration** are enabled, where available.&#x20;

Mobile devices have this on by default, as do tablets, but computers, specifically Windows machines lag when **Hardware Acceleration** is not enabled.&#x20;

### Enabling WebGL

If your browser supports WebGL, follow these instructions to enable it:

#### Chrome

First, enable hardware acceleration:

* Go to chrome://settings
* Click the **+ Show advanced settings** button
* In the **System** section, ensure the _'**use hardware acceleration when available'**_ checkbox is checked (you'll need to relaunch Chrome for any changes to take effect)

Second, inspect the status of WebGL:

* Go to chrome://gpu
* Inspect the **WebGL** item in the **Graphics Feature Status** list. The status will be one of the following:
  * _Hardware accelerated_ — WebGL is enabled and hardware-accelerated (running on the graphics card).
  * _Software only, hardware acceleration unavailable_ — WebGL is enabled, but running in software. See [here](http://www.chromium.org/developers/design-documents/gpu-accelerated-compositing-in-chrome#TOC-Appendix-B:-The-Software-Compositor) for more info: "For software rendering of WebGL, Chrome uses [SwiftShader](https://www.transgaming.com/swiftshader), a software GL rasterizer."
  * _Unavailable_ — WebGL is not available in hardware or software.

If the status is not _"Hardware accelerated"_, then the **Problems Detected** list (below the **Graphics Feature Status** list) may explain why hardware acceleration is unavailable. Please consult this list before contacting our support team. If you have a display driver older than 2010, it may be the cause of the issue. Please update your display drivers and then go back to chrome://gpu again to look for problems.

Please ensure you are not using an extension that may be disabling WebGL.

#### Opera

First, enable hardware acceleration:

* Go to about:config
* On the left hand menu, click "Browser"
* Click the **Show advanced settings** checkbox
* In the **System** section, ensure the **Use hardware acceleration when available** checkbox is checked (you'll need to relaunch Opera for any changes to take effect)

#### Firefox

First, enable WebGL:

* Go to about:config
* Search for webgl.disabled
* Ensure that its value is false (any changes take effect immediately without relaunching Firefox)

Second, inspect the status of WebGL:

* Go to about:support
* Inspect the **WebGL Renderer** row in the **Graphics** table:
  * If the status contains a graphics card manufacturer, model and driver (eg: _"NVIDIA Corporation -- NVIDIA GeForce GT 650M OpenGL Engine"_), then WebGL is enabled.
  * If the status is something like _"Blocked for your graphics card because of unresolved driver issues"_ or _"Blocked for your graphics driver version"_, then your graphics card/driver is blacklisted.

(Like Chrome, Firefox has a **Use hardware acceleration when available** checkbox, in **Preferences** > **Advanced** > **General** > **Browsing**. However, unlike Chrome, Firefox does not require this checkbox to be checked for WebGL to work.)

#### Safari

* Go to Safari's **Preferences**
* Select the **Advanced** tab
* Ensure that the **Show Develop menu in menu bar** checkbox is checked
* In Safari's **Develop** menu, ensure that **Enable WebGL** is checked
