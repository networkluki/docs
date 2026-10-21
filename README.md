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
├── index.html                     # Documentation homepage
├── 404.html
└── sites/
    ├── networkluki.com/index.md
    ├── theinfo.nu/index.md
    └── ipconfig.se/index.md
```

## Add an article to an existing website

1. Copy \u0060_templates/article.md\u0060 into a new directory, for example \u0060sites/ipconfig.se/api/ip-address/index.md\u0060.
2. Set \u0060layout: article\u0060 and \u0060website: ipconfig.se\u0060 in the YAML front matter.
3. Set \u0060title\u0060, \u0060description\u0060, \u0060section\u0060 and \u0060nav_order\u0060. For example, sections can be \u0060guides\u0060, \u0060api\u0060, \u0060security\u0060, \u0060deployment\u0060 or \u0060operations\u0060.
4. Add and verify Markdown content, then commit the article.

The URL in this example is **https://docs.networkluki.com/sites/ipconfig.se/api/ip-address/**. The article automatically appears in the ipconfig.se list because its front matter specifies the corresponding \u0060website\u0060 key.

## Add a new website

1. Add its \u0060key\u0060, \u0060name\u0060, \u0060category\u0060, \u0060description\u0060, \u0060url\u0060, \u0060path\u0060 and \u0060monogram\u0060 to \u0060_data/websites.yml\u0060.
2. Create \u0060sites/example.com/index.md\u0060 with \u0060layout: website\u0060, \u0060website: example.com\u0060 and \u0060permalink: /sites/example.com/\u0060.
3. Add articles beneath \u0060sites/example.com/\u0060 using the article template.

Use one website key consistently in the registry, landing page and each article. All URLs are paths under **docs.networkluki.com**, not separate DNS subdomains.

## Publishing

- GitHub Pages should publish from the \u0060main\u0060 branch root (or an equivalent Jekyll-compatible Pages build).
- Keep \u0060CNAME\u0060 at the publication root with only \u0060docs.networkluki.com\u0060.
- This site uses GitHub Pages' built-in Jekyll processing. **Do not add a \u0060.nojekyll\u0060 file**, because Markdown articles and layouts must be rendered.
- GitHub Pages changes become live after deployment; review changes in a pull request first.

## Local preview and verification

If Jekyll is installed locally, run:

```bash
bundle exec jekyll serve --host 127.0.0.1
```

Then open \u0060http://127.0.0.1:4000/\u0060. Verify that all website cards work, and that new articles appear in the appropriate website's article list.

## Security and content policy

Treat public documentation as publicly readable. Never commit secrets, authentication tokens, internal IP inventories, credentials, private hostnames or incident-sensitive operational details. Review technical commands before publishing.

All text and layouts are stored in this repository, with no external scripts or CSS dependencies.
