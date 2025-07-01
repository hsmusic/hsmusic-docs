# Field Ordering Guidelines

**In general,** you're probably going to be fine if you model off of existing YAMLs, no matter what kind of data you're adding. But not everything on the wiki is ordered quite consistently, so here's a golden guideline you can refer back to, when in doubt!

**This reference only offers how to order fields.** It doesn't tell you *what* those fields are about, and chances are very good that you won't want to use *all* fields, on... just about any document. This'll just help you know where to put 'em, when you do use 'em.

We're only covering the most complex and involved documents here at the moment - albums and tracks.

## Ordering track fields

The *current* canonical reference is in the source code: [`src/data/things/track.js`](https://github.com/hsmusic/hsmusic-wiki/blob/preview/src/data/things/track.js), ctrl+F `yamlDocumentSpec`. If something is missing here, go look there, and give us a shout!

- **Identifying metadata:**
  - `Track`
  - `Directory`
  - `Suffix Directory`
  - `Always Reference By Directory`
  - `Main Release`
  - `Bandcamp Track ID`
  - `Bandcamp Artwork ID`
  - `Additional Names`
  - `Date First Released`

- **Credits and contributors:**
  - `Artists`
  - `Contributors`

- **General configuration:**
  - `Count In Artist Totals`
  - `Has Cover Art`

- **General metadata:**
  - `Duration`
  - `Color`
  - `URLs`

- **Artworks:**
  - `Track Artwork`
  - `Cover Artists`
  - `Cover Art Date`
  - `Cover Art File Extension`
  - `Cover Art Dimensions`
  - `Art Tags`
  - `Referenced Artworks`
  - Try not to mix these formats up within the same track. If you're using `Track Artwork` in order to access cool stuff like `Source` and `Origin Details` (or just to specify multiple artworks), then skip out on *all* the other fields here, and specify them right on the artwork instead.
  - If only a small proportion of tracks in an album need `Track Artwork`, then you can use the old-fashioned fields for the rest (or the whole album), if you prefer. But `Track Artwork` is totally objectively just nicer, and more future-proof!

- **Referenced tracks:**
  - `Referenced Tracks`
  - `Sampled Tracks`

- **Additional files:**
  - `Additional Files`
  - `Sheet Music Files`
  - `MIDI Project Files`

- **Content entries:**
  - `Lyrics`
  - `Commentary`
  - `Crediting Sources`
  - `Referencing Sources`

- **Shenanigans:**
  - `Franchises`
  - `Inherit Franchises`
  - `Review Points`

## Ordering album fields

The *current* canonical reference is in the source code: [`src/data/things/album.js`](https://github.com/hsmusic/hsmusic-wiki/blob/preview/src/data/things/album.js), ctrl+F `yamlDocumentSpec`. If something is missing here, go look there, and give us a shout!

- **Identifying metadata:**
  - `Album`
  - `Directory`
  - `Directory Suffix`
  - `Suffix Track Directories`
  - `Always Reference By Directory`
  - `Always Reference Tracks By Directory`
  - `Bandcamp Album ID`
  - `Bandcamp Artwork ID`
  - `Additional Names`
  - `Date`
  - `Date Added`

- **Credits and contributors:**
  - `Artists`

- **General configuration:**
  - `Count Tracks In Artist Totals`
  - `Has Track Numbers`
  - `Listed on Homepage`
  - `Listed in Galleries`

- **General metadata:**
  - `Color`
  - `URLs`

- **Artworks:**
  - `Cover Artwork`
  - `Banner Artwork`
  - `Wallpaper Artwork`
  - `Cover Artists`
  - `Cover Art Date`
  - `Cover Art Dimensions`
  - `Default Track Cover Artists`
  - `Default Track Cover Art Date`
  - `Default Track Dimensions`
  - `Wallpaper Artists`
  - `Wallpaper Style`
  - `Wallpaper Parts`
  - `Banner Artists`
  - `Banner Dimensions`
  - `Banner Style`
  - `Cover Art File Extension`
  - `Track Art File Extension`
  - `Wallpaper File Extension`
  - `Banner File Extension`
  - `Art Tags`
  - `Referenced Artworks`
  - The same disclaimers for track artworks apply here, except that `Banner Artwork` and `Wallpaper Artwork` aren't meaningfully supported yet, so you should skip out on those. Also sorry there are so many fields here LOL. This is basically modeled after Niklink's additions, in particular [LOFAM5A2](https://hsmusic.wiki/album/lofam5a2/).

- **Groups:**
  - `Groups`

- **Content entries:**
  - `Commentary`
  - `Crediting Sources`

- **Additional files:**
  - `Additional Files`

- **Shenanigans:**
  - `Franchises`
  - `Review Points`
