# 3D Model Guide for Detective Monumento

This guide explains how to add 3D models to your AR experience.

---

## Quick Start: Using Simple Shapes

The easiest way to get started is using A-Frame's built-in primitives. No external files needed!

### Edit `ar-index.html`

Find the model entities (search for `<a-gltf-model`) and replace them with simple shapes:

**Example - Replace Friso model:**

```html
<!-- BEFORE (requires GLTF file) -->
<a-gltf-model 
    rotation="0 0 0" 
    position="0 0 0" 
    scale="0.3 0.3 0.3" 
    src="#model-friso">
</a-gltf-model>

<!-- AFTER (no file needed) -->
<a-box 
    color="#D4AF37" 
    rotation="0 45 0" 
    position="0 0 0" 
    scale="0.2 0.2 0.2"
    animation="property: rotation; to: 0 405 0; loop: true; dur: 10000">
</a-box>
```

### Available Primitives

```html
<!-- Golden Box -->
<a-box color="#D4AF37" scale="0.2 0.2 0.2"></a-box>

<!-- Sphere (like a pearl or orb) -->
<a-sphere color="#FFD700" radius="0.15"></a-sphere>

<!-- Cylinder (like a column) -->
<a-cylinder color="#D4AF37" height="0.3" radius="0.1"></a-cylinder>

<!-- Cone (like a pyramid) -->
<a-cone color="#D4AF37" height="0.3" radius-bottom="0.15"></a-cone>

<!-- Torus (ring shape) -->
<a-torus color="#D4AF37" radius="0.15" radius-tubular="0.03"></a-torus>

<!-- Octahedron (diamond shape) -->
<a-octahedron color="#FFD700" radius="0.15"></a-octahedron>
```

### Add Animations

Make your shapes more interesting:

```html
<a-box color="#D4AF37" scale="0.2 0.2 0.2"
    animation="property: rotation; to: 0 360 0; loop: true; dur: 5000"
    animation__2="property: position; to: 0 0.1 0; dir: alternate; loop: true; dur: 2000">
</a-box>
```

---

## Using Custom GLTF Models

For a more polished experience, use 3D models in GLTF format.

### Where to Find Free Models

