# Common Fields

## `Directory` field

[*See also: Guidelines for the Directory field.*](../guidelines/common-fields#directory-field)

When **declaring** a wiki object...

* A directory is the unique identifier for a given wiki object, differentiating it from other objects of the same type.
  * It's possible for two objects of *different* types to have the same directory, e.g. a group's eponymous album, or an art tag which incidentally has the same name and directory as an unrelated artist.

* Directories are important to actual page generation: they tell what subdirectory a given wiki object's page will be served at / written to. (Hence the name!)
  * For example, Land of Fans and Music 4's directory is `lofam4`, so anybody can access this album's wiki webpage at [https://hsmusic.wiki/album/<b>lofam4</b>/](https://hsmusic.wiki/album/lofam4/).

* Directories can be manually specified, and inherit from a wiki object's name otherwise. Best practice is generally to write them in "kebab-case", which means words are all lowercase and joined together by dashes / "minus" signs (`-`).
  * If a directory isn't specified manually, it follows this algorithm:
    1. Replace the spaces (` `) in the object's name with dashes (`-`).
    2. Replace any instances of "&" with "and".
    3. Discard any characters that aren't alphanumeric (or dashes).
    4. Replace consecutive dashes with just one dash (such as between strings of characters that were entirely removed).
    5. Discard dashes at the start or end.
    6. Make all remaining alphabet characters lowercase.
  * There are two main circumstances when a directory should be written manually: when there are multiple similarly named objects which need unique directories to differentiate them, and when an object's name doesn't lend well to the English-centric "`getKebabCase`" algorithm.
    * The way otherwise identical directories are differentiated will vary for each wiki (and often by further context). Some options include: differentiate tracks by shorthand album name, like `frost-vol6` vs `frost-medium`; differentiate albums by artist/band or year, like `homestuck-swagazaki`; differentiate artists by a longer unique username, like `kobacat` vs `kobacake`.
    * `getKebabCase` doesn't even try to support languages outside English effectively. If a name includes accents or punctuation which have a particular "ascii-fied" variant that is appropriate, that should be specified by hand. Lots of examples in HSMusic's artist data, e.g. `magnus-palsson` (Magnus Pålsson), `pokemon` (Pokémon), `satoru-kosaki` (Satoru Kōsaki).

When **referencing** a wiki object...

* Directories are used to create links between wiki objects. Most references take effect in both directions, but are only declared in one direction.
  * Example: A track page links to the track's artists, and those artists' pages each link back to the track; but those bidirectional references are only written in data files once, as the track lists its own artists, and each artist automatically computes which tracks include that artist in their artist lists.

* Most references are listed with an *object reference type*, a colon (`:`), and the object's directory.
  * Example: The album "Homestuck Vol. 6: Heir Transparent" has a manually written directory, `homestuck-vol-6`. YAML fields will reference this album as `'album:homestuck-vol-6'`. (Quotation marks are needed so it isn't treated as a YAML object, i.e. `{"album": "homestuck-vol-6"}`.)
  * Example: The track "Let's All Rock the Heist" doesn't have a manual directory, so it inherits from its name. YAML fields will reference this track as `'track:lets-all-rock-the-heist'`.

* When linking to an object from commentary and other static content, the same basic syntax is used, but with double square brackets (`[[hello world]]`) surrounding the reference. You can also use a pipe / vertical bar symbol (`|`) to show different link text than the object's actual name.
  * Example: `[[album:homestuck-vol-6]]`, `[[track:lets-all-rock-the-heist]]`
  * Example: `[[group:umspaf|UMSPAF]]` (shows "UMSPAF" instead of "Unofficial MSPA Fans")
  * Some wiki objects are represented by multiple pages (one of each type, e.g. info, gallery). See object format pages for info; replace the object reference type with the special string, for exmaple: `[[group-gallery:fandom]]`. When using the plain object reference type, the default is generally the "info" page.

* References may generally also be written as just the object's name. This is accepted as long as it's not ambiguous; if two objects (of the same type) share the same name, HSMusic will output an error letting you know to replace it with a `type:directory`-style reference.
  * In commentary and other static content, this works for tracks only, e.g. `[[Creata (Canon Edit)]]`.

## Static content

* A variety of fields across wiki data objects represent longer blocks of text, which are called "static content" or "multiline content". YAML has a number of ways to represent multiline strings, but generally a pipe and dash (`|-`) followed by a line break and the content indented is the way to go.

```yaml
Lyrics: |-
    Hello, world
    Hello, world
    Oh! hello, world
```

* Content tags can be used to insert links and (build-time) dynamic content. These usually use double square brackets, a "replacer tag", and a value. More complex syntax can be used for tags which take a variety of arguments.

```
This song is by [[artist:rick-astley]].
Want to listen to [[track:stone-halation|my favorite track]]?

[[string:artistPage.contributedDurationLine
  * artist = [[artist:quasar-nebula]]
  * duration = not even a moment]]
```

* Line breaks in static content generally represent paragraph breaks, with the exception of `Lyrics` fields, where a full empty line is used to split verses.

* Static content also supports very basic (non-nesting) block styling.
  * Put `> ` at the start of a series of lines to turn them into a blockquote.
  * Put `* ` to turn them into items of an unordered list.

## Commentary

* Commentary is [static content](#static-content).

* A given commentary field can contain multiple artists' commentary; each artist's commentary should have the header `<i>Artist Name:</i>`. This string is automatically matched and displayed on the artist's info page.
