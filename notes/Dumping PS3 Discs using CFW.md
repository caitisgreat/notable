---
tags: [Notebooks/Retro Gaming]
title: Dumping PS3 Discs using CFW
created: '2021-03-23T17:24:19.278Z'
modified: '2021-03-23T17:58:04.971Z'
---

# Dumping PS3 Discs using CFW

Source: [RPCS3 Wiki](https://wiki.rpcs3.net/index.php?title=Help:Dumping_PlayStation_3_games)

Requirements: [CFW or HEN](Jailbreak PS3 & Custom Firmware.md)

This method is the more reliable method of dumping disc games as it is guaranteed to work with every PS3 game disc in existence. However, during the dumping process, you will be limited to the PS3 Blu-ray reader's transfer speeds so the process may take longer than doing the same through a PC. If you have doubts on installing or using any of the tools mentioned below, please read [r/ps3homebrew's wiki](https://www.reddit.com/r/ps3homebrew/wiki/multiman).

1) Install multiMAN file manager.
1) Insert your disc into the PS3.
1) Highlight the game disc in [multiMAN](https://store.brewology.com/ahomebrew.php?brewid=24) and press Triangle and select Copy.  You can create an ISO or folder layout format of your game files. It is recommended to create a folder layout version of your game instead of an ISO for a smaller file size, due to ISOs copying the entire disc which is either 4.7 GB, 8.5 GB, 25GB, or 50GB.
1) Choose the location to save your dump. It can be your PS3's internal HDD, an external HDD or even set up an FTP connection between your PlayStation 3 and PC.
Overall, the FTP method will be the fastest option. If using FTP, make sure to set Transfer Type to Binary, otherwise your dumps may get corrupted.

_Note:_ The PlayStation 3 has a maximum file size of 4GB. When dumping games which contain files bigger than 4GB, multiMAN will automatically split those files. When you copy your dump over to your PC, remember to rejoin the split files back together with tools such as [ps3merge](http://karmian.org/projects/ps3merge), otherwise the dump won't work.
