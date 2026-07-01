# go-widgets landing

Hugo source for **<https://go-widgets.github.io/>** — the landing
page of the [`go-widgets`](https://github.com/go-widgets) org.

Preview locally:

```
hugo server
```

Build:

```
hugo --minify
```

The rendered site lives under `public/` (gitignored except when
GitHub Pages is deployed from that directory — see the workflow
under `.github/workflows/pages.yml`).

Layout is a single-page card grid: header + hero + tagline + pills +
a `.grid` of component cards driven by `hugo.toml`'s
`params.components` list. Adding a new sibling repo (e.g.
`go-widgets/svg`) means adding one `[[params.components]]` block
to `hugo.toml` and re-running `hugo --minify`.

## License

BSD-3-Clause.
