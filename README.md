[![CI](https://github.com/justinharringa/bota-hugo-theme/actions/workflows/ci.yml/badge.svg)](https://github.com/justinharringa/bota-hugo-theme/actions/workflows/ci.yml)

# bota-hugo-theme

A minimal [Bootstrap](https://getbootstrap.com)-based blog theme for [Hugo](https://gohugo.io) with per-post [Disqus](https://disqus.com) comments and a social-media-icon footer.

Live example: [harringa.com](https://harringa.com).

## Requirements

- Hugo **extended** ≥ `0.128.0` (uses `css.Sass`, which is the replacement for the removed `resources.ToCSS`).

## Installation

Add the theme as a git submodule under `themes/bota`:

```sh
git submodule add https://github.com/justinharringa/bota-hugo-theme.git themes/bota
```

Then set it in your site config:

```yaml
# config.yaml
theme: bota
```

## Required data

The footer iterates `data/social/*.yaml` to render social-media icons. Each file represents one account:

```yaml
# data/social/github.yaml
Name: GitHub
UserName: your-username
URL: github.com
```

`Name` is used both as the accessibility label and (lowercased) as the Font Awesome icon class, so it should match a Font Awesome icon name (`fa-github`, `fa-linkedin`, `fa-twitter`, etc.). Add as many files under `data/social/` as you like.

## Optional site params

All are set under `params:` in your site config.

| Param | Default | Effect |
|---|---|---|
| `author` | — | Value for the `<meta name="author">` tag. Per-post `author:` front matter overrides. If neither is set, the tag is omitted. |
| `SiteDescription` | — | Fallback for the `<meta name="description">` tag when a page has no `.Description`. |
| `blogPostTaxonomy` | `post` | Section/taxonomy name that holds your blog posts. Used on the home page index and RSS link. Set to `posts` if your content lives under `content/posts/`. |
| `date_format` | `Jan 2, 2006` | Go-time reference-date layout used to format post dates. |
| `showReadingTime` | `true` | Toggle the `· N min read` suffix under post titles. |
| `truncate` | `true` | When `true`, list/home pages show post summaries + "Read more…"; when `false`, full content. |

## Analytics

Wire `googleAnalytics` (or the more-recent `services.googleAnalytics.ID`) in your site config and Hugo's built-in analytics template emits the right tracking script — `gtag.js` for `G-` GA4 measurement IDs, `analytics.js` for legacy `UA-` property IDs:

```yaml
services:
  googleAnalytics:
    ID: "G-XXXXXXXXXX"
```

If neither is set, no tracking script is emitted.

## Comments (Disqus)

Set your Disqus shortname at the site level:

```yaml
disqusShortname: "your-shortname"
```

Each post will render Disqus comments below the body via Hugo's internal `disqus.html` template.

## Local development

```sh
git clone --recurse-submodules https://github.com/justinharringa/bota-hugo-theme.git
cd bota-hugo-theme/exampleSite
hugo server --themesDir ../..
```

`exampleSite/` is the minimal site used by CI to smoke-test the theme's templates on every PR.

## License

[MIT](LICENSE)
