## Local Development Server

When serving local HTML files for browser testing or inspection, always use Python's built-in HTTP server instead of Live Server or any VS Code extension.

Start it with:
```bash
python3 -m http.server 8080
```

Serve from the project root, then access files via `http://localhost:8080/path/to/file.html`. Never use `file://` protocol or assume any VS Code extension is running.