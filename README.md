hhkb-xkb
===
HHKB layout for standard us keyboards (and possibly other layouts)
>Originally made for my thinkpad keyboard, tested on Pop!_OS 20.04

Features
---
- Swap CapsLock and left Ctrl
- Swap Backspace and Backslash

How to
---
1) Clone the repository 
```
git clone https://github.com/KrauseKurt/hhkb-xkb.git
```
2) Navigate to **/usr/share/X11/xkb/rules** and open **evdev**

3) Add the following code at the end of the section `! option = symbols`
```
custom:hhkb_layout  = +custom(hhkb_layout)
```
4) Navigate to **/usr/share/X11/xkb/rules** and open **evdev.lst**

5) Add the following code at the end of the file
```
custom:hhkb_layout   Happy Hacking Keyboard layout
```
6) Navigate to **/usr/share/X11/xkb/symbols** and open your desired layout (for us layout the file is **us**)

7) Add the following code at the end of the file
```
partial modifier_keys
xkb_symbols "hhkb_layout"
{
    // Swap Backspace and Backslash
    key <BKSP> { [ backslash, bar ] };
    key <BKSL> { [ BackSpace, BackSpace ] };

    // Caps Lock to Ctrl
    key <LCTL> { [ Caps_Lock ] };                   // LCtrl becomes CapsLock
    key <CAPS> { [ Control_L ] };                   // CapsLock becomes LCtrl
    modifier_map Lock    { <LCTL> };
    modifier_map Control { <CAPS> };
};
```
8) Finally run the following command on the terminal and enjoy your new layout :
```
setxkbmap -option custom:hhkb_layout
```
