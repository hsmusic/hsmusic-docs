# Track Format

Track documents are stored in album files; after the album header document, use `Track: (Track Name)` to start a track document.

> Certain fields inherit from the album the track is part of. **Save time by using the corresponding album field, if most of the tracks in an album share the same value** (differing from wiki default):
>
> * track's `Artists` inherits from album's `Artists`
> * track's `Cover Artists` inherits from album's `Default Track Cover Artists`
> * track's `Cover Art Date` inherits from album's `Default Track Cover Art Date`, default: album release date
> * track's `Cover Art File Extension` inherits from album's `Track Art File Extension`, default: `jpg`
> * track's `Has Cover Art` inherits from album's `Has Track Art`, default: `true`

## Track objects

Referenced as `track:directory`.

* `Track`: track name
  * See [Album & Track Guidelines](../guidelines/albums-and-tracks.md#name-field).

* `Directory`: unique identifier among other tracks
  * This is used for the URL the track will be accessed at: https://hsmusic.wiki/track/DIRECTORY/
  * Tracks and other wiki objects reference a track by its directory: `'track:DIRECTORY'`.
  * If this isn't provided, it will automatically be generated from the title similarly to how Bandcamp works. It's tuned for English titles, so most other languages are best off specifying the directory manually.
  * Guideline: Use all lowercase, avoid non-ASCII characters, and reflect how a human reads the title: "Riches to Ruins Movements I & II", `riches-to-ruins-movements-i-and-ii`. Exercise some leeway for troll typing quirks: "We Are +og3th3r", `we-are-tog3th3r`.
  * Guideline: Directories are always unique for each of a given type of document. If two tracks would have the same directory, distinguish by album or else artist: `disc-1-lofam4`, `i-dont-want-to-miss-a-thing-aerosmith`.
  * Note: We don't currently have set guidelines for Japanese and other non-Latin scripts. (Compare: 暗闇の中の光, `light-in-the-darkness`, and がんばってＤＡＶＩＤさん, `vaporwave-2016-track11`.)

* `Duration`: track listening duration
  * **Examples:**
    * `0:57` (57 seconds)
    * `4:13` (4 minutes, 13 seconds)
    * `3:05:20` (3 hours, 5 minutes, 20 seconds)
  * If this isn't provided, track listings will display as `(_:__)`, and the track will be treated as zero seconds long (no duration).
  * Guideline: If a track doesn't have a clear-cut duration (e.g, dynamic loops ripped from old console games), it's probably best to leave it as unset.

* `Date First Released`: date of original release for tracks that were made available prior to album release (and other special cases)
  * Guideline: This is pretty much exclusively for organization purpose on artist pages, where it doesn't make sense to chronologically position a track at one time when it was first released years earlier. At this point, it's mostly defunct, since we have the "Originally Released As" feature for cataloguing specific releases (which displays more cleanly in the artist chronology, too). However, it may still be used in certain cases where there isn't another album release that has the relevant date.
    * For example, compilation album [The Funk McLovin Homestuck Experience](https://hsmusic.wiki/album/the-funk-mclovin-homestuck-experience/) uses `Original Date` for each track's earlier release on YouTube.
    * The 2019 re-release of [One Year Older](https://hsmusic.wiki/album/one-year-older/) includes a bonus track, [it's good to see you again](https://hsmusic.wiki/track/its-good-to-see-you-again/). Rather than create a whole new album with basically the same structure, an additional group ("2019 release") was added with the single new track, which is `Original Date`'d as a *later* date than the rest of the album, placing it correctly in Erik Scheele's track chronology.
    * All this is subject to change according to whatever form the upcoming "multiple releases" feature takes.

* `Cover Art Date`: date cover art created/added, if different from track/album release date
  * If left unspecified, inherits from the track's *manually specified* `Date First Released`; or the album's `Default Track Cover Art Date` field; or the album's original date.
  * This is displayed on track info pages only when different from the track's own release date.
  * Guideline: This is mostly used for digital track art anthologies, where fans come together to add original artworks to an album released without art.
  * Subject to change with upcoming "multiple artworks" feature.

* `Cover Art File Extension`: corresponds to media file
  * Don't include the "." separator: `Cover Art File Extension: png`, not `.png`.
  * If left unspecified, inherits from the album's `Track Art File Extension` field (*not* the album's `Cover Art File Extension`), or `jpg` by default.

* `Has Cover Art`: disable to inherit from album cover art, or enable for one track with unique art amongst an album mostly without
  * If left unspecified, inherits from the album's `Has Track Art` field, which is true by default.

* `Lyrics`: vocal lyrics
  * Guideline: Include the whole lyrics verbosely, instead of shorthands like "[2x Chorus]".
  * Guideline: Insofar as vocal lines can be discerned from instruments, try to transcribe everything, including non-"music" lines, quiet vocals, optionally echo effects, etc
  * Guideline: Just ask Niklink for decision making on any lyrics, he's to credit for pretty much all lyrics present on the site ATM lol

* `Commentary`: commentary from track artists and others related
  * See (TODO) Commentary Format

* `Additional Files`: bonus files associated with the track, currently unused
  * See (TODO) Additional Files Format

* `Originally Released As`: links track to its earliest release
  * Generally, this should be used instead of `Date Originally Released`, not alongside.
  * Tracks with this field are displayed on the wiki as "re-releases", dimmed out a little in chronological listings (such as the list of tracks that an artist composed).
  * Subject to change with upcoming "multiple releases" feature.

* `Referenced Tracks`: links track to musical references, usually by leitmotif
  * Guideline: List references by the order they are first present in the track; don't list an identical reference twice.
  * Often these are listed on Bandcamp pages already, and can be sourced from there, especially if you aren't familiar with the musical material being referenced.

* `Sampled Tracks`: links track to direct audio samples, often (but not exclusively) vocal clips
  * This feature is mostly unused right now.

* `Artists`: links track to its compositional artists
  * May include parenthical descriptions, e.g. `'L. L. Zamenhof (lyrics)'`.
  * Guideline: The line between "artists" and "contributors" is grey, and internally, it's an arbitrary distinction. "Artists" generally refers to people who played a major role in composing the track, while "contributors" tends to center on performance. See [`track:harlequin-rock-version`](https://hsmusic.wiki/track/harlequin-rock-version/) for an example.

* `Contributors`: links track to other contributors, e.g. vocalists, performers
  * May include parenthical descriptions, e.g. `'Willow Ascenzo (orchestra, choir)'`.
  * See `Artists` for guidelines.

* `Cover Artists`: links track to visual artists who created its artwork
  * May include parenthical descriptions, e.g. `'Kait Linney (lines)'`.
  * Visual and musical artists are the same document type, and some tracks actually have a shared composer and cover artist.
  * Format subject to change with upcoming "multiple artworks" feature.

* `Art Tags`: links track to art tags representing characters or features present in its artwork
  * Guideline: On HSMusic, we have two general categories of tags - characters and settings - and many tracks have both. Don't be afraid to create new tags for characters present in fanventures, etc (though we currently only tag *settings* from Homestuck proper).
  * Format subject to change with upcoming "multiple artworks" feature.
