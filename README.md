# Harvey in Hell — site

A static one-page site: `index.html` + `style.css`, no build step.

## 1. Drop in your images

Put these files in the `assets/` folder using these exact names (or edit the
paths in `index.html` if you'd rather rename them):

| Filename                              | Used for                          |
|----------------------------------------|------------------------------------|
| `hmi-logo.png`                         | Logo (header + footer)             |
| `hero-road.jpg`                        | Hero background (the desert road)  |
| `cover-harvey-in-hell.jpg`             | Show cover art box                 |
| `cast-chris-mcclure.jpg`               | Cast photo                         |
| `cast-romy-evans.jpg`                  | Cast photo                         |
| `cast-sabrina-knappett.jpg`            | Cast photo                         |
| `cast-michael-masurkevitch.jpg`        | Cast photo                         |
| `cast-allen-enlow.jpg`                 | Cast photo                         |
| `cast-pete-flatiche.jpg`               | Cast photo                         |
| `ep-*.jpg` (20 files, see index.html)  | Episode cover art                  |
| `wall-of-the-damned-bg.jpg`            | Background for the backer wall     |

Any image you don't have yet is fine to skip for now — the layout still
holds up with a missing image (you'll just see the dark background).

## 2. Wire up the trailer

Open `index.html`, find the `<iframe>` inside the Trailer section, and
replace `YOUTUBE_VIDEO_ID` with your video's ID:

```
https://www.youtube.com/watch?v=XXXXXXXXXXX
                                 ^^^^^^^^^^^ this part
```

## 3. Edit text content

- Hero tagline, trailer quote, and reviews are plain text in `index.html` —
  edit directly.
- Reviews are written out as styled quote cards rather than screenshots, so
  you can add/edit/remove them freely without needing image files.
- Cast bios and episode titles are already filled in from what you had;
  adjust wording as needed.
- The "Wall of the Damned" backer names are one `<p>` per name inside
  `.wall-names` — add, remove, or reorder freely; the layout re-flows
  automatically into columns.

## 4. The heat-haze warp effect

The hero background uses an animated SVG filter (`#heatwarp`, defined near
the top of `index.html`) that slowly distorts the road image — a
feTurbulence + feDisplacementMap combo, looping every ~22 seconds. To make
it stronger or subtler, tweak these two values in the `<filter>` block:

- `baseFrequency` values on `<animate>` — lower = larger, slower waves
- `scale` on `feDisplacementMap` — higher = more distortion

## 5. Deploy to GitHub Pages

1. Create a new repo on GitHub (e.g. `harvey-in-hell`).
2. Push these files to the repo root:
   ```
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/harvey-in-hell.git
   git push -u origin main
   ```
3. In the repo, go to **Settings → Pages**.
4. Under "Build and deployment", set **Source** to `Deploy from a branch`,
   branch `main`, folder `/ (root)`. Save.
5. GitHub will give you a URL like
   `https://YOUR_USERNAME.github.io/harvey-in-hell/` within a minute or two.

If you want a custom domain, add a `CNAME` file with your domain name in the
repo root and point your DNS at GitHub Pages per their docs.
