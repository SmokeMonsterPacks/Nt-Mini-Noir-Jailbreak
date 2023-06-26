-----------------
Table of Contents
-----------------

You can navigate this document by using this list of the major topics covered in it:

Updating the Firmware
Latest Update
Cores Menu
NES/Famicom Core Release Notes
Atari 2600 Core Release Notes
Atari 7800 Core Release Notes
Sega Genesis Core Release Notes
SMS Core Release Notes
Game Gear Core Release Notes
Colecovision Core Release Notes
Gameboy Core Release Notes
Gameboy Color Core Release Notes
Intellivision Core Release Notes
Mandelbrot Core Release Notes
Adventurevision Core Release Notes
Arcadia 2001 Core Release Notes
Channel F Core Release Notes
Creativision Core Release Notes
Gamate Core Release Notes
Game King Core Release Notes
Odyssey^2 Core Release Notes
RCA Studio 2 Core Release Notes
Supervision Core Release Notes
Videobrain Core Release Notes
Megaduck Release Notes
Controller Support Summary
Wireless Controller Functionality Reference
Required/Supported BIOS Files
Prior Update History

---------------------
Updating the Firmware
---------------------

First off, to use the JB mode, perform the following steps:

* Format an SD card with FAT32.
* Unzip this pack directly to the root of the SD card, keeping all directories/folders intact.
* Add your ROMs to the proper directory.  i.e. NES ROMs go in /NES/
* Insert the SD card into the nt mini and power it up.
* The system will perform an update which takes approximately 3 minutes.  The front LED will flash.
* After the update, the system will reboot automatically.
* The main menu should now give a new option, "Cores", to signify this is the JB mode!

If you wish to install JUST the updates and not reformat your card, perform the following steps:

* Replace the /SYSTEM/ directory on your SD card and all .NT2 files
* Add any subdirectories that do not exist on your current card
* Add any new BIOS files for Cores you wish to use, listed below, in the /BIOS directory.
* Load any newly supported games into the new directories.
* On powerup, the Nt Mini will update and will be ready to go!

CAUTION: be sure to replace the .NT2 files in /system/cores with the ones in this archive or else
new features and fixes that were added in this jailbreak version WILL NOT WORK.

-------------
Latest Update
-------------

(previous update notes will be found at the very bottom of the document)

v6.7 release 05/04/23

* Fixes to CPU:PPU alignment which include:
* Fixed: Battletoads crashing on level 2
* Fixed: Bonk's Adventure boss fight floor shaking
* Fixed: Crystalis/God Slayer's inability to start game, getting stuck
* Fixed: Famicom Disk Systems work regardless of dejitter setting (Not compatible with Zero Delay)
* Fixed: Flintstones: Rescue of Dino & Hoppy jumping title screen and status bar
* Fixed: Flintstones: Surprise at Dinosaur Peak jumping status bar
* Fixed: G.I. Joe cartridge crashing
* Fixed: Little Nemo cartridge freezing
* Fixed: Mega Man V robot screen jumping
* Fixed: Micro Mages graphical & audio glitches with cartridge
* Fixed: Shadow of the Ninja freeze on opening cutscene
* Fixed: Summer Carnival '92: Recca jumpy status bar
* Fixed: Mighty Final Fight freezing
* Fixed: Vice: Project Doom 2nd stage status bar jumping

* Fixed: Kirby's Adventure PAL palette corruption on EverDrive N8 Pro (requires latest EverDrive N8 Pro OS)
* Fixed: Vertical Green Lines in games using CHR-RAM (Castlevania, Legend of Zelda, Mega Man 1 & 2, Rygar, many others)     and EverDrive N8
* Fixed: Crystalis freezing when a controller is inserted into port 2
* Fixed: Paperboy Player 2 control input
* Fixed: Micro Mages 3-4 player control input
* Added: Headphone Jack L/R Swap to Audio - Headphones (note will swap RCA jacks to opposite of their labeling)
* Improved: Microphone sensitivity reversed, 0 is minimum intensity, 63 is maximum intensity. Default setting is tuned   for most games supporting the microphone.
* Improved: NSF Audio Levels & Panning settings separate from cartridge settings
* Fixed: Atari 2600 graphic issues.
* Fixed: Genesis, Sega Master System, Game Gear and ColecoVision Cores crash issue.
* Fixed: Intellivision RAM not cleared before loading a game.
* Improved: Intellivision's third fire button is now mapped to Famicom Network Controller's 0 button for easier access
* Improved: Intellivision numberpad 0 button has been remapped to Famicom Network Controller's . button.
* Improved: Odyssey^2 controllers swapped.


----------
Cores Menu
----------

The cores menu lets you select one of the various cores that are and will be available.  
To run a specific core (say, NES) simply select it.  The loading takes approximately 4 seconds.

During the core loading, the front LED will flicker rapidly to indicate it is loading.  While this happens, the monitor will show no signal, since the FPGA is being reconfigured at this time.
After the loading, the monitor will come back and you will be sitting in the file browser for this particular core (Mandelbrot does not have one).

The key setup for the core menus are:

* UP/DOWN: Navigate through the file browser one file at a time

* LEFT/RIGHT: Page through the files in the file browser quickly, 21 at a time

* B: Sends you up a directory

* A: Run the game.

* START: enter the settings menu. This is slightly different from the main menu.  There may be a "Core Options" settings menu.  Everything core specific will be found here.

* SELECT: exit the menu and return to the file browser.  Press select again to return to the currently running game.

------------------------------
NES/Famicom Core Release Notes
------------------------------

This core is extremely large and encompasses 280 mappers.  All the major mappers and many other mappers are implemented and work.  NES 2.0 headers are 100% supported and many NES 2.0 mappers are included.  Every mapper was completely rewritten using the most current information available.

*save games*
------------

Save game RAM is fully supported for many mappers, and has three modes:

* always save
* never save
* prompt

This allows you to control how save RAM saving works. Save filenames should be usable out to 256 characters or so now, which should encompass just about anything.

EEPROM and Flash saving are not supported.  EEPROM saving is used by some Mapper 16, Mapper 157 and all Mapper 159 games (Bandai releases and Datach Joint ROM System).  Flash saving is used by Mappers 30 and 111 (Homebrew releases).

*Expansion audio*
----------------

Expansion cartridge audio is supported.  Unlike cart mode, however, the act of loading a ROM will force the proper expansion chip to be selected.  This includes many pirate conversions of FDS games to cartridge (except for Tobadaise Daisuken, which had its FDS audio data removed.)  

*FDS*
-----
Full FDS disk drive and RAM adapter emulation has been added.  This allows FDS games to be played that consist of from 1 to 4 disk sides.   The FDS images must be a multiple of 65500 bytes, and cannot contain headers.  

Valid file sizes in bytes:

 65500 bytes - 1 disk side
131000 bytes - 2 disk sides (these first two are the most common)
196500 bytes - 3 disk sides (very rare)
262000 bytes - 4 disk sides (somewhat rare)

To use the FDS functionality, an FDS BIOS needs to placed into the /BIOS/
directory.  Any of the three BIOS dumps can be used: R0, R1, or the Twin
Famicom version.  It must be named fds.bin

Several methods to load disks and change sides are provided in a new menu
titled "FDS" that appears on the cores menu only when an FDS game is loaded.

By default, "automatic" mode is selected.  This mode will automatically load the first side of the FDS image and run it without user intervention.
It will also detect the side and disk the game is attempting to load, and will automatically select the side for you.
The loading prompts are also automatically passed so usually no intervention is required to play the games.

There are a few exceptions to this, however, and a few games need to be loaded manually.  These are listed later.

When an FDS game is loaded, a new FDS menu appears on the main menu.  This menu allows full control of the FDS "drive".

In the menu, the auto/manual selection can be made, and a disk ejected, and/or a new side can be selected. 

Saving:  When the file menu is opened,  the FDS disk data is saved to a .sav file like with cartridge games, however the data is no longer in .fds format;
it is in the expanded disk format with gaps and CRCs.  This is due to the fact that .fds files must be expanded to be loaded.
When loading a game with an existing .sav file, the .sav file will be loaded and the contents of the .fds will NOT be used, except to determine the number of disk sides the game
contains.

This means if you wish to reload a game from the .fds to play it, its .sav file must be deleted, or the .fds renamed.  This way the original file is not modified.

A .sav file will NOT be created unless the contents of the disk were modified. This means games that do not save to disk will not create .sav files.

There are three ways to handle disk changing:

Manual mode:  You must manually select disks and sides in the menu.
You do not need to eject before changing disks or sides; it will perform a
1/4th second eject for you.

