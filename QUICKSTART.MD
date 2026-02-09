# 🚀 Quick Start Guide

Get started with NutriScan Pro in under 5 minutes!

## 📥 Option 1: Use Online (Easiest!)

1. **Visit the Live Demo**
   ```
   https://your-username.github.io/nutriscan-pro/
   ```

2. **Start Scanning!**
   - Click on "AI Vision Scan" tab
   - Upload a food label image
   - Click "Analyze with AI Vision"
   - Get instant health insights!

---

## 💻 Option 2: Run Locally

### Prerequisites
- Any modern web browser
- (Optional) Python or Node.js for local server

### Steps

1. **Download the Code**
   ```bash
   # Clone repository
   git clone https://github.com/your-username/nutriscan-pro.git
   
   # Or download ZIP from GitHub
   ```

2. **Open the File**
   
   **Method A: Local Server (Recommended)**
   ```bash
   # Navigate to folder
   cd nutriscan-pro
   
   # Start server with Python
   python -m http.server 8000
   
   # OR with Node.js
   npx http-server
   
   # Open browser
   http://localhost:8000
   ```
   
   **Method B: Direct Open (Limited Features)**
   - Double-click `index.html`
   - Note: Camera features require HTTPS

3. **Start Using**
   - App opens in your browser
   - All features ready to use!

---

## 📱 Option 3: Deploy Your Own

### GitHub Pages (Free!)

1. **Fork Repository**
   - Click "Fork" on GitHub
   - Wait for fork to complete

2. **Enable GitHub Pages**
   - Go to Settings → Pages
   - Source: `main` branch
   - Click Save

3. **Access Your Site**
   ```
   https://your-username.github.io/nutriscan-pro/
   ```

**Full deployment guide:** See [DEPLOYMENT.md](DEPLOYMENT.md)

---

## 🎯 First-Time Usage

### AI Vision Scan (Recommended)

1. **Prepare Your Image**
   - Take a clear photo of any food label
   - Ensure ingredients are readable
   - Good lighting helps!

2. **Upload & Analyze**
   - Click "AI Vision Scan" tab
   - Drag & drop your image OR click to browse
   - Click "Analyze with AI Vision"
   - Wait 2-5 seconds

3. **View Results**
   - Health Score (0-100)
   - Grade (A-F)
   - Harmful ingredients highlighted
   - Healthier alternatives suggested

### Barcode Scanner

1. **Requirements**
   - HTTPS connection (GitHub Pages ✅)
   - Device camera
   - Camera permission

2. **Scan**
   - Click "Barcode" tab
   - Click "Start Barcode Scanner"
   - Allow camera access
   - Point at barcode
   - Auto-detects and analyzes!

### Manual Entry

1. **Enter Details**
   - Click "Manual" tab
   - Fill in product name
   - Add package size
   - Paste ingredients list

2. **Analyze**
   - Click "Analyze Food Product"
   - Get instant results!

---

## 💡 Tips for Best Results

### Image Quality
- ✅ Clear, focused image
- ✅ Good lighting
- ✅ Ingredients section visible
- ✅ Flat, unwrinkled label
- ❌ Blurry photos
- ❌ Dark/shadowy images
- ❌ Partial labels

### Understanding Results

**Health Score:**
- 80-100: Excellent (Green)
- 60-79: Good (Blue)
- 40-59: Moderate (Orange)
- 20-39: Poor (Red)
- 0-19: Avoid (Dark Red)

**Ingredient Warnings:**
- 🔴 Red = Dangerous (avoid)
- 🟡 Yellow = Caution (limit)
- 🟢 Green = Safe (okay)

**Nutritional Context:**
- WHO guidelines used
- Per 100g standardization
- Daily intake percentages

---

## 🐛 Troubleshooting

### AI Vision Not Working
```
❌ Problem: Error analyzing image
✅ Solution: 
   - Check internet connection
   - Try clearer image
   - Ensure label is in English (for now)
   - Check browser console for errors
```

### Camera Not Working
```
❌ Problem: Camera won't start
✅ Solution:
   - Use HTTPS (not HTTP)
   - Allow camera permission
   - Close other apps using camera
   - Try different browser
```

### Slow Performance
```
❌ Problem: App loading slowly
✅ Solution:
   - Clear browser cache
   - Check internet speed
   - Try different browser
   - Use local server instead
```

---

## 📚 Learn More

- **Full Documentation:** [README.md](README.md)
- **Deployment Guide:** [DEPLOYMENT.md](DEPLOYMENT.md)
- **Contributing:** [CONTRIBUTING.md](CONTRIBUTING.md)
- **Report Issues:** [GitHub Issues](https://github.com/your-username/nutriscan-pro/issues)

---

## 🎓 Tutorial Videos

*(Coming Soon)*
- Getting Started with NutriScan Pro
- How to Read Health Scores
- Understanding Ingredient Warnings
- Best Practices for Image Upload

---

## ❓ FAQs

**Q: Is this free to use?**
A: Yes! Completely free and open-source.

**Q: Do I need an API key?**
A: No! Works directly in your browser.

**Q: Does it work offline?**
A: AI Vision requires internet. Cached products work offline.

**Q: What languages are supported?**
A: Currently English. More languages coming soon!

**Q: Is my data stored anywhere?**
A: Only in your browser's LocalStorage. No server storage.

**Q: Can I use this for commercial purposes?**
A: Yes! MIT License allows commercial use.

---

## 🤝 Need Help?

- 💬 [GitHub Discussions](https://github.com/your-username/nutriscan-pro/discussions)
- 🐛 [Report Bug](https://github.com/your-username/nutriscan-pro/issues/new?template=bug_report.md)
- ✨ [Request Feature](https://github.com/your-username/nutriscan-pro/issues/new?template=feature_request.md)

---

## 🌟 What's Next?

After getting started:
1. ⭐ Star the repository if you find it useful
2. 🍴 Fork and customize for your needs
3. 🤝 Contribute improvements
4. 📢 Share with friends and family
5. 💬 Join discussions and community

---

**Happy Scanning! 🎉**

*Making healthier food choices, one scan at a time.* 🥗
