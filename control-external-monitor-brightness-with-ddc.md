# control external monitor brightness with ddc

## what is DDC
[Display Data Channel - Wikipedia](https://en.wikipedia.org/wiki/Display_Data_Channel)

it's how your monitor communicates to your PC stuff like e.g. what resolution it supports.

But it can also be a bi-directional communication, and communicate other info, such as brightness, contrast, volume, input select, etc.

I find it very helpful to always have a utility handy to change the monitor brightness, so I can manually adjust it based on the ambient light in the room, weather, personal preference, etc.


## linux
package `ddccontrol` is in the ubuntu repos, and it works well enough.
(There's probably a way to set it up with hotkeys, but I haven't bothered to do that yet.)


## windows

ClickMonitorDDC is my favorite app for this.
It just sits in the tray and pops out a menu for changes, and also can change brightness when you mouseover the tray icon and scroll the mouse wheel.
(Also I think it has hotkey support? I haven't tried that)

It used to be at clickmonitorddc.bplaced.net but unfortunately that appears to be defunct now. But luckily, it's [saved on the internet archive](https://web.archive.org/web/20200910145554/https://clickmonitorddc.bplaced.net/)!
So I guess that means that version 7.2 is the last version of this software that will ever be released.
Which is sad, but not all that sad, because it seems to be very much feature-complete.

