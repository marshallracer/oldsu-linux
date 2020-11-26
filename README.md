# osu-wine-install-script

Yet another osu-wine installer! This one basically just goes through the steps listed [here](https://osu.ppy.sh/community/forums/topics/367783) with the exception of the optional Japanese fonts fix.

# Instructions

1. Install wine and winetricks.
2. `git clone https://github.com/mrniceguy127/osu-wine-install-script.git`
3. `cd osu-wine-install-script`
4. `./install-osu` When you see the winecfg window pop up, make sure to follow the instructions shown in the terminal. osu! will also launch at some point, so make sure to close it when it does.
  * If you want to use the alsa tweak (see guide linked at the top), do `ALSATWEAK="true" ./install-osu`. I made this an option because it gave me a lot of audio problems (extremely fast/staticy/distorted).
5. Launch osu. You can either type `osu` in the command line, or if you like GUI's, you can just search "osu" in whatever application launcher you might have. Use the command `osukill` to force kill osu.

You can also specifiy your own WINEPREFIX, WINESERVER, WINE, WINECFG, and WINETRICKS in your environment. Defaults are used otherwise of course. e.g. `WINEPREFIX="..." WINE="..." WINESERVER="..." WINECFG="..." ./install-osu`

# Discord Rich Presence

Check [here](https://osu.ppy.sh/community/forums/topics/1005264?start=7313104).

Basically, you just want to set your wine prefix to `~/osu-wine` when launching that discord ipc bridge executable. For example: `WINEPREFIX="$HOME/osu-wine" wine winediscordipcbridge.exe `

I've included an example script in this repo that launches osu along with the rich presence ipc bridge.

# File listing

- Default WINEPREFIX: `~/osu-wine`
- osu! folder shortcut: `~/osu`
- osu! launch script: `/usr/bin/osu`
- osu! kill script: `/usr/bin/osukill`
- osu! desktop file: `/usr/share/applications/osu!.desktop`
- osu! logo file: `/usr/share/icons/osulogo.png`


# Installation Troubleshooting

> Running /usr/bin/wineserver -w. This will hang until all wine processes in prefix=/home/user/osu-wine terminate

Winetricks got stuck here forever multiple times while installing fonts. I never found out if it was ever able to complete. I ended up just doing this in a separate terminal everytime it got stuck: `WINEPREFIX="$HOME/osu-wine" wineserver -k`.
