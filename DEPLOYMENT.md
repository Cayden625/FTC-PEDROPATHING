# Deployment Instructions

## Pedro Pathing Visualizer

This is a clone of the Pedro Pathing Visualizer with all functionality intact.

### Live Development Server

The application is currently running at: **https://5173-iq5ear1ljz2mwxwazxmry-5c13a017.sandbox.novita.ai**

### GitHub Repository

Repository: **https://github.com/Cayden625/FTC-PEDROPATHING**

---

## Deploying to GitHub Pages

To deploy this application to GitHub Pages, follow these steps:

### Step 1: Enable GitHub Pages

1. Go to your repository: https://github.com/Cayden625/FTC-PEDROPATHING
2. Click on **Settings** → **Pages** (in the left sidebar)
3. Under "Build and deployment":
   - **Source**: Select "GitHub Actions"

### Step 2: Add the Deployment Workflow (Manual)

Since the automated push of workflows is restricted, you'll need to add the workflow file manually:

1. Go to your repository on GitHub
2. Navigate to `.github/workflows/` directory (create if it doesn't exist)
3. Create a new file called `deploy.yml`
4. Copy the following content:

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

5. Commit the file directly to the main branch

### Step 3: Trigger Deployment

Once the workflow file is added:
1. The deployment will automatically trigger
2. Wait for the GitHub Action to complete (check the "Actions" tab)
3. Your site will be live at: `https://cayden625.github.io/FTC-PEDROPATHING/`

---

## Alternative Deployment Options

### Option 1: Deploy Pre-built Files

The production files are already built in the `dist/` folder. You can:

1. Copy the `dist/` folder contents
2. Upload to any static hosting service:
   - **Netlify**: Drag and drop the dist folder
   - **Vercel**: Import the repository
   - **Cloudflare Pages**: Connect your repository
   - **Firebase Hosting**: Use `firebase deploy`

### Option 2: Local Development

To run locally:

```bash
# Install dependencies
npm install

# Run development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

---

## Features Included

This deployment includes all features from the original Pedro Pathing Visualizer:

✅ Interactive path planning with Bézier curves
✅ Robot position and heading visualization
✅ Control points editing
✅ Path optimization
✅ Wait time insertion
✅ Field image customization
✅ Export/Import path configurations
✅ Code generation for Java/Kotlin
✅ Real-time path preview
✅ Grid snapping and alignment tools
✅ Dark/Light mode support

---

## Credits

- Original Project: [Pedro Pathing Visualizer](https://github.com/Pedro-Pathing/Visualizer)
- Developed by: FTC Team #16166 Watt's Up
- Enhanced by: Matthew Allen ([PedroPathingVisualizer](https://github.com/Mallen220/PedroPathingVisualizer))
- License: BSD 3-Clause License

---

## Support

For issues or questions about the Pedro Pathing system:
- Visit: https://pedropathing.com/
- Discord: https://discord.gg/2GfC4qBP5s
- GitHub Issues: https://github.com/Pedro-Pathing/Visualizer/issues
