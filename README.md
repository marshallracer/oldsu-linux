# oldsu-linux

An oldsu-wine installer, based on mrniceguy127's installer for regular osu! This one basically just goes through the steps listed [here](https://osu.ppy.sh/community/forums/topics/367783) with the exception of the optional Japanese fonts fix. Also MASSIVE thanks to sech1p for their immense contributions and optimazations. <#

# Instructions

1. Install wine and winetricks. This has been tested with wine-staging 5.22 at the time of writing. Newer versions should also work fine but mileage may vary.
2. `git clone https://github.com/marshallracer/oldsu-linux`
3. `cd oldsu-linux`
4. `./install-oldsu` (linux only: or `./install-oldsu --no-root` if you want use the noroot version of oldsu installer script) Keep in mind that because of the necessary dependencies installed through winetricks it WILL take a while to install everything.
5. Launch oldsu. You can either type `oldsu` in the command line, or if you like GUI's, you can just search "oldsu" in whatever application launcher you might have. Use the command `oldsukill` to force kill oldsu. If you have macOS - you will find oldsu! in Launchpad.
> should you use the noroot script keep in mind to add the new folder to your $PATH (e.g. `nano $HOME/.bashrc`): `export PATH=$HOME/.local/bin:$PATH`

You can also specifiy your own WINEPREFIX, WINESERVER, WINE and WINETRICKS in your environment. Defaults are used otherwise of course. e.g. `WINEPREFIX="..." WINE="..." WINESERVER="..." ./install-oldsu`

# Discord Rich Presence

Check [here](https://osu.ppy.sh/community/forums/topics/1005264?start=7313104).

Thanks to jvyden for their code which includes discordrpc during the install. It should launch automatically when starting oldsu! via terminal or through your application launcher.

# File listing

- Default WINEPREFIX: `~/Games/oldsu-wine`
- oldsu! folder shortcut: `~/Games/oldsu`
- oldsu! launch script: `/usr/bin/oldsu` (root) or `~/.local/bin/oldsu` (no-root) or `/Applications/oldsu\!.app/Contents/MacOS/oldsu` (macOS)
- oldsu! kill script: `/usr/bin/oldsukill` (root) or `~/.local/bin/oldsukill` (no-root)
- oldsu! desktop file: `~/.local/share/applications/oldsu!.desktop`
- oldsu! logo file: `~/.local/share/icons/oldsulogo.png`


# Installation Troubleshooting

(this should hopefully not happen anymore but stays in case your install may hang anyway)

> Running /usr/bin/wineserver -w. This will hang until all wine processes in prefix=/home/user/oldsu-wine terminate

Winetricks sometimes gets stuck during some parts of the install of .NET. Whenever it gets stuck just type the following command in a seperate terminal: `WINEPREFIX="$HOME/Games/oldsu-wine" wineserver -k`.
