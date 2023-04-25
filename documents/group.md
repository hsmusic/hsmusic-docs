# Group Format

Group documents are stored all in one file, `groups.yaml`, one document (entry) per group. They're further categorized by group category documents.

The groups file will, in its entirety, look something like this:

```yaml
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
