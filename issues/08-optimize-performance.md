# Optimize performance: Replace Tailwind CDN with compiled CSS

## Issue
The presentation loads the entire Tailwind CSS library (3.4 MB) from a CDN on every page load, even though it only uses a small subset of classes.

```html
<!-- Current: Loads full Tailwind library -->
<script src="https://cdn.tailwindcss.com"></script>
```

## Performance Impact
- **3.4 MB** initial download (gzipped: ~500KB)
- Blocking JavaScript that parses and generates CSS at runtime
- Slower initial render
- Unnecessary for a single static HTML file

## Suggested Solution

### Option 1: Inline Critical CSS (Recommended)
Extract only the used CSS classes and inline them:

```bash
# Use Tailwind CLI to generate minimal CSS
npx tailwindcss -o styles.css --minify
```

Then inline in the HTML or link to a small external file.

**Result**: ~5-10 KB instead of 3.4 MB

### Option 2: Use Tailwind Play CDN with JIT
Use the JIT mode which is more efficient:
```html
<script src="https://cdn.tailwindcss.com?plugins=forms,typography"></script>
<script>
  tailwind.config = {
    theme: { extend: {} }
  }
</script>
```

### Option 3: Pre-build CSS
1. Create `tailwind.config.js`
2. Build production CSS: `npx tailwindcss -i input.css -o output.css --minify`
3. Link to `output.css` (~10-20 KB)

## Impact
- **50-100x smaller** file size
- Faster initial load
- No JavaScript blocking
- Better for offline use

## Benchmark
- Current: ~3.5 MB total (HTML + Tailwind CDN)
- Optimized: ~35 KB total (HTML + inline CSS)

**100x improvement** in file size!

## Priority
**Medium** - Significant performance improvement
