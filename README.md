# sv-SE Keycodes
sv-SE keycodes for use with Arduino HID/keyboard emulation libraries such as TinyUSB, USBHIDKeyboard, etc.

Normally, a key-combination (e.g. SHIFT + 7) is required in order to enter some characters. However, the first four keycodes are from the keypad instead to make them easier to type programmatically. They produce the same ASCII characters as if they were typed normally. The rest are normal keycodes for keys.

### Examples
The following examples use the [Expressif USBHIDKeyboard library](https://github.com/espressif/arduino-esp32/blob/master/libraries/USB/src/USBHIDKeyboard.h).

Normal use of keycodes

```C
#include "USBHIDKeyboard.h"

USBHIDKeyboard kb;

void typeKey() {
    kb.pressRaw(CKEY_A);
    kb.releaseRaw(CKEY_A);
}
```

If you wish to use key-combinations, here is one way of doing it

```C
#include "USBHIDKeyboard.h"

USBHIDKeyboard kb;

/*
 * Colon      SHIFT + .
 * Percent    SHIFT + 5
 * AMPERSAND  SHIFT + 6
 * etc.
 */
void typeCombination() {
    kb.press(MODIFIER);
    kb.print("KEY");
    kb.releaseAll();
}
```
