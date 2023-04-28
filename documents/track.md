# Track Format

> Tracks are by far the most populous type of content on a music wiki. While albums have the most connections to other kinds of data, tracks themselves are the most "atomic" unit. Besides basic per-track information, HSMusic's strength lies in defining tracks in relation to each other: motif-referenced tracks, audio samples, re-releases, all tie tracks from different releases together in a wiki-wide net. And tracks automatically show up on artist's credit pages and in a selection of listings, all without ever duplicating anything in the actual data files — making wiki maintenance hassle-free and fitting new music into the wiki as a whole easy and rewarding!

Track documents are stored in album files; after the album header document, use `Track: (Track Name)` to start a track document.

Tracks only have a few key fields, with lots of additional fields filling in further details, bonus files, and relationships with artists and other tracks. So, some tracks are as detailed as this...

```
Track: Sburban Jungle (Brief Mix)
Artists:
- Michael Guy Bowman
Duration: '1:36'
URLs:
- https://youtu.be/DKmXadfEnog
Cover Art File Extension: jpg
Referenced Tracks:
- track:sburban-jungle
Sampled Tracks:
- track:sburban-jungle
Sheet Music Files:
- Title: Sheet music by Gamehunter
  Files:
  - 'Sburban Jungle (Brief Mix) - Gamehunter.pdf'
MIDI Project Files:
- Title: MIDI by Unknown
  Files:
  - 'Sburban Jungle (Brief Mix) - Unknown.mid'
Commentary: |-
    <i>Michael Guy Bowman:</i>
    At this point I was just giddy about the release of "Sburban Jungle", although the version that appears here is deliberately truncated. The full version later released on [[album:homestuck-vol-4|Volume 4]] was already fully written at this point, although we figured that it would be best to give only a taste and otherwise save it for later.
```

...while others only handle the essentials!

```
Track: Once Upon a Time
Duration: '1:28'
URLs:
- https://tobyfox.bandcamp.com/track/once-upon-a-time-2
- https://www.youtube.com/watch?v=3BR7-AzE2dQ
- https://open.spotify.com/track/4XX5uZb9PvTKh8Nm2KSJfk
```

> Certain fields inherit from the album the track is part of. **Save time by using the corresponding album field, if most of the tracks in an album share the same value** (differing from wiki default):
>
> * track's `Artists` inherits from album's `Artists`
> * track's `Cover Artists` inherits from album's `Default Track Cover Artists`
> * track's `Cover Art Date` inherits from album's `Default Track Cover Art Date`, default: album release date
> * track's `Cover Art File Extension` inherits from album's `Track Art File Extension`, default: `jpg`
> * track's `Has Cover Art` inherits from album's `Has Track Art`, default: `true`

## Track objects

Referenced as `track:directory` or by name.

### Essential info fields

