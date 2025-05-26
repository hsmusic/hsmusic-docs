# Changelog Guidelines

Here's a reference how-to with all the current standards for [the changelog](https://hsmusic.wiki/changelog/) on HSMusic Wiki. You're encouraged to follow along and add changelog entries to your own pull requests / branches as you make data changes and additions; you can also refer here if you're filling out the changelog for someone else's branch, or your own, after the fact.

Throughout this document, **"the changelog"** is the entire changelog; **"changelogs"** are the complete top-to-bottom parts of the changelog, dated and titled, one for each update; **"changelog sections"** are the parts of entries titled "album additions", "data fixes" etc; and **"changelog entries"** are the individual list-items representing each change and addition.

### Starting the changelog for a new update

At the moment, all changelogs are kept in one data file, `static-page/changelog.yaml`. When you want to start the changelog for a new update, start from a clean git workspace, and make a commit that *only* includes the name of the update (or a placeholder), the date (or a placeholder), and a handful of expected section titles. For example:

```
<h2 id="1-jan-2099" class="major-release"><html:a href="#1-jan-2099">[[date:1 January 2099]] - Allan, wouldn't you?</a></h2>
<h3>album additions</h3>
<h3>other additions</h3>
<h3>data fixes</h3>
<h3>directory changes</h3>
```

If this is planned to be a major release (one that includes album additions or substantial new site features), keep the `class="major-release"` attribute; otherwise, remove it.

You'll want to put this at the top of the changelog, above the otherwise-latest changelog, with a blank line between the two. (There are never any blank lines *within* a changelog.)

Commit this, and rebase commits which actually introduce data changes on top of it - the changelog commit should be the first for each update. (Entries may be added into this changelog either as part of the commits that make data changes, or in chunks when reviewing/finalizing pull requests.)

It's OK to add new sections to this changelog in later commits. Filling out the basic ones just helps with rebasing early on in the update.

### Finalizing the changelog when an update releases

Make sure the name and date are replaced if they were placeholders, and remove any blank sections. If this is a major update, check that there's a `class="major-release" attribute, and add a line (before the first section) linking to the news entry for this update:

```
<h2 id="12-jun-2024" class="major-release"><html:a href="#12-jun-2024">[[date:12 June 2024]] - Snow Pollen Appreciation Station</a></h2>
(news entry: [[news-entry:snow-pollen-appreciation-station]])
```

Now's the last time to review the album addition order, and if the update includes a ton of albums, you might consider filling out an "album additions credits" area to amke that list more browsable.

Other than that, the changelog should be good to go!

### Which stuff *doesn't* go in the changelog?

Almost everything goes in the changelog! It's easier to summarize what doesn't:

* Most artist updates, including renames, new aliases, and new or removed visiting links (or dead URLs).
    * We do add a changelog entry when multiple artists are merged into one, though we don't list any of the names except the remaining/merged artist.
    * We do note directory changes for artists (in a directorylog), but only if the changes were exclusively for disambiguation, not the result of a rename.
* New groups that are implied through the album additions section anyway.
* Fixes for albums and tracks (etc) that are brand new to the update this entry represents - generally, the relevant people are credited in the "thanks" line for the album addition, instead.
* Minor commentary formatting tweaks - usually to individual tracks rather than across an album. Even small commentary additions go in the changelog, but just adding links to mentioned tracks (for example) can go unmentioned.

Everything else goes in the changelog. The appropriate position should be in the list below, but if it isn't, give us (Nebula) a shout/ping - we'll direct you to the right spot, and update the list, too.

### Ordering and sectioning changelog entries

Changelog entries are for the most part grouped into these high-level sections:

1. site changes (new or updated features)
2. bug fixes
3. album additions
4. other additions, or just "additions" if this update has no new albums
5. data changes (usually editorial stuff or smaller presentational tweaks)
6. data fixes
7. directory changes

