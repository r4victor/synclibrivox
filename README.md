# synclibrivox

## Overview

<b>synclibrivox</b> is a collection of files for LibriVox recordings needed to produce ebooks with synchronized text and audio using [syncabook](https://github.com/r4victor/syncabook). If someone used <b>syncabook</b> to create an ebook for a LibriVox recording and commited source files to this repository, you can create an ebook for that recording using <b>syncabook</b> just by getting the files with `download_files` command and then assembling them to EPUB with `create` command.
## Repository contents

The repository contains all neccessary source files needed to produce an ebook except for audio files. Each book has a directory with the following contents:

* `metadata.json` file contains all information neccessary to produce an ebook (title, author, narrator, etc.)

* `sync_text/` directory contains XHTML files with the book's contents and which are synchronized with the audio

* `no_sync_text/` directory contains `nav.xhtml` (table of contents) and `colophon.xhtml` (credits to contributors) and any other files which are not synchronized with the audio

* `smil` directory contains SMIL files (synchronization data)

* `text.txt` file contains plaintext transcript of the book

* `plaintext/` directory contains transcript of the book splitted into multiple files which are then converted to XHTML files


`map.json` is a mapping from the LibriVox audiobook URL to the corresponding directory in the repository. It is used by <b>syncabook</b>'s `download_files` command to get the files given LibriVox URL.

## How to use

<b>syncabook</b> provides `download_files` command that downloads files from <b>synclibrivox</b> repository as well as auido files from librivox.org. In order to create an ebook using files from this repo you need to run two commands:

```
$ syncabook download_files `librivox_url` `ebook_dir`
```
and then
```
$ syncabook create `ebook_dir`
```

If you've cloned this repo and have all neccessary files except for audio, run `download_files` command with `--skip-text` argument to download audio files only:

```
$ syncabook download_files --skip-text `librivox_url` `ebook_dir`
```
