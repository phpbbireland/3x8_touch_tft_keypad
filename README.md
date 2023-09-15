# 3x5_touch_tft_keypad

<br>
<img src="/images/imagebuild.png" width=480>  

Example of finished project (stl files here) [Thinyverse](https://www.thingiverse.com/thing:6145160).  

**Hardware:**
- The project uses the Makerfabs-ESP32-S3-SPI-TFT-with-Touch board...
- A 320px240px image (.bmp) and a few icons for buttons...
- Menu line: [the_key_type], the_macro_text (characters), see example **sample_menu** text file...
- Menu files have on blank lines and no comments...
- File updated, includes Stack issue fix...
- Removed code no longer required...

**The Basics:**  
We start with a 480px by 320px background image, it consists of 16 button areas (identified by the red outlined squares).
Then using an image editor, edit Grid480x320.bmp file and import the desired button icons (64px by 64px images works well) into each of the outlined button icons positions. Once finished, export the final image as menu1.bmp and save to SD card.  

<br>
<img src="/images/blankbg.bmp" width=360>  
blankbg.bmp  
<br>

Next, create a text file called ***menu1*** and add 15 lines of text (each consisting of what we would need to type to execute the given programs, see **sample_menu** for example), then save the file to the SD card.  

```
freecad
[T]/usr/bin/flatpak run --branch=stable --arch=x86_64 --command=kicad --file-forwarding org.kicad.KiCad
/opt/sublime_text/sublime_text
/home/Mike/Downloads/arduino-1.8.19/arduino
[T]ls -l
[LA]3
/usr/share/playonlinux/playonlinux --run 'Fireworks'
firefox
xfce4-terminal
kcalc
[RA]4
meld
[NEXT]
/home/Mike/AppImages/Stellarium.AppImage
[PREV]
```
<br>
<img src="/images/menu1.bmp" width=360>  
Example Main menu (menu1.bmp)<br><br>
<img src="/images/menu5.bmp" width=360>  
Example media menu (/images/menu5.bmp)<br><br>

**Special keys:**  
- [LA] = Left Alt - [RA] = Right Alt
- [LS] = Left Shift - [RS] = Right Shift
- [LC] = Left Ctrl - [RC] = Right Ctrl
- [SU] = Super Key
- [TA] = Tab (used in conjunction with Alt, Ctrl Keys)
- [F?] = Function Keys, F1 to F24 (example [F4], [F12] etc..) ***are these needed***)
- [T]   = Open A Terminal
- [T]program_name... Launch program inside a terminal...
  
**Programming:**  
Install the Arduino IDE, add required libraries (see top of code.ino for required libraries), compile and upload *code.ini* sketch to the ESP32-S3 SPI board (don't forget to insert the SD card)...

**TBA:**  
Generating macro keyboard data is context/window-focus sensitive, that is, the active program will try to implement the keystrokes, so for testing under Linux I normally open a terminal manually, the press a key. I have added the [T] special key, to open a terminal before process the rest of the menu line (some programs require launching from a terminal, but it also helps to remove undesirable affects).  

**sample_menu:**  
Each line of the menu text can contain:  
-  A program name (can include the path) to launch, for example: ~/{HOME}/this_path/this_program.  
-  Special key combinations: [LA]+3 or [LC]+[F10] or [SHIFT]+[LC]+[LA]+x.
-  To open a terminal before processing a menu line use: [T]program_name_link_etc
-  Any combination of keys up to 128 characters.  

**After initial programming of the TFT board:**  
All changes are made to the *menu1* text file and/or the *menu1.bmp* image on the SD card, no need to recompile as these changes are imported from SD card on every boot.  

**Currently:**  
It is possible to implement as many menus as required, for example, menus might allow loading of sub-menus, with each sub-menu having 12 or 13 buttons (two would be required for navigation, one addiional for HOME menu).
...

***Future:***  
Optional 5x4 layout (20 key) (keysGrid480x320.bmp),
<br>
<img src="/images/Grid480x320.bmp" width=480>  
Anything is possible with edits to the code, you could use a larger TFT.  
Macro Keyboards are more useful for complex Video/Audion editing and hardware projects and they can always be repurpose.  
Hope it's useful to someone.  

***Some updates:***
- The ***alt*** [folder](alt/currentTestCode.ino) may contain code I am currently working on (latest tests).
- Stack issue fixed (thanks to MicroController over at ESP32 forums).  

Note, Some code is in the public domain (example code), remaining code © Michael O'Toole 2023  

Mike
