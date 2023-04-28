# Flash Format

> Flashes make a handy little view for interactive or animated pieces in a larger work. Admittedly, they're definitely Homestuck-centric, so they're not super flexible for fitting into other sorts of wikis yet! Flashes feature tracks (which will automatically link to the flashes they're featured in) and can have contributor credits. They're sectioned by flash acts, which make for a dynamic (albeit currently hard-coded) sidebar and a very fancy gallery-style index.

Flash documents are stored all in one file, `flashes.yaml`, one document (entry) per flash. They're grouped by flash act documents.

The website section for flashes is called "Flashes & Games". Apart from this, these data objects are always called flashes.

The flashes file will, in its entirety, look something like this:

```
Act: Act 1 - The Note Desolation Plays
Anchor: a1
Color: '#7799ff'
Jump: Side 1 (Acts 1-5)
Jump Color: '#4ac925'
---
Flash: 'John: Examine games on CD rack.'
Page: '31'
Date: April 16, 2009
Featured Tracks:
- Problem Sleuth Theme
# ...
---
Act: Act 6 Intermission 3 - Ballet of the Dancestors
Anchor: a6i3
Color: '#b536da'
---
Flash: '[S] ACT 6 INTERMISSION 3'
Page: '5263'
Date: August 31, 2012
Contributors:
- Killian Ng (art)
- Xamag (art)
# ...
```

## Flash documents

Referenced as `flash:directory`.

* `Flash`: flash name
* `Directory`: unique identifier among other flashes (inherits from Page before Name)
* `Page`: page number on https://homestuck.com
* `URLs`: web URLs for flash playback (or game purchase)

* `Date`: flash posting/release date
* `Cover Art File Extension`: corresponds to media file

* `Featured Tracks`: tracks that play (in full or part) as part of the flash
* `Contributors`: artists who contributed directly to flash, e.g. art media, programming

## Flash act documents

* `Act`: act name
* `Color`: theme color representing act
* `Anchor`: unique identifier among other acts
* `Jump`: title of quick link on Flashes & Games index
* `Jump Color`: color of quick link on Flashes & Games index
