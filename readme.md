# Documentation for Piklist

## How this site works:

### Search
- Search is based on [this tutorial](https://gist.github.com/cmod/5410eae147e4318164258742dd053993).
- The search library is [fuse.js](https://fusejs.io/)
- [Fuse search parameters](https://fusejs.io/api/options.html) are located in `var options` in `/themes/piklist-theme/static/js/fastsearch.js`, with the other search logic.
- Fuse determines search results by reading `/themes/piklist-theme/layouts/_default/index.json`
- When the `hugo` command is run, index.json is built.
- You can view the index at `https://docs.piklist.com/index.json`