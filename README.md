# Pedro Pathing Visualizer - Complete Deployment

## ✅ Project Successfully Deployed!

This is a complete, fully-functional clone of the Pedro Pathing Visualizer for FTC robotics path planning.

---

## 🔗 Quick Links

- **GitHub Repository**: https://github.com/Cayden625/FTC-PEDROPATHING
- **Live Demo (Temporary)**: https://5173-iq5ear1ljz2mwxwazxmry-5c13a017.sandbox.novita.ai
- **Original Project**: https://github.com/Pedro-Pathing/Visualizer
- **Official Website**: https://pedropathing.com/

---

## 📦 What's Included

All original features are preserved:

- ✅ **Interactive Path Planning** - Visual Bézier curve path creation
- ✅ **Robot Position Control** - Set starting position, heading, and waypoints
- ✅ **Control Points** - Add and adjust path control points
- ✅ **Path Optimization** - Automatic path smoothing and optimization
- ✅ **Wait Commands** - Insert timed waits at any point
- ✅ **Field Customization** - Use custom field images
- ✅ **Code Export** - Generate Java/Kotlin code for FTC robots
- ✅ **Import/Export** - Save and load path configurations
- ✅ **Grid System** - Snap to grid for precise alignment
- ✅ **Theme Support** - Dark and light mode
- ✅ **Real-time Preview** - See path changes instantly

---

## 🚀 Deployment to GitHub Pages

To make this website publicly accessible via GitHub Pages:

### Step 1: Enable GitHub Pages
1. Go to: https://github.com/Cayden625/FTC-PEDROPATHING/settings/pages
2. Under "Build and deployment":
   - **Source**: Select "GitHub Actions"

### Step 2: Add Deployment Workflow
1. In your repository, click "Add file" → "Create new file"
2. Name it: `.github/workflows/deploy.yml`
3. Paste this content:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main ]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      
      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'
      
      - name: Install dependencies
        run: npm ci
      
      - name: Build
        run: npm run build
      
      - name: Setup Pages
        uses: actions/configure-pages@v4
      
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: './dist'

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

4. Commit directly to main branch
5. Wait 2-3 minutes for deployment
6. Your site will be live at: **https://cayden625.github.io/FTC-PEDROPATHING/**

---

## 💻 Local Development

### Prerequisites
- Node.js 18+ installed
- npm or yarn package manager

### Commands

```bash
# Install dependencies
npm install

# Start development server (runs on http://localhost:5173)
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview

# Type checking
npm run check
```

---

## 🌐 Alternative Deployment Options

### Netlify (Easiest)
1. Go to https://app.netlify.com/
2. Drag and drop the `dist/` folder
3. Done! Your site is live

### Vercel
1. Import repository from GitHub
2. Vercel auto-detects Vite config
3. Deploy with one click

### Cloudflare Pages
1. Connect your GitHub account
2. Select the FTC-PEDROPATHING repository
3. Build command: `npm run build`
4. Output directory: `dist`

---

## 📋 Project Structure

```
pedro-pathing-visualizer/
├── src/                  # Source code
│   ├── lib/             # Components and utilities
│   ├── app.scss         # Global styles
│   └── main.ts          # Entry point
├── public/              # Static assets
│   ├── fields/          # FTC field images
│   └── fonts/           # Custom fonts
├── dist/                # Built production files
├── index.html           # HTML template
├── vite.config.ts       # Vite configuration
├── tailwind.config.js   # Tailwind CSS config
└── package.json         # Dependencies
```

---

## 🛠️ Technology Stack

- **Framework**: Svelte 4
- **Build Tool**: Vite 5
- **Language**: TypeScript
- **Styling**: Tailwind CSS + SASS
- **Graphics**: D3.js + Two.js
- **UI**: Custom Svelte components

---

## 📝 License

BSD 3-Clause License (same as original project)

---

## 🙏 Credits

- **Original Development**: FTC Team #16166 Watt's Up
- **Enhanced Version**: Matthew Allen
- **Maintained By**: Pedro Pathing Team

---

## 📞 Support & Resources

- **Documentation**: https://pedropathing.com/docs
- **Discord Community**: https://discord.gg/2GfC4qBP5s
- **Report Issues**: https://github.com/Pedro-Pathing/Visualizer/issues
- **FTC Resources**: https://www.firstinspires.org/robotics/ftc

---

## ⚡ Quick Start Guide

1. **Clone this repository**
   ```bash
   git clone https://github.com/Cayden625/FTC-PEDROPATHING.git
   cd FTC-PEDROPATHING
   ```

2. **Install and run**
   ```bash
   npm install
   npm run dev
   ```

3. **Open browser**
   - Navigate to http://localhost:5173
   - Start creating paths!

---

**Deployment Date**: January 20, 2026
**Status**: ✅ Complete and Functional