1. **Sketchfab** (https://sketchfab.com/)
   - Search: "treasure", "artifact", "monument", "gem"
   - Filter: "Downloadable", "Free"
   - Download as GLTF

2. **Poly Pizza** (https://poly.pizza/)
   - Great for low-poly models
   - All models are free
   - Already optimized for web

3. **Google Poly Archive** (via third-party mirrors)
   - Historical 3D models
   - Cultural artifacts

### Model Requirements

- ✅ **Format**: GLTF (.gltf) or GLB (.glb)
- ✅ **Size**: Under 5MB per model
- ✅ **Polygons**: Under 10,000 triangles (for mobile performance)
- ✅ **Textures**: Embedded or in same folder

### Adding Models to Your Project

1. **Download** your GLTF model

2. **Rename** it to match the game:
   - `fragment-friso.gltf`
   - `fragment-pampa.gltf`
   - `fragment-urna.gltf`
   - `tower-complete.gltf`

3. **Place** in `assets/` folder

4. **Test** - The game will automatically load them!

### Adjusting Model Size and Position

Models might appear too big, too small, or in the wrong position. Edit `ar-index.html`:

```html
<a-gltf-model 
    src="#model-friso"
    position="0 0 0"        <!-- X Y Z position -->
    rotation="0 0 0"        <!-- X Y Z rotation in degrees -->
    scale="0.3 0.3 0.3">    <!-- X Y Z scale (1.0 = original size) -->
</a-gltf-model>
```

**Tips:**
- Start with `scale="0.1 0.1 0.1"` and increase
- Use `position="0 -0.2 0"` to move down
- Use `rotation="0 180 0"` to flip around

---

## Creating Your Own Models

### Using Blender (Free)

1. **Download Blender**: https://www.blender.org/

2. **Create** your model (keep it simple!)

3. **Export as GLTF**:
   - File → Export → glTF 2.0
   - Format: glTF Embedded (.gltf)
   - Include: Selected Objects
   - Check "Apply Modifiers"

4. **Optimize**:
   - Keep polygon count low (< 10K)
   - Use simple materials
   - Embed textures

### Using Online Tools

**Tinkercad** (https://www.tinkercad.com/)
- Easy 3D modeling in browser
- Export as OBJ, then convert to GLTF

**Converter** (https://products.aspose.app/3d/conversion/obj-to-gltf)
- Convert OBJ to GLTF online

---

## Model Optimization

### Reduce File Size

Use **gltf-pipeline** (command line):

```bash
npm install -g gltf-pipeline

gltf-pipeline -i model.gltf -o model-optimized.gltf -d
```

### Online Optimizer

**glTF Viewer** (https://gltf-viewer.donmccurdy.com/)
- Upload model
- View statistics
- Download optimized version

---

## Troubleshooting

### Model doesn't appear

- ✅ Check file path is correct
- ✅ Verify file is in `assets/` folder
- ✅ Check browser console (F12) for errors
- ✅ Try with a simple primitive first

### Model is too big/small

- Adjust `scale` attribute
- Try values from 0.01 to 2.0

### Model is in wrong position

- Adjust `position` attribute
- Y axis is up/down
- X axis is left/right
- Z axis is forward/back

### Model appears black

- Model may need lighting
- Add to scene:
  ```html
  <a-light type="ambient" intensity="0.5"></a-light>
  <a-light type="directional" intensity="0.8" position="1 1 1"></a-light>
  ```

### Performance issues

- ✅ Reduce polygon count
- ✅ Use simpler textures
- ✅ Use primitives instead of complex models
- ✅ Test on target device (mobile)

---

## Recommended Models for Each Mission

### Friso (Stone Relief)
- Search: "stone tablet", "ancient scroll", "relief carving"
- Style: Historical, stone texture
- Color: Gray, beige, white

### Pampa (Bull Statue)
- Search: "bull", "cow", "bronze statue"
- Style: Sculptural, metallic
- Color: Bronze, copper, gold

### Urna (Eternal Flame)
- Search: "flame", "fire", "torch", "brazier"
- Style: Glowing, animated
- Color: Orange, yellow, red

### Torre (Tower)
- Search: "tower", "monument", "obelisk", "flag"
- Style: Architectural, grand
- Color: Stone, with Argentine flag colors

---

## Example: Complete Model Setup

```html
<!-- In <a-assets> section -->
<a-assets>
    <a-asset-item id="model-friso" src="./assets/fragment-friso.gltf"></a-asset-item>
</a-assets>

<!-- In target entity -->
<a-entity id="target-friso" mindar-image-target="targetIndex: 0">
    <a-gltf-model 
        src="#model-friso"
        position="0 0 0"
        rotation="0 0 0"
        scale="0.3 0.3 0.3"
        animation="property: rotation; to: 0 360 0; loop: true; dur: 10000; easing: linear">
    </a-gltf-model>
    
    <a-text 
        value="Fragmento del Friso" 
        position="0 -0.3 0" 
        align="center" 
        color="#FFD700" 
        scale="0.5 0.5 0.5">
    </a-text>
</a-entity>
```

---

## Quick Reference

| Task | Solution |
|------|----------|
| Start simple | Use `<a-box>`, `<a-sphere>`, etc. |
| Find models | Sketchfab, Poly Pizza |
| Format | GLTF or GLB |
| Size limit | < 5MB, < 10K polygons |
| Too big | Reduce `scale` |
| Too small | Increase `scale` |
| Wrong position | Adjust `position` |
| Optimize | Use gltf-pipeline |

---

**Ready to add 3D magic to your AR experience!** ✨
