# WebGL2 - Hello World (网络图形库2 - 你好，世界)
## https://kennyfully881230.github.io/webgl2_hello_world/

This repository contains a simple "Hello World" example demonstrating basic WebGL2 rendering by drawing a single green point on a canvas.

这个仓库包含一个简单的“你好，世界”示例，通过在画布上绘制一个绿色的点来展示基本的 WebGL2 渲染。

## English Version

### Overview

This project initializes a WebGL2 rendering context, compiles and links a vertex shader and a fragment shader, and then draws a single point on the canvas.

### How it Works

1.  **Context Initialization**: The code first obtains the WebGL2 rendering context from the HTML `<canvas>` element. This context, stored in the `gl` variable, is essential for all subsequent WebGL2 operations.

2.  **Shader Creation**:
    * **Vertex Shader**: This shader is responsible for setting the position and size of the point. `gl_Position` is set to `vec4(0.0, 0.0, 0.0, 1.0)`, which places the point at the center of the clip space. `gl_PointSize` is set to `100.0`, determining the diameter of the point in pixels.
    * **Fragment Shader**: This shader determines the color of the point. `fragColor` is set to `vec4(0.0, 1.0, 0.0, 1.0)`, which corresponds to a pure green RGBA color.

3.  **Shader Compilation and Program Linking**:
    * Each shader (vertex and fragment) is created using `gl.createShader()`, its source code is attached with `gl.shaderSource()`, and then compiled with `gl.compileShader()`.
    * A WebGL program is created with `gl.createProgram()`.
    * Both compiled shaders are attached to the program using `gl.attachShader()`.
    * Finally, `gl.linkProgram()` combines the attached shaders into an executable program.
    * `gl.useProgram()` installs this linked program onto the GPU, making it active for rendering.

4.  **Rendering**:
    * `gl.drawArrays(gl.POINTS, 0, 1)` is called to draw the point.
    * `gl.POINTS` specifies that the primitive type to be drawn is a point.
    * `0` indicates the starting index in the vertex arrays.
    * `1` specifies that one vertex should be rendered.
    * Behind the scenes, the vertex shader executes once for the single vertex. Rasterization then generates fragments for the 100-pixel circle, and the fragment shader colors all these fragments green, which are then drawn to the canvas (framebuffer).

### Coordinate Systems

* **Normalized Device Coordinates (NDC)**: In WebGL, coordinates range from -1 to 1 along the X and Y axes.
* **Viewport**: This maps the NDC to the actual canvas pixels (320x320 in this example).
* `gl_Position`: This is the output in clip space, before perspective division.

### Files

* `index.html`: The main HTML file containing the canvas and the embedded WebGL2 JavaScript code.

---

## 中文版本

### 概述

本项目初始化一个 WebGL2 渲染上下文，编译并链接一个顶点着色器和一个片段着色器，然后在画布上绘制一个点。

### 工作原理

1.  **上下文初始化**: 代码首先从 HTML `<canvas>` 元素获取 WebGL2 渲染上下文。这个上下文存储在 `gl` 变量中，对所有后续的 WebGL2 操作都至关重要。

2.  **着色器创建**:
    * **顶点着色器**: 这个着色器负责设置点的位置和大小。`gl_Position` 被设置为 `vec4(0.0, 0.0, 0.0, 1.0)`，将点放置在裁剪空间的中心。`gl_PointSize` 被设置为 `100.0`，决定了点在像素中的直径.
    * **片段着色器**: 这个着色器决定了点的颜色。`fragColor` 被设置为 `vec4(0.0, 1.0, 0.0, 1.0)`，对应于纯绿色 RGBA 颜色。

3.  **着色器编译与程序链接**:
    * 每个着色器（顶点和片段）都使用 `gl.createShader()` 创建，其源代码通过 `gl.shaderSource()` 附加，然后使用 `gl.compileShader()` 进行编译。
    * 使用 `gl.createProgram()` 创建一个 WebGL 程序。
    * 两个已编译的着色器都使用 `gl.attachShader()` 附加到程序中。
    * 最后，`gl.linkProgram()` 将附加的着色器组合成一个可执行程序。
    * `gl.useProgram()` 将这个链接好的程序安装到 GPU 上，使其在渲染时处于活动状态。

4.  **渲染**:
    * 调用 `gl.drawArrays(gl.POINTS, 0, 1)` 来绘制点。
    * `gl.POINTS` 指定要绘制的图元类型是点。
    * `0` 表示顶点数组中的起始索引。
    * `1` 指定要渲染的顶点数量。
    * 在底层，顶点着色器为单个顶点执行一次。然后光栅化为100像素的圆生成片段，片段着色器将所有这些片段着色为绿色，最后绘制到画布（帧缓冲区）上。

### 坐标系统

* **标准化设备坐标 (NDC)**: 在 WebGL 中，坐标范围沿 X 和 Y 轴从 -1 到 1。
* **视口**: 这将 NDC 映射到实际的画布像素（本例中为 320x320）。
* `gl_Position`: 这是裁剪空间中的输出，在透视除法之前。

### Files

* `index.html`: 包含画布和嵌入式 WebGL2 JavaScript 代码的主 HTML 文件。
