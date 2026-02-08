# Patch Nova to Match GitHub

Patches Nova.app's Markdown preview to exactly match GitHub's rendering with:

- **GitHub Markdown Alerts** (`> [!NOTE]`, `> [!TIP]`, etc.)
- **Syntax Highlighting** (using starry-night - GitHub's Prettylights)
- **Mermaid Diagrams**

## Installation

```bash
sudo swift patch-nova.swift install   # Install all extensions
swift patch-nova.swift status          # Check installation status
sudo swift patch-nova.swift restore    # Restore from backups
```

## How It Works

1. **Local Bundles** - JS and CSS stored in `lib/` directory
2. **Auto-Updates** - GitHub Actions rebuilds bundles weekly from upstream
3. **Embedded** - All assets embedded as base64 into Nova's runtime
4. **GitHub Exact** - Uses same Prettylights library as GitHub.com

## Structure

```
lib/                           # Compiled bundles (1.3MB total)
├── starry-night-bundle.js    # Common language grammars
└── starry-night.css          # GitHub's exact CSS

scripts/                       # Build tools
├── build-bundle.mjs          # esbuild bundler
└── package.json              # Dependencies

.github/workflows/             # Auto-update workflow
```

## Features

✅ Fully local - no CDN dependencies at runtime
✅ Auto-updates weekly from `@wooorm/starry-night`
✅ Common grammars only (JS, TS, Python, Go, etc.)
✅ GitHub exact colors for light/dark modes

## License

MIT
