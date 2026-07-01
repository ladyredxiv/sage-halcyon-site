# Sage Halcyon Site

This is a plain static website for cPanel/Stellar hosting.

## Site Data

The site is now scaffolded for multiple series.

- `data/series.json` is the source of truth for series.
- `data/books.json` is the source of truth for books.
- `books.json` is kept as a compatibility copy for older/simple page scripts.

When updating book data, update `data/books.json` and keep `books.json` in sync.

## Update A Book

Edit `data/books.json`.

Each book can use these fields:

```json
{
  "id": "unique-book-id",
  "title": "Book Title",
  "series_id": "thistledown",
  "series": "Thistledown",
  "series_position": 1,
  "blurb": "Short sales blurb.",
  "status": "out-now",
  "status_label": "Out now",
  "cover_image": "images/cover-file.jpg",
  "page_url": "book-title.html",
  "featured": false,
  "show_on_home": true,
  "home_sort": 1,
  "release_sort": 1,
  "tropes": ["slow burn", "found family"],
  "links": [
    { "label": "Buy now", "url": "https://example.com" },
    { "label": "Read sample", "url": "https://example.com" }
  ]
}
```

Supported statuses:

- `out-now`
- `coming-soon`
- `planned`

If `links` is empty, the site shows the book status instead of a button. Add the main sales/preorder link first so it becomes the primary button.

Homepage rules:

- One book should usually have `"featured": true`.
- Set `"show_on_home": true` for books that should appear in the homepage Latest Releases shelf.
- The homepage intentionally caps the latest shelf to three books.
- The full catalog belongs on `reading-order.html` and series pages.

## Add A Series

Edit `data/series.json`.

```json
{
  "id": "series-id",
  "title": "Series Title",
  "subtitle": "Short positioning line",
  "status": "active",
  "description": "Reader-facing series description.",
  "reading_order_label": "Best read in release order",
  "page_url": "series-page.html",
  "featured": true,
  "home_sort": 1
}
```

## Add A Cover

Put the cover image in `images/`, then set `cover_image` in `books.json`.

Example:

```json
"cover_image": "images/my-new-cover.jpg"
```

## Deploy With cPanel Git Version Control

The `.cpanel.yml` file copies `index.html`, `books.json`, and `images/` into `/home/sageodnk/public_html/` when cPanel deploys the repo.

If your live site files belong somewhere other than `/home/sageodnk/public_html/`, update the `DEPLOYPATH` line in `.cpanel.yml`.
