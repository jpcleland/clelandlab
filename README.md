# Cleland Lab website

A small, dependency-free static site: five HTML pages plus one stylesheet. No build
step, no framework, no npm. Edit the HTML, push, done.

```
index.html          Home — hero, research teaser, news, recruitment, funder logos
research.html       Research themes
publications.html   Publication list
members.html        Lab members + alumni
join.html           Open positions
style.css           All styling (colours are variables at the top)
assets/             Your images go here
```

## Putting it online with GitHub Pages (about 5 minutes)

1. Create a new repository on GitHub — e.g. `clelandlab.github.io` or just `lab-website`.
2. Upload these files to the root of the repo (drag-and-drop works: **Add file → Upload files**).
   Or from a terminal:

   ```bash
   git init
   git add .
   git commit -m "Initial lab website"
   git branch -M main
   git remote add origin https://github.com/YOURNAME/YOURREPO.git
   git push -u origin main
   ```

3. In the repo: **Settings → Pages**. Under *Source* choose **Deploy from a branch**,
   branch `main`, folder `/ (root)`. Save.
4. Wait a minute; the site appears at `https://YOURNAME.github.io/YOURREPO/`.

### Using your own domain (e.g. clelandlab.com)

1. Buy the domain, then in **Settings → Pages → Custom domain** enter it and save.
   This creates a `CNAME` file in the repo.
2. At your domain registrar add DNS records:
   - `A` records for the apex domain pointing to `185.199.108.153`, `185.199.109.153`,
     `185.199.110.153`, `185.199.111.153`
   - a `CNAME` record for `www` pointing to `YOURNAME.github.io`
3. Back in Settings → Pages, tick **Enforce HTTPS** once the certificate is issued.

## Editing

**Text** — everything in square brackets `[like this]` is a placeholder. Search the
files for `[` and replace. Nothing else needs touching.

**Colours** — the top of `style.css`:

```css
--accent:      #8c1d2c;   /* dark red */
--accent-dark: #6a1521;   /* hover state */
--accent-soft: #f6ecee;   /* pale tint behind tags and figures */
```

Change those three and the whole site changes.

**Images** — drop files into `assets/` and swap the placeholder blocks. E.g. on the
homepage replace

```html
<div class="hero-figure">assets/hero.jpg — drop a microscopy image…</div>
```

with

```html
<div class="hero-figure"><img src="assets/hero.jpg" alt="Short description"></div>
```

An animated GIF works here too, as on mzhulab.com. Member photos look best square
(~600×600 px) in `assets/people/`.

**Adding a publication** — copy one `<li>` block in `publications.html`. Bold your own
name with `<b>Cleland J</b>`. Add a new `<h2 class="year-head">` for each new year.

**Adding a person** — copy one `.person` block in `members.html`. If there's no photo
yet, the initials placeholder looks fine.

**Adding a news item** — copy one `<li>` in the `.news` list on `index.html`, newest first.

## Note on the header and footer

Because this is plain HTML with no templating, the nav bar and footer are repeated in
all five files. If you change a link, change it in all five. (If that becomes annoying,
the site can be converted to Jekyll — which GitHub Pages builds automatically — so the
header lives in one file.)

## Previewing locally

```bash
python3 -m http.server 8000
```

then open <http://localhost:8000>. Or just double-click `index.html`.
