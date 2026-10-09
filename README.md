# go-widgets.github.io

The landing page for [go-widgets](https://github.com/go-widgets), built with
Hugo and deployed by GitHub Actions to <https://go-widgets.github.io/>.

It is laid out like the [go-fileshare](https://go-fileshare.github.io/) and
[go-authn](https://go-authn.github.io/) landings. `layouts/partials/styles.html`
is the same file as theirs, byte for byte: it takes its colours from
`[params.brand]` in `hugo.toml`, and only those values differ (go-widgets'
teal, from [go-widgets/brand](https://github.com/go-widgets/brand)). Fix the
stylesheet in one org, copy it to the others unchanged.

⚠ Pages must be set to **build from the workflow**, not from a branch:

```sh
gh api -X PUT repos/go-widgets/go-widgets.github.io/pages -f build_type=workflow
```

A repository left on the legacy Jekyll builder publishes this README over the
Hugo output while the workflow reports success.

## Layout

| Path | What |
|---|---|
| `layouts/index.html` | the page |
| `layouts/partials/styles.html` | the shared stylesheet and theme toggle script |
| `layouts/partials/icons/` | Octicons (MIT, `OCTICONS-LICENSE`), copied verbatim |
| `hugo.toml` | `[params.brand]`, one `[[params.modules]]` per module, one `[[params.surfaces]]` per surface |

The counts on the page (modules, surfaces) are computed from those lists,
never typed beside them. The terminal panel is a real transcript; its source
is in the comment above it.

Adding a module means a `[[params.modules]]` block **and** its name in the
list in `.github/workflows/ci.yml`. The second list is deliberate: a check
that read the page's own data would agree with the page whatever it left out.

## Workflows

| Workflow | When | What |
|---|---|---|
| `pages.yml` | pull requests, `main` | builds the site; only `main` deploys it |
| `ci.yml` | pull requests | every module is on the page; no brand colour was turned into `ZgotmplZ` |
| `links.yml` | pull requests | builds, then fetches every link and image the page carries |

## Working locally

```sh
hugo server
```

## Licence

BSD-3-Clause.
