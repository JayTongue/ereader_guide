# Ereader Guide

This is my ereader guide. It's mostly for me, but it's here in case other people want to refer to it too. Although all this information is from places I found online, I wanted to have a place where I could pull it all together for easy reference.

------------------------
### Kobo Clara HD:

#### Upgrade Space

A number of Kobo devices (mostly the older ones) use an mini SD card for storage. This means that it can easily upgrade the internal memory. The steps are pretty simple.

1. Open the back of the device.
2. Remove the old SD card.
3. Connect the SD card to a computer and dd the entire drive onto a larger SD card.
4. Use a tool like GParted to expand the size of the new partition to take up the whole drive.
5. Reinsert the SD card and reassemble.

#### Use without Rakuten Account

Initially, the Kobo will require you to connect to wifi and either create or log into a Rakuten account in order to use your device. This can be bypassed by editing the SQL account file. 

1. Locate the SQL file at .kobo/KoboReader.sqlite
2. Open the file with sqlite3 
3. `INSERT INTO user(UserID,UserKey) VALUES('1', '');`
4. Exit and restart the Kobo

#### Nickel Menu 

This custom menu by Patrick Gaskin is the key to unlocking the full functionality of your Kobo. It is regularly maintained and easily installed. 

1. Back up all data first
2. Follow the official installation instructions here: https://pgaskin.net/NickelMenu/#install

#### KOReader and Plato

These are much more powerful book reading softwares that greatly enhance the reading experience. However, they are definitely not for everyone. If you don't need this level of customizability or control, then the stock software is honestly fine. 

These are also regularly updated and maintained by great community members.

Both can be downloaded and installed with a "One-Click" installer:
1. Download the "KOReader AND Plato" option from https://www.mobileread.com/forums/showthread.php?t=314220
2. Extract the zip into the root directory of the device
3. If there is already an `.adds` file, just put the extracted `.adds` contents into the existing one.

#### Kepubify

Kepub is a variation on the EPUB standard by Kobo. KEPUBs can offer some performance increases such as faster page turns, zoomable images, and better footnote linking. While KEPUBs can be read by anything that can read EPUBs, Kobo readers, which handle KEPUB natively, are uniquely good at it. According to online information, Kepubs work by using an SQLite db to index books faster. Kepub books will have a `*.kepub.epub` extension.

Patrick Gaskin also made and maintains a CLI and online tool called kepubify: https://pgaskin.net/kepubify/

This is relatively easy to install
1. Mac: `brew install kepubify`, Linux: 'go install github.com/pgaskin/kepubify@latest'
2. Syntax: 
```
  kepubify /path/to/the/book.epub #single book
  kepubify --output "/path/to/save/the/book/" /path/to/the/book.epub #single book to path
  kepubify -o "converted" *.epub #all books with .epub in current dir into /converted
```
#### Calibre

While Kepubify is incredible for converting EPUB to KEPUB, there will often be a need to convert other ebook file types into EPUB/KEPUB. This can be done with Calibre (https://manual.calibre-ebook.com/generated/en/cli-index.html). You can use the UI, but why would you? 

After installation and path configuration (this will vary by machine), the command is very simple:

	ebook-convert input_file output_file [options]

See docs for full options.

If you are converting any other ebook file type (azw3, mobi), you shouldn't have to do to much processing. If you're converting pdf.. good luck.

#### Dictionaries

One of the biggest advantages of breaking out of the kindle or kobo ecosystems is the ability to use any sort of dictionary you want so long as it is a readable format, such as [StarDict](https://en.wikipedia.org/wiki/StarDict). For instance, although the Chinese-English Wikitionary is good, it doesn't have pinyin. The CC-CEDICT, however, does have pinyin. 

This is a sample workflow for how to side-load the CC-CEDICT dictionary onto KoReader.

1. download the CC-CEDICT from the official source: https://cc-cedict.org/wiki/ . This will decompress to a `*.u8` file
2. The `*.u8` needs to be converted to StarDict format. This online tool works well: https://dictz.github.io/cc-cedict_converter.html
3. The tool will yield three files `*.dict.dz` , `*.ifo` , `*.idx` .
   * If any of the files are `*.gz`, these will need to be decompressed.
4. Copy all these files to `/koreader/data/dict/`

	
	
