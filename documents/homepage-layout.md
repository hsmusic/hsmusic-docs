# Homepage Layout Format

The homepage layout file has a header document describing details about the overall homepage structure, then a document for each "row" in the main content area.

Homepage layout documents affect only the homepage. Refer to [Wiki Info Format](wiki-info.md) for options that customize the appearance or behavior of an entire wiki.

The homepage layout file will, in its entirety, look something like this:

```yaml
Sidebar Content: ...
Navbar Links: ...
---
Row: Official Discography
Type: albums
Display Style: carousel
# ...
---
Row: New Additions
Type: albums
Display Style: grid
# ...
```

## Homepage layout - header document

* `Sidebar Content`: multiparagraph text/content to be show in homepage sidebar box
  * This supports content links, image embeds, etc just like any other multiline content area.
  * The special text `[[news]]` will be replaced with a small section for the latest news entries.

* `Navbar Links`: links to show in homepage navigation bar
  * These must all be inline links without any additional text (the title of the link can be customized, though).
  * Examples: `[[static:discord]]`, `[[listing-index:-|Listings]]`

## Homepage layout - row documents

All row documents accept the following options:

* `Row`: title to display above row contents
* `Color`: custom color for links in content

* `Type`: specify basic kind of content being displayed & access additional related fields
  * There's currently only one supported row type, `albums`. More will probably be added in the future.

### `Type: albums` row documents

* `Display Style`: `grid` (default) or `carousel`
  * `grid` displays albums with the same basic layout as gallery pages.
    * The grid layout on the homepage is currently hard-coded in CSS. Sorry!
    * 2 rows of 3 larger grid items, then any number of rows of 4 smaller grid items.
  * `carousel` shows a slowly wrap-scrolling, shorter but wider grid of albums.
    * Carousel reels have some niche sizing particulars (see `carouselLayoutMap`), but basically fit 4 to 18 items and display them across 1 to 3 rows (preferring 2) and 4 to 6 columns (avoiding blank space).
    * The items in a carousel scroll automatically but all of them are always visible at once. The left edge wraps precisely "around the back" to the right edge.

* `Group`: group to pull most recent albums from if paired with `Count`; special values: `new-releases`, `new-additions`
  * Special value `new-releases`: pull the latest albums chronologically released (by `Date`), regardless of when they were added to the wiki
  * Special value `new-additions`: pull the albums most recently added to the wiki (by `Date Added to Wiki`), regardless of when they were chronologically released
* `Count`: number of albums to pull (if paired with `Group`)

* `Albums`: manual list of albums to display
  * If both (dynamic) `Group`/`Count` and (manual) `Albums` are specified, the (manual) `Albums` will show up at the end of the list. They don't count towards `Count`, i.e. if you want 12 albums in total and two of them are manually specified, set `Count` to 10.

* `Actions`: list of quick links to display at end of grid or below carousel
  * Like `Navbar Links` in the header document, these must all be inline links.
  * Example: `[[group-gallery:official|Explore Official!]]`
