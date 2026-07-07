# Hugo Layout Tree Scanner Design

**Date:** 2026-05-13  
**Project:** fcj-workshop-template  
**Status:** Approved (Option 2)

## Goal
Chuy?n script quét React component hierarchy sang script quét Hugo frontend layout ð? xu?t ASCII tree ph?c v? UI debugging và hý?ng d?n AI s?a giao di?n.

## Scope
- Quét l?p template dependency:
  - `{{ partial "..." . }}`
  - `{{ template "..." . }}`
  - `{{ block "..." . }}` / `{{ define "..." }}`
  - shortcodes (`{{< name >}}`, `{{% name %}}`)
- Quét l?p HTML structure trong m?i template/partial/shortcode:
  - tag hierarchy
  - `class`/`id`
  - layout-centric class filtering (`--layoutOnly`)
- Resolve ýu tiên override:
  - `layouts/**` ýu tiên hõn `themes/**/layouts/**`

## Chosen Approach
**Option 2: Tokenizer nh? cho Go-template + HTML parser**.

### Why
- Chính xác hõn regex thu?n v?i template l?ng nhau.
- Nh? hõn AST ð?y ð? cho Go template.
- Ð? tín hi?u cho m?c tiêu FE debugging và AI-assisted redesign.

## Non-Goals
- Không mô ph?ng runtime Hugo hoàn ch?nh.
- Không resolve toàn b? d? li?u ð?ng (`if/range/with` theo content th?c).
- Không parse CSS/SCSS selector graph ð?y ð? ? phiên b?n ð?u.

## Architecture
1. File discovery
- Input roots:
  - local: `layouts/**`
  - theme fallback: `themes/*/layouts/**`
- Entry candidates m?c ð?nh:
  - `_default/single.html`
  - `_default/list.html`
  - `index.html`
  - `404.html`

2. Template dependency extraction
- Scan token patterns cho `partial/template/block/define/shortcode`.
- Build directed graph file-to-file.
- G?n annotation `missing` và `recursive` khi c?n.

3. HTML structure extraction
- Lo?i b?/ðánh d?u template directives trý?c khi parse HTML.
- Parse HTML thành node tree (tag/class/id).
- V?i vùng template ð?ng, thêm pseudo-node: `branch`, `loop`, `dynamic`.

4. Merge output model
- Node ki?u:
  - `template` (file-level)
  - `element` (HTML tag)
  - `dynamic` (template expression/control flow)
- M?t output tree ch?a c? dependency và structure.

5. ASCII renderer
- Render format g?n v?i script c? ð? tái s? d?ng workflow prompt cho AI.
- Optional JSON output cho pipeline khác.

## CLI Proposal
- `--entry <path>`
- `--focus <name-or-file>`
- `--scope up|down|full`
- `--layoutOnly`
- `--maxDepth <n>`
- `--json`
- `--theme <name>` (optional)

## Validation Criteria
- Ch?y ðý?c trên repo hi?n t?i không crash.
- Resolve ðúng local override so v?i theme file cùng tên.
- ASCII tree hi?n th? ðý?c c?:
  - chu?i include template
  - c?u trúc tag/class chính
- Có ðánh d?u r? khi g?p recursion/missing.

## Risks & Mitigation
- Hugo template syntax ða d?ng: b?t ð?u b?ng t?p pattern ph? bi?n, log unknown tokens ð? m? r?ng d?n.
- HTML parse sai do template chen gi?a tag: thay directive b?ng placeholders an toàn trý?c parse.
- Tree quá l?n: thêm `--focus`, `--scope`, `--maxDepth` ð? ki?m soát.

## Deliverables
- Script m?i (TypeScript) phù h?p Hugo project.
- Tài li?u usage ng?n + ví d? l?nh.
- Output m?u cho `single.html` ho?c `index.html`.