Semiautomatic mode functionality:  This is the default mode.  Pressing select
will eject the disk as long as select is down, and for about 1/2 second after
the button is released, and then auto-select the proper disk and side.

Some games such as Doki Doki Panic have an unusually long wait to check for a disk being ejected so this accommodates that.  
Note that since select ejects the disk, it is not a good idea to do this while a game is loading since it will throw an error 01.
Usually most games can recover from this though, and will attempt to load again.
The same caveats with automatic mode follow over to semiautomatic mode with regards to a few games not being able to autodetect the side/disk.
No known games or software have an issue with the disk being ejected once they have loaded, and only check it when they wish to load or are actively loading.

Automatic mode functionality:  The automatic mode works fine for most games
except those outlined below.  It has a few extra features that are activated
by use of the select button on player 1.  Some games, such as Zelda, will skip the title screen and directly load the game.  To see the title screen, the select button can be held which will stop the automatic switching from happening until it is released.  

On a few games, it can take a few seconds for the automatic loading process
to start.  This is normal because every game has to read the state of the disk, and each one does it differently.

A few games that use custom loading routines can produce "ERR 01" errors  If
this happens simply hold the select button down during the loading process.
If a game seems unresponsive or won't autoload the disk, try holding down select for a second or so and/or tapping it to see if that unsticks it.  

These games cannot be used with auto mode because they have custom disk routines, or they do not specify the proper side when loading:

Doremikko - does not specify proper side to load
Koneko Monogatari - uses custom disk routines and not the BIOS
Some unlicensed games don't specify the side to load
Bishoujo Shashinkan - Moving School - reboots unless run in manual mode

*other features*
----------------

Nt Mini Noir supports NES ROMs up to 16MiB in size with up to 32KiB of CHR-RAM and 64KiB of PRG-RAM.  So you cannot have a 16MiB PRG-ROM with 64KiB of CHR-RAM, for example.  

Some mappers (mapper 90, multicart mappers, drip mapper) support dip switches.  These  can be found under the "Core Options" menu which is accessed by hitting START on the file browser for the NES core.

Each time a game is loaded, the dipswitches will be cleared.  

For the Nintendo World Championships 1990 and Nintendo Campus Challenge 1991 competition cartridges, Dips 1-4 set the competition time and Dip 5 removes the time limit.  Here are the settings for Dips 1-4:

Dips
4321 - |time (mins)
------------------
OOOO - 5.001
OOOC - 5.316
OOCO - 5.629
OOCC - 5.942
OCOO - 6.254 (Official Tournament Times)
OCOC - 6.567
OCCO - 6.880
OCCC - 7.193
COOO - 7.505
COOC - 7.818
COCO - 8.131
COCC - 8.444
CCOO - 8.756
CCOC - 9.070
CCCO - 9.318
CCCC - 9.695

O = switch open ("off"), C = switch closed ("on")

Dip Switches always default to Off, so you should set the Dip Switches and then press Reset.  These games are usually started by pressing Select.

Coin insertion is done using the trigger on a 12 button controller, and can also be done on the dipswitch submenu if this mapper supports.  All Vs. mappers and mapper 126 (arcade board) use this.

Nt Mini Noir's Core Jailbreak has full Vs. System support for any known game which does not use Vs. Dual System capabilities.  This means that Vs. Balloon Fight, Vs. Baseball, Vs. Ice Climber Dual, Vs. Mahjong, Vs. Tennis and Vs. Wrecking Crew are not playable, but the rest are playable.

Vs. System games require full NES 2.0 headers to work properly.  Use the NES 2.0 XML Database and the NES Header Repair Tool Python Script to fix your headers.

Vs. Tetris - Has only 24KiB of PRG-ROM but the jailbreak will only load a ROM with 32KiB of PRG-ROM.  You can add 8,192 padding bytes of 00s inserted between the header and start of the PRG-ROM to get the game to work.

Vs. Raid on Bungeling Bay - Must have its protection check patched out.

Vs. System games obtain their settings from a bank of eight dip switches, these will be found as Dips 1-8 under Core Options - Dip Switches.  If you are not using a SNES-style controller, you can Add a Coin with the Dip Switch menu.  

With Vs. System games, you start games with the Select button on either Controller I or, for a two-player game, Controller II.  

Zappers are supported for Vs. games that use a light gun.

Vs. System games that use one of the 2C04 PPUs will show very incorrect colors when run on a PPU that uses a regular palette (2C02, 2C03, 2C05, 2C07)  On Nt Mini Noir the S-Video and Composite video output options generate palette colors like an original 2C02 or 2C07 would and cannot change their palettes.  The result is that you will need to use Component, RGB or HDMI video to play these games with the proper colors.  

*problem solving*
-----------------

This core is taking full advantage of NES 2.0 headers.  This includes mappers, save RAM size, etc.  It is highly recommended that you upgrade your ROM set.  If some games will not run, it most likely is because the core needs more information contained in the 2.0 header, such as Star Tropics. Star Tropics is actually mapper 4.1 (MMC6).

Some of the Sachen multi-carts also have issues inherent to their ROMs : Super Cartridge Ver 1 - 4 in 1 - Honey Peach has a broken triangle channel during title screen music, Super Cartridge Ver 5 - 7 in 1 - Magical Mathematics is missing its title screen audio and Super Cartridge Ver 7 - 4 in 1 - Silver Eagle's main character sprite gets glitchy when shooting.

