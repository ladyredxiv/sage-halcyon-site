# Sage Halcyon Site

This is a plain static website for cPanel/Stellar hosting.

## Update A Book

Edit `books.json`.

Each book can use these fields:

```json
{
  "id": "unique-book-id",
  "title": "Book Title",
  "series": "Thistledown",
  "series_position": 1,
  "blurb": "Short sales blurb.",
  "status": "out-now",
  "status_label": "Out now",
  "cover_image": "images/cover-file.jpg",
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

## Add A Cover

Put the cover image in `images/`, then set `cover_image` in `books.json`.

Example:

```json
"cover_image": "images/my-new-cover.jpg"
```

## Deploy With cPanel Git Version Control

The `.cpanel.yml` file copies `index.html`, `books.json`, and `images/` into `/home/sageodnk/public_html/` when cPanel deploys the repo.

If your live site files belong somewhere other than `/home/sageodnk/public_html/`, update the `DEPLOYPATH` line in `.cpanel.yml`.
