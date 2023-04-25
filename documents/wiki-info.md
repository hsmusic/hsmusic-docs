# Wiki Info Format

The wiki info document covers options that customize the appearance or behavior of an entire wiki. It is one document (entry) stored in one file, `wiki-info.yaml`.

## Wiki info document

### Essential info fields

* `Name`: full name of the wiki
* `Short Name`: shorter wiki name (for use in page titles, navbar, etc)
* `Color`: default theme color to apply across the wiki
* `Description`: short description for use in web search results
* `Footer Content`: text and links to include in footer on most wiki pages
* `Default Language`: main language for wiki content; content pages for other languages are written as subdirectories
* `Canonical Base`: base URL where site is published (used for search engine optimization)

### Features

* `Divide Track Lists By Groups`: list of groups for which referenced track lists should be divided, e.g. Official Discography, Fandom, Beyond
* `Enable Flashes & Games`: generate pages related to flash documents
* `Enable Listings`: generate listing pages, e.g. tracks sorted by name, artists sorted by contributions
* `Enable News`: generate news entry pages and index
* `Enable Art Tag UI`: generate content and pages related to art tags (content warning tags are still usable if disabled)
* `Enable Group UI`: generate UI for navigating between groups
