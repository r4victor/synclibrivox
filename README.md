# synclibrivox

## Overview

<b>synclibrivox</b> is a collection of files for LibriVox recordings needed to produce ebooks with synchronized text and audio using [syncabook](https://github.com/r4victor/syncabook). If someone used <b>syncabook</b> to create an ebook for a LibriVox recording and commited source files to this repository, you can create an ebook using <b>syncabook</b> just by getting the files with `download_files` command and then assembling them to EPUB with `create` command.
## Repository contents

The repository contains all neccessary source files needed to produce an ebook except for audio files. Each book has a directory with the following contents:

* `metadata.json` file contains all information neccessary to produce an ebook (title, author, narrator, etc.)

* `sync_text/` directory contains XHTML files with the book's contents and which are synchronized with the audio

* `no_sync_text/` directory contains `nav.xhtml` (table of contents) and `colophon.xhtml` (credits to contributors) and any other files which are not synchronized with the audio

* `smil` directory contains SMIL files (synchronization data)

* `text.txt` file cotains plaintext transcript of the book

* `plaintext/` directory contains transcript of the book splitted into multiple files which are then converted to XHTML files


`map.json` is a mapping from the LibriVox audiobook URL to the corresponding directory in the repository. It is used by <b>syncabook</b>'s `download_files` command to get files given LibriVox URL.