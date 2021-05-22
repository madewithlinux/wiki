# WinXP-style Alt-Tab

# problem

Windows 7 and above ship an alt-tab menu that shows thumbnails of open applications.

The problem with this is
* the size of the alt-tab menu is quite large
* the alt-tab UI renders immediately
  * (in contrast to most linux environments, where the UI waits a second to render. This allows it to not render at all, and instead switch windows immediately, if the `alt` is released inside the timeout.)

Thus, when switching between applications frequently (e.g. with two windows tiled side-by-side), the alt-tab UI menu is constantly flickering in and out of existence. This causes headaches for some people (myself included)

# potential solution: WinXP-style Alt-Tab

There is a secret keyboard shortcut that activates a much smaller and simpler alt-tab menu:

> To trigger the old XP style one, you’ll need to do the following:
> 
>  * Hold down the Left (or Right) Alt key.
>  * Press and release the other Alt key.
>  * Keep holding down that first Alt key, and then press Tab.
> 
> And Voila! The ugly old XP-style one will show up.

reference: [Stupid Geek Tricks: Windows 7 Easter Egg Shows the XP Alt-Tab Prompt](https://www.howtogeek.com/howto/5200/stupid-geek-tricks-windows-7-easter-egg-shows-the-xp-alt-tab-prompt/)

## problem: too hard to type
This keyboard shortcut is a huge pain to type. Two hands just to alt-tab!?! No thank you!!!

**solution:** use a QMK keyboard macro to tap the other alt key:

```c
enum custom_keycodes {
    TABALT = SAFE_RANGE,
};
bool process_record_user(uint16_t keycode, keyrecord_t *record) {
    switch (keycode) {
    case TABALT:
        if (record->event.pressed) {
            if ((get_mods() == MOD_BIT(KC_LALT))) {
                tap_code(KC_RALT);
            }
            register_code(KC_TAB);
        } else {
            unregister_code(KC_TAB);
        }
        break;
    }
    return true;
};

// and then replace KC_TAB with TABALT in layout definition
```

See [my full keyboard layout file](https://github.com/madewithlinux/qmk_firmware/blob/master/keyboards/kbdfans/kbd75/keymaps/madewithlinux/keymap.c) for full implementation, including a function key to toggle it on and off, and using part of my keyboard's RGB underglow as an indicator.


## another problem: the switched-away-from app receives an alt tap

In many apps (chrome, firefox, vscode, etc), pressing and releasing the alt key moves the keyboard focus to some kind of menu.
Thus, with the above keyboard-macro-based mitigation, switching between windows could cause menus to focus undesirably.

I don't have a solution for this yet.


# alternative solution: regedit

reference: [Stupid Geek Tricks: How to Switch Windows 7 to the XP Style Alt-Tab Switcher](https://www.howtogeek.com/howto/28344/stupid-geek-tricks-how-to-switch-windows-7-to-the-xp-style-alt-tab-switcher/)

pros:

* no "alt tap" issue (as described above)

cons:

* cannot easily switch back to the regular switcher (the thumbnails are sometimes convenient to have)
* regedit `:/`


