# SDCC MSX ROM SPRITES 12 Functions Library (object type)

Version: 1.1

Author: mvac7/303bcn

Architecture: MSX

Format: C Object (SDCC .rel)

Programming language: C

WEB:
 
mail: mvac7303b@gmail.com




### History of versions:
- v1.1 (2/02/2017) current version


## 1. Introduction

Open Source library with functions to directly access to sprites of the TMS9918A.

Provides basic functions for initialization and display Sprites and functions for access specific parameters (positioning, color, pattern, visibility and EarlyClock).

The SPRITES_12 version is designed to work with TMS9918, although it also allows using the G3 screen mode (V9938), in a simplified manner. 

The functions that assign a color, such as PUTSPRITE or SetSpriteColor, will do it in all the lines of the sprite, so it will NOT be useful to take advantage of the multicolored improvement of the sprites of the V9938.

The Early Clock functions have also been adapted for the G3 mode, since they access the color table of the sprite planes and write in all the lines.

It's complemented with the TMS9918A MSX ROM Library.

It uses the functions from the MSX BIOS, so it is designed to create applications in ROM format.
  
Use them for developing MSX applications using Small Device C Compiler (SDCC) compilator.

Includes an application for test and learning purposes.


About the Sprite libraries:

I'm developing several libraries for the management of MSX Sprites, both for the creation of ROMs (using the BIOS), and MSXDOS executables. 
They are designed for the development of applications for the first generation of MSX but some of the variations are directed in how certain functions behave when using the G3 mode of the video processor V9938 and thus be able to take advantage of it, when it is executed in a MSX2 or higher.

The projected libraries are the following:
- SPRITES S (Small) - Basic functions for the initialization and visualization of Sprites. It is more compact so it takes up less space in our application.
- SPRITES - It includes the same functions as the Small version and adds to access specific parameters (positioning, color, pattern, visibility and EarlyClock).
- SPRITE 12 - Same as SPRITES but in the G3 screen mode (V9938), it treats the color parameters in a simplified way. Assign the color parameters and EarlyClock to all the lines of the Sprites.
- SPRITE DUMP - Uses a buffer in RAM that has to be dumped in each interruption. Includes a Sprite Flicker, to allow viewing up to 8 sprites per line.

To optimize our development, I recommend building your library with only those functions you need.

I have yet to develop a library to work with the multi-colored Sprites of the V9938.



## 2. Acknowledgments
  
Thanks for Info & help, to:

* Avelino Herrera > http://msx.atlantes.org/index_es.html
* Nerlaska > http://albertodehoyonebot.blogspot.com.es
* Fubu > http://www.gamerachan.org/fubu/
* Marq/Lieves!Tuore > http://www.kameli.net/lt/
* Sapphire/Z80ST > http://z80st.auic.es/
* Pentacour > http://pentacour.com/
* JamQue/TPM > http://www.thepetsmode.com/
* Andrear > http://andrear.altervista.org/home/msxsoftware.php
* Konamiman > https://www.konamiman.com
* MSX Assembly Page > http://map.grauw.nl/resources/msxbios.php
* Portar MSX Tech Doc > http://nocash.emubase.de/portar.htm
* MSX Resource Center > http://www.msx.org/
* Karoshi MSX Community > http://karoshi.auic.es/
* BlueMSX >> http://www.bluemsx.com/
* OpenMSX >> http://openmsx.sourceforge.net/
* Meisei  >> ?



## 3. Requirements

* Small Device C Compiler (SDCC) v3.6 http://sdcc.sourceforge.net/
* Hex2bin v2.2 http://hex2bin.sourceforge.net/ 



## 4. Functions

* void SetSpritesSize(char size) - Set size type for the sprites.
* void SetSpritesZoom(boolean zoom) - Set zoom type for the sprites.
* void ClearSprites() - Initialises all sprite data.
* void PUTSPRITE(char plane, char x, char y, char color, char pattern) - Displays the sprite pattern.
* void SetSpritePattern(char plane, char pattern) - Assign a pattern to a sprite plane.
* void SetSpriteColor(char plane, char color) - Assign a color to a sprite plane.
* void SetSpritePosition(char plane, char x, char y) - Assigns the position coordinates of a sprite plane.
* void SetSpriteVisible(char plane, boolean state) - Hides or shows a sprite plane.
* void SetEarlyClock(char plane) - Apply the Early Clock of a sprite plane. Move 32 points to the left the X position of the sprite.
* void UnsetEarlyClock(char plane) - Disables the Early Clock. Restore the position of a sprite plane.
