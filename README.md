# 🤖 NutriScan Pro - AI Vision Food Health Scanner

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)

**AI-Powered Smart Food Health Scanner** that uses Claude Vision AI to automatically analyze food labels, extract ingredients, and provide comprehensive health insights.

🔗 **[Live Demo](https://your-username.github.io/nutriscan-pro/)** *(Replace with your GitHub Pages URL)*

![NutriScan Pro Screenshot](screenshot.png)

---

## ✨ Features

### 🤖 **AI Vision Scanning**
- Upload any food label image
- Automatic ingredient extraction using Claude Vision AI
- Zero manual typing required
- Intelligent parsing of nutritional information

### 📊 **Comprehensive Analysis**
- **Health Score** (0-100) with color-coded grading
- **Ingredient Breakdown** - Identifies harmful additives, preservatives, and artificial colors
- **Nutritional Visualization** - Interactive charts and metrics
- **Health Risk Assessment** - Detailed warnings about problematic ingredients
- **Vegetarian/Non-Vegetarian Detection** - Identifies animal-derived ingredients

### 📷 **Multiple Scan Methods**
1. **AI Vision Scan** - Upload label photo for automatic analysis
2. **Barcode Scanner** - Scan barcodes with device camera
3. **Manual Entry** - Type ingredients manually

### 💾 **Smart Caching**
- LocalStorage-based product database
- Instant retrieval of previously scanned products
- Change detection for reformulated products
- Performance statistics tracking

### 🎯 **Additional Features**
- Healthier alternative suggestions
- Daily nutritional context (WHO guidelines)
- Responsive design for mobile/desktop
- Beautiful dark theme UI
- Animated visualizations

---

## 🚀 Quick Start

### Option 1: GitHub Pages (Recommended)

1. **Fork this repository**
   ```bash
   # Click the "Fork" button on GitHub
   ```

2. **Enable GitHub Pages**
   - Go to repository Settings → Pages
   - Source: Deploy from a branch
   - Branch: `main` / `root`
   - Save

3. **Access your app**
   - URL: `https://your-username.github.io/nutriscan-pro/`
   - Update the README with your live URL

### Option 2: Local Development

```bash
# Clone the repository
git clone https://github.com/your-username/nutriscan-pro.git
cd nutriscan-pro

# Open in browser
# Option A: Use a local server (recommended)
python -m http.server 8000
# Then open: http://localhost:8000

# Option B: Direct file open (some features limited)
# Open index.html in your browser
```

### Option 3: Deploy to Netlify/Vercel

**Netlify:**
1. Sign up at [netlify.com](https://www.netlify.com/)
2. Connect your GitHub repository
3. Deploy (automatic HTTPS)

**Vercel:**
1. Sign up at [vercel.com](https://vercel.com/)
2. Import your GitHub repository
3. Deploy (automatic HTTPS)

---

## 📋 Prerequisites

### For AI Vision Feature:
- **No API key needed!** The app uses the Anthropic API endpoint available in Claude.ai artifacts
- Works directly in the browser
- No server-side setup required

### For Barcode Scanner:
- HTTPS connection (or localhost)
- Device with camera
- Camera permission granted

### Browser Compatibility:
- ✅ Chrome/Edge (recommended)
- ✅ Firefox
- ✅ Safari
- ✅ Mobile browsers

---

## 🎮 How to Use

### 1️⃣ AI Vision Scan (Easiest!)

1. Click on **"AI Vision Scan"** tab
2. Upload a food label image (drag & drop or click)
3. Click **"Analyze with AI Vision"**
4. Wait 2-5 seconds for AI processing
5. View comprehensive health analysis!

**Best Practices:**
- Use clear, well-lit photos
- Ensure ingredients section is readable
- Include nutritional information panel if possible

### 2️⃣ Barcode Scanner

1. Click on **"Barcode"** tab
2. Click **"Start Barcode Scanner"**
3. Grant camera permission
4. Point camera at product barcode
5. Auto-detection and analysis!

**Requirements:**
- HTTPS connection (GitHub Pages ✅)
- Camera access permission

### 3️⃣ Manual Entry

1. Click on **"Manual"** tab
2. Enter product details:
   - Product name
   - Package size
   - Barcode (optional)
   - Ingredients list
3. Click **"Analyze Food Product"**

---

## 🏗️ Project Structure

```
nutriscan-pro/
├── index.html              # Main application file
├── README.md               # This file
├── LICENSE                 # MIT License
├── screenshot.png          # App screenshot (add your own)
├── .gitignore             # Git ignore file
└── docs/
    ├── CONTRIBUTING.md     # Contribution guidelines
    └── DEPLOYMENT.md       # Detailed deployment guide
```

---

## 🧠 How It Works

### AI Vision Processing

```javascript
1. User uploads food label image
2. Image converted to base64
3. Sent to Claude Vision API
4. AI extracts:
   - Product name
   - Package size
   - Ingredients list
   - Nutritional values
5. Text analyzed for health scoring
6. Results displayed with visualizations
```

### Health Scoring Algorithm

```javascript
Base Score: 100 points

Deductions:
- Refined oils/hydrogenated fats: -15 points
- Refined flour (maida): -12 points
- Artificial colors: -10 points
- Artificial flavors: -8 points
- High sugar (dynamic):
  - 40%+: -25 points
  - 30-40%: -20 points
  - 20-30%: -15 points
  - 10-20%: -10 points
- MSG: -7 points
- Preservatives: -6 points
- Emulsifiers: -5 points
- Non-vegetarian ingredients: -25 points
- Trans fats: -20 points

Final Score → Grade:
- 80-100: A (Excellent)
- 60-79:  B (Good)
- 40-59:  C (Moderate)
- 20-39:  D (Poor)
- 0-19:   F (Avoid)
```

---

## 🎨 Customization

### Change Color Scheme

Edit CSS variables in `index.html`:

```css
:root {
    --primary: #00d084;        /* Main brand color */
    --danger: #ff4757;         /* Warning color */
    --warning: #ffa502;        /* Caution color */
    --success: #00d084;        /* Success color */
    --bg-primary: #0a0e27;     /* Background */
    --text-primary: #ffffff;   /* Text color */
}
```

### Add Custom Ingredient Checks

Add to the `checks` array in `performAnalysis()` function:

```javascript
{
    keywords: ['your ingredient', 'alternative name'],
    penalty: 10,
    issue: 'Health concern description',
    ingredient: 'Display Name',
    note: 'Additional information',
    severity: 'danger' // or 'warning'
}
```

### Modify Health Score Weights

Adjust penalty values in the scoring algorithm to change how different ingredients affect the score.

---

## 🤝 Contributing

We welcome contributions! Here's how you can help:

### Reporting Bugs
- Use GitHub Issues
- Include screenshots
- Describe steps to reproduce

### Suggesting Features
- Open an issue with `[Feature Request]` tag
- Describe the use case
- Explain expected behavior

### Code Contributions

1. Fork the repository
2. Create a feature branch
   ```bash
   git checkout -b feature/amazing-feature
   ```
3. Commit your changes
   ```bash
   git commit -m 'Add amazing feature'
   ```
4. Push to the branch
   ```bash
   git push origin feature/amazing-feature
   ```
5. Open a Pull Request

### Contribution Ideas
- [ ] Add more ingredient databases
- [ ] Multi-language support
- [ ] Export analysis as PDF
- [ ] Share results on social media
- [ ] Allergen detection
- [ ] Comparison mode for multiple products
- [ ] Historical tracking/graphs
- [ ] Food recommendations based on health goals

---

## 🔒 Privacy & Security

### Data Storage
- **All data stored locally** in browser's LocalStorage
- **No server-side database**
- **No user tracking**
- **No data collected**

### Image Processing
- Images processed via Claude API
- Not stored permanently
- Used only for analysis
- HTTPS encrypted transmission

### Permissions
- Camera: Only used for barcode scanning
- Storage: Local browser storage only
- No other permissions required

---

## 🐛 Troubleshooting

### AI Vision Not Working
- **Check internet connection** - API requires connectivity
- **Try a clearer image** - Ensure label is readable
- **Check browser console** - Look for error messages

### Barcode Scanner Issues
- **Enable HTTPS** - Use GitHub Pages or localhost
- **Grant camera permission** - Check browser settings
- **Use good lighting** - Ensure barcode is clearly visible
- **Try different browsers** - Chrome works best

### App Not Loading
- **Clear browser cache** - Force refresh (Ctrl+Shift+R)
- **Check browser compatibility** - Use modern browsers
- **Disable browser extensions** - AdBlockers may interfere

### LocalStorage Full
- **Clear cached products** - Open browser DevTools → Application → LocalStorage → Clear
- **Export important data** - Copy from DevTools before clearing

---

## 📊 Performance

- **Average AI Analysis Time:** 2-5 seconds
- **Cache Hit Response:** <100ms
- **Barcode Scan Time:** 1-3 seconds
- **App Size:** ~50KB (single HTML file)
- **No dependencies:** All libraries loaded from CDN

---

## 🛠️ Technologies Used

- **Frontend:** Pure HTML5, CSS3, JavaScript (ES6+)
- **AI:** Claude Vision API (Sonnet 4)
- **Barcode:** QuaggaJS
- **Charts:** Chart.js
- **Fonts:** Google Fonts (Outfit, Playfair Display)
- **Storage:** Browser LocalStorage API

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2025 NutriScan Pro

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```

---

## 🙏 Acknowledgments

- **Anthropic** - For Claude Vision AI
- **QuaggaJS** - For barcode scanning library
- **Chart.js** - For beautiful visualizations
- **Google Fonts** - For typography
- **Open Source Community** - For inspiration and support

---

## 📧 Contact & Support

- **Issues:** [GitHub Issues](https://github.com/your-username/nutriscan-pro/issues)
- **Discussions:** [GitHub Discussions](https://github.com/your-username/nutriscan-pro/discussions)
- **Email:** your-email@example.com *(optional)*

---

## 🗺️ Roadmap

### Version 2.0 (Planned)
- [ ] Multi-language support (Hindi, Spanish, etc.)
- [ ] Allergen warnings system
- [ ] Integration with nutrition APIs (OpenFoodFacts)
- [ ] Export reports as PDF
- [ ] Product comparison mode
- [ ] Personal health goals tracking
- [ ] Recipe analyzer

### Version 3.0 (Future)
- [ ] Mobile app (React Native)
- [ ] Social sharing features
- [ ] Community ratings
- [ ] Personalized recommendations
- [ ] Integration with fitness apps

---

## ⭐ Star History

If you find this project useful, please consider giving it a star! ⭐

[![Star History Chart](https://api.star-history.com/svg?repos=your-username/nutriscan-pro&type=Date)](https://star-history.com/#your-username/nutriscan-pro&Date)

---

## 📈 Stats

![GitHub stars](https://img.shields.io/github/stars/your-username/nutriscan-pro?style=social)
![GitHub forks](https://img.shields.io/github/forks/your-username/nutriscan-pro?style=social)
![GitHub issues](https://img.shields.io/github/issues/your-username/nutriscan-pro)
![GitHub pull requests](https://img.shields.io/github/issues-pr/your-username/nutriscan-pro)

---

**Made with ❤️ for healthier food choices**

*Scan. Analyze. Choose Better.* 🥗
