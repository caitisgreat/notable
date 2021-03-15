---
tags: [Notebooks/Retro Gaming, Wii, Wii U]
title: Extract Wii VC titles from Wii U
created: '2021-03-15T17:22:09.460Z'
modified: '2021-03-15T20:04:35.966Z'
---

# Extract Wii VC titles from Wii U

**Originally from [here](https://forum.wii-homebrew.com/index.php/Thread/59652-TuT-English-How-to-dump-and-convert-an-eShop-Wii-game-into-an-ISO-for-Dolphin/)**

This guide assumes you are using a Windows PC.

Nintendo re-released some retail Wii games digitally on the Wii U eShop under the Virtual Console section which are downloaded directly onto the system. For some games this is actually the cheapest way to obtain them (Metroid Prime Trilogy is a good example of this, used copies sell for WAY more than what the game is on the eShop).

But these games are a pain to dump (DDD crashes and the FTP method can't read the files) and the game files are stored in this weird ".NFS" format.  This format is similar to WBFS, in that it contains multiple parts of the game data in separate files, but Dolphin can't read the NFS format nativity.

In order to get these files, you'll need to use the [Wii U NAND Dumper](https://github.com/koolkdev/wiiu-nanddumper/releases) and dump the entire MLC in order to correctly dump these files.

*Note: You'll need an SD card with at least 16GB or 32GB of free space depending on which model of the Wii U you have (16 for the white, 32 for the black "deluxe" model).*

Then, use the [WFS extract tool](https://github.com/koolkdev/wfslib/releases) to extract the MLC dump. Your games will be found under `usr \ title` in the MLC folder. 

*Note: your MLC dump may be split into multiple files, you can merge them by running the following command in a command line window in the same directory as the MLC part files: `copy /b mlc.bin.part?? mlc.full.bin`*

Now that you have the NFS files, you'll have to convert it into an ISO image for Dolphin to be able to run the dump.

This is possible using a tool known as [nfs2iso2nfs](https://github.com/FIX94/nfs2iso2nfs/releases).

The tool is pretty self-explanatory, it allows you to decrypt the NFS files back into an ISO image, the only problem is, the program requires the Wii Common Key (not the Wii U Common Key). I cannot tell you where to obtain this (other than from your own console) as sharing it is illegal, but once you have it create a new text document and name it "wii_common_key" (without the quotation marks) and paste the key's value into the file, then save it as a .bin file. Now run the program and it should start doing it's thing, this might take a while depending on the size of the game. At the end, you'll end up with a file named "game.iso". Congratulations, you have successfully converted the game into a format Dolphin can understand.

Side-note, these versions of the games have the Update partition removed from them since they are redundant (due to the Wii U shipping with the latest firmware for Wii mode), so Dolphin will complain about that in the Verify tab, but this won't effect anything.

