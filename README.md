# `pywal2alacritty`

> 🎨 A shell script to get colors from [Pywal](https://github.com/dylanaraps/pywal) and apply to [Alacritty](https://alacritty.org/config-alacritty.html) TOML config with regular expressions.

## 🤔 Why?
Currently, there's no easy way to send [wal](https://github.com/dylanaraps/pywal/) colors to Alacritty config in macOS. So I wrote this script to auto-update colors as a workaround.

## 🔽 Setup
**Dependencies:** `grep`, `sed`

Go to [raw file](https://github.com/egeesin/alacritty-color-export/raw/master/script.sh) and save to your script directory ($PATH) or open your terminal emulator:

**Note:** If you're behind Alacritty [13.0.0](https://alacritty.org/changelog_0_13_0.html), get the script from v0.1.1 release in [Tags](https://github.com/egeesin/pywal2alacritty/tags) list in order to import colors to .

```sh
git clone https://github.com/egeesin/alacritty-color-export
cd alacritty-color-export
chmod +x script.sh
```

## 🎛️ Usage
Before executing the script, comment existing color declarations out in order to avoid duplication errors and keep your initial colors (No need if you have your colors imported somewhere else).
Also make sure you run ``wal -i <image.png>`` (or ``wal -ni <image.png>`` if you're on macOS) at least once to have the colors ready in your Wal cache folder so the script can convert it.

```sh
# Run the script
./path/to/script.sh

# Run the script with custom config path
./path/to/script.sh <config.toml>
```

## 🚧 Example

**1. Terminal Emulator**
```sh
$ ./path/to/script.sh
```

**2. Input (`~/.cache/wal/colors.sh`):**
```sh
...
# Special
background='#180f18'
foreground='#cbc2e1'
cursor='#cbc2e1'

# Colors
color0='#180f18'
color1='#6A538E'
color2='#464AAB'
color3='#916A98'
color4='#C569B5'
color5='#EBB0B2'
color6='#AD93D5'
color7='#cbc2e1'
color8='#8e879d'
color9='#6A538E'
color10='#464AAB'
color11='#916A98'
color12='#C569B5'
color13='#EBB0B2'
color14='#AD93D5'
color15='#cbc2e1'
...
```

**3. Output (Default Alacritty config path: `~/.config/alacritty/alacritty.toml`):**
```toml
...

[window.padding]
x = 12
y = 22

# BEGIN ACE
[colors.primary]
background = '#180f18'
foreground = '#cbc2e1'

[colors.cursor]
text   = '#180f18' # Apply background color to color of text inside cursor
cursor = '#cbc2e1' # Apply foreground color to color of cursor

[colors.vi_mode_cursor]
text    = '#180f18' # Same as above
cursor  = '#cbc2e1'

[colors.search.matches]
foreground = '#180f18' # Same as above
background = '#cbc2e1' # Apply bright/white color to bg color of matching search

[colors.search.focused_match]
foreground = 'CellBackground'
background = 'CellForeground'

[colors.line_indicator]
foreground = 'None'
background = 'None'

[colors.footer_bar]
foreground = '#8e879d'
background = '#cbc2e1'

[colors.selection]
text       = 'CellBackground'
background = 'CellForeground'

[colors.normal]
black   = '#180f18'
red     = '#6A538E'
green   = '#464AAB'
yellow  = '#916A98'
blue    = '#C569B5'
magenta = '#EBB0B2'
cyan    = '#AD93D5'
white   = '#cbc2e1'

[colors.bright]
black   = '#8e879d'
red     = '#6A538E'
green   = '#464AAB'
yellow  = '#916A98'
blue    = '#C569B5'
magenta = '#EBB0B2'
cyan    = '#AD93D5'
white   = '#cbc2e1'
# END ACE
```
**Note:** If you'd like to have different colors for cursor, search matches/focuses from Vi-mode of Alacritty, edit the `script.sh` based on variables like $color1, $color2 etc.

## 🔗 Related Links
- [pywal Issue #37 - Alacritty doesn't seem to be working with wal](https://github.com/dylanaraps/pywal/issues/37)

## 🤝 Contribution
Don't forget to backup config and thank you for your contribution in advance. Any information from testing on different systems would valuable to anyone who interested in this script. Issues and PR's are welcomed.

## 🤷 License
This software is under [The Do What The Fuck You Want To Public License (WTFPL)](http://www.wtfpl.net/about/).
