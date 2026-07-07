# Hugo Layout Tree Scanner Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Build a Hugo-compatible frontend layout scanner that outputs an ASCII tree combining template dependency and HTML layout structure.

**Architecture:** Add a standalone TypeScript CLI that scans Hugo `layouts/` plus theme fallback, extracts template dependency links (`partial`, `template`, `block`, `define`, shortcode), parses HTML fragments with template placeholders, then renders a merged tree in ASCII/JSON.

**Tech Stack:** Node.js, TypeScript, `glob`, `node-html-parser` (or equivalent lightweight HTML parser), filesystem path utilities.

---

### Task 1: Scaffold script location and CLI contract

**Files:**
- Create: `tools/hugo-layout-tree.ts`
- Modify: `package.json` (only if script aliases are added)

**Step 1: Write the failing test (smoke contract)**
Create a command contract checklist in comments at top of script:
- expects flags: `--entry --focus --scope --layoutOnly --maxDepth --json`
- prints help with `--help`

**Step 2: Run script to verify failure baseline**
Run: `node tools/hugo-layout-tree.ts --help`
Expected: FAIL (file missing or TS not executable yet)

**Step 3: Write minimal implementation**
- Add shebang and argument parsing scaffold.
- Implement `--help` output and basic option normalization.

**Step 4: Run script to verify it passes baseline**
Run: `node tools/hugo-layout-tree.ts --help`
Expected: PASS, usage text shown.

**Step 5: Commit**
```bash
git add tools/hugo-layout-tree.ts
git commit -m "feat: scaffold hugo layout tree cli"
```

### Task 2: Implement file discovery with theme fallback precedence

**Files:**
- Modify: `tools/hugo-layout-tree.ts`

**Step 1: Write failing test (manual assertion run)**
Run: `node tools/hugo-layout-tree.ts --json`
Expected: FAIL or empty because discovery not implemented.

**Step 2: Implement minimal discovery**
- Collect local templates under `layouts/**`.
- Collect theme templates under `themes/*/layouts/**`.
- Build resolver where local path wins over same relative theme path.

**Step 3: Verify discovery output**
Run: `node tools/hugo-layout-tree.ts --json`
Expected: JSON includes discovered entries and resolved active file map.

**Step 4: Commit**
```bash
git add tools/hugo-layout-tree.ts
git commit -m "feat: add hugo layout file discovery and override resolution"
```

### Task 3: Add template dependency extraction

**Files:**
- Modify: `tools/hugo-layout-tree.ts`

**Step 1: Write failing check**
Run: `node tools/hugo-layout-tree.ts --entry _default/single.html --json`
Expected: dependency list missing `partials/*` links.

**Step 2: Implement parser rules**
- Add regex/token rules for:
  - `partial`
  - `template`
  - `block` / `define`
  - shortcode calls
- Resolve targets to local/theme active file.
- Mark unresolved as `missing`.

**Step 3: Verify dependency graph**
Run: `node tools/hugo-layout-tree.ts --entry _default/single.html --json`
Expected: JSON graph edges contain partial/template/shortcode references.

**Step 4: Commit**
```bash
git add tools/hugo-layout-tree.ts
git commit -m "feat: extract hugo template dependency graph"
```

### Task 4: Add HTML structure extraction with dynamic markers

**Files:**
- Modify: `tools/hugo-layout-tree.ts`

**Step 1: Write failing check**
Run: `node tools/hugo-layout-tree.ts --entry _default/single.html`
Expected: only file nodes, no HTML tags/class summaries.

**Step 2: Implement HTML pass**
- Preprocess directives (`{{ ... }}`) into safe placeholders.
- Parse HTML nodes.
- Capture tag name, class, id.
- Convert template control directives to `dynamic` nodes (`branch`, `loop`, `dynamic`).

**Step 3: Verify structure output**
Run: `node tools/hugo-layout-tree.ts --entry _default/single.html`
Expected: ASCII tree includes HTML tag nodes and class/id snippets.

**Step 4: Commit**
```bash
git add tools/hugo-layout-tree.ts
git commit -m "feat: parse html structure with hugo dynamic markers"
```

### Task 5: Add renderer features (focus/scope/layoutOnly/maxDepth/json)

**Files:**
- Modify: `tools/hugo-layout-tree.ts`

**Step 1: Write failing checks**
Run:
- `node tools/hugo-layout-tree.ts --focus header --scope up`
- `node tools/hugo-layout-tree.ts --layoutOnly`
- `node tools/hugo-layout-tree.ts --maxDepth 3`
Expected: flags ignored or incorrect behavior.

**Step 2: Implement output controls**
- `--focus`: target file/node pruning
- `--scope`: `up | down | full`
- `--layoutOnly`: filter class tokens by layout dictionary
- `--maxDepth`: hard cut with summary note
- `--json`: machine-readable node graph

**Step 3: Verify with real project commands**
Run:
- `node tools/hugo-layout-tree.ts --entry _default/single.html`
- `node tools/hugo-layout-tree.ts --entry _default/single.html --layoutOnly`
- `node tools/hugo-layout-tree.ts --entry _default/single.html --json`
Expected: stable tree and valid JSON.

**Step 4: Commit**
```bash
git add tools/hugo-layout-tree.ts
git commit -m "feat: add output modes and tree focus controls"
```

### Task 6: Documentation and sample outputs

**Files:**
- Create: `docs/hugo-layout-tree-usage.md`
- Modify: `CONTINUITY.md` (optional short note)

**Step 1: Write docs draft**
- Purpose
- CLI examples
- Known limitations
- Troubleshooting

**Step 2: Generate sample output for docs**
Run: `node tools/hugo-layout-tree.ts --entry _default/single.html --layoutOnly`
Expected: output captured in docs snippet.

**Step 3: Final verification**
Run:
- `node tools/hugo-layout-tree.ts --help`
- `node tools/hugo-layout-tree.ts --entry _default/list.html`
- `node tools/hugo-layout-tree.ts --entry index.html`
Expected: no crash, deterministic output.

**Step 4: Commit**
```bash
git add docs/hugo-layout-tree-usage.md CONTINUITY.md
git commit -m "docs: add usage guide for hugo layout tree scanner"
```
