Volume Icon
===========
This is a fork of [Volume Icon](http://softwarebakery.com/maato/volumeicon.html) by [Maato](http://softwarebakery.com/maato/contact.html) .

Enhancements
------------
* built-in **OSD** support via `libnotify` (optional)
	* `./configure --prefix=/usr --enable-notify`
* support for multiple "sound cards"
	* to use the second sound card just add `card=hw:1` to `[Alsa]` section in `~/.config/volumeicon/volumeicon`
* better *(more compatible)* default `volume up` and `volume down` hotkeys (`XF86AudioRaiseVolume`, `XF86AudioLowerVolume`)

License
-------
Volume Icon is provided **as-is** under the **GPLv3** license. For more information see COPYING.
