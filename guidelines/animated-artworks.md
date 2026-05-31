# Animated Artwork Guidelines

The music wiki is not capable of automatically downscaling GIFs for the purposes generally served by thumbnails, i.e. reducing file size while preserving a reasonable degree of picture quality, so that artworks still look good on users' devices, but don't use up so much network bandwidth. Large images take a long time to download and can leave the page potentially unresponsive. Small images help the page respond quickly and, in the case of GIFs, ensure the artwork animates almost as soon as it is first visible at all. As such, GIFs must be manually adjusted/compressed to keep a low filesize. Details follow in this document.

## "Eye strain" warning

Unlike audio and video elements, animated artworks play as soon as they are loaded (basically as soon as you can see the page). Since automatic motion is an extremely uncommon element on the music wiki in general, we make use of an "eye strain" warning tag (`cw: eye strain`) to keep some artworks concealed until clicked. There is not an objective threshold for when to use this warning. View existing examples and ask in the wiki Discord if you aren't sure.

## Compressing GIFs

We highly recommend using [Ezgif.com](https://ezgif.com) for all GIF editing, as long as your network connection is fast enough you can tolerate uploading and downloading/previewing medium to large files. Offline tools like Imagemagick and ffmpeg exist and can be used mostly analogously, but this document assumes access to Ezgif.

This section also covers guidelines. If downscaling GIFs were a trivial process (and if we had the will to code it!) then the wiki would take care of compression automatically. But some artworks will compress better than others, so combine techniques as you see fit. We always provide reference to the original GIF (see section later in this document), so there is less weight on your shoulders than you might worry. If the artwork "feels" about like the original, or a reasonably close approximation, then the fine details, which are difficult to precisely control, don't matter so much.

The music wiki does not support APNG files, mostly because the thumbnail generator can't automatically differentiate between regular PNG and animated PNG. In the future, higher-quality animated artworks will be possible at the same file size. Similar techniques as below should still apply where needed.

### Current targets

"Soft" maximum in file size: ±2.8 MB (2,800,000ish bytes)
"Hard" maximum in file size: ±3.0 MB (3,000,000ish bytes)
"Soft" minimum in file size: ±1.0 MB (1,000,000ish bytes)

Maximum in image dimensions: 500x500

GitHub cannot host files greater than 100 MB. (Consequently, neither can the wiki.) This has bearing on including the original file under "additional files" (see section later in this document).

### Techniques

**Always start with the original GIF.** This ensures you don't inadvertently "double up" on similar types of compression and reach a worse picture quality than if you'd followed the same sequence of changes, but started from the original file. Even if you are adjusting existing GIFs in the wiki's media files, ensure you are working with the original file or an equivalent hosted on the wiki or elsewhere. "The original file" is generally included with the album download or in a "bonus art" package. The wiki is generally thorough with its "additional artwork" sourcing, so you should be able to start from the wiki page itself to locate the original.

**Don't stress about recording the exact sequence you follow.** You can take notes for your own learning or share details if you like, but none of this is expected. Compressed animated artworks will always be recreated at a later point and the exact same sequence will rarely if ever be followed. No one render carries all that much importance.

**Drop frames from very large artworks with a fast framerate.** GIF file sizes are basically proportional to the number of frames, so dropping half the frames is very effective. This should only be done with animations that have very smooth motion, i.e. tweening rather than frame-by-frame illustration.

* (Ezgif) -> Optimize -> GIF optimizer
* Set "Optimization method" to "Remove every 2nd frame", which is under the "Drop frames" section of the dropdown
* Keep "Adjust speed to match the original" checked (this checkbox appears once you've picked "Remove every 2nd frame")

**Scale the artwork down.** Refer to "current targets" above. This is a good early step because, like dropping frames, it discards actual pixels / color values. GIFs are optimized in terms of unique colors so the fewer pixels, the easier to optimize.

* (Ezgif) -> Transform -> Resize
* Fill "width" and "height" boxes with the target dimensions
* Leave "Percentage" empty
* Leave "Resize method" on its default
* If you're working with a non-square artwork, set "If the aspect ratio does not match" to "Force original aspect ratio"
* If the original artwork is already at the target dimensions or smaller, skip scaling it down
* If the artwork is near the "soft minimum" target file size once you've scaled it down, you can stop here and skip any further optimizations

**Just try small numbers in the "GIF optimizer" screen.** You can start with "Lossy GIF" and a low compression level (minimum is 5), but we usually set "Optimization method" to "Combined: remove duplicates + transparency + lossy" and also start with a low "Fuzz %". We can't offer specific threshold values; smaller values are better, and smaller filesize is better, and these are arbitrarily pitted against each other. Follow your heart. Regardless, if your GIF is well above the "soft minimum" even if it's still below "soft maximum", then we recommend trying a low compression level. If it substantially reduces the filesize, the change should be easily agreeable (hardly affect picture quality in a noticeable way).

## Refer to original artworks

First ensure the animated artwork is visibly labeled "downscaled".

```
Track Artwork:
- Label: Alternate artwork (downscaled)
  Directory: alternate
```

Include a "via" field (`Source`) to indicate where the original is accessible.

```
Track Artwork:
- Label: Alternate artwork (downscaled)
  Directory: alternate
  …
  Source: album download
```

Include an entry in `Additional Files`. If the file is greater than 100 MB then GitHub will refuse to accept your file and you must remove it from your commit (consequently, we can't exchange/sync the file, so can't include it on the wiki). In this case write an entry like below:

```
Additional Files:
- Title: Alternate artwork (original file)
  Description: >-
    This file is too large to currently include on the music wiki! It's included in the album download, though.
```

Otherwise, include the original artwork in `album-additional` (with track number removed but otherwise keeping original filename). Refer to it in an `Origin Details` field on the artwork, as well.

```
Track Artwork:
- Label: Alternate artwork (downscaled)
  Directory: alternate
  …
  Source: album download
  Origin Details: >-
    See "additional files" for original .gif

Additional Files:
- Title: Alternate artwork (original file)
  Description: Included in the album download.
  Files: [Naught (Alt).gif]
```

Skip the `Artists` field in the "additional files" entry, because the artists are already credited on the relevant track artwork.
