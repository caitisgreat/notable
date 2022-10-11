---
tags: [RetroGaming/Preservation]
created: '2021-06-23T17:08:15.317Z'
---
Information below sourced from: [RetroPie UK](https://retropie.org.uk/docs/CHD-files/) & the [Emulation General Wiki](https://emulation.gametechwiki.com/index.php/Save_Disk_Space_for_ISOs)

# CHD

CHD is a lossless compression format originally developed for MAME, for the hard-drive contents of certain arcade machines. It has since been used in several other emulators as a means of storing CD-ROM game data. For CD-based games, it compresses the contents of a disc image (`.cue` + `.bin` files) to a single `.chd` file.

* `Archive-quality dump?` Yes (with CHD version 5)
* `Gain:` Immediate
* `Tools Used:`  chdman (included with MAME)
* `Can be reverted?` Yes, using extractcd (included with MAME)
* `Playable on Hardware?` No.
* `Playable on Emulators?` MAME, DuckStation, PCSX2 (since March of 2021) and DEmul. Some libretro cores for other emulators are starting to add support.
* `Can process multi track bin files?` Yes.

MAME uses the CHD format for disc images in general and includes tools to convert back and forth. Before MAME v145, CHD was in version 4 and it bumped to version 5 from MAME v146 and further. The CHD v5 uses 7zip's LZMA compression on the game data and lossless FLAC compression for the audio data to optimize compression even further than using BIN+CUE+MP3/WAV data separation alone. CHDv5 is truely lossless.

# Creating CHDs from CD-ROMs

`CHD` files can be created using the `chdman` program, developed by the [MAME project](https://mamedev.org).  It is a command line application and creating a `.chd` file from an existing `.cue` is performed by running the following scripts.

## Linux

To compress every file in subdirectories within a folder, use:

```shell
for i in */*.cue; do chdman createcd -i "$i" -o "${i%.*}.chd"; done
```
To restore CD-ROM game data in subdirectories within a folder, use:

```shell
for i in */*.cue; do chdman extractcd -i "$i" -o "${i%.*}.chd"; done
```

## Windows

To compress every file in subdirectories within a folder, use:

```batch
for /R %%I in (*.cue, *.gdi) do chdman createcd -v -i "%%I" -o "%%~dpI%%~nI.chd"
```
To restore CD-ROM game data in subdirectories within a folder, use:

```batch
for /R %%I in (*.cue, *.gdi) do chdman extractcd -v -i "%%I" -o "%%~dpI%%~nI.chd"
```
