# Gentoo on MacbookPro 7,1 (Mid 2010)

Configuration files and utility scripts, for use or reference

Installation details:
https://wiki.gentoo.org/wiki/Apple_MacBook_Pro_13-inch_(mid_2010)

Unlike the above guide, I use the [open source broadcom drivers](http://wireless.wiki.kernel.org/en/users/Drivers/b43)

The `fix-eviocgabs-error` script fixes [this issue](https://github.com/systemd/systemd/issues/5079)

# Configuration

## Bootmanager: refind
`/mnt/efi/EFI/refind/refind.conf`

## make.conf
`/etc/portage/make.conf.macbook`

## X trackpad settings
`/etc/X11/xorg.conf.d/50-synaptics.conf`

## Keyboard customization / Scancode remapping
`/etc/udev/hwdb.d/70-custom-internal-keyboard.hwdb`

The builtin keyboard is an USB keyboard, so you'll need to get scancodes
with evtest and not i.e. showkey. You want the value field:

Event time 12312421.123212, type 4 (EV_MSC), code 4 (MSC_SCAN), value *70005*

One thing of note: I have an Norwegian "105"-key layout. Because of a bug in
the linux kernel, grave and the 105th key does not report their scancodes
when the ISO layout is on. I disable the ISO layout in the local.d start script
in order to remap those keys.

# Scripts

## Startup script
`/etc/local.d/macbook.start`

## Power management network control script
`/etc/pm/sleep.d/00-network`

## Volume control

`/usr/local/bin/alsactl`

`/usr/local/bin/pulsectl`

`/usr/share/sounds/alsactl/camera-shutter.wav`

Modification of [Camera Shutter Click](soundbible.com/563-Camera-Shutter-Click.html) by Mike Koening under [Attribution 3.0](http://creativecommons.org/licenses/by/3.0)
Some seconds of silence removed.

## Display and keyboard backlight brightness

`/usr/local/bin/mac-brightness`

## FN key state toggle

`/usr/local/bin/mac-fn-toggle`

## Monitor Hotplug

`/usr/local/bin/monitor-hotplug`

`/etc/monitor-hotplug`

`/etc/udev/rules.d/99-monitor-hotplug.rules`

For attaching/detaching monitors to the DisplayPort
