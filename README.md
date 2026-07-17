# Manuscript Workbench

Manuscript Workbench is a small, local-first formatter for people preparing Minecraft books with the [Stendhal mod](https://www.curseforge.com/minecraft/mc-mods/stendhal). It turns a plain-text draft into Stendhal's serialized manuscript format and keeps the result visible while you write.

This is an independent community utility. It is not affiliated with or endorsed by Stendhal, its authors, CurseForge, Mojang Studios, or Microsoft. The project source is available in this [GitHub repository](https://github.com/maxjustships/stendhal-book-exporter).

## Use it

1. Open `index.html` in a modern browser.
2. Enter an optional title and author, then write or paste the source manuscript.
3. Inspect or select the live Stendhal output.
4. Choose **Export .stendhal** to download the exact preview as a UTF-8 plain-text file.
5. Import that file through the book import workflow provided by your installed Stendhal version. Consult the mod's current documentation or interface for the applicable import steps.

No installation, package manager, build step, account, or network connection is required to run the formatter. The Stendhal and repository links only open if you choose them.

## Formatting rules and limitations

- Source text is processed one line at a time. An empty source line becomes an empty group.
- Words are wrapped into groups of at most 19 JavaScript string units (UTF-16 code units), including spaces considered during wrapping.
- Words longer than 19 units are kept whole rather than split, so an oversized group can exceed the nominal limit.
- Regular wrapped groups have trailing whitespace removed. Leading whitespace and whitespace-only source lines are not preserved as prose indentation.
- A page holds at most 14 groups and at most 256 serialized page characters, including newlines between groups.
- An oversized group is placed intact on its own page and can therefore make that page exceed 256 characters.
- Every serialized page begins with `#- `. Pages are joined with a single newline.
- Output begins with `title`, `author`, and `pages` fields. Blank metadata falls back to `Untitled` and `Anonymous`.
- Metadata and manuscript content are serialized as entered; the tool does not validate game glyph support or escape format-significant content.
- The exported file is UTF-8 `text/plain`, with no byte-order mark and no terminal newline added.

## Privacy

Formatting and export happen entirely in the browser. Manuscript text is not uploaded, transmitted, or stored by this page. Closing or reloading the page clears unsaved input under normal browser behavior.

## Development

Open `index.html` directly in a browser. All product HTML, CSS, and JavaScript are inline, and there are no runtime dependencies or build commands.

## Structure

- `index.html` — the complete formatter and interface
- `README.md` — project, usage, and format notes
- `LICENSE` — MIT license

## License

Released under the MIT License. See `LICENSE`.
