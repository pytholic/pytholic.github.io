# Personal Portfolio Website

A simple, maintainable personal portfolio website built with Jekyll and Tailwind CSS (CDN).

## Structure

```
portfolio/
├── index.html          # Home page
├── works.html          # Projects showcase (hand-maintained list)
├── posts.html          # Technical posts (hand-maintained list)
├── notes.html          # Personal notes listing (auto-generated from _notes/)
├── uses.html           # Gear and setup
├── works/<slug>/       # One folder per project
├── posts/<slug>/       # One folder per technical post
├── _notes/             # Markdown notes (philosophy, science, etc.) — auto-listed on notes.html
├── _layouts/           # Jekyll layouts (default, post, note)
├── _includes/          # Shared nav.html / footer.html
├── _config.yml         # Jekyll config
└── images/
    ├── dp.jpg          # Profile photo
    ├── works/          # Project thumbnails
    └── uses/           # Gear photos
```

## Features

- **Jekyll-powered**: shared nav/footer/layout live in one place (`_includes/`, `_layouts/`), not copy-pasted per page
- **Tailwind CSS (CDN)**: no CSS build step
- **Markdown notes**: write a `.md` file in `_notes/`, it's automatically listed on `/notes.html`
- **Dark mode**: theme toggle, persisted via localStorage
- **Responsive**: Mobile-first design

## Local Testing

Requires Ruby + Jekyll (see [Setup](#setup) below if not installed yet).

```bash
export PATH="/opt/homebrew/opt/ruby/bin:$PATH"   # only needed once per terminal session (already in ~/.zshrc)
bundle exec jekyll serve --livereload
```

Then visit `http://localhost:4000`. `--livereload` auto-refreshes the browser on save; drop it to refresh manually. Stop with `Ctrl+C`.

### Setup (one-time)

```bash
brew install ruby
export PATH="/opt/homebrew/opt/ruby/bin:$PATH"
bundle config set --local path 'vendor/bundle'
bundle install
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

### Add a new note

1. Create a Markdown file in `_notes/`, e.g. `_notes/my-new-note.md`
2. Add front matter at the top:
   ```yaml
   ---
   title: "Your Note Title"
   date: 2026-08-09
   tags: [Philosophy, Books]
   ---
   ```
3. Write the body in Markdown below the front matter
4. Save — it appears on `/notes.html` automatically (newest first), no other file to edit

### Add a new project to Works, or a new technical post

These aren't Markdown-driven — copy an existing folder as a starting point:

```bash
cp -r works/some-existing-project works/my-new-project
# or
cp -r posts/some-existing-post posts/my-new-post
```

1. Edit `<slug>/index.html`: keep the `---\ntitle: "..."\n---` front matter block at the top, replace the content below it
2. Add a card linking to it in `works.html` or `posts.html` (these lists are still hand-maintained)
3. For a Works project, copy its thumbnail/screenshots to `images/works/` or into the project folder itself, matching existing projects

### Update Bio

Edit `index.html` and modify the Bio section with new entries.

## Customization

### Shared nav, footer, and page shell

- **Nav links / active-tab logic** → `_includes/nav.html` (one edit applies to every page)
- **Footer / copyright / license line** → `_includes/footer.html`
- **Overall page shell** (`<head>`, fonts, Tailwind config, colors) → `_layouts/default.html`
- **Post-style header** (title/date/tags block used by posts and notes) → `_layouts/post.html` / `_layouts/note.html`

### Change Colors

Edit the Tailwind config in `_layouts/default.html`:

```javascript
tailwind.config = {
    theme: {
        extend: {
            colors: {
                theme: {
                    bg: 'var(--color-bg)',
                    accent: 'var(--color-accent)',
                    // ...see _layouts/default.html for the full list
                }
            }
        }
    }
}
```

The actual color values live in `theme.css` as CSS variables.

### Update Social Links

Edit the social links section in `index.html` with your own URLs.

## Tech Stack

- **Jekyll**: Static site generator (layouts, includes, Markdown collections)
- **Tailwind CSS (CDN)**: Utility-first styling
- **GitHub Pages**: Free hosting, builds Jekyll automatically on push

## License

MIT License - feel free to use this template for your own portfolio!

## Author

Haseeb Raja
- GitHub: [@pytholic](https://github.com/pytholic)
- LinkedIn: [@pytholic](https://www.linkedin.com/in/pytholic/)
- Email: rajahaseeb147@gmail.com
