# oldsu-wine-install-script

An oldsu-wine installer, based on mrniceguy127's installer for regular osu! This one basically just goes through the steps listed [here](https://osu.ppy.sh/community/forums/topics/367783) with the exception of the optional Japanese fonts fix.

# Instructions

1. Install wine and winetricks. This has been tested with the latest version of wine-staging 5.22 at the time of writing.
2. `git clone https://github.com/marshallracer/oldsu-wine-install-script.git`
3. `cd oldsu-wine-install-script`
4. `./install-oldsu` When you see the winecfg window pop up, make sure to follow the instructions shown in the terminal. Keep in mind that because of the necessary dependencies installed through winetricks it WILL take a while to install everything.
  * If you want to use the alsa tweak (see guide linked at the top), do `ALSATWEAK="true" ./install-oldsu`. This is only an option as people have been reporting audio problems (extremely fast/staticy/distorted).
5. Launch oldsu. You can either type `oldsu` in the command line, or if you like GUI's, you can just search "oldsu" in whatever application launcher you might have. Use the command `oldsukill` to force kill oldsu.

You can also specifiy your own WINEPREFIX, WINESERVER, WINE, WINECFG, and WINETRICKS in your environment. Defaults are used otherwise of course. e.g. `WINEPREFIX="..." WINE="..." WINESERVER="..." WINECFG="..." ./install-oldsu`

# Discord Rich Presence

Check [here](https://osu.ppy.sh/community/forums/topics/1005264?start=7313104).

Thanks to j4yden for their code which includes discordrpc during the install. It should launch automatically when starting oldsu! via terminal or through your application launcher.

# File listing

- Default WINEPREFIX: `~/Games/oldsu-wine`
- oldsu! folder shortcut: `~/Games/oldsu`
- oldsu! launch script: `~/.bin/oldsu`
- oldsu! kill script: `~/.bin/oldsukill`
- oldsu! desktop file: `~/.local/share/applications/oldsu!.desktop`
- oldsu! logo file: `~/.local/share/icons/oldsulogo.png`


# Installation Troubleshooting

(this should hopefully not happen anymore but stays in case your install may hang anyway)

> Running /usr/bin/wineserver -w. This will hang until all wine processes in prefix=/home/user/oldsu-wine terminate

Winetricks got stuck here forever multiple times while installing .NET. Whenever it gets stuck just type the following command in a seperate terminal: `WINEPREFIX="$HOME/Games/oldsu-wine" wineserver -k`.
