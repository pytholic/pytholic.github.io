# Personal Portfolio Website

A simple, maintainable personal portfolio website built with plain HTML and Tailwind CSS (CDN).

## Structure

```
portfolio/
├── index.html          # Home page
├── works.html          # Projects showcase
├── blog.html           # Blog posts (coming soon)
├── uses.html           # Gear and setup
└── images/
    ├── dp.jpg          # Profile photo
    ├── works/          # Project thumbnails
    └── uses/           # Gear photos
```

## Features

- **No build step**: Pure HTML with Tailwind CSS via CDN
- **Dark mode**: Modern dark theme with blue accents
- **Responsive**: Mobile-first design
- **Fast loading**: Minimal dependencies
- **Easy to maintain**: Direct file editing

## Local Testing

Simply open `index.html` in your browser:

```bash
# Option 1: Direct file open
open index.html

# Option 2: Python HTTP server
python3 -m http.server 8000
# Then visit http://localhost:8000

# Option 3: Node.js HTTP server
npx http-server -p 8000
```

## Deployment to GitHub Pages

1. Create a new repository named `pytholic.github.io` on GitHub

2. Initialize git and push:
```bash
git init
git add .
git commit -m "Initial commit: Simple portfolio website"
git branch -M main
git remote add origin https://github.com/pytholic/pytholic.github.io.git
git push -u origin main
```

3. Enable GitHub Pages:
   - Go to repository Settings
   - Navigate to Pages section
   - Source: Deploy from branch `main` (root directory)
   - Click Save

4. Your site will be live at: `https://pytholic.github.io`

## Updating Content

### Add a new project to Works page

1. Copy project thumbnail to `images/works/`
2. Edit `works.html`
3. Add a new card in the appropriate section:

```html
<a href="https://github.com/pytholic/project-name" target="_blank" class="block bg-dark-card rounded-lg overflow-hidden hover:ring-2 hover:ring-dark-accent transition-all">
    <img src="images/works/project-thumb.png" alt="Project Name" class="w-full h-48 object-cover">
    <div class="p-4">
        <h3 class="font-bold text-lg mb-2">Project Name</h3>
        <p class="text-gray-400 text-sm">Brief description</p>
    </div>
</a>
```

### Add a blog post

Edit `blog.html` and uncomment/duplicate the article template:

```html
<article class="bg-dark-card rounded-lg p-6 hover:ring-2 hover:ring-dark-accent transition-all">
    <a href="https://medium.com/@username/post-slug" target="_blank" class="block">
        <h2 class="text-xl font-bold mb-2 hover:text-dark-accent">Post Title</h2>
        <p class="text-gray-400 text-sm mb-3">January 19, 2026</p>
        <p class="text-gray-300">Brief description of the blog post...</p>
    </a>
</article>
```

### Update Bio

Edit `index.html` and modify the Bio section with new entries.

## Customization

### Change Colors

Edit the Tailwind config in each HTML file's `<script>` tag:

```javascript
tailwind.config = {
    theme: {
        extend: {
            colors: {
                dark: {
                    bg: '#1a202c',      // Background color
                    card: '#2d3748',    // Card background
                    text: '#e2e8f0',    // Text color
                    accent: '#4299e1'   // Accent color (links, buttons)
                }
            }
        }
    }
}
```

### Update Social Links

Edit the social links section in `index.html` with your own URLs.

## Tech Stack

- **HTML5**: Semantic markup
- **Tailwind CSS (CDN)**: Utility-first styling
- **GitHub Pages**: Free hosting

## License

MIT License - feel free to use this template for your own portfolio!

## Author

Haseeb Raja
- GitHub: [@pytholic](https://github.com/pytholic)
- LinkedIn: [@pytholic](https://www.linkedin.com/in/pytholic/)
- Email: rajahaseeb147@gmail.com
