# Zipped Album format (zlbm)
***A suggestion for an open single-file music album format***

## Specification
A simple ZIP file (not necessarily compressed; .zlbm extension recommended), with properly tagged (title, albumartist/artist, tracknumber, date) audio files in lossy (Ogg Opus; 96 - 128 Kb/s recommended) or lossles (FLAC; 44.1/48 Khz, 16 bit recommended) format, and an optional digital booklet (PDF; square paper size) of which the first page is the album cover. For compatility with current players, additional (cover) images (JPEG, PNG; square format) can be included. For creating custom compilation albums/mixtapes without changing the tags of the included audio files, an optional playlist (XSPF) might specify any of the following: title, creator, date and track order.

```
├── *.zlbm|*.zip|*
│   ├── *.opus|flac
│   ├── ...
│   ├── [*.pdf]
│   ├── [*.jpeg|png]
│   ├── ...
|   ├── [*.xspf]
```

## Examples
The following ZIP files would each be recognized as a Zipped Album. While I am not aware of any player that suports showing the PDF booklet (I am working on one though!), there are players that will play the audio and show the cover image if present (e.g. Foobar2000, DeadBeeF).

**Simplest form with a PDF booklet:**
```
├── Artist-Album_Title.zlbm
│   ├── Artist-Album_Title-01-First_Song.opus
│   ├── Artist-Album_Title-02-Second_Song.opus
│   ├── Artist-Album_Title-03-Third_Song.opus
│   ├── Artist-Album_Title-04-Fourth_Song.opus
│   ├── Artist-Album_Title.pdf
```

**Two variants with additional images:**
```
├── Artist-Album_Title.zip
│   ├── Artist-Album_Title-01-First_Song.opus
│   ├── Artist-Album_Title-02-Second_Song.opus
│   ├── Artist-Album_Title-03-Third_Song.opus
│   ├── Artist-Album_Title-04-Fourth_Song.opus
│   ├── Artist-Album_Title_booklet.pdf
│   ├── back.jpeg
│   ├── front.jpeg
```

```
├── Artist-Album_Title.zip
│   ├── 01.opus
│   ├── 02.opus
│   ├── 03.opus
│   ├── 04.opus
│   ├── booklet.pdf
│   ├── folder.jpeg
```

**The format of an album downloaded from Bandcamp, inlcuding only a cover image:**
```
├── Artist - Album Title.zip
│   ├── Artist - Album Title - 01 First Song.flac
│   ├── Artist - Album Title - 02 Second Song.flac
│   ├── Artist - Album Title - 03 Third Song.flac
│   ├── Artist - Album Title - 04 Fourth Song.flac
│   ├── cover.png
```

**A custom made mixtape that includes neither a PDF booklet nor any images, but a playlist:**
```
├── fladdsAwesomeMixtape.zip
│   ├── ArtistA_TitleW.opus
│   ├── ArtistB_TitleX.opus
│   ├── ArtistC_TitleY.opus
│   ├── ArtistD_TitleZ.opus
│   ├── playlist.xspf

```

Contents of playlist.xspf:

```
<?xml version="1.0" encoding="UTF-8"?>
<playlist version="1" xmlns="http://xspf.org/ns/0/">

    <title>Awesome Mixtape</title>
    <creator>fladd</creator>
    <date>2021-04-29T01:40:09.330469+02:00</date>

    <trackList>
        <track>
            <location>ArtistB_TitleX.opus</location>
        </track>
        <track>
            <location>ArtistD_TitleZ.opus</location>
        </track>
        <track>
            <location>ArtistC_TitleY.opus</location>
        </track>
        <track>
            <location>ArtistA_TitleW.opus</location>
        </track>
    </trackList>

</playlist>
```

## FAQ

* **Why?**
  
  ~~Before music was entirely digital, albums came as a single entity, in a nice package with a dedicated booklet full of information. An album was a product as a whole. Digital music has lost this. You get individual music files, no package and ususually a cover image at best, but no booklet. Zipped Album is an attempt to regain some of that in a digital format.~~
  
  I am getting old.
  
* **How do I play a Zipped Album?**

  I created [Zipped Album Player (ZAP)](https://github.com/zipped-album/zap) as cross-platform player with full Zipped Album support. However, some other players are capable of at least playing the audio part of a Zipped Album (i.e. they won't show the booklet). These include [Foobar2000](https://foobar2000.org) and [DeaDBeeF](https://deadbeef.sourceforge.io/).
  