This is a reliable section-ordering, but occasionally new or one-off sections are used to bring together a lot of related changes/additions, e.g. for the new [additional names](https://hsmusic.wiki/changelog/#additional-names-intro) feature. You can adjust the layout of the sections for an update if it would suit that update well. Most times the order above should work, though.

Within each section, we try to stick to a particular order, so that changelogs are consistently navigable update-to-update. Any deviation from the order below is probably unintentional - and there *are* deviations, certainly in previous updates. If you're looking for something missing here, give us (Nebula) a ping! We'll tell you where it goes and fit it below.

1. site changes
2. bug fixes
    * No order specified for these two; the feature/code composition of each update varies pretty immensely, so follow your gut or check with us... we're almost certainly the ones filling it out anyway...
3. album additions
    * First list albums that are *not* sub-sectioned (nested) under groups or artists, then list the sub-sectioned albums.
    * For albums not sub-sectioned under a group or artist: list Official -> Fandom -> Beyond, then chronologically.
    * For albums sub-sectioned under a group or artist, just list chronologically.
    * The order of sub-sections, if present, is basically arbitrary, but typically we'll see music teams - especially fandom groups - sorted higher up than individual artists. We also see "latest releases" generally sorted earlier than album additions that represent an artist or group's long-term existing discography.
    * Album additions can be reorganized and restructured as suitable for a given update, including collapsing credits into an "album addition credits" item, for example. When in doubt, try comparing to a recent similarly-sized update. Reviewing the album addition list happens close to an update's release, when the scope of an update is fully clear, so there isn't a lot of pressure to place individual album entries in "the best spot" PR by PR.
4. other additions / additions
    * new flashes
    * new tracks - In existing albums **outside** Additional Tracks: for example, a track that was added to [More Homestuck Fandom](https://hsmusic.wiki/album/more-homestuck-fandom/) because it was referenced by some other track or featured in a flash should *not* be listed here.
    * new series - For existing groups.
    * commentary additions
    * artwork additions - ["Alternate/multiple artworks"](https://github.com/hsmusic/hsmusic-wiki/issues/70) or within commentary entries but *without* associated actual commentary.
    * background additions - For albums without backgrounds previously.
    * art tag additions
    * additional name additions
    * "additional file" additions - Including midi/project files and sheet music.
    * artwork and layout-media additions - New banners, new backgrounds/wallpapers.
    * lyric additions - For tracks that didn't already have lyrics, or new independent [lyrics entries](https://github.com/hsmusic/hsmusic-wiki/issues/397).
    * listening link additions - Including for platforms an album didn't already have links for. Don't include *fixed* listening links here.
    * commentary citation additions - For entries that didn't already have citations.
5. data changes
    * general overarching changes to an existing album's presentation - To align with a particular release or viewpoint on the album.
    * albums moved between groups - Existing groups only.
    * other presentation tweaks for albums - Adjusting banner/wallpaper styles, colorizing tracks.
    * presentational changes for artists and groups - Revised descriptions, series getting shuffled around, etc.
    * truly miscellaneous presentational changes - Anything that comes across less as a *fix,* more as an "editorial" change. These often come about because we changed what a concept in the wiki "means", and adjusted existing entries in accordance. No order specified.
    * tracks newly marked as a rerelease
    * tracks moved within an album, track section changes, and tracks moved from one album to another - Changes only, not fixes.
    * most general removals - Usually because something that previously existed as its own thing (e.g. a track) is now folded into a newer feature (e.g. additional names), but also editorial changes, like newly considering two very-similar things as one and the same. Takedowns (that are not private/unlisted for any reason), usually of particular media files, also go here.
6. data fixes
    * reference fixes for tracks
    * featuring fixes for flashes
    * crediting fixes for tracks, albums, flashes, etc
    * merged artists - Alphabetical, and show only the merged/kept name.
    * track section fixes - Like newly marking an existing track as a bonus track.
    * name fixes - Not for artists.
    * general data fixes - Stuff that's not covered anywhere else (above or below), like erroneous track durations or flash dates.
    * art tag fixes - Generally for existing tags that were missing from existing artworks' tag lists; list content warning additions too.
    * lyric fixes - For existing lyrics.
    * additional file fixes - Obvious errors; more "editorial" changes usually belong in "data changes" instead.
    * commentary fixes - Typos, mostly. Don't mention changes to do with how an artist is referred to (names, pronouns).
    * listening link fixes
    * duplicate track removals (etc) - Obvious errors only, like a track being represented in both [More Homestuck Fandom](https://hsmusic.wiki/album/more-homestuck-fandom/) and an actual album, or a track in [References Beyond Homestuck](https://hsmusic.wiki/album/references-beyond-homestuck/) not actually being referenced anywhere.
7. directory changes
    * album directory changes
    * track directory changes
    * artist/group directory changes - For disambiguation where only the directory was changed, *not* when an artist was updated in a manner that wouldn't otherwise be noted in the changelog.
    * If a ton of directory changes are closely related, consider grouping them under a separate directorylog.

Most categories above may contain relevant changes across the wiki. **Consider placement in the list above first;** next, order by (the most primary) group - Official -> Fandom -> Beyond - and finally chronologically. For example, reference fixes across the wiki always go earlier than lyric fixes across the wiki, but *within the list of reference fixes,* you sort fixes in [Homestuck Vol. 10](https://hsmusic.wiki/album/homestuck-vol-10/) closer to the top than fixes in [Land of Fans and Music 2](https://hsmusic.wiki/album/lofam2/).

Sometimes groups of related changes are sub-sectioned together, and placement within a changelog is more or less arbitrary. We don't really do this anymore but you'll see it throughout lots of old changelog entries.

### Who gets thanked? And in what order?

Virtually every changelog entry gets "thanks" text (inline, usually at the end of the entry), acknowledging contributors to that particular change. We err inclusively - if someone helped at all, they probably belong thanked!

Ordering typically depends on the placement of the change:

* For changes under "album additions"...
    1. person who literally wrote the data additions; if multiple, earlier contributors first
    2. person/people who reviewed the data additions / pull request; if multiple, earlier reviewers first
    3. general discussive contributors - Anyone who offered feedback throughout the process, that someone working more directly on the addition feels affected the results, directly or indirectly.
    4. general "background" contributors - Anyone, typically outside the HSMusic Discord server and involved with the album being added, who offered advice, feedback, or permissions to use their own material (e.g. commentary in another Discord server).
* For changes under "other additions"...
    1. person who caught/suggested the thing being added
    2. All the same order as "album additions" above.
* For changes under "data changes" and "data fixes"...
    1. person who caught/reported the thing being fixed
    2. general discussive contributors - If the person reviewing the pull request is also the one raising and summarizing/taking conclusions from discussion, they go at the start of this section.
    3. person who literally wrote the data change/fix
    4. person who reviewed the data change/fix

Most times, an individual person/name represents multiple roles above. Place them according to the earliest role.

You can refer to [#hsmusic-chat, 10/20/2024](https://discord.com/channels/749042497610842152/779895315750715422/1297741088404144178) for a handful of examples of entries with a lot of thanked names. An important summary from Lan re: "thanks" lines:

> There is a reason we *do not* credit specific roles in the same space as we "rank" inline credits. We inevitably have to choose some order for credits, short of alphabetization; we want to give the ordering *some* meaning, like, you should be able to say "let's go fucking ping Surge for being at the top of the Your Majesty credit list, she might remember what was going on here"; but we don't want anyone feeling that the list imparts any *judgement* or opinion of, whose contributions Counted More, really. They all count, it's just a light categorization for the sake of having *some* type of mnemonic.
