# Common Field Guidelines

These guidelines are sorted alphabetically. Some link back to other sections in the guidelines area, so this is a good place to start browsing if you're just getting started with the data format and looking for details on any commonly occurring fields.

### `Additional Files` field

Additional files are extra files pertinent to a particular album or track — usually ones which come with the album download or are "companion" files, like album booklets, desktop wallpapers, included lyrics files, etc. The format for `Additional Files` is a little more involved than most other fields. Here's an example:

```
Additional Files:
- Title: Album Booklet
  Files:
  - Gristmas Carols.pdf
- Title: Bandcamp Banner and Background
  Files:
  - banner.png
  - bg.jpg
```

The `Title` is a human-readable name clearly identifying what you'd be downloading, and `Files` is a list of available files. Often times there's only one file associated, but if a few files are clearly related to each other, they can be bunched up under the same title.

The actual files are stored in the wiki's `media` folder, under `album-additional` (which is adjacent to `album-art`). They're grouped together by album (according to the album's directory, like track art). For example:

```
data/
  albums/
    gristmas-carols.yaml

media/
  album-art/
    gristmas-carols/
      cover.png
      track1.png
      (etc)
  album-additional/
    gristmas-carols/
      Gristmas Carols.pdf
      banner.png
      bg.jpg
```

You can use the `Sheet Music Files` and `MIDI Project Files` fields, which follow the same exact format, to collect those files under a more particular field, which will make them get a specialized look on the wiki and show up in listings like "Tracks - with Sheet Music". (Media files listed in these fields are stored in the same folder under `album-additional`.)

### `Color` field

Colors are always represented with hexadecimal values on the wiki. We don't support "special" colors like `red`, `blue` or `turquoise`, nor alternative color formats like `hsl` and `lch`. Colors are three- or four-channels (red, green, blue, optionally alpha) and each channel gets one or two digits:

* `#rrggbb` format: `#f8d4a0` is a bright pastel orange.
* `#rgb` format: `#88a` is the same as `#8888aa` (cold grey).
* Alpha channel (transparency) is supported too: `#rrggbbaa`, `#rgba`.

Colors are used all over the wiki, but generally speaking every data object is associated with one color, and that's used as the basis for colors displayed on any associated pages, as well as for most links to the object. Some objects will inherit the color from a "parent" object by default, for example tracks of an album or groups under the same category. If no color is specified and there's not a relevant "parent" object with its own color, objects take the color from the [Wiki Info document](../documents/wiki-info.md).

If you're running your own wiki, you can apply whatever colors you like or selectively tag certain objects but not others. On HSMusic, we apply custom colors to every instance of these kinds of objects:

* Albums
* Group categories (but not individual groups)
* Flash acts (but not individual flashes)
* Art tags

On HSMusic, we try to choose a color for each album (for example) which matches the art and design for that album. There's some room for creative liberty here (for example, choosing an accent color rather than the most prevalent color in a design). Some examples to consider:

* [Ancestral](https://hsmusic.wiki/album/ancestral/): red from the blood across the moon (rather than one of the purples or blue-greens making up the misty colors in the background)
* [Shortcuts](https://hsmusic.wiki/album/shortcuts/): muted blue-grey reflecting the calmer, more down-to-earth feel of the album (it's roughly pulled from the album wallpaper; the cover itself has similarly muted colors, without an obvious "primary" color behind its design)
* [DELTARUNE Chapter 1 OST](https://hsmusic.wiki/album/deltarune-ch1-ost/): bright cyan pulled from the "empty town" wallpaper (rather than the heart red in the logo, which would just be repeated for each chapter's album)

On HSMusic, for accessibility purposes, we also aim to keep each color clearly visible against a dark background. Troll-related art tags and tracks are colored according to their caste, for example, but since indigo-blue blood in Homestuck is very dark (for text visible against a white background), a different brighter blue is used instead. Use a tool like [Accessible Colors](https://accessible-colors.com) to check for AA compliant colors (contrast ratio at least 4.5 and, on the wiki, usually a fair bit higher; make sure to set the background color around `#222`).

### `Commentary` field

Artists often share their thoughts on their music and other artworks! These can be chronicled in the `Commentary` field on albums and tracks.

Commentary fields contain multiple lines of text. To represent that in YAML, put `|` and `-` together at the end of the line with `Commentary:`, then put the same number of spaces (generally 4) before each line in the commentary field. For example:

```
Track: A Very Merry Gristmas Indeed
Artists:
- ndividedbyzero
Commentary: |-
    <i>ndividedbyzero:</i>
    When I set out to make my first song for this album I only had two things in mind. The first was to make at least part of it feel like one of those classic 80s Christmas songs that everyone loves, a la Wham!. The second was to make it feel like the in-betweens of the holiday experience: after the unwrapping of presents or whichiver main celebration applies, in the midst of the gathering, before everyone's said their goodbyes and while the spirit of holiday cheer still remains. A theme you could have a cup of hot chocolate to while engaging a seldom-seen relative in lighthearted conversation.
    Whether I succeeded in these things is up to you. But in any case, I had a whole lot of fun making this!
---
Track: You're A Mean One, Mr. Slick
...
```

(You can include blank lines to make reading the YAML file easier, but on the site, they're just skipped: every line is considered a separate paragraph, so include all the text in a paragraph on one line and enable soft word wrap in your text editor to make editing easier.)

Commentary will often reference other tracks, albums, or artists. You can make the wiki display a clickable link using special square-bracket tags:

```
Track: Sburban Cascantdown
Artists:
- Noisemaker
Commentary: |-
    <i>Noisemaker:</i>
    To be completely honest it's just [[track:cascante]] from [[album:cool-and-new-voulem1|Voulem 1]]. I regret not using my otamatone but at least [[artist:bambosh]] got some [[track:backyard-dumb|sweet use]] out of it.
```

If the name of the track you're linking (for example) is already how the commentary author wrote it, you just include it as `[[track:`, then the directory of the track, then `]]`. If the author wrote it differently or referenced it as some natural part of the sentence, add a `|` symbol after the directory, then fill the words in before `]]`.

If something has multiple commentary entries (from different artists), put them together in the same field, using a `<i>Artist Name:</i>` line to differentiate each entry:

```
Album: Homestuck Vol. 10
Commentary: |-
    <i>Robert J! Lake:</i> (project manager)
    This almost didn't happen.
    As of release day, it's been exactly four full years since the last numbered Homestuck volume, with only one full album between then and now.
    (more commentary)

    <i>Marcy Nabors:</i> (co-organizer, mastering engineer)
    Homestuck Volume 10, the big 1-0!
    (more commentary)
    Enjoy the tunes!

    <i>Lexxy:</i> (cover artist)
    Homestuck will always hold a warm, nostalgic place in my heart, so despite drafting up a handful of concepts - from the graphic and representational to the tongue-in-cheek referential - I ultimately ended up going with the one that expressed that affection the most.
```

### `Directory` field

[*See also: Behaviour details about the Directory field.*](../documents/common-fields#directory-field)

The directory field identifies what address an object will be accessed at online, and how a particular data object will be referenced by other objects on the wiki (and text content). Almost every kind of object on the wiki has a directory!

Directories are calculated automatically based on data object names, but they can also be specified by hand when necessary. If two objects of the same sort share a name (or have names which are similar enough to make the same directory), the wiki software will report that you need to give at least one of them a custom directory and resolve the conflict. Also, the algorithm for generating a directory is only tuned for English, and fails on just about anything besides the standard Latin/ASCII script. You'll want to specify a directory by hand in these cases.

<!-- On a technical level, directories are necessary for differentiation, but they're also meant to be read and written by humans - you'll deal with directories a lot as you enter data, and they're the identifying part of wiki page URLs too. That means directories should always be clearly legible, and should be descriptive when you need to specify one manually to resolve a conflict. For example, don't give Light from *Homestuck Vol. 5* the directory `light` and Light from *Medium* the directory `light-2`; instead, give them `light-vol5` and `light-medium`. -->

Some examples of when you might manually set a directory:

* Resolving a conflict: name three tracks named "Penumbra Phantasm" need to be distinguished somehow! On HSMusic, we usually distinguish by album: [`penumbra-phantasm`](https://hsmusic.wiki/track/penumbra-phantasm/) for the original, [`penumbra-phantasm-act-8`](https://hsmusic.wiki/track/penumbra-phantasm-act-8/) from Act 8 Volume 1, and [`penumbra-phantasm-aspect-clock`](https://hsmusic.wiki/track/penumbra-phantasm-aspect-clock/) from ASPECT/CLOCK. When tracks are from the same album or aren't associated with a specific album (on the wiki), we use the artist instead: [`i-dont-want-to-miss-a-thing`](https://hsmusic.wiki/track/i-dont-want-to-miss-a-thing/) from the official album Homestuck Vol. 6, and [`i-dont-want-to-miss-a-thing-aerosmith`](https://hsmusic.wiki/track/i-dont-want-to-miss-a-thing-aerosmith/) for the movie original it's based on.

* "Vaporwave" style titles with spaces between each letter - the directory algorithm turns "a e s t h e t i c a d e" to `a-e-s-t-h-e-t-i-c-a-d-e`, but it's just more useful in URLs and wiki data to refer to it as `aestheticade`, for example.

* Complete bullshit titles! "kis da boy #<3 #<3 #otp #aaAAAAAA #OMFG #!!!" is turned into `kis-da-boy-3-3-otp-aaaaaaaa-omfg`. This is awful (those hearts have nothing to do with the number 3, to say the least), so you could assign it a more reasonable directory like [`kis-da-boy`](https://hsmusic.wiki/track/kis-da-boy/).

* Non-latin scripts in titles get skipped altogether by the directory algorithm, so these titles need to either be romanized or translated manually. (On HSMusic, this usually depends on how English speakers typically refer to the title in question.)

* Similar to the above, accented Latin letters also need to be handled manually. For example, "Funiculì, Funiculà" would automatically be assigned the directory `funicul-funicul`; instead we manually specify it as [`funiculi-funicula`](https://hsmusic.wiki/track/funiculi-funicula/).

* Same deal for variant Latin scripts like small-caps: "ᴀsᴘᴇᴄᴛ/ᴄʟᴏᴄᴋ" would get a totally empty directory according to the algorithm! It's specified manually as [`aspect-clock`](https://hsmusic.wiki/album/aspect-clock/).

* In the most extreme cases, you may need to resort to violence. `『H☯MESTUCK VAP☯RWAVE 2016 RUH-RUH-RUH-ＲＥＭＩＸ』アンドレア・ヒューシー・グーグル翻訳` is not `h-omestuck-vap-rwave-2016-ruh-ruh-ruh` but `vaporwave-2016`, and `ＳジＢャＵンＲグＢル` is not an empty directory but `vaporwave-2016-track5`.

### `Lyrics` field

Lyrics are multiline strings, and they support `[[track:sburban-jungle]]`-style links just like the `Commentary` field. [Read more about formatting the Commentary field.](#commentary-field) (Just about all the same formatting applies here!)

The only formatting difference is with how line breaks and empty lines work. Write them the same way most lyrics sites do: an empty line represents the space between two verses, and lines which are "together" will be displayed in the same HTML paragraph, with line breaks preserved. Here's how a `Lyrics` field might look:

```
Lyrics: |-
    We're no strangers to love
    You know the rules and so do I
    A full commitment's what I'm thinking of
    You wouldn't get this from any other guy

    I just wanna tell you how I'm feeling
    Gotta make you understand

    Never gonna give you up
    Never gonna let you down
    Never gonna run around and desert you
    Never gonna make you cry
    Never gonna say goodbye
    Never gonna tell a lie and hurt you
```

There are a bunch of details on how we format lyrics for HSMusic in particular, so [learn more about formatting lyrics](lyrics.md) if you're adding an album to the HSMusic wiki or want to see how we do things!

### `Name` field

- [Name albums and tracks according to Bandcamp release](./albums-and-tracks.md#name-field)