(complete list of implemented and tested mappers)
0     - NROM
1.0   - MMC1 
1.5   - MMC1 with fixed PRG banking
2.0   - UNROM normal (no bus conflicts)
2.2   - UNROM bus conflicts
3     - CNROM normal (no bus conflicts)
3.2   - CNROM bus conflicts
4.0   - MMC3B
4.1   - MMC6
4.3   - MC-ACC (Acclaim MMC3 clone with different IRQ timing)
4.4   - MMC3A
5     - MMC5
7     - AxROM normal (no bus conflicts)
7.2   - AxROM bus conflicts
9     - MMC2
10    - MMC4
11    - colordreams (has bus conflicts)
12    - MMC3A variant with upper CHR bit select
13    - CPROM (has bus conflicts)
15    - mapper 15
16.4  - Bandai IRQ counter not latched
16.5  - Bandai IRQ counter latched (no EEPROM support yet)
18    - jaleco
19    - namco N163
21.0  - VRC2/VRC4
21.1  - VRC4a
22    - VRC2a
23.0  - VRC2/VRC4
23.1  - VRC4f
23.2  - VRC4e
23.3  - VRC2b
24    - VRC6
25.0  - VRC2/VRC4
25.1  - VRC4b
25.2  - VRC4d
25.3  - VRC2c
26    - VRC6
27    - World Hero
28    - action 53
29    - Sealie Computing Glider
30    - UNROM512 (no flash support yet)
31    - NSF
32.0  - Irem G-101
32.1  - Irem G-101 variant with 1 screen mirroring
33    - Taito TC0190
34    - BNROM and NINA-001
35    - mapper 90 variant with WRAM
36    - TXC 01-22000-400
37    - SMB + Tetris + NWC
38    - Bit Corp Crime Busters
39    - Subor Study and Game
40    - NTDEC 2722 SMB2j
41    - Caltron 6 in 1
42    - Bio Miracle FDS
43    - TONY-I and YS-612
44    - Super Big 7 in 1
45    - GA23C Multicarts
46    - Rumble Station
47    - Super Spike + NWC
48    - Taito TC0350
49    - Super HIK 4 in 1
50    - N-32 SMB2j
51    - 11 in 1 ball games
52    - Multicarts
53    - supervision 16 in 1
54    - Novel Diamond 999999 in 1
55    - Mario1-Malee2
56    - Kaiser SMB3
57    - Super GK 6 in 1
58    - Multicarts
59    - T3H53 Multicarts
60    - Reset-based multicarts
61    - 20 in 1
62    - 700 in 1
63    - Powerful 250 in 1
64    - Tengen RAMBO-1
65    - Irem H3001
66    - GxROM
67    - Sunsoft-3
68.0  - Sunsoft-4
68.1  - Sunsoft-4 dual cartridge system
69    - Sunsoft FME-7
70    - Bandai simple
71.0  - Codemasters UNROM-like
71.1  - Fire Hawk variant
72    - Jaleco JF-17
73    - VRC3
74    - Waixing 43-393/860908C
75    - VRC1
76    - Namco 3446
77    - Irem with VRAM
78.1  - Irem Cosmo Carrier
78.3  - Irem Holy Diver
79    - NINA-03 / NINA-06
80    - Taito X1-005
81    - Super Gun
82    - Taito X1-017
83.0  - Cony Mapper 256K CHR / heuristic
83.1  - 512K CHR
83.2  - 1M CHR
85    - VRC7
86    - Jaleco JF-13
87    - Jaleco 
88    - Namco 118 variant
89    - Sunsoft
90    - mapper 90 inhibited ROM nametables and mirroring
91    - JY Company Super Fighter 3
92    - Jaleco
93    - Sunsoft-2
94    - UN1ROM
95    - Namco 118 variant
96    - Bandai simple
97    - Irem TAM-S1
99    - Vs. System
101   - Jaleco JF-10
102   - drip (moved to 284)
103   - Doki Doki Panic FDS conversion
104   - Pegasus 5 in 1
105   - NES-EVENT
106   - SMB3 bootleg
107   - Magic Dragon
108.1 - FDS-to-cartridge conversions
108.2 - FDS-to-cartridge conversions
108.3 - FDS-to-cartridge conversions
108.4 - FDS-to-cartridge conversions
109   - Great Wall (duplicate of 137)
110   - Sachen 74LS374N (duplicate of 243)
111   - GTROM (no flash support yet)
112   - San Guo Zhi - Qun Xiong Zheng Ba
113   - HES 6 in 1
114.0 - Multiple MMC3 with scrambling
114.1 - Multiple MMC3 with scrambling
115   - SFC-02B/-03/-004 boards
116.0 - SOMARI-P
116.1 - SOMARI-P
117   - san guo zhi 4
118   - TKSROM MMC3 + single screen mirroring
119   - TQROM MMC3 + CHR/RAM switching
120   - 3D worldrunner FDS conv.
121   - A9713 MMC3-clone-bearing protected board
122   - same as 184
123   - Scrambled MMC3
124   - Super Game Mega Type III (arcade board)
125   - FDS Monty on the Run
126   - MMC3 based multicart
127   - funky double dragon 2 pir8
128   - super HiK 4 in 1- chi den
129   - duplicate of 213
130   - NS03 7 in 1 multicart
131   - duplicate of 205
132   - TXC
133   - Sachen Jovial Race & Drunkard
134   - MMC3 clone with extensions
135   - (dupe) sachen 8259A-1 (mapper 141)
136   - Sachen 3011
137   - Sachen 8259D
138   - Sachen 8259B
139   - Sachen 8259C
140   - Jaleco JF-11/JF-14
141   - Sachen 8259A
142   - Kaiser FDS ports
143   - Sachen with lame protection
144   - Death Race
145   - Sachen CNROM-like
146   - functional equivelant to NINA-03
147   - Sachen 3018
148   - Sachen SA-008-A
149   - Sachen SA-0036
150   - Sachen SA-015
151   - Vs. VRC1
152   - Bandai
153   - Bandai with WRAM
154   - Namco 118 variant
155   - MMC1 without WRAM protection
156   - Open Daou
157   - Bandai joint ROM system
158   - Tengen 800037
159   - Bandai with 24C01 EEPROM (no EEPROM support yet)
163   - Nanjing Copy Protected clone games
164   - Final Fantasy V
166   - Subor
167   - Subor
168   - Racermate
169   - Contra 168 in 1
170   - Shiko Game Syu
171   - MMC1 with hardwired mirroring
172   - Super Mega P-4070 board
173   - Idea-Tek
174   - NTDec 5 in 1
180   - Crazy Climber
182   - same as 114
183   - Pirate Gimmick
184   - Sunsoft
185.4 - Protected CNROM
185.5 - Protected CNROM
185.6 - Protected CNROM
185.7 - Protected CNROM
186   - Studybox
187   - MMC3 clone with extensions
188   - Bandai Karaoke (microphone is supported)
189   - Thunder Warrior
190   - Magic Kid GooGoo
191   - MMC3 clone similar to 119
192   - MMC3 clone similar to 119 but lets RAM/ROM work at the same time
193   - NTDEC TC-112
194   - Super Robot Taisen
196   - MMC3 hacks that use BNROM and other address lines than A0
198   - Chinese Mapper
200   - 1200 in 1
201   - 8 in 1
202   - 150 in 1
203   - 35 in 1
204   - 64 in 1
205   - 15 in 1
206   - Namco 118
207   - Taito X1-005
209   - mapper 90 variant (original version with selectable ROM nametables and mirroring)
210   - namco 175/340
210.1 - namco 175 with hardwired mirroring
211   - mapper 90 variant forced ROM nametables and mirroring
212   - Super HIK 300 in 1
213   - duplicate of 58
214   - Super Gun 20 in 1
215   - MMC3 with scrambling
216   - magic jewelry 2
217   - 255 in 1
218   - Magic Floor
221   - NTDEC N625092 multicarts
225   - 52 Games
226   - 76 in 1
227   - 1200 in 1
228   - Action 52
229   - 31 in 1
230   - 22 in 1
231   - 20 in 1
232.0 - Codemasters Quattro series (hard reset to get back to menu)
232.1 - Aladdin version (hard reset to get back to menu)
233   - 42 in 1
234   - AVE Maxi 15
235   - Golden Game 150 in 1
236   - Realtec 8155 multicarts
237   - Teletubbies 420 in 1
240   - misc chinese mapper
241   - BxROM-like
242   - Wai Xing Zhan Shi
243   - Sachen SA-020A
244   - C&E Decathlon
245   - Waixing MMC3 clone
246   - Taiwan mapper
248   - same as 115
249   - funky MMC3 pirate doodle
250   - Time Diver Avenger
253   - VRC4 clone with VRAM extentions, waixing
254   - al senshi nicol
255   - 115 in 1
262   - Sachen Street Heroes (dipswitch 0 sets the game title screen)
281   - mapper 90 variant 256K outer bank
282   - mapper 90 variant 256K outer bank
284   - drip
290   - Asder 20 in 1
295   - mapper 90 variant 128K outer bank
302   - FDS Gyruss conversion
304   - Several FDS conversions
305   - FDS Castlevania 2
306   - Exciting Basket FDS conversion
307   - FDS Metroid
312   - Highway Star FDS Conversion
331   - duplicate of 130
346   - Zanac FDS Conversions
358   - mapper 90 variant 512K outer bank
389   - Caltron 9 in 1
413   - Super Russian Roulette
512   - Sachen Game of the Goose (honk honk!)
513   - Sachen Princess Maker game port
516   - Edubank MMC3 thing
533   - Sachen Middle School English
534   - Atari Flashback, Intellivision Play Power
552   - Taito X1-017
553   - Sachen Penguin and Seal (original version)
554   - FDS Castlevania conversion
555   - NES-EVENT2

CopyNES Mini
------------

This lets you dump cartridges and their save RAM (if equipped) directly to the SD card!  There are many supported mappers.

To dump a game, follow these steps:

* Insert the game in question into the cartridge slot.
* Select 'Run Cartridge' to make sure it works and is making good contact.
* Enter the Tools menu and select "Copynes Mini".
* Select the mapper that your game uses.  Use the NES 2.0 XML Database to find the mapper for your game.
* Note that it might take a while (up to 30 seconds) to determine the size of
  the ROMs on the cartridge.
* After the game is dumped, you can enter a filename using the Confirm button.  If no
  name is entered, it will save it with a filename determined by the sumcheck of the ROM.
* If your game has battery backed WRAM, checking the Battery box with the Confirm button will save the contents of that WRAM to an .sav file.
* Hitting Confirm will save the ROM, hitting Back will cancel any writing to the SD Card and your ROM and RAM will not be saved.

That's it!  You can test the game by going into the cores menu and selecting "NES", then
going to the /COPYNES/ directory and running the ROM.

-----------------------------
Atari 2600 Core Release Notes
-----------------------------

The Atari 2600 core currently only supports joystick games.

Atari 2600 games determine the number of scanlines they will use.  In HDMI mode, the display window for Atari 2600 games is 160 pixels by 238 pixels, which is adequate for most games.  A few games (Pick and Pile, and Acid Drop) produce far too many scanlines, the viewport can be centered so that most of the screen is visible.

Controller mapping:
-------------------

It is suggested to use a SNES controller or a Super Famicom NTT Data Keypad.  If not, the difficulty switches and TV type and Supercharger load functionality is present in the core options menu.

You can swap joystick ports virtually, because some games seem to use one or the other.  This is also accessible in the core options menu.

Y is the fire button (B on an NES controller).  

Left and right triggers toggle the difficulty switch for this player, while on
player 1 X and A toggle the B&W/colour switch.  X is colour, A is B&W.

