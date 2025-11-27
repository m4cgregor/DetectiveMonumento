# AR Setup Guide - Detective Monumento

## Quick Start

Your AR-enabled game is ready! This guide will help you set up real image targets and 3D models.

---

## 📸 Step 1: Prepare Target Images

### What Makes a Good Target Image?

For MindAR to track reliably, your target images should have:
- ✅ **High resolution** (at least 480x640 pixels, 300+ DPI recommended)
- ✅ **Good contrast** and distinct features
- ✅ **Clear details** (edges, patterns, textures)
- ✅ **Even lighting** (avoid shadows and glare)
- ❌ **Avoid** plain colors, symmetrical patterns, or blurry images

### Taking Photos of Monument Details

1. **Friso (Relief Carving)**
   - Photo the stone relief showing historical figures
   - Get close enough to see details
   - Ensure good lighting and sharp focus

2. **Pampa (Bull Statue)**
   - Photo the bronze bull sculpture
   - Capture distinctive features
   - Frame it to fill most of the image

3. **Urna (Eternal Flame)**
   - Photo the ceremonial urn with flame
   - Include surrounding architectural details
   - Capture from a consistent viewing angle

4. **Torre (Tower)**
   - Photo the central tower
   - Can be from the patio looking up
   - Include distinctive architectural features

### Save Your Images

Save your photos as:
- `target-friso.png` or `.jpg`
- `target-pampa.png` or `.jpg`
- `target-urna.png` or `.jpg`
- `target-torre.png` or `.jpg`

Place them in the `assets/` folder.

---

## 🎯 Step 2: Compile Image Targets

MindAR needs to convert your images into a special `.mind` file format.

### Using the Online Compiler

1. **Go to**: https://hiukim.github.io/mind-ar-js-doc/tools/compile

2. **Upload your images**:
   - Click "Select Images"
   - Upload all 4 target images in order:
     1. target-friso.png
     2. target-pampa.png
     3. target-urna.png
     4. target-torre.png
   
   ⚠️ **Order matters!** The first image becomes targetIndex 0, second becomes 1, etc.

3. **Start Compilation**:
   - Click "Start"
   - Wait for processing (may take 1-2 minutes)

4. **Download Result**:
   - Download the generated `targets.mind` file
   - Place it in `assets/targets.mind`

### Alternative: Command Line Compiler

If you prefer using Node.js:

```bash
npm install -g mind-ar-cli

mind-ar-compiler \
  assets/target-friso.png \
  assets/target-pampa.png \
  assets/target-urna.png \
  assets/target-torre.png \
  assets/targets
```

This creates `assets/targets.mind`.

---

## 🎨 Step 3: Add 3D Models (Optional)

The game will work without 3D models, but they make it more engaging!

### Finding 3D Models

