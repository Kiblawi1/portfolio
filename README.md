# Portfolio site for Abdulrahman Kablawi

Static site published with GitHub Pages from the `main` branch of this repository.

- Live portfolio: https://kiblawi1.github.io/portfolio/
- Stable QR link:  https://kiblawi1.github.io/portfolio/go/

## Why the QR points at /go/

The QR code printed on the CV encodes the `/go/` address, not the portfolio itself.
`go/index.html` is a one-line redirect page. If the portfolio ever moves (custom domain,
another host, a new repo), only that redirect changes and every printed CV keeps working.

## How to change where the QR sends people

1. Open `go/index.html`.
2. Replace the address in these three places with the new one:
   - `<meta http-equiv="refresh" content="0; url=NEW-ADDRESS">`
   - `<link rel="canonical" href="NEW-ADDRESS">`
   - the `<a href="NEW-ADDRESS">` fallback link
3. Commit and push to `main`. GitHub Pages republishes within about a minute.

Keep this repository and the `/go/` folder online even if the portfolio itself moves,
because printed QR codes cannot be updated.

## Updating the portfolio content

Edit `index.html` and `style.css`, add images under `images/`, commit, push.
Image credits in the footer must be kept in step with `image_log.csv` in the working folder.

## Maintenance notes

- No build step, no JavaScript, no external dependencies.
- `.nojekyll` stops GitHub from running Jekyll on the files.
- GitHub Pages does not support true HTTP 302 redirects for project sites, so `/go/` uses a
  0-second meta refresh, which every phone browser follows instantly.