In most games, left trigger is hard, and right trigger is easy.

Select and start are select and reset, respectively.

Core Options menu:
------------------

You can enable/disable the Atarivox and the controller swap.  A toggle for the difficulty and TV type switches is present.  An option to load the next portion of a Supercharger ROM is also here.

Supercharger games:
-------------------

If you wish to play Supercharger games, you must rename the 2K Supercharger BIOS ROM to "scbios.bin" and place it in the /BIOS/ directory.

When you wish to load a Supercharger game, press both A and X to 'press play on tape'.
If you have a multiload game, you can press these again to do the next load when the
game calls for it.

Note: it takes about 1-2 seconds for the load to start when the A/X combo is pressed or the menu entry selected and pressed. 

Atarivox:
---------

Atarivox is supported, via a PIC18F1320.  The PIC ROM code is stored as avoxrom.bin and the PIC EEPROM data is stored as avoxee.bin. avoxrom.bin is 8K bytes, and avoxee.bin is 256 bytes.
Place these two files in the /BIOS directory.  

Note that the EEPROM is the data on the PIC micro itself, and not the high score/setting EEPROM. The EEPROM that stores high scores, etc. is not implemented at this time.

Supercharger Demo Unit:
-----------------------

The demo unit is fully supported.  To run it, you need to make a single 66K
file consisting of the 64K worth of data EPROMs, followed by the 2K EPROM.

Palettes:
---------

All three palettes are supported: NTSC, PAL, and SECAM.  There is also an 
"automatic" mode that will select between NTSC and PAL in most cases.  It does
this by checking the scanline count.  If it's greater than 284, then the PAL
palette is selected, otherwise NTSC is.

You can force a palette to either of the three, or automatic in the core settings
menu.

Mappers and ROMs:
-----------------

The 2600 has no standardized ROM header format, making it difficult to determine the identity of any extra hardware on the cartridge.

The 2600 core determines the ROM's mapper based on file size, and then file
extension.

The mapper is determined like so:

(filesize)
2048 bytes - standard 2K game, no bankswitching
4096 bytes - standard 4K game, no bankswitching
8192 bytes - standard 8K game, uses F8 (FFF8/FFF9) bankswitching
16384 bytes - standard 16K game, uses F6 (FFF6-FFF9) bankswitching
32768 bytes - standard 32K game, uses F4 (FFF4-FFFA) bankswitching
65536 bytes - Dynacom Megaboy
12288 bytes - RAM+ (FA)
10240 bytes - Pitfall 2 (DPC)
10495 bytes - Pitfall 2 (DPC)
24576 bytes - 24K (FA2)
8448 bytes - Supercharger single load
16896 bytes - Supercharger dual load
25344 bytes - Supercharger triple load
33792 bytes - Supercharger quad load
67584 bytes - Supercharger demo unit

For 8K, 16K, and 32K games, superchip RAM is detected by looking at
the first 256 bytes of the file.  If it is all 0x00 or 0xff then
the game is assumed to have RAM here.

At this point, the extension is checked.  If it matches one of the below, then this
mapper is selected:

*.ACT - Activision 8K FE banking
*.PB  - Parker Bros. E0 mapping
*.TV  - Tigervision 3F mapping  
*.TVR - Tigervision 3E (with RAM) mapping
*.MN  - M-network E7 mapping
*.CV  - Commavid extra RAM
*.EB  - Econobanking
*.EF  - EF Bankswitching
*.EFR - EF with RAM
*.UA  - UA bankswitching
*.X07 - X07 bankswitching
*.SB  - Superbanking