* `Track`: track name
  * [Learn about naming albums and tracks for HSMusic.](../guidelines/albums-and-tracks.md#name-albums-and-tracks-according-to-bandcamp-release)
* `Directory`: unique identifier among other tracks
  * [Learn about the Directory field, used by almost every wiki object.](../guidelines/common-fields.md#directory-field)
  * This is used for the URL the track will be accessed at: https://hsmusic.wiki/track/DIRECTORY/
  * Tracks and other wiki objects reference a track by its directory: `'track:DIRECTORY'`.
* `Duration`: track listening duration
  * These are written in standard "hour:minute:second" format, e.g:
    * `0:57` (57 seconds)
    * `4:13` (4 minutes, 13 seconds)
    * `3:05:20` (3 hours, 5 minutes, 20 seconds)
  * If `Duration` isn't provided, track listings will display `(_:__)`, and the track will be skipped when summing together lengths to get an album's total duration.
  * On HSMusic, if a track doesn't have a clear-cut duration (e.g, dynamic loops ripped from video games which didn't get an official in-game soundtrack release), don't include a duration for the track at all.
* `Date First Released`: date of original release for tracks that were made available prior to album release (and other special cases)
  * This is pretty much exclusively for organization purpose on artist pages, where it doesn't make sense to chronologically position a track at one time if it was first released years earlier! At this point, `Date First Released` is more or less defunct, since we have the `Originally Released As` field for cataloguing specific releases (which displays more cleanly in the artist chronology, too). However, `Date First Released` may still be used in certain cases where there isn't another album release that has the relevant date.
    * For example, compilation album [The Funk McLovin Homestuck Experience](https://hsmusic.wiki/album/the-funk-mclovin-homestuck-experience/) uses `Date First Released` for each track's earlier release on YouTube.
    * The 2019 re-release of [One Year Older](https://hsmusic.wiki/album/one-year-older/) includes a bonus track, [it's good to see you again](https://hsmusic.wiki/track/its-good-to-see-you-again/). Rather than create a whole new album with basically the same structure, an additional track section ("2019 release") was added with the single new track, which has `Date First Released` set to a *later* date than the rest of the album. This way, the track is positioned correctly in Erik Scheele's track chronology.

### Configuration & layout

* `Cover Art Date`: date cover art created/added, if different from track/album release date
  * Usually all the art for an album is released at the same time. If that time is different from when the album itself released, set the album's `Default Track Cover Art Date`. If specific tracks got their art added at a different time than the rest, use `Cover Art Date` on those tracks.
  * If left unspecified, inherits from the track's *own* `Date First Released`; or the album's `Default Track Cover Art Date` field; or the album's original date.
  * This is displayed on track info pages only when different from the track's own release date.
* `Cover Art File Extension`: corresponds to media file
  * [Learn about file extension fields.](../common-fields.md#file-extension-fields)
  * If left unspecified, inherits from the album's `Track Art File Extension` field (*not* the album's `Cover Art File Extension`), or `jpg` by default.
* `Has Cover Art`: disable to inherit from album cover art, or enable for one track with unique art amongst an album mostly without
  * If left unspecified, inherits from the album's `Has Track Art` field, which is true by default.
  * Generally you'll only use this field if one or a few tracks uniquely lack (or have) cover art while most of the others do (or don't).

### Content fields

* `URLs`: web URLs for track playback or purchase
* `Commentary`: commentary from track artists and others related
  * [Learn how to format the Commentary field.](../guidelines/common-fields.md#commentary-field)
* `Lyrics`: lyrics for vocals
  * [Learn how to format the Lyrics field.](../guidelines/common-fields.md#lyrics)
  * [Read detailed guidelines on filling out lyrics for HSMusic.](../guidelines/lyrics.md)
* `Additional Files`: bonus files associated with the track (there aren't any current uses of this field on the wiki)
* `Sheet Music Files`: PDFs and other files containing sheet music for the track
* `MIDI Project Files`: MIDI files for the track as well as DAW or tracker/sequencer project files
  * These three fields share the same structured format - [learn how to format fields like Additional Files.](../guidelines/common-fields.md#additional-files-field)

### Relational fields

* `Originally Released As`: links track to its earliest release
  * Generally, don't combine with this `Date Originally Released` - use whichever is more appropriate.
  * Tracks with this field are displayed on the wiki as "re-releases", dimmed out a little in chronological listings (such as the list of tracks that an artist composed).
* `Referenced Tracks`: links track to musical references, usually by leitmotif
* `Sampled Tracks`: links track to direct audio samples, often (but not exclusively) vocal clips
* `Artists`: links track to its compositional artists
* `Contributors`: links track to other contributors, e.g. vocalists, performers
  * [Learn about differentiating artists and contributors for HSMusic.](../guidelines/albums-and-tracks.md#differentiate-between-artists-and-contributors)
* `Cover Artists`: links track to visual artists who created its artwork
  * All artist fields may include descriptions of the contribution in parentheses, e.g. `L. L. Zamenhof (lyrics)`, `Willow Ascenzo (orchestra, choir)`, `Kait Linney (lines)`.
* `Art Tags`: links track to art tags representing characters or features present in its artwork
