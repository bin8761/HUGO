# Hugo Layout Tree Usage

Script: `tools/hugo-layout-tree.js`

## Quick Start

```bash
node tools/hugo-layout-tree.js --entry _default/single.html
```

```bash
# Scan all default entries in one run
node tools/hugo-layout-tree.js --all --layoutOnly --maxDepth 4
```

```bash
# Xuấn file JSON
node tools/hugo-layout-tree.js --all --json > all-ui-tree.json
```


```bash
# Xuất file ASCII
node tools/hugo-layout-tree.js --all --layoutOnly --maxDepth 4 > all-ui-tree.txt
```


## Useful Commands

```bash
# Layout-focused output
node tools/hugo-layout-tree.js --entry index.html --layoutOnly --maxDepth 4

# Focus a specific node/path
node tools/hugo-layout-tree.js --entry _default/single.html --focus footer --scope down

# JSON output for feeding to AI
node tools/hugo-layout-tree.js --entry _default/single.html --json > ui-tree.json
```

## Flags

- `--entry <path>`: entry template under active Hugo layouts (local override first, then theme fallback)
- `--all`: scan all default entries (`_default/single.html`, `_default/list.html`, `index.html`, `404.html`)
- `--focus <text>`: find node by name/path substring
- `--scope up|down|full`: focused output scope
- `--layoutOnly`: filter classes to layout-centric signals
- `--maxDepth <n>`: trim deep branches
- `--json`: output structured JSON

## Notes

- Active layout resolution priority: `layouts/**` > `themes/*/layouts/**`.
- Dependency extraction supports: `partial`, `template`, `block`, shortcode calls.
- Dynamic template directives are emitted as `[dynamic]` nodes.
