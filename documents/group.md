# Group Format

> Groups are all about organizing related albums into a distinct chronology and giving it context! For most visitors, they're the starting point for exploring and navigating a wiki; they give the wiki its top-level structure, and are also the main data source used in the homepage's layout. Groups are a very general feature, and can be made for a wide variety of uses! Groups themselves are categorized, so you can use groups for multiple purposes on a single wiki — the Homestuck Music Wiki uses groups for music teams, bands, and solo musicians, "fanventures" and game projects with multiple releases, as well as an essential scope identifying how closely tied any album is to Homestuck itself. If you're contributing one or more new albums, [learn more about grouping albums for HSMusic.](../guidelines/groups.md)

Group documents are stored all in one file, `groups.yaml`, one document (entry) per group. They're further categorized by group category documents.

The groups file will, in its entirety, look something like this:

```
Category: HSMusic
Color: '#0088ff'
---
Group: Official Discography
Directory: official
# ...
---
Group: Fandom
# ...
---
Category: Fan-musician groups
Color: '#ffec14'
---
Group: Homestuck Gaiden
URLs:
# ...
---
Group: Unofficial MSPA Fans
URLs:
# ...
```

## Group documents

Referenced as `group:directory`; extra links: `[[group-gallery:directory]]`.

* `Group`: group name
* `Directory`: unique identifier among other groups
* `Description`: any-length description of the group (use `<hr class="split">` for paragraphs beyond the brief summary)
* `URLs`: web URLs where the group can be visited

* `Featured Albums`: optional list of "featured" albums; if present, displayed in a carousel on group gallery page

## Group category documents

* `Category`: group category name
* `Color`: color for category and all included groups
