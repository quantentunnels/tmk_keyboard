# ErgoDox
An ergonomic keyboard with split design.

## Resources
* [ergodox.org](official page)
* [gh-ergo](Geekhack thread)
* [ben-firmware](benblazak's firmware)

## LED support
TMK for Ergodox has support for up to seven LED's:
 - Out of the box three LEDs on the right hand side for CapsLock, NumLock and ScrollLock (the last to are not working as of yet)
 - three on the left hand side (see http://geekhack.org/index.php?topic=22780.msg873819#msg873819 for more details)
 - Teensy onboard LED

 Any of these leds can be used as layer indicator or NumLock/CapsLock/ScrollLock led.

 [Here is an example](https://github.com/cub-uanic/tmk_keyboard/blob/cub_layout/keyboard/ergodox/matrix.c#L121-167)

 how you can assign some meaning to each led.
 In this code only left leds are used to show layers, but you can
 [change `led_set()`](https://github.com/cub-uanic/tmk_keyboard/blob/cub_layout/keyboard/ergodox/led.c)
 and do anything you want with all leds.

## Build

### Compile firmware
Q: Where to get binaries?
A: There are no pre-compiled binarys available at the moment.

Q: How to compile?
A: It's actually pretty darn easy:

    $ git clone https://github.com/cub-uanic/tmk_keyboard.git
    $ cd tmk_keyboard/keyboard/ergodox
    $ make -f Makefile.lufa <which>

where <which> is which layout you want to build.
Tweak the layout file and repeat the make step. You can also create a new layout and add it as a build option, instead of stealing someone else's.

### Send firmware to Teensy
There are two possibilites:
(1) graphical PJRC loader
(2) commandline loader


## Layouts
Some layouts are included, but you can define your own layout based on these. The layout files are named 'keymap_<name>.c'.

# Things TO-DO

- [ ] Flash NumLock led only when "numpad" layer is active
- [ ] Command (in terms of IS_COMMAND) to switch to no-leds mode
- [ ] Increase count of ACTION keys
- [ ] Fix command_state() onboard led: it should flash only when kbd in some specific mode (CONSOLE || MOUSE)
- [ ] ergodox_blink_all_leds() should save current state of leds, and restore after blink. initial state of all leds == off
- [ ] add support for pseudo-backlight (reversed LEDs) + docs/photo
- [ ] command to debug all LEDs (on/off/blink)
- [ ] proper (in-core) implementation of DEBUG_MATRIX_SCAN_RATE (non-Ergodox specific)
- [ ] proper (in-core) support for per-layer fn_actions[]

