Here’s a detailed and professional README for your package:

---

# 🖼️ WASM Spritesheet Generator

[![NPM Version](https://img.shields.io/npm/v/wasm-spritesheet-generator.svg)](https://www.npmjs.com/package/wasm-spritesheet-generator)
[![License](https://img.shields.io/github/license/saksham-tomer/wasm-spritesheet-generator.svg)](https://github.com/saksham-tomer/wasm-spritesheet-generator/blob/main/LICENSE)

**WASM Spritesheet Generator** is a high-performance, WebAssembly-powered utility written in Rust for generating spritesheets and metadata from image arrays. It is ideal for game developers, web developers, or anyone working with animations, textures, or custom graphics pipelines. 

Published as an npm package, this tool provides seamless integration into JavaScript and TypeScript projects.

---

## 🌟 Features

- **High Performance**: Utilizes Rust's speed and WebAssembly's lightweight nature for blazing-fast spritesheet generation.
- **Rich Metadata**: Automatically generates detailed metadata (frames, coordinates, sizes) in JSON format.
- **Cross-Platform**: Runs in modern browsers and Node.js environments.
- **PNG Output**: Generates spritesheets in PNG format with complete control over canvas dimensions.
- **TypeScript Ready**: Fully compatible with TypeScript for type-safe development.
- **Simple Integration**: Easy-to-use JavaScript/TypeScript interface for developers of all levels.

---

## 📦 Installation

Install the package via npm:

```bash
npm install wasm-spritesheet-generator
```

Or with Yarn:

```bash
yarn add wasm-spritesheet-generator
```

---

## 🚀 Getting Started

### **Basic Usage**

Here's how to use `wasm-spritesheet-generator` in your JavaScript or TypeScript project:

1. **Import and Initialize**:
   ```javascript
   import init, { generate_spritesheet } from "wasm-spritesheet-generator";

   // Initialize WASM
   await init();
   ```

2. **Generate a Spritesheet**:
   ```javascript
   const images = [/* Uint8Array of image data */];
   const canvasWidth = 1024; // Desired canvas width

   const result = generate_spritesheet(images, canvasWidth);

   const { metadata, imageBuffer } = result;

   // Display or download the generated spritesheet
   const blob = new Blob([imageBuffer], { type: "image/png" });
   const imageUrl = URL.createObjectURL(blob);
   console.log("Spritesheet Metadata:", metadata);
   ```

3. **Render the Spritesheet**:
   ```jsx
   <img src={imageUrl} alt="Generated Spritesheet" />
   ```

---

## 📚 API Documentation

### **`init()`**
Initializes the WebAssembly module. Must be called before using other functions.

**Returns**:
- `Promise<void>`

---

### **`generate_spritesheet(images: Uint8Array[], canvasWidth: number): Result`**

Generates a spritesheet and metadata.

**Parameters**:
- `images` (Array of `Uint8Array`): The array of raw image data (e.g., PNG, JPEG).
- `canvasWidth` (number): The desired width of the canvas. Images will wrap onto new rows if they exceed this width.

**Returns**:
- `Result`:
  - `metadata`: JSON metadata describing the frames and overall spritesheet (see example below).
  - `imageBuffer`: `Uint8Array` of the generated PNG spritesheet.

**Example Metadata**:
```json
{
  "frames": {
    "Image1.png": {
      "frame": { "x": 0, "y": 0, "w": 128, "h": 128 },
      "rotated": false,
      "trimmed": false,
      "spriteSourceSize": { "x": 0, "y": 0, "w": 128, "h": 128 },
      "sourceSize": { "w": 128, "h": 128 }
    }
  },
  "meta": {
    "app": "WASM Spritesheet Generator",
    "version": "1.0",
    "image": "spritesheet.png",
    "format": "RGBA8888",
    "size": { "w": 1024, "h": 256 },
    "scale": "1"
  }
}
```

---

## ⚙️ How It Works

### **Rust and WASM at Its Core**
This package is built with Rust, a systems programming language known for its performance and safety. The core logic handles:
1. **Image Decoding**: Parsing raw image data into manageable structures.
2. **Canvas Composition**: Arranging images into a single canvas, managing offsets and rows.
3. **Metadata Generation**: Generating detailed JSON metadata describing the positions and sizes of frames.
4. **Image Encoding**: Outputting the final canvas as a PNG buffer.

Using WebAssembly (WASM), the compiled Rust code runs natively in your browser or Node.js environment with near-native performance.

### **Advantages of WASM in Web Development**
- **Efficiency**: WASM executes at near-native speed, much faster than JavaScript for compute-heavy tasks.
- **Compact**: Rust-compiled WASM binaries are small, making this package lightweight.
- **Cross-Language Integration**: Seamlessly bridges high-performance Rust with JavaScript, combining the best of both worlds.

---

## 🛠️ Advanced Features

- **Custom Canvas Width**: Control how images are arranged by adjusting the canvas width.
- **Frame Metadata**: Includes detailed frame-specific data such as trimming, rotation, and source size.
- **Downloadable Spritesheets**: Easily generate downloadable assets for use in games or applications.

---

## 🏆 Advantages

1. **Blazing-Fast Performance**: Built on Rust, optimized with WebAssembly.
2. **Developer-Friendly**: Simple API, rich metadata, and detailed logs for debugging.
3. **Cross-Platform**: Works in any modern browser or Node.js environment.
4. **Customizable Output**: Adjust canvas width, generate detailed metadata, and control frame arrangement.

---

## 👨‍💻 Example Projects

Explore how this package can be used in real-world scenarios:
- **Game Development**: Create optimized texture atlases for 2D animations.
- **Web Applications**: Dynamically generate spritesheets for online design tools.
- **Interactive Graphics**: Preprocess assets for complex interactive experiences.

---

## 📝 License

This project is licensed under the [MIT License](https://github.com/saksham-tomer/wasm-spritesheet-generator/blob/main/LICENSE).

---

## 🙌 Contributing

Contributions are welcome! Feel free to open issues or submit pull requests on the [GitHub repository](https://github.com/saksham-tomer/wasm-spritesheet-generator).

---

## 🖖 About the Author

Developed by [Saksham Tomer](https://github.com/saksham-tomer), a passionate developer exploring the intersection of Rust, WASM, and web development.

---

This README ensures users understand the purpose, features, and advantages of your package while providing clear instructions for usage and customization. Let me know if you'd like any further refinements!
