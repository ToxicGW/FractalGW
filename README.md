#  FractalGW: Mandelbrot & Julia Sets (OSL)


<video src="https://github.com/ToxicGW/FractalGW/blob/main/FractalGW-Overview.mp4" width="100%" autoplay loop muted controls></video>

🖌A custom Open Shading Language (OSL) shader designed for Blender's cycle engine. This project uses precise mathematical loops to generate both the Mandelbrot set and infinite variations of the Julia set natively within your shader node tree. 

It also features an integrated **renormalized smoothing algorithm** to eliminate pixel errors or artifacts which makes it perfect for high-resolution arts that can be used in space or any custom arts with infinite zoom exploration.


---

## ✨ Key Features

* **Index-Based Engine:** A single integer value (acts as dropdown or menu switch) toggles the Mandelbrot set or the Julia sets seamlessly.
* **Renormalized Smoothing:** Applies double-logarithm color smoothing ($I_{smooth} = i + 1 - \frac{\ln(\ln(|Z|))}{\ln(2)}$) to completely remove harsh, jagged "stair-step" color rings.
* **Infinite Zoom:** Bypasses standard texture coordinate limits, allowing you to dive thousands of layers deep into fractal boundaries without quality loss.
* **Full Manual Customization:** Exposes raw mathematical parameters directly as node sliders. You can plug custom coordinate vectors, drivers, or animation keys directly into the shader properties.


---

## ⚠️ Important Performance Notes

* **CPU Only:** Because this shader uses Open Shading Language scripting loops, it requires Blender's OSL backend which runs strictly on the **CPU** inside the Cycles engine. 
* **Render Time:** This is a mathematically heavy "slow yet accurate method" since it evaluates complex number math loops per pixel, render times will be noticeably longer than standard native shader nodes. It is highly optimized for **accuracy and visual flexibility** rather than real-time playback.


---

## 🎛️ Controller Settings

You have full control over the fractal generation via the following input sliders on the Script node:

* **Fractal Type (from 0 to 3):** Set to `0` for the standard Mandelbrot set. Set to `1` to unlock the Julia set.
*  Set to `2` to see connected Dendrite shape.
*  Set to `3` for manual reshaping or modifications.
* **X-axis & Y-axis (Julia Constants):** (Only active in Julia mode) Tiny decimal adjustments (like $C_x: -0.4$, $C_y: 0.6$) will completely morph the geometry into dendrites, spirals or animal-like fractal shapes.
* **Zoom:** Multiplies your coordinate depth to scale into the fractal borders.
* **Max Iterations:** Controls the calculation depth. Increase this value as you zoom deeper to preserve crisp edge details.


---

## 🛠️ How to Setup and Run in Blender

1. Change your Render Engine to **Cycles** inside the *Render Properties* panel.
2. Check the box labeled **Open Shading Language** (Note: Your render device dropdown will automatically grey out or switch to CPU).
3. Open Blender's **Text Editor** workspace, create a new text block, and paste the code from `FractalGW.osl`.
4. In your **Shader Editor**, press `Shift + A`, add a `Script` node, switch its mode to *External*, and select your text file from the dropdown.
5. Connect the **Object** output port of a *Texture Coordinate* node straight into the **Vector** input slot of your new Script node.
6. Feed the output `Factor` or `FractalColor` pins into a *ColorRamp* node or directly into your __*emission*__ or __*principle BSDF*__ as shader node.


---

## 📦 Repository Structure

* `FractalGW.osl` - The core Open Shading Language script.
* `FractalGW_demo.blend` - A pre-built Blender scene file with the OSL script loaded and linked to a materials setup.
* `.gitignore` - Custom rules to ignore compiled shader binaries (`*.oso`) and auto-saved backup files (`*.blend1`).

---

## 📄 License
This project is shared under the **GNU GPLv3 License**. Feel free to use this project file in your personal art projects, commercial rendering pipelines or educational demonstrations as open-source format.