Note: A popular ROM pack may show certain characters in file names as flashing characters (i.e. pele's soccer).  These show up as flashing characters in the menu. This is normal because they are outside of the ASCII range later.

The following changes need to be made to get these games to run:

These need the .ACT extension:
Decathlon
Robot Tank
Thwocker

These need the .PB extension:
Frogger II
Gyruss
James Bond 007
Lord of the Rings
Montezuma's Revenge
Mr Do's Castle
Popeye
Q-bert's Qubes
Star Wars: Return of the Jedi
Star Wars: The Arcade Game
Super Cobra
Tooth Protectors
Tutankham

These need the .TV extension:
Espial
Miner 2049'er
Miner 2049'er Vol 2
Polaris
River patrol
Springer

These need the .MN extension:
Bump 'n' Jump
Burgertime
Masters of the Universe
Anteater
Golden SKull
Treasures of Tarmin

These need the .CV extension:
Magicard
Video Life

Other changes:

Dig Dug needs to have the first 256 bytes zeroed out (or set to all FF's) so that
the extra RAM can be detected properly.

-----------------------------
Atari 7800 Core Release Notes
-----------------------------

This Atari 7800 core supports official games and pokey sound.  It currently only supports joysticks and does not run 2600 games. Two button controllers appear to be working.

Controller mapping:
-------------------

This core requires the use of a SNES controller if you wish to manipulate the pause button and difficulty switches.

X is pause on either controller.
L and R triggers change the difficulty switch position for the respective player.

Select and start are select and reset, respectively.

The difficulty switches can also be toggled with Core Options.

Mappers and ROMs:
-----------------

Atari 7800 ROMs use headers.  There are a few ROMs with bad headers, here is how to fix some of them :

* Commando has no Pokey sound - the header needs to have it enabled. (0036h needs to be 03h instead of 02h)
* There's a broken version of Summer Games and Winter Games.  Both need address 0036h changed from 02h to 06h.
* There is a broken version of Sentinel as well.  Byte 0036h needs to be 02h instead of 03h.

This core needs a BIOS to run which you can select with Core Options.  The Core will load the file 7800bios.bin found in the /BIOS/ Directory by default.

-------------------------------
Sega Genesis Core Release Notes
-------------------------------

The Sega core supports all official Genesis ROMs except for Virtua Racing and does not run 32x ROMs and some uncommon Taiwan unlicensed games.

*Button Mapping*
----------------

With a NES controller, Button C on a Genesis 3-button controller is mapped to Select.  Other mappings are as follows :

Genesis   SNES/NTT Data Keypad
    A   =   B
    B   =   Y
    C   =   A
    X   =   X
    Y   =   L
    Z   =   R

Genesis   8bitdo M30
    A   =   B
    B   =   Y
    C   =   A
    X   =   X
    Y   =   Z
    Z   =   C

Genesis   Famicom Network
    A   =   0
    B   =   B
    C   =   A
    X   =   6
    Y   =   #
    Z   =   .

------------------------------
SMS/SG-1000 Core Release Notes
------------------------------

The SMS core runs games released for the Sega Mark III and the Master System.
This core also runs SG-1000 games but you must use the Japanese BIOS or no BIOS, however.

You can select a BIOS or disable a BIOS in the "Core Options" menu.  Disabling it all the time may not be ideal because a few games rely on it running first to set memory (see below for a list).

The BIOS is only loaded when a game is loaded.  To change the BIOS you must reload the game. If it is missing, loading will fail and it will return you to the core menu.  Place the BIOS into the /BIOS/ directory on the SD card and try again, or turn the BIOS off in the "Core Options" menu.

The core will load the file with the name smsbios.bin by default if one is found in the /BIOS/ directory.

You may need to change to an "export" region under "System/Hardware" to get some games or BIOSes to work. 

Because there are three mappers supported, selecting one of the different mappers works by changing the file extention of the ROM file.  

A ROM that's 48K or less in size is run without a mapper;  it is just loaded straight into 0000-BFFF.  

A ROM with a size greater than 48K will use the standard Sega mapper.

Other mappers supported:

*.SCM - selects the SMS Codemasters mapper.  The following games require it :

Cosmic Spacehead
Dinobasher - Starring Bignose the Caveman (Proto)
The Excellent Dizzy Collection (Proto)
Fantastic Dizzy
Micro Machines

*.SKR - select the SMS Korean mapper.  The following games require it :

Dallyeora Pigu Wang (Korea) (Unl)
Jang Pung II (Korea) (Unl)
Jang Pung 3 (Korea) (Unl)
Samgukji 3 (Korea) (Unl)

Any other extention is valid, and will just load as either no mapper or the standard Sega one.

The system will properly run larger, bankswitched BIOS ROMs such as the combined BIOS+Hang On,
etc. ROMs.

Some ROMs have a useless 512 byte header at the beginning that is mostly 0's. If this is found, it is ignored.

Some versions of the system have a "game reset" button.  You may activate this feature by pressing select and X at the same time on a SNES controller or by pressing the "End" button on Famicom Network or Super Famicom NTT Data Keypad.  That is a safeguard to prevent it accidentally being pressed and resetting the game.

Pause is mapped to the start button like you'd expect.

Lastly, you can turn the YM2413 on and off.  This is because a couple games crash if it's on.

*Problems and how to solve them*
--------------------------------

SG-1000:
Unselect "Use BIOS" for playing these games or select the Japanese BIOS.
Also, select Japan as the Region in System/Hardware.

Terebi Oekaki: needs a drawing tablet and will not start without it.

SMS:
You may need to pivot between the US and Japanese BIOSes for certain games to work.  The US BIOS performs a region check and will not play games (such as Sega's Japanese games) that do not pass the check.

* PAL games might have problems such as sprite flicker- this is normal and happens on an NTSC system too.

* Some games (Walter Payton Football, Spy vs. Spy) need the US BIOS to work.  The former runs but has initial title screen corruption and the latter doesn't start at all.

* MSX Ports larger than 48K use unusual mappers and are not supported.

* Games that require a paddle controller, light gun or the 3-D glasses will not work.  

* Wanted - you must turn off FM for this game to work but it still requires a light gun, so the game is not playable.

* Super Tank - select one of the "export" options in System/Hardware.

* Back to the Future 3 - locks up at black screen because it detects PAL/NTSC and will refuse to work if it detects NTSC.  It is a PAL game.

----------------------------
Game Gear Core Release Notes
----------------------------

Early models of Game Gear did not include a BIOS, but later ones did.  If you wish to see that blue startup screen, you can by selecting the BIOS file under "core options".  The core will load a file with the name ggbios.bin by default if found in the /BIOS/ directory.

Because there are three mappers, selecting one of the different mappers works by changing the file extention of the ROM file.  

A ROM that's 48K or less in size is run without a mapper;  it is just loaded straight into 0000-BFFF.  

A ROM greater than this size will use the standard Sega mapper.

Other mappers supported:

*.GCM - selects the SMS Codemasters mappers
*.GKR - selects the SMS Korean mapper.

Any other extention is valid, and will just load as either no mapper or the standard Sega one.

*Problems and how to solve them*
--------------------------------

These games are not actually Game Gear games but were released on the system and operate in SMS mode. You can play them on the SMS core:

Castle of Illusion - Starring Mickey Mouse
Cave Dude (Proto)
Chase H.Q.
The Excellent Dizzy Collection
Fantastic Dizzy
Jang Pung II/Street Battle (Unl)
Olympic Gold
Out Run Europa
Predator 2
Prince of Persia
Rastan Saga
R.C. Grand Prix
Street Hero (Unl)
Super Kick Off
Super Tetris (Unl)
WWF WrestleMania Steel Cage Challenge

These games need the .GCM file extension :

CJ Elephant Fugitive
Cosmic Spacehead
(Archer MacLean's) Dropzone
Ernie Els Golf
The Excellent Dizzy Collection
Fantastic Dizzy
(S.S. Lucifer) Man Overboard!
Micro Machines
Micro Machines 2: Turbo Tournament
Pete Sampras Tennis

The Core will not play any games that use EEPROM for saving, they will refuse to load.  The following games are the only known games to use EEPROM :

Hyper Pro Yakyuu '92
Majors Pro Baseball, The
Pro Yakyuu GG League
World Series Baseball
World Series Baseball '95 (including prototypes)

Colecovision Core Release Notes
-------------------------------

The Coleco core will run games designed for the unenhanced ColecoVision as well as Super Game Module games.

Loading a BIOS is required for this Core to load ROMs.  Load a BIOS under the core options menu.  The Core will automatically load a file named "colbios.bin" if found in the /BIOS/ directory, but you can use the Select New BIOS File option to select a BIOS file with any name.

*Button mapping*
----------------

A SNES Controller (or any compatible 12-button controller) is necessary to use this Core.  The Famicom Network Controller or Super Famicom NTT Data Keypad are the ideal controllers for this core.  The Super Famicom NTT Data Keypad's numberpad is directly mapped the Coleco controller's numberpad.  Same for the Famicom Network Controller.

If using a standard SNES Controller, this is how the Coleco numberpad maps to the SNES buttons :

Start - mapped to 1 (this usually selects the easiest game difficulty)
Select - mapped to 3 (this usually selects a harder game)

X - mapped to #  (a popular option for some games to use as a start button)
A - mapped to *  (another popular option to start games)

The other numbers are gotten by using the left and right triggers in various combinations with directionals:

Ltrig + up = 0
Ltrig + right = 1
Ltrig + down = 2
Ltrig + left = 3

Rtrig + up = 4
Rtrig + right = 5
Rtrig + down = 6
Rtrig + left = 7

Ltrig + Rtrig + up = 8
Ltrig + Rtrig + right = 9

*Special ROM handling*
---------------------------------
Two reproduction games, The Black Onyx and Boxxle use EEPROM for saving, 256 bytes and 32KB, respectively.  Rename their extensions to .ce0 and .ce1, respectively to get them working.  
A third reproduction game, Gradius, saves to flash memory and uses a custom mapper.  Rename its extension to .cf0 to get it working. 

--------------------------
Gameboy Core Release Notes
--------------------------

The Gameboy core supports games using MBC1, MBC2, MBC3 (except RTC saving) and MBC5 (except rumble).  You must select the Gameboy's bootstrap (BIOS) for it to work.  
dmgbios.bin is the default file to be loaded if found in the /BIOS/ directory.  The Super Gameboy bootstrap also seems to work and skips the scrolling intro.

--------------------------------
Gameboy Color Core Release Notes
--------------------------------

The Gameboy Color core supports games using MBC1, MBC2, MBC3 (except RTC saving) and MBC5 (except rumble).  You must select the Gameboy Color's bootstrap (BIOS) for it to work.
gbcbios.bin is the default file to be loaded if found in the /BIOS/ directory.

--------------------------------
Intellivision Core Release Notes
--------------------------------

The Intellivision core supports games for the base system, the Intellivoice speech attachment and to some extent, the Enhanced Computer System addon (ECS).

You may load the Executive BIOS file for the Intellivision by name.  You will also need the GROM binary placed in the /BIOS/ directory.

To use the Intellivoice, the 2K ROM for the speech chip has to be present in the /BIOS/ directory and named 012.bin.

*Controller support*
--------------------

Only the Super Famicom NTT Data Keypad or the Famicom Network Controller can fully map the numberpads of the Intellivision controller.

By default, the controller plugged into port two on the console will likely be seen as player one by the game, so the Core Options menu allows you to swap controllers.  It also allows you to enable ECS, Intellivoice and Intellicart mapping.  

*INTV2 ROM Format*
------------------

Because Intv games map themselves into various areas of memory, the ROM must be able to tell the Core into which areas of memory address space game code and data are to be loaded.  There is more than one existing format for Intellivision ROMs.

The existing Intellivision ROM conventions were deemed unsuitable to the Intellivision Core.  To make something usable, a new file format was created called INTV2.  It has the extension .intv and the Core will only load Intellivision ROMs in this format.

The files are a relatively simple format.  All data is stored in little endian form, with the lowest 8 bits first and the upper 2 bits (for decles) stored next with the top 6 bits 0's.  This format allows the storage of 16 bit words too, since some homebrews use these instead.  It is also stored in little endian format.

Since the ROMs self-map into memory, some provision to define where data goes is needed, thus a chunked format was devised.   

Each file consists of 1 or more chunks, which define the start address in memory where the data is to be loaded, and its length followed by the actual data.  The last chunk is simply an address and length of 0.

All address and length values are little endian.  Each field is 32 bits.  The first 64K of the address space is the Intellivision's memory map directly.  Each address is a word address, so 0x5000 is word address 0x5000 (which would technically be byte 0xa000 on a modern system).

Here's an example using Burgertime.  It is a 16K game (8K words).  It maps into memory at 0x5000, and has a length of 0x2000 (words).  It is constructed as so:

/ address \ /  length \     ROM data          / address \ /  length \
00 50 00 00 00 20 00 00 <16K of data follows> 00 00 00 00 00 00 00 00

Bit 16 of the address right now selects if this area is writeable or not (i.e. RAM).
The other bits may be used in the future for bankswitched games and/or homebrews as they arise.

The BIOS you wish to use also needs to be in this format, since the different BIOSes (i.e. intv2) load data in different places.

-----------------------------
Mandelbrot Core Release Notes
-----------------------------

The Mandelbrot Core only works with an HDMI video connection, it does not work via analog video output.  To exit the Core "blind", press Menu, then B then A.

With a NES Controller, zooming into the Set is accomplished by using button B and zooming out by using button A.  Moving the D-pad will move around the Set.  Pressing Start will reset to the default view of the Set and pressing Select will show a Julia Set representation based on the current center coordinates of the screen for the Mandelbrot Set.  The further you are zoomed in on the Mandelbrot Set, the Julia Index changes in increasingly finer steps.  

The Core has a finite ability to zoom in on a Set and eventually will begin to "stretch" the image instead of zooming in on the patterns. If zoomed in beyond the maximum zoom, you may see a display glitch of purple vertical lines.  This glitch will persist until you press Start to reset the zoom and positioning or zoom into a frame without the purple stripes and then zoom out.

This Core is best experienced with a SNES Controller.  With a SNES Controller, button Y zooms in and button B zooms out.  The Mandelbrot Set renders internally at 640x480, but the resolution is halved 320x240 by default, use button A to change it to 640x480.  The higher resolution will make movement and zooming slower, as will increasing the Number of Iterations in the Core Options, but will give more detail to the set.  The shoulder buttons L and R allow for color cycling outside the plotted set and the X button will adjust the Julia Index to sweep through many nearby Julia Sets.

----------------------------------
Adventurevision Core Release Notes
----------------------------------

The Adventurevision core runs all games.  The Code Red demo does not run as well as the games because it does not use BIOS routines for graphics drawing.

There are two BIOS files needed for this core:

avbios.bin    - This is the 1K ROM found inside the 8048 on the system.
avsound.bin   - This is the 512 byte ROM on the sound CPU.

Both of these need to be put in the /BIOS/ directory and named as identified above.

Turtles seems to have a graphical "bug" on it, the right size of the maze is shifted right by a pixel, but this is how the real system runs it.

Defender likewise has a bad collision bug on original hardware, you can often shoot through enemies, this appears to occur due to the game checking only when your shots touch the edge of an enemy sprite.

-------------------------------
Arcadia 2001 Core Release Notes
-------------------------------

The Aradia 2001 core runs known 2001 games, but there are other systems based on the same/similar chips.  Games for these systems may or may not run on this core.  

Several prototypes of released games have graphics issues that the released versions fixed.  

Some homebrews games rely on the numberpad rather than the joystick to move.

Controls:
---------

You can use the keypad of a Super Famicom NTT Data Keypad or press "chords" on a SNES controller.  The "chording" works similar to the Colecovision:

Ltrig + up = 0
Ltrig + right = 1
Ltrig + down = 2
Ltrig + left = 3

Rtrig + up = 4
Rtrig + right = 5
Rtrig + down = 6
Rtrig + left = 7

Ltrig + Rtrig + up = 8
Ltrig + Rtrig + right = 9
Ltrig + Rtrig + down = *

These buttons don't require chording:

X = #
A = option (both controllers)
start = start (both controllers)
select = select (both controllers)
Y = fire button

----------------------------
Channel F Core Release Notes
----------------------------

The Channel F BIOS is required to be present in the /BIOS/ directory and it must be named cfbios.bin.

*Button mapping*
----------------

There are four buttons on the Channel F system to select a game, time length, and other things. Starting a game involves optionally setting these to start playing.

On this core, the mapping of these four buttons is as such to a SNES controller:

1 - left trigger
2 - right trigger
3 - select
4 - start

If you have a Super Famicom NTT Data Keypad, 1, 2, 3, 4 map to 1, 2, 3, 4 on the Super Famicom NTT Data Keypad's numeric keypad.  

Using it:

When the system is reset, it says G? on the screen.  It is asking which game to play.  Hitting
one of the four buttons results in selecting one of the 4 games on the cartridge.

 (left trigger) 1 - "game 1" (from the cart, or the BIOS if "play bios games" file is run)
(right trigger) 2 - "game 1" (from the cart, or the BIOS if "play bios games" file is run)
       (select) 3 - "game 3" (from the cart)
        (start) 4 - "game 4" (from the cart)

Next, it will print S? on the screen.  You can either start a game now or enter more options.
These options are:


 (left trigger) 1 - time limit
(right trigger) 2 - game speed/(mode or motion)
        (start) 4 - start game immediately

If you press 1 for a time limit, then T? is displayed.  You can choose a time limit using the
four buttons:

 (left trigger) 1 - 2 minutes
(right trigger) 2 - 5 minutes
       (select) 3 - 10 minutes
        (start) 4 - 20 minutes

At this time, you can press either 1, 2, or 4 since it should be back at the S? prompt.

If you had pressed 2 for a mode (motion / speed) M? will be displayed.   Generally, 1-4
will be the speed of the game from slow to fast.

 (left trigger) 1 - speed 1
(right trigger) 2 - speed 2
       (select) 3 - speed 3
        (start) 4 - speed 4

As with the time setting, it should be back at the S? prompt, ready for the next option.

For general-variety playing, you can simply load a game and hit ltrig/rtrig/select/start then start
to start one of the 4 games.

It seems many games choose one controller port at random to use for player 1 (i.e. some games use controller port 1, some use controller port 2) so if a game does not seem playable, add a second controller or swap ports.

-------------------------------
Creativision Core Release Notes
-------------------------------

You must press reset after loading a game on this system to play it.

The Creativision plays games and supports the keyboard but tape saving and loading are not working.

The Creativision BIOS must be present in the /BIOS/ directory and named
crbios.bin.

*Button mapping*
----------------

Even though there is no support for a physical keyboard, the games are still playable using a regular controller.

The B and A buttons are mapped to the two fire buttons, and start/select are mapped to the two most common buttons used to start the games.  

On startup, most games will run, show a demo mode and even appear to respond to controller input.  To get out of demo mode, you must reset the system.

-------------------------
Gamate Core Release Notes
-------------------------

This core needs a BIOS, and there's two known BIOSes-  a Bit Corp version and a UMC version. Either can be used, but it must be named:

gmbios.bin

and placed in the /BIOS directory on your SD card.

There are three mappers on the system, and two of these can be distinguished by file size, however the multicart(s) need the .GML extension.  So rename the file from i.e. 4-in-1.bin to 4-in-1.gml to run it.

----------------------------
Game King Core Release Notes
----------------------------

This core needs a BIOS.  It should be named:

gkbios.bin

Sometimes it can be found named gm218.bin

placed it in the /BIOS directory on your SD card.

There's three built in games to the system, so if you wish to play these,
simply run the included file, "play bios games.bin".  This is an empty file
consisting of nothing but bytes of 0xff.  This simulates having no cartridge
in the system.

----------------------------
Odyssey^2 Core Release Notes
----------------------------

The Odyssey^2 core supports keyboards via PS2 and an adapter that plugs into the Famicom expansion port.  If you wish to make an adapter, you can find the
schematic in the /SYSTEM/ directory.

The Voice speech expansion add-on is also complete and fully functional if you wish to hear speech/sound effects in the games that support it.

Some games (such as Frogger) play poorly with The Voice being enabled all the time, but most games will work fine with it enabled.  On Frogger it will constantly repeat an allophone over and over.  This is not a bug but a byproduct of how The Voice works.  

This core needs a BIOS.  It should be named:

o2bios.bin    - Main 8048 BIOS (1K byte)

This BIOS file can be selected with Core Options.

If you wish to use the voice, you need three files:

019.bin       - Speech ROM in the SP0256-019 speech chip (2K bytes)
sp128_03.bin  - Speech ROM resident in the speech module (16K bytes)
sp128_04.bin  - Speech ROM in Sid the Spellbinder (16K bytes)

Place them in the /BIOS/ directory and name them as indicated above.

Controller mapping:

The controller maps the directionals directly to the Odyssey^2 directions as you'd expect.  On a SNES controller the mapping is as follows :

Y is the fire button
start is "1" on the keyboard
select is "2" on the keyboard
A is "3" on the keyboard
X is "4" on the keyboard
Ltrig is "enter" on the keyboard
Rtrig is "clear" on the keyboard

Note that some games swap the two controllers from the majority of games, so player 2 is actually the controller to use for single player games.

Keyboard mapping:

If you make or buy the PS2 adapter and use a PS2 keyboard you can use it directly to simulate the Odyssey^2 keyboard.

All Odyssey^2 keys map to their corresponding keys on a PC keyboard except "clear" which is mapped to backspace.

Most games can be played without the keyboard, due to the mapping of 1-4 from the keyboard which are usually used to start games.  Some games like Killer Bees start using the fire button.

-------------------------------
RCA Studio 2 Core Release Notes
-------------------------------

The Studio 2 core runs games and homebrew.

The video display can be problematic on this Core, showing the following issues:

* The selected entry on the menus flashes really fast.  
* The screen might scroll on reset
* You cannot see the menu on composite/rgb if the CPU is reset.

These problems are related to how the system renders video,  the CPU itself drives the video display, and when the CPU does not run, it does not generate video timing.  

Many games on this system them start with a black screen until you press a button.  This is normal, refer to the instruction manual to determine how to start the game.

This system requires a BIOS, and it must be named "rca2bios.bin" and placed in the /BIOS/ directory.

Controller mapping:
-------------------

The system has two 10 key keypads.  These are almost always used as a "joystick".  Here is how it maps to a SNES Controller :

1, 2, 3, 6, 9, 8, 7, 4 equal up, up/left, up, up/right, right, down/right, down,
down/left, and left respectively.  
5 and 0 are mapped to Y and B respectively.

You can hold down A which will disable the D pad on the controller so you can easily press 1, 3, 9, or 7 (the diagonals) without hitting one of the cardinal
directions.

If you have a Super Famicom NTT Data Keypad, you can use its numberpad to hit 0-9.

This core uses a monochrome menu.  This is normal.

Note: When the system is first started and a game is loaded, it's overwritten by the BIOS games,
so the first games that will play are the BIOS games.  Loading another game or the same one again
will cause it to load the game as desired.

------------------------------
Supervision Core Release Notes
------------------------------

The Supervision core plays all games and does not require a BIOS.

sssnake appears to output a very quiet sound when you pick something up, but this is a bug in the program.  The game is playing one of the drum samples really slowly so it doesn't make much sound.

-----------------------------
Videobrain Core Release Notes
-----------------------------

The Videobrain supports keyboards via a PS2 keyboard and the Odyssey^2 adapter.

This core needs a pair BIOS ROMs. They must be named:

uvres1.bin    - The first BIOS file (2K bytes)
uvres2.bin    - The second BIOS file (2K bytes)

Place them in the /BIOS/ directory.

Controller mapping:

The controller maps the directionals directly to the Videobrain's directionals

B is the fire button

Keyboard mapping:
-----------------

If you use the PS2 adapter and keyboard, the PC keyboard maps as follows :

A-Z maps to A-Z
Capslock is the Shift key because the Capslock function is controlled by the system.  The state of shift is indicated on screen with a box at the bottom right.  If it's black, it's unshifted and A-Z works like usual.  If it's grey, shift is on and symbols and numbers are usable.  The mapping of the keyboard when shifted and unshifted is as follows:

Non-shifted characters:

A-Z, 0, space

Shifted characters:

1-9, !, #, $, %, *, (, ), -, +, =, ., ', ", ?
F9  - cent symbol
F10 - pi symbol
F11 - division symbol
F12 - multiplication symbol

These characters and symbols are "dual mapped", because shift/nonshift is not known by the keyboard, due to the shift being handled in the VideoBrain itself, so if you are unshifted and press %, Q will print to the screen.  Likewise if it is shifted and Q is pressed, % will appear.

F1 - restart/erase
F2 - run/stop
F3 - alarm/special
F4 - clock/next
F5 - color/previous
F6 - text/back

Playing the games:
------------------

Many of the games need the keyboard to start them.

There is an empty binary file that lets you use the built in BIOS functions.

----------------------
Megaduck Release Notes
----------------------

Megaduck has no BIOS but it does have mappers.

*Special ROM handling*
---------------------------------
There are two different mappers for Megaduck.  They are selected by extension.  .MD1 selects the single 32K selectable bank mode, and .MD2 selects the 16K selectable bank mode.  
All games greater than 32K need the .MD2 extension except for the following two games: Puppet Knight and Suleiman's Treasure. These need the .MD1 extension.  32K games do not need a special extension.

--------------------------
Controller Support Summary
--------------------------

Core Name               NES     SNES    FC Net  NTT Data   Note Ref #

NES                     F       E       L       E           1
NSF Player              F       F       N       F
Atari 2600              F       E       N       E           2
Atari 7800              F       E       N       E           3
Genesis                 L       F       F       F           4
SMS/SG-1000             F       E       E       E           5
Game Gear               F       F       F       F
Colecovision            L       F       E       E           6
Gameboy                 F       F       N       F
GBC                     F       F       N       F
Intellivision           L       L       F       F           7
Mandelbrot              L       F       N       F           8
SPC Player              F       F       N       F
Adv. Vision             F       F       N       F           
Arcadia 2001            L       F       N       E           6
Channel F               L       F       N       E           9
Creativision            F       F       N       F          10
Gamate                  F       F       N       F
Game King               F       F       N       F
Odyssey^2               L       L       N       L          11
RCA Studio II           F       E       N       E+         12
Supervision             F       F       N       F
Video Brain             L       L       N       L          11
Megaduck                F       F       N       F

Key                     Designation     Explanation
Full Functionality      F               Controller is fully functional with this Core
Extra Functionality     E               Controller brings extra convenience to using the Core, but is not essential
Limited Functionality   L               Controller does not have sufficient features to play all games another controller has for this Core

Notes

1 - FC Network works as a Standard Famicom Controller 3 with its limitations (no menu access, requires per-game support to be read as Controller 1).  SNES Shoulder Buttons allow Vs. Coin input.

2 - SNES Buttons Allow Control over TV Type, Difficulty Switches and Supercharger Load without Menu Access

3 - SNES Buttons Allow Control Pause and Difficult Switches without Menu

4 - NES cannot support 6-button controller input

5 - Non-NES controllers add reset button support, which was only present for original Master Systems

6 - NES has no numberpad support, SNES requires D-Pad and Button combo for numberpad

7 - NES and SNES have no numberpad support

8 - SNES Buttons allow for resolution change (A), color cycling (L & R) and Julia Index manipulation (X)

9 - NES has limited console switch support, SNES uses lettered buttons for console switches

10 - Keyboard not supported, this is the best option the Core supports

11 - System includes a keyboard, 100% software compatibility is limited without the Custom PS/2 Adapter

12 - SNES lets you hold A to hit diagonals easily, NTT allows numberpad use (the controllers for this system are just numberpads)

-------------------------------------------
Wireless Controller Functionality Reference
-------------------------------------------

8bitdo Product  Protocol    Functionality   Receiver Type       Notes

NES30/SNES30@   Bluetooth   SNES            Retro Receiver      Discontinued, requires old custom firmware^
M30/SN30*       Bluetooth   NES             Retro Receiver      Current Firmware
M30/SN30        2.4g        SNES            SNES 2.4g Adapter   Requires SNES to NES adapter
M30/SN30/N30    2.4g        NES             NES 2.4g Adapter    You can use M30 and SN30 controllers, but the extra buttons will not work.

@ - The NES30 came with the original Nt Minis and was sold standalone.  It has four red action buttons and two shoulder buttons.  The SNES30 has the diagonal Start and Select button layout of an original SNES controller.
* - Presumably any current 8bitdo Bluetooth controller would work to this extent, NES30 also works with this limitation if current firmware is used.
^ - Download firmware here : https://support.analogue.co/hc/en-us/articles/115001657087-Using-the-Retro-Receiver-for-NES-with-the-Nt-mini, ignore what it says about Nt Mini Noir.

Putting Controllers into Pairing Mode
-------------------------------------

To put the SN30, N30, SNES30 or NES30 into pairing mode, press Select for 3 seconds until the blue LED starts to rapidly blink.  To put the M30 into pairing mode, press Mode (-) for 3 seconds until the blue LED starts to rapidly blink.

-----------------------------
Required/Supported BIOS Files
-----------------------------

                    Required Name
Core Name           /Default Name*  Byte Size   CRC32       Description
---------------     --------------  ---------   --------    --------------------
                    

Adventurevision     avbios.bin        1024      279E33D1    8048 internal ROM
                    avsound.bin        512      81E95975    Sound CPU ROM

Atari 2600          avoxrom.bin       8192      EB8DE7CD    Atarivox PIC ROM
                    avoxee.bin         256      66C92EF6    Atarivox PIC EEPROM
                    scbios.bin        2048      C3A3F073    Supercharger BIOS
                        
Atari 7800          7800bios.bin*     4096      5D13730C    7800 USA BIOS
                        
Channel F           cfbios.bin        2048      2882C02D    Channel F BIOS
                    
ColecoVision        colbios.bin*      8192      3AA93EF3    ColecoVision Official BIOS
                                      8192      39BB16FC    ColecoVision BIOS with Replacement Font and No Time Delay
                                     16384      4999ABC6    Bit Corp BIOS with built-in game
                                      8192      2ABA3C91    ColecoVision BIOS with No Time Delay
                                      8192      434E237F    ColecoVision BIOS with No Time Delay PAL Setting

Creativision        crbios.bin        2048      05602697    Creativision BIOS

Gamate              gmbios.bin        4096      03A5F3A7    The first BIOS (i.e. UMC version)
                    gmbios2.bin       4096      07090415    Optional second BIOS (i.e. Bit Corp version)
                                
Game King           gkbios.bin      524288      5A1ADE3D    Game King BIOS
        
Game Boy            dmgbios.bin*       256      C2F5CC97    Bootstrap ROM for early Japanese DMGs
                                       256      59C8598E    Bootstrap ROM for DMGs (mainstream)
                                       256      E6920754    Bootstrap ROM for Game Boy Pocket
                                       256      EC8A83B9    Bootstrap ROM for Super Game Boy (no scrolling logo)
                                       256      53D0DD63    Bootstrap ROM for Super Game Boy 2 (no scrolling logo)

Game Boy Color      gbcbios.bin*      2304      E8EF5318    Bootstrap ROM for early Japanese GBCs
                                      2304      41884E46    Bootstrap ROM for GBCs (mainstream)

Game Gear           ggbios.bin*       1024      0EBEA9D4    Boot screen shown on later Game Gears

Intellivision       012.bin           2048      8BD786EC    Speech ROM in the SP-256-012 on the Intellivoice
                                      8192      683A4158    Built-in Graphics ROM for Intellivision Master Component
                    intvexec1.bin*    8208      EEB54C63    Executive ROM for Intellivision 1
                                      8728      A85FC6DD    Executive ROM for Intellivision 2   
                                      8208      F52718C0    Executive ROM for Sears Super Video Arcade
                        
Master System       smsbios.bin*      8192      0072ED54    USA/Europe BIOS v1.3
                                      8192      1A15DFCC    USA M404 Prototype BIOS (works with few games)
                                      8192      B3D854F8    Europe BIOS v2.0
                                      8192      48D44A13    Japanese Master System BIOS v2.1

NES                 fds.bin           8192      1C7AE5D5    Famicom Disk System BIOS
                                      8192      5E607DCF    Famicom Disk System BIOS Rev. 1
                                      8192      4DF24A6C    Twin Famicom BIOS
                    
Odyssey^2           o2bios.bin        1024      8016A315    Main 8048 BIOS
                    019.bin           2048      19355075    Speech ROM in the SP0256-019 speech chip on The Voice
                    sp128_03.bin     16384      66041B03    Speech ROM resident in the The Voice speech module 
                    sp128_04.bin     16384      6780C7D3    Speech ROM in Sid the Spellbinder

RCA Studio 2        rca2bios.bin      2048      A494B339    RCA Studio 2 BIOS
                    
Videobrain          uvres1.bin        2048      065FE7C2    The first BIOS file
                    uvres2.bin        2048      1D85D7BE    The second BIOS file

If there is an * next to a file name, that means that the Core supports loading a BIOS file from the file browser and can have any name, but the Core will load a file located in \BIOS with this name (without the *) by default.
If the name in the column to the right to the Core Name has no * next to it then the core is looking for that specific file name, but the data in that file can match any of the checksums given for that BIOS.  

--------------------
Prior Update History
--------------------

v6.6 release 02/11/21

(general)
* All cores should have their video window properly centered on the X and Y axis when the sliders for position are in the center.  The exception is for cores with an extremely low original resolution, such as Game King. 
* All scaling defaults have been updated to more useful values.  
* Added SPD HDMI Packet to identify console as "Nt Mini Noir"

(NES)
* Added cheat codes menu when running ROMs via jailbreak
* Added ability to decrement letters on cheat code and Copynes mini by pressing select
* Replaced Firebrandx palette with the latest one ("Smooth_-_Balanced_Greys_FBX")
* Fixed Vs. Hogan's Alley and Duck Hunt "gun stolen" alarm sound going off all the time or in the menu
* Fixed FDS RAM Adapter, Super Mario Bros. and many other games exhibiting graphics issue when cartridges were being used
* Fixed Vs. Mighty Bomb Jack reversed controls
* Fixed Trojan audio channels cutting off early
* Fixed playing a Vs. game then an FDS game caused a bad palette
* Fixed Vs. coin insertion not working when using a SNES or NTT Data Keypad
* Fixed Sunsoft 5B audio implementation
* Fixed Battletoads and Double Dragon player 2 selection box moving on its own
* Fixed games (i.e. Kickmaster) with mappers that used A12 for scanline counts had jittering graphics in 16 sprite mode
* Fixed FDS manual disk ejection not working correctly
* Fixed Copynes mini not properly exiting high resolution mode from the file menu
* Fixed Maniac Mansion's intermitent flickering top line
* Fixed Eggerland - Meikyuu no Fukkatsu and Egger Land - Souzou e no Tabidachi's popping square channel

(GBC)
* Fixed Barbie Pet Rescue's blank screen before the title
* Fixed Pokemon Pinball's corrupt frames when screen was blanked
* Fixed Bear in the Big Blue House hanging on the title screen
* Fixed Bear in the Big Blue House's palette issue at the top of the screen
* Fixed Super Mario Deluxe (and other games) palette issues
* Fixed Mia Hamm Soccer title screen graphic issues
* Fixed Jungle Book: Mowgli's Wild Adventure corruption when paused/unpaused
* Fixed Klax crash when reaching level 5
* Fixed Mickey's Speedway palette issues
* Fixed Perfect Dark non-working digitized audio
* Fixed Perfect Dark status bar on the right not displaying

(Genesis)
* Added full screen dithering, setting the dithering slider to 63 (maximum) will enable it
* Removed non-functional cropping menu - use the crop left/right and top/bottom settings in video extras menu
* Fixed interlaced mode display issues

(Game Gear)
* Fixed top line not visible

(2600)
* Fixed graphic issues on certain units (random pixels on green screens)
* Fixed palette sometimes flashing when entering/exiting the menu

(Supervision)
* Fixed Journey to the West

(Gamate, 2600, Intellivision)
* Fixed scaling values


v6.5 release 12/15/20

(general)
* Controller test added
* Fixed L/R reverse on RCA jacks
* Fixed filter cutoff display bug

(NES)
* Added full FDS support with manual, semiautomatic and automatic side switching (see NES section below for operation notes)
* Added Super Russian Roulette mapper (#413)
* Added support for Haunted Halloween '85 and '86
* Added Vs. palette support for composite and s-video
* Reduced default expansion audio level for better balance with internal audio.
* Passthrough mode can now be cancelled by tapping reset twice.
* Fixed CopyNES mini save WRAM dumping, save games on cartridges can now be preserved
* Fixed Vice Project Doom / Gun-Dec starting in debug mode with second controller plugged in
* Fixed VRC6 register swap function.  Use both VRC6 and VRC6 Swap for Madara and Esper Dream 2 and just VRC6 for Akumajou Densetsu
* Fixed FDS Audio channel imbalance when panning sliders are centered
* Fixed small FDS channel bug
* Fixed popping square wave audio in Egger Land - Souzou e no Tabidachi and Eggerland - Meikyuu no Fukkatsu
* Fixed Vs. Goonies graphic issue
* Fixed Game of the Goose graphic issues (#512)
* Fixed DPCM corruption bug for PAL and Dendy Modes
* Fixed MMC5 Castlevania III PAL cartridge functionality
* Fixed Dendy mode for EverDrives and Cartridges
* Fixed Dendy mode NMI flag

(GB/GBC)
* Fixed palette issues affecting multiple games (Pokemon Pinball, Mega Man Xtreme, Pooh & Tigger's Hunny Safari, Harvest Moon 3)
* Fixed wave channel audio bug
* Fixed Tokyo Disney crash when playing 5th level
* Fixed crash in Barbie Magic Genie Adventure when using powers
* Fixed Razor Freestyle Scooter and Lufia failing to load
* Fixed Lego Racers cloud color bug
 
(Colecovision)
* Added Famicom Network controller functionality
* Fixed Penguin Adventure

(Genesis)
* Added Famicom Network controller functionality
* Fixed Audio sliders bug

(SMS)
* Added Famicom Network controller functionality
* Fixed BIOSes loading built in games
* Use "end" button on Famicom Network or Super Famicom NTT Data Keypad to simulate pressing console reset button

(Intellivision)
* Added Famicom Network controller functionality.  0, A, B are the three buttons. 0 on the keypad is remapped to .
* Added Player 1/2 swap to cores menu

(SPC)
* Fixed audio static bug

----------------------
v6.2 release, 11/23/20

* initial release
