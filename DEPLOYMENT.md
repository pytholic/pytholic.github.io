# Quick Deployment Guide

## Option 1: GitHub Pages (Recommended)

### Step 1: Create GitHub Repository
1. Go to https://github.com/new
2. Repository name: `pytholic.github.io`
3. Set to Public
4. Don't initialize with README
5. Click "Create repository"

### Step 2: Push Your Code
```bash
# Initialize git (if not already done)
git init

# Add all files
git add .

# Create initial commit
git commit -m "Initial commit: Simple portfolio website"

# Set main branch
git branch -M main

# Add remote
git remote add origin https://github.com/pytholic/pytholic.github.io.git

# Push to GitHub
git push -u origin main
```

### Step 3: Enable GitHub Pages
1. Go to your repository on GitHub
2. Click "Settings"
3. Scroll down to "Pages" in the left sidebar
4. Under "Source", select branch: `main`
5. Select folder: `/ (root)`
6. Click "Save"

### Step 4: Wait and Visit
- GitHub Pages will build your site (takes 1-2 minutes)
- Your site will be live at: `https://pytholic.github.io`

---

## Option 2: Custom Domain (Optional)

If you want to use a custom domain like `rajahaseeb.com`:

1. Buy a domain from any registrar (Namecheap, Google Domains, etc.)

2. Add a `CNAME` file in your repository root:
```bash
echo "yourdomain.com" > CNAME
git add CNAME
git commit -m "Add custom domain"
git push
```

3. Configure DNS at your domain registrar:
   - Add an `A` record pointing to GitHub Pages IPs:
     - `185.199.108.153`
     - `185.199.109.153`
     - `185.199.110.153`
     - `185.199.111.153`
   - Or add a `CNAME` record pointing to `pytholic.github.io`

4. Update GitHub Pages settings with your custom domain

---

## Testing Locally

Before deploying, test your site locally:

```bash
# Option 1: Python
python3 -m http.server 8000

# Option 2: Node.js
npx http-server -p 8000

# Then visit: http://localhost:8000
```

---

## Quick Updates

After making changes:

```bash
git add .
git commit -m "Update: describe your changes"
git push
```

Site updates automatically within 1-2 minutes!

---

## Troubleshooting

### Site not loading?
- Check GitHub Actions tab for build errors
- Ensure GitHub Pages is enabled in Settings
- Wait 5 minutes for DNS propagation

### Images not showing?
- Check file paths are correct (case-sensitive!)
- Ensure images are in the `images/` folder
- Verify images are committed to git

### CSS not working?
- Tailwind CDN should load automatically
- Check browser console for errors
- Try hard refresh: Cmd+Shift+R (Mac) or Ctrl+Shift+R (Windows)

---

## Need Help?

- GitHub Pages Docs: https://docs.github.com/en/pages
- Tailwind CSS Docs: https://tailwindcss.com/docs
- Contact: rajahaseeb147@gmail.com
