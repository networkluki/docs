# NetworkLuki Documentation

Central GitHub Pages documentation portal for **https://docs.networkluki.com/**.

Documentation is organized by website. Each website has its own landing page and automatically lists Markdown articles assigned to it.

## Repository structure

```text
docs/
├── CNAME                         # Custom domain (one domain for this Pages site)
├── _config.yml                   # Jekyll configuration
├── _data/websites.yml            # Website registry and homepage cards
├── _layouts/                      # Shared page templates
│   ├── default.html
│   ├── website.html
│   └── article.html
├── _templates/article.md         # Example article front matter
├── assets/css/site.css            # Shared styling
├── assets/icons/                 # Docs favicon and per-website SVG icons
│   ├── docs.svg
│   ├── networkluki.svg
│   ├── theinfo.svg
│   └── ipconfig.svg
├── index.html                     # Documentation homepage
├── 404.html
└── sites/
    ├── networkluki.com/index.md
    ├── theinfo.nu/index.md
    └── ipconfig.se/index.md
```

## Add an article to an existing website

1. Copy `_templates/article.md` into a new directory, for example `sites/ipconfig.se/api/ip-address/index.md`.
2. Set `layout: article` and `website: ipconfig.se` in the YAML front matter.
3. Set `title`, `description`, `section` and `nav_order`. For example, sections can be `guides`, `api`, `security`, `deployment` or `operations`.
4. Add and verify Markdown content, then commit the article.

The URL in this example is **https://docs.networkluki.com/sites/ipconfig.se/api/ip-address/**. The article automatically appears in the ipconfig.se list because its front matter specifies the corresponding `website` key.

## Add a new website

1. Add its `key`, `name`, `category`, `description`, `url`, `path` and `monogram` to `_data/websites.yml`. Add `icon: /assets/icons/example.svg` for a custom icon (otherwise the monogram is shown).
2. Create `sites/example.com/index.md` with `layout: website`, `website: example.com` and `permalink: /sites/example.com/`.
3. Add articles beneath `sites/example.com/` using the article template.

SVG icons are kept in `assets/icons/`. `docs.svg` is the browser favicon and header logo. Website icons are referenced through the `icon` field in `_data/websites.yml` and displayed on site cards and documentation landing pages. Keep SVGs self-contained: no scripts, external references or remote assets.

Use one website key consistently in the registry, landing page and each article. All URLs are paths under **docs.networkluki.com**, not separate DNS subdomains.

## Publishing

- GitHub Pages should publish from the `main` branch root (or an equivalent Jekyll-compatible Pages build).
- Keep `CNAME` at the publication root with only `docs.networkluki.com`.
- This site uses GitHub Pages' built-in Jekyll processing. **Do not add a `.nojekyll` file**, because Markdown articles and layouts must be rendered.
- GitHub Pages changes become live after deployment; review changes in a pull request first.

## Local preview and verification

If Jekyll is installed locally, run:

```bash
jekyll serve --host 127.0.0.1
```

Then open `http://127.0.0.1:4000/`. Verify that all website cards work, and that new articles appear in the appropriate website's article list.

## Security and content policy

Treat public documentation as publicly readable. Never commit secrets, authentication tokens, internal IP inventories, credentials, private hostnames or incident-sensitive operational details. Review technical commands before publishing.

All text and layouts are stored in this repository, with no external scripts or CSS dependencies.
