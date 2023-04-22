---
title: Using textures in WebGL
slug: Web/API/WebGL_API/Tutorial/Using_textures_in_WebGL
---

{{DefaultAPISidebar("WebGL")}} {{PreviousNext("Web/API/WebGL_API/Tutorial/Creating_3D_objects_using_WebGL", "Web/API/WebGL_API/Tutorial/Lighting_in_WebGL")}}

现在我们已经创建好了一个可以旋转的 3D 的立方体，接下来是时候使用贴图来代替每个面的单一的颜色了。

## 加载纹理

首先加入加载纹理的代码。现在我们只使用一张单一的纹理贴到立方体的 6 个面上，但是同样的方法可以用来加载任意数量的纹理贴图。

> **备注：** 值得注意的一点是对纹理的加载同样需要遵循[跨域访问规则](/zh-CN/docs/Web/HTTP/CORS)；也就是说你只能从允许跨域访问的网址加载你需要的纹理。见[下方跨域纹理](#跨域纹理)小节以了解详情。

> **备注：** 在你的“webgl-demo.js”脚本中添加下面的两个函数：

```js
//
// Initialize a texture and load an image.
// When the image finished loading copy it into the texture.
//
function loadTexture(gl, url) {
  const texture = gl.createTexture();
  gl.bindTexture(gl.TEXTURE_2D, texture);

  // Because images have to be downloaded over the internet
  // they might take a moment until they are ready.
  // Until then put a single pixel in the texture so we can
  // use it immediately. When the image has finished downloading
  // we'll update the texture with the contents of the image.
  const level = 0;
  const internalFormat = gl.RGBA;
  const width = 1;
  const height = 1;
  const border = 0;
  const srcFormat = gl.RGBA;
  const srcType = gl.UNSIGNED_BYTE;
  const pixel = new Uint8Array([0, 0, 255, 255]); // opaque blue
  gl.texImage2D(
    gl.TEXTURE_2D,
    level,
    internalFormat,
    width,
    height,
    border,
    srcFormat,
    srcType,
    pixel
  );

  const image = new Image();
  image.onload = () => {
    gl.bindTexture(gl.TEXTURE_2D, texture);
    gl.texImage2D(
      gl.TEXTURE_2D,
      level,
      internalFormat,
      srcFormat,
      srcType,
      image
    );

    // WebGL1 has different requirements for power of 2 images
    // vs. non power of 2 images so check if the image is a
    // power of 2 in both dimensions.
    if (isPowerOf2(image.width) && isPowerOf2(image.height)) {
      // Yes, it's a power of 2. Generate mips.
      gl.generateMipmap(gl.TEXTURE_2D);
    } else {
      // No, it's not a power of 2. Turn off mips and set
      // wrapping to clamp to edge
      gl.texParameteri(gl.TEXTURE_2D, gl.TEXTURE_WRAP_S, gl.CLAMP_TO_EDGE);
      gl.texParameteri(gl.TEXTURE_2D, gl.TEXTURE_WRAP_T, gl.CLAMP_TO_EDGE);
      gl.texParameteri(gl.TEXTURE_2D, gl.TEXTURE_MIN_FILTER, gl.LINEAR);
    }
  };
  image.src = url;

  return texture;
}

function isPowerOf2(value) {
  return (value & (value - 1)) === 0;
}
```

函数 `loadTexture()` 首先调用 WebGL 的 {{domxref("WebGLRenderingContext.createTexture()", "createTexture()")}} 函数来创建一个 WebGL 纹理对象 texture。接下来使用 {{domxref("WebGLRenderingContext.texImage2D()", "texImage2D()")}} 以上传一个蓝色的像素点。这样我们就可以在图片下载完成之前使用这个蓝色的纹理了。

要从图片文件加载纹理，接下来创建一个 `Image` 对象，并为 `src` 设置我们想要用作纹理的图片的 URL。我们为 `image.onload` 设置的函数会在图片下载完成时被调用。那时我们再次调用 {{domxref("WebGLRenderingContext.texImage2D()", "texImage2D()")}}，这次我们将图片作为纹理的数据源。之后，我们根据下载的图像在两个维度上是否为 2 的幂来设置纹理的过滤（filter）和平铺（wrap）。

接下来为了真正地形成纹理，我们通过把新创建的纹理对象绑定到 `gl.TEXTURE_2D` 来让它成为当前操作纹理。然后通过调用 {{domxref("WebGLRenderingContext.texImage2D()", "texImage2D()")}} 把已经加载的图片图形数据写到纹理。

> **备注：** 在多数情况下，纹理的宽和高都必须是 2 的幂（如：1，2，4，8，16 等等）。如果有什么特殊情况请参考下面的“[非 2 的幂纹理](#非_2_的幂纹理)”小节。

代码的接下来两行设置了纹理过滤器，过滤器用来控制当图片缩放时像素如何生成如何插值。在这个例子里，我们对图片放大使用的是线性过滤，而对图片缩小使用的是多级渐进纹理过滤。接下来我们通过调用 {{domxref("WebGLRenderingContext.generateMipMap()", "generateMipMap()")}} 来生成多级渐进纹理，接着通过给 `gl.TEXTURE_2D` 绑定值 `null` 来告诉 WebGL 我们对当前纹理的操作已经结束了。

### 非 2 的幂纹理

一般来说，宽和高都是 2 的幂的纹理使用是最理想的。2 的幂纹理在渲染内存里的存储更高效，而且对它们的使用限制也更少。由美术工作人员生成的纹理最终在用来渲染前都应该使用放大或缩小的方式把它生成为 2 的幂纹理，其实事实上来说，在创作纹理之初就应该直接使用大小是 2 的幂的宽和高。纹理的每一边都应该是像 1，2，4，8，16，32，64，128，256，512，1024 或 2048 这样的值。当然也要注意尺寸的大小，因为虽说现在的大部分设置都已经可以支持 4096 像素的图片，但也不是全部；而有一些设备甚至可以支持 8192 或更高像素呢。

有的时候从你的特定情况出发，使用 2 的幂纹理会比较困难。当使用到第三方的资源时，一般来说最好的方式就是先使用 HTML5 的画布把图片修正成 2 的幂然后再放到 WebGL 中进行渲染使用，这样一来，如果图片拉伸比较明显的话纹理坐标的值可需要适当地进行修正。

但是，如果你一定要使用非 2 的幂纹理的话，WebGL 也有原生支持，不过这些支持是受限的。当然在某些情况下使用非 2 的幂纹理也是很有用的，比如这张纹理刚好与你的显示器的分辨率相匹配，或者使用画布重新生成纹理的方式并不值得时。但是要特别注意的是：这种非 2 的幂纹理不能用来生成多级渐进纹理，而且不能使用纹理重复（重复纹理寻址等）。

使用重复纹理寻址的一个例子就是使用一张砖块的纹理来平铺满一面墙壁。

多级渐进纹理和纹理坐标重复可以通过调用 {{domxref("WebGLRenderingContext.texParameter()", "texParameteri()")}} 来禁用，当然首先你已经通过调用 {{domxref("WebGLRenderingContext.bindTexture()", "bindTexture()")}} 绑定过纹理了。这样虽然已经可以使用非 2 的幂纹理了，但是你将无法使用多级渐进纹理，纹理坐标包装，纹理坐标重复，而且无法控制设备如何处理你的纹理。

```js
// gl.NEAREST is also allowed, instead of gl.LINEAR, as neither mipmap.
gl.texParameteri(gl.TEXTURE_2D, gl.TEXTURE_MIN_FILTER, gl.LINEAR);
// Prevents s-coordinate wrapping (repeating).
gl.texParameteri(gl.TEXTURE_2D, gl.TEXTURE_WRAP_S, gl.CLAMP_TO_EDGE);
// Prevents t-coordinate wrapping (repeating).
gl.texParameteri(gl.TEXTURE_2D, gl.TEXTURE_WRAP_T, gl.CLAMP_TO_EDGE);
```

现在，当使用以上参数时，兼容 WebGL 的设备就会自动变得可以使用任何分辨率的纹理（当然还要考虑像素上限）。如果不使用上面这些参数的话，任何非 2 的幂纹理使用都会失败然后返回一张纯黑图片。

## 映射纹理到面

现在，纹理已经加载好了，而且已经可以使用了。但是在使用之前我们还要创建好纹理坐标到立方体各个面的顶点的映射关系。下面的代码通过替换之前的设置每个面颜色的代码，当然还是在 `initBuffers()` 函数里。

> **备注：** 将下面函数添加到“init-buffer.js”模块中：

```js
function initTextureBuffer(gl) {
  const textureCoordBuffer = gl.createBuffer();
  gl.bindBuffer(gl.ARRAY_BUFFER, textureCoordBuffer);

  const textureCoordinates = [
    // Front
    0.0, 0.0, 1.0, 0.0, 1.0, 1.0, 0.0, 1.0,
    // Back
    0.0, 0.0, 1.0, 0.0, 1.0, 1.0, 0.0, 1.0,
    // Top
    0.0, 0.0, 1.0, 0.0, 1.0, 1.0, 0.0, 1.0,
    // Bottom
    0.0, 0.0, 1.0, 0.0, 1.0, 1.0, 0.0, 1.0,
    // Right
    0.0, 0.0, 1.0, 0.0, 1.0, 1.0, 0.0, 1.0,
    // Left
    0.0, 0.0, 1.0, 0.0, 1.0, 1.0, 0.0, 1.0,
  ];

  gl.bufferData(
    gl.ARRAY_BUFFER,
    new Float32Array(textureCoordinates),
    gl.STATIC_DRAW
  );

  return textureCoordBuffer;
}
```

首先，代码创建了一个 GL 缓存区，用来保存每个面的纹理坐标信息，然后把这个缓存区绑定到 GL 以方便我们写入数据。

数组变量 `textureCoordinates` 中定义好了与每个面上的每个顶点一一对应的纹理坐标。请注意，纹理坐标的取值范围只能从 0.0 到 1.0，所以不论纹理贴图的实际大小是多少，为了实现纹理映射，我们要使用的纹理坐标只能规范化到 0.0 到 1.0 的范围内。

纹理坐标信息给定了之后，把这个数组里的数据都写到 GL 缓存区，这样 GL 就能使用这个坐标数据了。

接下来，我们需要更新 `initBuffers()` 来创建并返回纹理坐标缓冲区而不是颜色缓冲区。

> **备注：** 在“init-buffers.js”模块的 `initBuffers()` 函数中，用下面一行替换 `initColorBuffer()` 的调用：

```js
const textureCoordBuffer = initTextureBuffer(gl);
```

> **备注：** 在“init-buffers.js”模块的 `initBuffers()` 函数中，用以下内容替换 `return` 语句：

```js
return {
  position: positionBuffer,
  textureCoord: textureCoordBuffer,
  indices: indexBuffer,
};
```

## 更新着色器

为了使用纹理来代替单一的颜色，着色器程序和着色器程序的初始化代码都需要进行修改。

### 顶点着色器

接下来我们会修改顶点着色器代码，现在不再需要获取顶点颜色数据，而是获取纹理坐标数据。

> **备注：** 在你的 `main()` 函数中更新 `vsSource` 定义，像这样：

```js
const vsSource = `
    attribute vec4 aVertexPosition;
    attribute vec2 aTextureCoord;

    uniform mat4 uModelViewMatrix;
    uniform mat4 uProjectionMatrix;

    varying highp vec2 vTextureCoord;

    void main(void) {
      gl_Position = uProjectionMatrix * uModelViewMatrix * aVertexPosition;
      vTextureCoord = aTextureCoord;
    }
  `;
```

代码的关键更改在于不再获取顶点颜色数据转而获取和设置纹理坐标数据；这样就能把顶点与其对应的纹理联系在一起了。

### 片段着色器

那么片段着色器也要相应地进行更改：

```js
const fsSource = `
    varying highp vec2 vTextureCoord;

    uniform sampler2D uSampler;

    void main(void) {
      gl_FragColor = texture2D(uSampler, vTextureCoord);
    }
  `;
```

现在的代码不会再使用一个简单的颜色值填充片段颜色，片段的颜色是通过采样器使用最好的映射方式从纹理中的每一个像素计算出来的。

### Attribute 与 Uniform 位置

因为我们修改了 attribute 并添加了 uniform，所以我们需要查找它们的位置。

> **备注：** 在你的 `main()` 函数中，像这样更新 `programInfo` 的定义：

```js
const programInfo = {
  program: shaderProgram,
  attribLocations: {
    vertexPosition: gl.getAttribLocation(shaderProgram, "aVertexPosition"),
    textureCoord: gl.getAttribLocation(shaderProgram, "aTextureCoord"),
  },
  uniformLocations: {
    projectionMatrix: gl.getUniformLocation(shaderProgram, "uProjectionMatrix"),
    modelViewMatrix: gl.getUniformLocation(shaderProgram, "uModelViewMatrix"),
    uSampler: gl.getUniformLocation(shaderProgram, "uSampler"),
  },
};
```

## 绘制具体纹理贴图的立方体

对 `drawScene()` 函数的更改很简单。

> **备注：** 在“draw-scene.js”模块的 `drawScene()` 函数中添加以下函数：

```js
// tell webgl how to pull out the texture coordinates from buffer
function setTextureAttribute(gl, buffers, programInfo) {
  const num = 2; // every coordinate composed of 2 values
  const type = gl.FLOAT; // the data in the buffer is 32-bit float
  const normalize = false; // don't normalize
  const stride = 0; // how many bytes to get from one set to the next
  const offset = 0; // how many bytes inside the buffer to start from
  gl.bindBuffer(gl.ARRAY_BUFFER, buffers.textureCoord);
  gl.vertexAttribPointer(
    programInfo.attribLocations.textureCoord,
    num,
    type,
    normalize,
    stride,
    offset
  );
  gl.enableVertexAttribArray(programInfo.attribLocations.textureCoord);
}
```

> **备注：** 在你的“draw-scene.js”模块的 `drawScene()` 函数中，用下面一行替换 `setColorAttribute()` 的调用：

```js
setTextureAttribute(gl, buffers, programInfo);
```

然后添加代码来指定要映射到面的纹理。

> **备注：** 在你的 `drawScene()` 函数中，就在对 `gl.uniformMatrix4fv()` 的两次调用之后，添加以下代码：

```js
// Tell WebGL we want to affect texture unit 0
gl.activeTexture(gl.TEXTURE0);

// Bind the texture to texture unit 0
gl.bindTexture(gl.TEXTURE_2D, texture);

// Tell the shader we bound the texture to texture unit 0
gl.uniform1i(programInfo.uniformLocations.uSampler, 0);
```

WebGL 提供了至少 8 个纹理单元，`gl.TEXTURE0` 是第一个。若我们想要改变第一个单元，我们需要调用 {{domxref("WebGLRenderingContext.bindTexture()", "bindTexture()")}} 以将纹理绑定到纹理单元 0 的 `TEXTURE_2D` 绑定点。然后告诉着色器所用纹理单元 0 作为 `uSampler`。

最后，在 `drawScene()` 函数中添加 `texture` 作为参数，包括它被定义和被调用的地方。

> **备注：** 更新你的 `drawScene()` 函数的定义以添加新的参数：

```js-nolint
function drawScene(gl, programInfo, buffers, texture, cubeRotation) {
```

> **备注：** 更新你的 `main()` 函数中调用 `drawScene()` 的地方：

```js
drawScene(gl, programInfo, buffers, texture, cubeRotation);
```

好，现在我们的立方体就会像这样旋转起来了。

{{EmbedGHLiveSample('dom-examples/webgl-examples/tutorial/sample6/index.html', 670, 510) }}

[查看完整示例代码](https://github.com/mdn/dom-examples/tree/main/webgl-examples/tutorial/sample6) | [在新窗口里打开示例](https://mdn.github.io/dom-examples/webgl-examples/tutorial/sample6/)

## 跨域纹理

加载 WebGL 纹理应该也可以说是跨域访问控制里的一个话题。为了在我们的显示内容里使用其他域名里的纹理图片，允许跨域访问也是要考虑的。可以通过查看[HTTP 访问控制](/zh-CN/docs/Web/HTTP/CORS)来获取到更多的相关细节。

[这篇文章](https://hacks.mozilla.org/2011/11/using-cors-to-load-webgl-textures-from-cross-domain-images/)也对跨域加载纹理到 WebGL 做出了解释。而且文章里面还包含了一个使用的[例子](https://people.mozilla.org/~bjacob/webgltexture-cors-js.html)。

被污染过的（只写）画布是不能拿来当作 WebGL 纹理来使用的。举个例子来说，当把一张跨域的图片画到一个 2D 的 {{ HTMLElement("canvas") }} 中时，这个画布就是“被污染过的”。

{{PreviousNext("Web/API/WebGL_API/Tutorial/Creating_3D_objects_using_WebGL", "Web/API/WebGL_API/Tutorial/Lighting_in_WebGL")}}
