# Math & Diagrams

VNote renders mathematical formulas and several kinds of diagrams directly from your Markdown, so technical notes stay readable in the editor and beautiful in read mode. The source remains plain text: formulas use dollar delimiters and diagrams use fenced blocks.

## Math formulas

VNote uses **KaTeX** by default to typeset LaTeX math. KaTeX, its fonts, and the preview rasterizer are bundled, so reading, editor previews, and exports work offline. **Settings → Markdown Editor → Math renderer** lets you choose **KaTeX**, **MathJax**, or **Typst**. The following examples use LaTeX syntax for KaTeX/MathJax.

- **Inline** math goes between single dollar signs: `$E = mc^2$`.
- **Block** (display) math goes in a `$$ … $$` block:

```md
$$
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
$$
```

Math renders in read mode and in the editor's in-place and side-by-side previews (see [Editor Basics](editor-basics.md)).

For [encrypted notes](../managing-notes/encrypted-notes.md), authorized read and side-by-side previews use **Typst** when selected, otherwise bundled **KaTeX**. **Typst is the only supported in-place math renderer for protected notes**; this exception does not remove other protected-note restrictions or bypass unlocking and authorization.

### Typst math

Select **Typst** under **Math renderer** to use the bundled native runtime. Keep the same `$…$` and `$$…$$` delimiters, but write **Typst math syntax**, not LaTeX. Changing the renderer does not translate existing formulas. For example:

```md
Inline: $frac(a, b)$

$$
integral_a^b f(x) dif x = F(b) - F(a)
$$
```

Typst math supports in-place and live previews. Ordinary Markdown notes also support self-contained HTML/PDF exports and Cross Copy; protected-note export and copy restrictions still apply. For a complete typeset document rather than math inside Markdown, create a [native Typst note](typst.md).

### Fenced Typst blocks

A `typst` fence renders Typst markup independently of **Math renderer** — it works even when KaTeX or MathJax is selected:

````md
```typst
#set page(width: 8cm, height: 4cm, margin: 0.5cm)
= A Typst block
$ frac(a, b) $
```
````

Blocks preserve authored page sizes and multi-page output in previews, exports, and Cross Copy. Embedded Markdown blocks omit Typst's default page margin to align with surrounding content; explicit margins such as the one above are preserved. Standalone `.typst` document layouts are unchanged.

### Customizing MathJax {#customizing-mathjax}

Select **MathJax** under **Math renderer** to enable **Override MathJax script** in the same settings page. Enter the script URL for your chosen MathJax build, or a local file URL such as `file:///C:/Users/foo/mathjax/tex-svg.js` for an installed offline copy with its required resources. Leave the field empty to use the default script. There is no need to copy and edit VNote’s `web/js/mathjax.js` just to change this URL. See also the [FAQ](../help/faq.md#custom-mathjax).

## Diagrams

VNote renders diagrams from fenced code blocks using several diagram engines. Write the diagram in its own language and VNote turns it into a rendered figure.

### Mermaid

````md
```mermaid
graph LR
    A[Start] --> B{Decision}
    B -->|Yes| C[Do it]
    B -->|No| D[Skip]
```
````

### PlantUML

````md
```plantuml
@startuml
Alice -> Bob: Hello
Bob --> Alice: Hi
@enduml
```
````

**Settings → Markdown Editor → PlantUml** chooses **Web service** or **Local JAR**; local rendering requires Java and a PlantUML JAR. **PlantUml format** selects **SVG** (default) or **PNG** for read mode and exports; editor previews always use PNG. Sequence diagrams containing `newpage` show each page in read mode and stack the pages into one editor-preview image, without changing the source.

### Graphviz (DOT)

````md
```dot
digraph G {
    A -> B;
    B -> C;
    A -> C;
}
```
````

Graphviz accepts `dot`/`graphviz` and engine-named fences: `neato`, `twopi`, `circo`, `fdp`, `sfdp`, `patchwork`, and `osage`. **Settings → Markdown Editor → Graphviz** selects **Web service** or **Local executable**; configure the Graphviz executable for local rendering. The `sfdp` engine requires local Graphviz. Other flow/graph formats are supported as well.

## Requirements and settings

- **KaTeX**, **Typst**, and **Mermaid** render locally out of the box. MathJax availability depends on the selected script and its resources.
- For **PlantUML** and **Graphviz**, choose local tools when you need offline rendering; check the engine options and required paths in [Settings](../customization/settings.md) if a diagram fails.

Because diagrams and math are plain text, they diff cleanly under version control and export together with your note — see [Export](../productivity/export.md).
