# oldsu-wine-install-script

An oldsu-wine installer, based on mrniceguy127's installer for regular osu! This one basically just goes through the steps listed [here](https://osu.ppy.sh/community/forums/topics/367783) with the exception of the optional Japanese fonts fix.

# Instructions

1. Install wine and winetricks. Additionally for the redirector, you need the [dotnet-runtime](https://docs.microsoft.com/en-us/dotnet/core/install/linux) package.
2. `git clone https://github.com/marshallracer/oldsu-wine-install-script.git`
3. `cd oldsu-wine-install-script`
4. `./install-oldsu` When you see the winecfg window pop up, make sure to follow the instructions shown in the terminal.
  * If you want to use the alsa tweak (see guide linked at the top), do `ALSATWEAK="true" ./install-oldsu`. I made this an option because it gave me a lot of audio problems (extremely fast/staticy/distorted).
5. Copy the redirector files from the `linux redirector` folder from within the oldsu! folder to the main oldsu! folder itself and launch the https-redirector with `dotnet flandre-https-linux.dll` from the terminal from within the oldsu! folder. This step will not be necessary in future versions of oldsu!
6. Launch oldsu. You can either type `oldsu` in the command line, or if you like GUI's, you can just search "oldsu" in whatever application launcher you might have. Use the command `oldsukill` to force kill oldsu.

You can also specifiy your own WINEPREFIX, WINESERVER, WINE, WINECFG, and WINETRICKS in your environment. Defaults are used otherwise of course. e.g. `WINEPREFIX="..." WINE="..." WINESERVER="..." WINECFG="..." ./install-oldsu`

# Discord Rich Presence

Check [here](https://osu.ppy.sh/community/forums/topics/1005264?start=7313104).

Basically, you just want to set your wine prefix to `~/Games/oldsu-wine` when launching that discord ipc bridge executable. For example: `WINEPREFIX="$HOME/Games/oldsu-wine" wine winediscordipcbridge.exe `

I've included an example script in this repo that launches oldsu along with the rich presence ipc bridge.

# File listing

- Default WINEPREFIX: `~/Games/oldsu-wine`
- oldsu! folder shortcut: `~/Games/oldsu`
- oldsu! launch script: `/usr/bin/oldsu`
- oldsu! kill script: `/usr/bin/oldsukill`
- oldsu! desktop file: `/usr/share/applications/oldsu!.desktop`
- oldsu! logo file: `/usr/share/icons/oldsulogo.png`


# Installation Troubleshooting

> Running /usr/bin/wineserver -w. This will hang until all wine processes in prefix=/home/user/oldsu-wine terminate

Winetricks got stuck here forever multiple times while installing fonts. I never found out if it was ever able to complete. I ended up just doing this in a separate terminal everytime it got stuck: `WINEPREFIX="$HOME/Games/oldsu-wine" wineserver -k`.
