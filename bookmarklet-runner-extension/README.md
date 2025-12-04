# Bookmarklet Runner Chrome Extension

Run bookmarklets from the [oaustegard/bookmarklets](https://github.com/oaustegard/bookmarklets) repository directly without adding them to your bookmarks bar.

## Features

- **One-click execution**: Run any bookmarklet on the current page instantly
- **Domain filtering**: Bookmarklets with `@domains` metadata only appear on matching sites, and are hoisted to the top of the list
- **Auto-grouping**: Bookmarklets with common prefixes (e.g., `bsky_*`) are grouped into collapsible sections (collapsed by default)
- **Search**: Filter bookmarklets by name, description, or filename
- **README links**: Bookmarklets with companion README files show a 📖 link
- **Keyboard navigation**: 
  - `Alt+B` opens the extension
  - `↓` from search moves to first item
  - `↑/↓` navigates the list (including group headers)
  - `←/→` collapses/expands groups
  - `Enter` executes bookmarklet or toggles group
  - `Esc` returns focus to search
- **Persistent state**: Manually expanded groups stay expanded between sessions
- **Auto-caching**: Fetches from GitHub once per hour, cached locally

## Bookmarklet Metadata

The extension parses optional metadata from bookmarklet files:

```javascript
javascript:
/* @title: My Bookmarklet Name */
/* @description: What this bookmarklet does */
/* @domains: example.com, sub.example.com */
(function() {
  /* actual code */
})();
```

All `@` tags are optional:
- **@title**: Display name (defaults to filename with underscores replaced by spaces)
- **@description**: Brief description (defaults to first comment or "Run {title}")
- **@domains**: Comma-separated list of domains. When specified, the bookmarklet **only appears** on matching sites. Bookmarklets without `@domains` appear everywhere.

## README Files

Companion README files are automatically linked if they follow the naming convention:
- `bookmarklet_name_README.md` or `bookmarklet_name.README.md`

For example, `bsky_advanced_search.js` pairs with `bsky_advanced_search_README.md`.

## Installation

### From source (Developer Mode)

1. Download/clone this extension folder
2. Open Chrome and navigate to `chrome://extensions/`
3. Enable **Developer mode** (toggle in top-right)
4. Click **Load unpacked**
5. Select the `bookmarklet-runner-extension` folder
6. The extension icon will appear in your toolbar

### Set keyboard shortcut (optional)

1. Go to `chrome://extensions/shortcuts`
2. Find "Bookmarklet Runner" 
3. Set your preferred shortcut (default: `Alt+B`)

### Pin the extension (recommended)

1. Click the puzzle piece icon in Chrome toolbar
2. Click the pin icon next to "Bookmarklet Runner"

## Usage

1. Navigate to any webpage
2. Press `Alt+B` or click the extension icon
3. Search or scroll to find your bookmarklet
4. Click or press Enter to execute

## Limitations

- Cannot run on `chrome://`, `chrome-extension://`, or `edge://` pages (browser restriction)
- Some bookmarklets may fail on pages with strict Content Security Policy (CSP)
- Requires internet connection to initially fetch bookmarklets (cached afterward)

## Customization

To use with a different bookmarklets repository, edit `popup.js`:

```javascript
const REPO_OWNER = 'your-username';
const REPO_NAME = 'your-repo';
```

## License

MIT
