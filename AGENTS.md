# AGENTS.md

VNote documentation site: **MkDocs Material**, bilingual (English + `简体中文`), deployed to GitHub Pages at custom domain `docs.vnote.fun`.

## Commands (Windows / pwsh)
Use the venv interpreter directly — the venv is not auto-activated:
- Serve w/ live reload: `.\.venv\Scripts\mkdocs.exe serve`
- Validate before pushing: `.\.venv\Scripts\mkdocs.exe build --strict` (CI/PR gate — must be 0 warnings)
- Recreate env: `python -m venv .venv; .\.venv\Scripts\python.exe -m pip install -r requirements.txt`

## i18n structure (mkdocs-static-i18n, `suffix` mode)
- English is the default: `foo.md`. Chinese is a sibling `foo.zh.md`; ZH serves under `/zh/`.
- Every new English page should get a `.zh.md` counterpart (missing translations fall back to English).
- Nav labels are translated via `plugins.i18n.languages[zh].nav_translations` in `mkdocs.yml` — add a mapping there for any new nav entry, not in the nav tree.

## Authoring conventions
- Do NOT hard-wrap prose in any language. Keep each paragraph, list item, and card body on a single physical line. In Markdown a newline between two CJK characters renders as a visible space (e.g. `都是 纯文本`), so wrapped Chinese text shows spurious spaces; wrapping English is also disallowed for consistency.
- Between Chinese and adjacent Latin words or numbers, keep a single space (e.g. `基于 Qt`, `Markdown 体验`), matching the `nav_translations` style in `mkdocs.yml`.

## Gotchas
- Do NOT enable `theme.features: navigation.instant` — it breaks the i18n language switcher and fails `--strict`.
- `docs/CNAME` (`docs.vnote.fun`) must be preserved; it ships to the Pages deploy.
- The Material console banner about "MkDocs 2.0" is upstream noise, not an error.

## Repo conventions (from global AGENTS.md)
- Prefer PowerShell over Bash. Only commit when explicitly asked; use a night-time author/commit date.
