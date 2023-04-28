# Album Format

> Albums form the bulk of content on a music wiki! They're the kernel of data everything else is structured around: related albums are collated in groups, albums contain tracks, albums credit artists, albums include art tags and their tracks are featured in flashes, and so on. The process of adding totally new data to a music wiki almost always starts from albums.
> 
> Albums contain lots of objective data about a release and its tracks, such as release date, personnel/artist credits, related groups, listening URLs, and so on. Albums also cover the presentation of a release and its tracks, with styling info such as theming color, wallpaper and banner, and miscellaneous configuration like disabling track numbers altogether. And albums can contain lots of surrounding goodies, such as sheet music, bonus files, and artist commentary!

Album documents are stored each in its own file, alongside all the tracks associated with that album, at `album/<directory>.md`. Albums are represented by the first document in an album file, with all the rest being track (or track section) documents.

A typical album file will, in its entirety, look something like this:

```
# /path/to/data...   /album/homestuck-vol-7.yaml
Album: 'Homestuck Vol. 7: At the Price of Oblivion'
Directory: homestuck-vol-7
Date: May 31, 2011
---
Section: Main album
---
Track: Black Rose / Green Sun
Artists:
- Malcolm Brown
# ...
---
Track: At The Price of Oblivion
# ...
---
Section: Bonus tracks
---
Track: Maplehoof's Adventure
Artist: Michael Guy Bowman
# ...
```

## Album documents

Referenced as `album:directory` or by name; extra links: `[[album-commentary:directory]]`, `[[album-gallery:directory]]`.

### Essential info fields

* `Album`: album name
  * [Learn about naming albums and tracks for HSMusic.](../guidelines/albums-and-tracks.md#name-albums-and-tracks-according-to-bandcamp-release)
* `Directory`: unique identifier among other albums
  * [Learn about the Directory field, used by almost every wiki object.](../guidelines/common-fields.md#directory-field)
  * This is used for the URL the album will be accessed at: https://hsmusic.wiki/album/DIRECTORY/
  * Groups and other wiki objects reference an album by its directory: `album:DIRECTORY`.
  * An album's filename should match its directory - for example, *Homestuck Vol. 5* automatically gets the directory `homestuck-vol-5` and its data is kept in the file `album/homestuck-vol-5.yaml`. (The filename isn't actually processed for any data purposes; it's just easier to locate an album's data this way.)
* `Color`: theme color representing album
* `Date`: album release date
* `Cover Art Date`: date cover art created/added, if different from album release date
* `Default Track Cover Art Date`: date track art created/added, if different from album release date
  * On HSMusic, this is used for "anthology" art projects where the fan community creates art for each track in an album that originally released without any art. Check out [Homestuck Vol. 5](https://hsmusic.wiki/album/homestuck-vol-5/) and [Beyond Canon](https://hsmusic.wiki/album/beyond-canon/) for examples!
  * If one or a few tracks vary from most of the album, give the track its own `Cover Art Date` field.
* `Date Added`: date album added to wiki

### Content fields

* `URLs`: web URLs for album playback or purchase
* `Commentary`: album-wide commentary from anyone involved in making it
  * [Learn how to format the Commentary field.](../guidelines/common-fields.md#commentary-field)
* `Additional Files`: bonus files associated with the album, e.g. album booklet, desktop wallpapers, credits files
  * [Learn how to format the Additional Files field.](../guidelines/common-fields.md#additional-files-field)

### Configuration & layout

* `Has Cover Art`: display album main cover art (default: true)
* `Has Track Art`: display unique art for each track, instead of inheriting from the album cover (default: true)
* `Has Track Numbers`: display track numbers in main track listing and sidebar (default: true)
* `Listed on Homepage`: include this album in automatically generated listings on the main homepage (default: true)
* `Listed in Galleries`: include this album in automatically generated group gallery pages (default: true)

### Relational fields

* `Artists`: compositional artists who were largely responsible for the entire album, usually used for solo albums
* `Cover Artists`: visual artists who created the album's cover artwork
* `Wallpaper Artists`: visual artists who created the album's wallpaper art; setting this enables displaying custom wallpaper art for the album
* `Banner Artists`: visual artists who created the album's banner art; setting this enables displaying a banner for the album
* `Default Track Cover Artists`: visual artists who were largely responsible for the entire album's track artworks
  * If one or a few tracks vary from most of the album, give those tracks each its own `Cover Artists` field.
  * If most of the tracks in an album have the same cover artists but one or a few tracks don't have unique cover art at all, give those tracks each the field `Has Cover Art: false`.
* `Wallpaper Style`: CSS property/values to apply to the wallpaper for light tweaks of the original asset
* `Banner Style`: CSS property/values to apply to the banner for light tweaks of the original asset
* `Banner Dimensions`: precise dimensions of banner image file e.g. `1100x158` (used to avoid layout shift when loading album page)
* `Wallpaper File Extension`: corresponds to media file (`bg.jpg`, `bg.png`)
* `Banner File Extension`: corresponds to media file (`banner.jpg`, `banner.png`)
* `Cover Art File Extension`: corresponds to media file (`cover.jpg`, `cover.png`)
* `Track Art File Extension`: corresponds to media files (`sburban-jungle.png`)
  * If one or a few tracks vary from most of the album, give those tracks each its own `Cover Art File Extension` field.
  * [Learn about file extension fields.](../common-fields.md#file-extension-fields)
* `Groups`: links album to group documents, which generally represent bands, online communities, specific projects, etc
* `Art Tags`: art tags representing characters or features present in the album's cover artwork

## Track section documents

* `Section`: track section name
* `Color`: color-codes track sections if specified
* `Date Originally Released`: default applied to tracks in this section

## Track documents

See [Track Format](track.md).
