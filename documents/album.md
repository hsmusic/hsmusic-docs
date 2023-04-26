# Album Format

Album documents are stored each in its own file, alongside all the tracks associated with that album, at `album/<directory>.md`. Albums are represented by the first document in an album file, with all the rest being track (or track section) documents.

A typical album file will, in its entirety, look something like this:

```yaml
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

Referenced as `album:directory`; extra links: `[[album-commentary:directory]]`, `[[album-gallery:directory]]`.

### Essential info fields

* `Album`: album name
* `Directory`: unique identifier among other albums
  * This is used for the URL the album will be accessed at: https://hsmusic.wiki/album/DIRECTORY/
  * Groups and other wiki objects reference an album by its directory: `album:DIRECTORY`.
  * This is usually generated automatically from the album's name. [Learn more.](../guidelines/common-fields.md#directory-field)
  * Just for albums, the directory should match the filename, e.g. *Homestuck Vol. 5* automatically gets the directory `homestuck-vol-5` and its data is saved in the file `album/homestuck-vol-5.yaml`. (The filename isn't actually processed for any data purposes, it's just easier to navigate if it matches the directory.)
* `Date`: album release date
* `Cover Art Date`: date cover art created/added, if different from album release date
* `Date Added`: date album added to wiki
* `Color`: theme color representing album
* `URLs`: web URLs for album playback or purchase

### Content fields

* `Commentary`: album-wide commentary from anyone involved in making it
  * [Learn more about formatting the Commentary field.](../guidelines/common-fields.md#commentary-field)
* `Additional Files`: bonus files associated with the album, e.g. album booklet, desktop wallpapers, credits files

### Configuration & layout

* `Has Cover Art`: display album main cover art (default: true)
* `Has Track Art`: display unique art for each track, instead of inheriting from the album cover (default: true)
* `Has Track Numbers`: display track numbers in main track listing and sidebar (default: true)
* `Listed on Homepage`: include this album in automatically generated listings on the main homepage (default: true)
* `Listed in Galleries`: include this album in automatically generated group gallery pages (default: true)
* `Default Track Cover Art Date`: date track art created/added, if different from album release date; provides default which may be overridden by a track's `Cover Art Date` field
* `Cover Art File Extension`: corresponds to media file (`cover.jpg`, `cover.png`)
* `Track Art File Extension`: corresponds to media files; provides default which may be overridden by a track's `Cover Art File Extension` field

### Relational fields

* `Artists`: compositional artists who were largely responsible for the entire album, usually used for solo albums
* `Wallpaper Artists`: visual artists who created the album's wallpaper art; setting this enables displaying custom wallpaper art for the album
	* `Wallpaper Style`: CSS property/values to apply to the wallpaper for light tweaks of the original asset
	* `Wallpaper File Extension`: corresponds to media file (`bg.jpg`, `bg.png`)
* `Banner Artists`: visual artists who created the album's banner art; setting this enables displaying a banner for the album
	* `Banner Style`: CSS property/values to apply to the banner for light tweaks of the original asset
	* `Banner File Extension`: corresponds to media file (`banner.jpg`, `banner.png`)
	* `Banner Dimensions`: precise dimensions of banner image file e.g. `1100x158` (used to avoid layout shift when loading album page)
* `Cover Artists`: visual artists who created the album's cover artwork
* `Default Track Cover Artists`: visual artists who were largely responsible for the entire album's track artworks; may be overridden by a track's `Cover Artists` field
* `Groups`: links album to group documents, which generally represent bands, online communities, specific projects, etc
* `Art Tags`: art tags representing characters or features present in the album's cover artwork

## Track section documents

* `Group`: track section name
* `Color`: color-codes track sections if specified
* `Date Originally Released`: default applied to tracks in this section

## Track documents

See [Track Format](track.md).
