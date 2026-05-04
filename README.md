# go-vanity

Static site for `go.dagstack.dev` — Go module vanity import paths for [dagstack](https://github.com/dagstack).

## How it works

Hosted on GitHub Pages with `CNAME = go.dagstack.dev`. For each Go module under `dagstack/*-go`, an `<module>/index.html` page emits the standard `<meta name="go-import">` tag pointing at the canonical GitHub repo:

```html
<meta name="go-import" content="go.dagstack.dev/config git https://github.com/dagstack/config-go">
```

`go get go.dagstack.dev/config` queries `https://go.dagstack.dev/config?go-get=1`, parses the meta tag, and clones the GitHub repo behind the vanity URL.

## Adding a module

1. Create `<module>/index.html` mirroring `config/index.html` with new module name.
2. Update root `index.html` to list the module.
3. Commit + push — GitHub Pages auto-deploys.

## DNS / GH Pages setup

- DNS CNAME `go.dagstack.dev` → `dagstack.github.io`.
- This repo `dagstack/go-vanity` has Pages enabled (Settings → Pages → Source: deploy from `main` branch / root).
- File `CNAME` (root) = `go.dagstack.dev` — tells GH Pages the custom domain.
