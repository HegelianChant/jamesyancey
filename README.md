# Personal site

A hand-built HTML/CSS site on Jekyll, set up so GitHub Pages builds it
automatically — no Actions workflow, no separate build step to maintain.
Jekyll only handles templating (shared header/footer, post listing pages);
every layout and every line of CSS is yours, in `_layouts/`, `_includes/`,
and `assets/css/style.css`.

## Structure

```
_config.yml          site settings, nav, collections
_layouts/            page templates (default, post, photo, travel)
_includes/            header.html, footer.html
_posts/               blog posts   → yourname.github.io/blog/...
_photos/               photo journal entries → /photos/...
_travel/               travel journal entries → /travel/...
assets/css/style.css   all the styling
assets/img/            images
index.html             homepage
about.html
blog/index.html         blog listing
photos/index.html       photo grid
travel/index.html       travel listing
```

## Adding content

- **Blog post** — new file in `_posts/`, named `YYYY-MM-DD-title.md`, with
  front matter `title:` and `tags:`. Body is Markdown.
- **Photo album** — new file in `_photos/`, named `YYYY-MM-title.md`. Front
  matter: `title:`, `date:`, `location:`, `cover:` (image shown on the
  albums index), and a `photos:` list, each with `image:` and an optional
  `caption:`. See `_photos/2026-09-glasgow.md` for the exact shape. The
  album's own page shows every photo in the list, two per row.
- **Travel entry** — new file in `_travel/`, named `YYYY-MM-DD-title.md`,
  with `title:`, `date:`, `location:`.

## Running locally

Requires Ruby (check with `ruby -v`; install via [rbenv](https://github.com/rbenv/rbenv)
or [asdf](https://asdf-vm.com/) if needed).

```
bundle install
bundle exec jekyll serve
```

Visit `http://localhost:4000`. Jekyll rebuilds automatically as you edit.

## Deploying to GitHub Pages

1. Push this repo to GitHub.
2. In the repo, go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to "Deploy from a branch"
   and pick `main` (root).
4. GitHub builds the Jekyll site itself — no CI config needed.

**If this is a user/org site** (repo named `yourusername.github.io`):
leave `url` and `baseurl` blank in `_config.yml`. It'll be live at
`https://yourusername.github.io`.

**If this is a project site** (any other repo name): set `baseurl` in
`_config.yml` to `/your-repo-name`, and set `url` to
`https://yourusername.github.io`. It'll be live at
`https://yourusername.github.io/your-repo-name`.

## Custom domain (optional)

Add a `CNAME` file at the repo root containing just your domain
(e.g. `example.com`), and point your domain's DNS at GitHub Pages per
[their docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site).

## Design system

- **Palette**: warm paper (`--paper`) and dark ink (`--ink`) with a single
  rust accent (`--accent`), plus a light/dark auto-switch via
  `prefers-color-scheme`. All defined as CSS custom properties at the top
  of `style.css` — change them there to retint the whole site.
- **Type**: Archivo (grotesque sans) for headings/nav/labels, Source Serif 4
  for body copy and long-form reading.
- **Layout**: a fixed nav column + content grid on desktop (Swiss-style,
  left-aligned, asymmetric), collapsing to a stacked header on mobile.
  Hairline rules separate list entries — they mark where one entry ends
  and the next begins, not decoration.