**Free Resources:**
- [Sketchfab](https://sketchfab.com/) - Search for "monument", "artifact", "treasure"
- [Poly Pizza](https://poly.pizza/) - Free low-poly models
- [Google Poly Archive](https://poly.google.com/) - Historical models

**What to Look For:**
- GLTF or GLB format (required for A-Frame)
- Low polygon count (< 10K polygons for mobile performance)
- Appropriate theme (historical artifacts, monuments, treasures)

### Adding Models to Your Game

1. Download GLTF/GLB models
2. Rename them:
   - `fragment-friso.gltf`
   - `fragment-pampa.gltf`
   - `fragment-urna.gltf`
   - `tower-complete.gltf`
3. Place in `assets/` folder

### Creating Simple Placeholder Models

If you don't have custom models, you can use A-Frame primitives. Edit `ar-index.html` and replace:

```html
<a-gltf-model src="#model-friso"></a-gltf-model>
```

With:

```html
<a-box color="#D4AF37" scale="0.2 0.2 0.2"></a-box>
```

Or other primitives: `<a-sphere>`, `<a-cylinder>`, `<a-cone>`, etc.

---

## 🧪 Step 4: Testing Your AR Experience

### Desktop Testing

1. **Open in Browser**:
   - Open `ar-index.html` in Chrome or Firefox
   - Allow camera access when prompted

2. **Print Target Images**:
   - Print your target images on paper
   - Or display them on another screen

3. **Point Camera**:
   - Point your webcam at the printed/displayed images
   - The 3D models should appear when detected

### Mobile Testing (Recommended)

AR works best on mobile devices!

**Requirements:**
- ✅ HTTPS connection (required for camera access)
- ✅ Modern browser (iOS Safari 11+, Android Chrome 67+)

**Option 1: Local Server with HTTPS**

```bash
# Install http-server with SSL
npm install -g http-server

# Run with SSL (creates self-signed certificate)
http-server -S -C cert.pem -K key.pem
```

Then access via `https://your-local-ip:8080/ar-index.html`

**Option 2: Deploy to GitHub Pages**

1. Create a GitHub repository
2. Upload all files
3. Enable GitHub Pages in settings
4. Access via `https://username.github.io/repo-name/ar-index.html`

**Option 3: Use Ngrok**

```bash
# Install ngrok
npm install -g ngrok

# Serve your directory
npx http-server

# In another terminal, create tunnel
ngrok http 8080
```

Use the HTTPS URL provided by ngrok.

---

## 🔧 Troubleshooting

### "Targets not detected"

- ✅ Ensure `targets.mind` file exists in `assets/`
- ✅ Check image quality (high contrast, clear features)
- ✅ Ensure good lighting when scanning
- ✅ Hold camera steady for 1-2 seconds
- ✅ Try different distances (20-50cm usually works best)

### "3D models not appearing"

- ✅ Check browser console for errors (F12)
- ✅ Verify GLTF files are in `assets/` folder
- ✅ Ensure file names match exactly
- ✅ Try using simple primitives first (see Step 3)

### "Camera not working"

- ✅ Must use HTTPS (not HTTP)
- ✅ Grant camera permissions in browser
- ✅ Check if another app is using camera
- ✅ Try a different browser

### "Performance issues"

- ✅ Reduce 3D model polygon count
- ✅ Use simpler models or primitives
- ✅ Close other browser tabs
- ✅ Test on a newer device

---

## 📱 Recommended Testing Workflow

1. **Start Simple**:
   - Test with one target first
   - Use simple primitives instead of complex models
   - Verify detection works

2. **Add Complexity**:
   - Add remaining targets one by one
   - Replace primitives with GLTF models
   - Test each addition

3. **Optimize**:
   - Adjust model scales in code
   - Fine-tune animations
   - Test on target device (mobile)

---

## 🎮 Game Flow

1. **Home Screen** → Click "JUGAR"
2. **Intro Screen** → Click "ACEPTAR MISIÓN"
3. **Hub (Medallion)** → Click empty slot to start mission
4. **AR Camera** → Point at target, wait for detection
5. **Auto-confirm** → After 2 seconds of stable tracking
6. **Success Screen** → Shows stars earned
7. **Repeat** → Complete all 3 missions
8. **Final Mission** → Activate the tower
9. **Win Screen** → See total score

---

## 📝 Customization Tips

### Adjust 3D Model Size

In `ar-index.html`, find:

```html
<a-gltf-model scale="0.3 0.3 0.3" ...>
```

Change scale values (try 0.1 to 1.0).

### Change Detection Time

Find this line:

```javascript
detectionTimeout = setTimeout(() => {
    if (currentTargetDetected) {
        confirmFound();
    }
}, 2000); // ← Change this (milliseconds)
```

### Add Sound Effects

Add to `<a-assets>`:

```html
<audio id="sound-found" src="assets/found.mp3"></audio>
```

Then in `confirmFound()`:

```javascript
document.getElementById('sound-found').play();
```

---

## 🆘 Need Help?

**MindAR Documentation**: https://hiukim.github.io/mind-ar-js-doc/

**A-Frame Documentation**: https://aframe.io/docs/

**Community Support**:
- MindAR GitHub Issues: https://github.com/hiukim/mind-ar-js/issues
- A-Frame Discord: https://aframe.io/community/

---

## ✅ Checklist

- [ ] Took photos of 4 monument details
- [ ] Compiled images into `targets.mind` file
- [ ] Placed `targets.mind` in `assets/` folder
- [ ] (Optional) Added GLTF models to `assets/`
- [ ] Tested on desktop with webcam
- [ ] Set up HTTPS for mobile testing
- [ ] Tested on mobile device
- [ ] Verified all 3 missions work
- [ ] Tested final tower mission
- [ ] Checked win screen displays correctly

**You're ready to play!** 🎉
