---
title: Dumping PS3 content from PSN
created: '2021-04-01T22:46:46.620Z'
modified: '2021-04-01T23:59:05.548Z'
---

# Dumping PS3 content from PSN

Content URLs can be retrieved from: https://github.com/yne/psndl

Instructions Sourced from: [RPCS3 Wiki](https://wiki.rpcs3.net/index.php?title=Help:Dumping_PlayStation_3_games)

## Dumping PSN games

Dumping digital PSN games is a little bit different. There are two files needed to play a PSN game. The first is the actual game file that comes in a .pkg format and the second is the license file that is used to activate the game which needs to be in a .rap format. As mentioned in the overview, you need a CFW PS3 or OFW PS3 to extract the license file of your game. The actual game file can be downloaded directly from your PC. It's also important to note that some games do not have or need a license file (mostly free games and DLCs).

As of March 29, 2021 you can no longer access entitlement information from PC. The only viable way left is to dump all content using your PS3.

### Obtaining content and license files

This process involves using file managers to copy files from your PS3. This can be done with CFW PS3s or PS3s with HEN enabled. The steps involved to install CFW or HEN to your PS3 are well outside the scope of this guide and will not be covered here. Users are requested to refer to r/ps3homebrew's wiki or Google for more information.

To obtain the game content files:

1) Download and install games and DLCs you're interested in:

* If you queue content download into background, the associated .pkg file will be saved inside /`dev_hdd0/vsh/task/XXXXXXXX` folders until you manually install it through XMB action

* These files are often incomplete, so please [verify](https://github.com/13xforever/psn-pkg-validator/releases/tag/v1.3.1) every .pkg file you got from there

2) Copy associated game folders from `/dev_hdd0/game/`

To obtain the license files for your games:

1) Boot your PS3 and start downloads for any PSN titles. You can pause and cancel the downloads immediately after it begins to prevent the game files from being downloaded to your PS3 unnecessarily. The license files are downloaded prior to the game files and will remain even if the download is cancelled.

2) Next, we need to retrieve 3 types of files:

* First up is the **.rif** files which are the encrypted license files. Every game and DLC should have its own unique rif file. These files are located in `/dev_hdd0/home/000000XX/exdata/` where `XX` is the user ID number. Using the file manager of your choice, copy all the files to an external USB drive, external HDD or use FTP to directly send these files to your PC.

* Next, copy over the **act.dat** file which is present in the same location as the rif files. Each user account will have a unique act.dat and you are required to copy the act.dat of the user account used to connect to PSN.

* Finally, we need to find the **IDPS**. This is not a file but a 32-character hex string. There are multiple ways to view a console's IDPS.  If you happen to use HEN, then on your PS3 go to `Network\Hybrid Firmware Tools\Dump tools\Dump IDPS` which will dump the IDPS value to the the HFW settings log.  It'll be at `/dev_hdd0/tmp/hfw_settings.log` Once you find this number, note it down so that it can be used at a later point.

3) On your PC, download [RifConv](https://mega.nz/#!NP5WTayL!Grzqe_BQlrmK4_ofCGGVNZX4WkBSN54BDel399aWsMI) and [HxD Hex Editor](https://mh-nexus.de/en/hxd/) (or any other hex editor).

4) Create a new file and name it **idps.hex**. Open idps.hex with the hex editor and type in the IDPS number you noted down from your PS3. Hit save and close the file.

5) Launch RifConv and ensure you're on the Rif2Rap tab. Add the idps.hex, act.dat and folder containing all .rif files in their respective fields.

6) Hit Create and a new folder called **created_raps** should appear. This folder will contain the decrypted license files in the **.rap** format that can be used in RPCS3.
