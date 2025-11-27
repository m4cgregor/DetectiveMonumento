# Detective Monumento - Web AR Game

An immersive Web AR experience where players hunt for historical fragments at the Monumento a la Bandera using their mobile device camera.

## 🎮 About

Detective Monumento is a location-based AR treasure hunt game that uses **MindAR.js** for image target tracking. Players scan real monument details with their camera to discover 3D artifacts and solve puzzles.

## ✨ Features

- 🎯 **Image Target Tracking** - Uses MindAR to detect monument details
- 📱 **No App Required** - Pure web-based AR experience
- 🏛️ **3 Missions** - Find fragments at Friso, Pampa, and Urna
- ⭐ **Scoring System** - Earn up to 9 stars based on performance
- 🎨 **3D Models** - Interactive GLTF models overlay on targets
- 🇦🇷 **Cultural Heritage** - Learn about Argentine history

## 🚀 Quick Start

### For Players

1. Visit the game URL on your mobile device (requires HTTPS)
2. Allow camera access
3. Follow the in-game instructions
4. Point your camera at monument details to find fragments!

### For Developers

1. **Clone/Download** this repository

2. **Prepare Target Images**:
   - Take photos of monument details
   - Compile them using MindAR compiler
   - See `AR_SETUP_GUIDE.md` for detailed instructions

3. **Add 3D Models** (optional):
   - Place GLTF models in `assets/` folder
   - Or use simple A-Frame primitives

4. **Serve with HTTPS**:
   ```bash
   npx http-server -S
   ```

5. **Open on Mobile**:
   - Navigate to `https://your-ip:8080/ar-index.html`
   - Grant camera permissions
   - Start playing!

## 📁 Project Structure

```
DetectiveMonumento/
├── index.html              # Original mockup (non-AR version)
├── ar-index.html           # AR-enabled game (use this!)
├── AR_SETUP_GUIDE.md       # Complete setup instructions
├── README.md               # This file
└── assets/                 # AR assets
    ├── targets.mind        # Compiled image targets (you create this)
    ├── target-*.png        # Source images for targets
    └── *.gltf              # 3D models for each mission
```

## 🎯 Game Flow

1. **Home** → Start game
2. **Intro** → Learn the mission
3. **Hub** → Select a fragment to find
4. **AR Scan** → Point camera at monument detail
5. **Detection** → 3D model appears when target found
6. **Success** → Earn stars and return to hub
7. **Repeat** → Complete all 3 missions
8. **Final** → Activate the tower for victory!

## 🛠️ Technology Stack

- **MindAR.js** - Image tracking AR library
- **A-Frame** - WebXR framework for 3D/AR
- **Vanilla JS** - Game logic and state management
- **GLTF** - 3D model format

## 📱 Browser Support

- ✅ iOS Safari 11+
- ✅ Android Chrome 67+
- ✅ Desktop Chrome/Firefox (for testing with webcam)

**Note**: HTTPS is required for camera access!

## 🔧 Setup & Configuration

See `AR_SETUP_GUIDE.md` for complete instructions on:
- Taking good target images
- Compiling images with MindAR
- Adding custom 3D models
- Testing on mobile devices
- Troubleshooting common issues

## 📖 Documentation

- **AR Setup Guide**: `AR_SETUP_GUIDE.md`
- **MindAR Docs**: https://hiukim.github.io/mind-ar-js-doc/
- **A-Frame Docs**: https://aframe.io/docs/

## 🎨 Customization

### Change 3D Model Size

Edit `ar-index.html`, find the model entity:

```html
<a-gltf-model scale="0.3 0.3 0.3" ...>
```

Adjust scale values as needed.

### Modify Detection Timing

In `ar-index.html`, find:

```javascript
detectionTimeout = setTimeout(() => {
    confirmFound();
}, 2000); // Change this value (milliseconds)
```

### Add Sound Effects

Add audio files to `assets/` and reference in A-Frame:

```html
<a-assets>
    <audio id="found-sound" src="assets/found.mp3"></audio>
</a-assets>
```

## 🐛 Troubleshooting

**Targets not detecting?**
- Ensure `targets.mind` file exists in `assets/`
- Check image quality (high contrast, clear features)
- Improve lighting conditions
- Hold camera steady

**3D models not showing?**
- Verify GLTF files are in `assets/` folder
- Check browser console for errors
- Try using simple primitives first

**Camera not working?**
- Must use HTTPS (not HTTP)
- Grant camera permissions
- Check if another app is using camera

See `AR_SETUP_GUIDE.md` for more troubleshooting tips.

## 📝 License

This project is for educational purposes. Monument images are from Wikimedia Commons.

## 🙏 Credits

- **MindAR** by hiukim - https://github.com/hiukim/mind-ar-js
- **A-Frame** by Mozilla - https://aframe.io
- Monument images from Wikimedia Commons

## 🤝 Contributing

Feel free to fork and customize for your own location-based AR experiences!

---

**Ready to hunt for history?** 🏛️🔍✨
