# Alacritty Color Export

A temporary, Regex based solution to export generated (Wal) colors into Alacritty config with one command.

**Warning:** If the latest Alacritty [release](https://github.com/jwilm/alacritty/releases/latest) outdates the script and includes any changes on config syntax it may corrupt your Alacritty config. Don't forget to backup your config first!

Currently tested on macOS 10.14.6 and 10.15.2 with Alacritty **0.3.3** and worked as intended.
Sed commands may differ on untested distros and give errors.

## Initial Purpose
Currently there's no easy way to send [wal](https://github.com/dylanaraps/pywal/) colors to alacritty config in Mac. So I created this script to automatically update colors as a temporary solution.

## Installation
**Deps:** grep, sed

You can simply go to [raw file](https://github.com/egeesin/alacritty-color-export/raw/master/script.sh) and save the file to your script directory or open your terminal emulator:

```sh
git clone https://github.com/egeesin/alacritty-color-export
cd alacritty-color-export
chmod +x script.sh
```

## Usage
Before executing the script, comment existing color declarations out in order to avoid duplication errors and keep your initial colors.
Also to get colors, you must have run ``wal -i <image.png>`` (or ``wal -ni <image.png>`` if you on Mac) once. If you already did, then...

```sh
# Execute
./script.sh

# Execute with custom config
./script.sh <config.yml>
```

**IMPORTANT:** In the mean time, after successful exportation, don't delete or move ``# BEGIN ACE`` and ``# END ACE`` in your main config file. Otherwise, next time you execute this script, when sed command can't find BEGIN ACE, wipes out whole config. If you have any safer alternative solutions please feel free to create new PR.

## Example

##### Terminal emulator:

```bash
$ ./script.sh
```

##### Input (~/.cache/wal/colors):

```
#0e0400
#BB6E37
#AE8F38
#C3913F
#DBAA4B
#F7C95E
#E3BB87
#f5e6c6
#aba18a
#BB6E37
#AE8F38
#C3913F
#DBAA4B
#F7C95E
#E3BB87
#f5e6c6
```

##### Output (alacritty.yml):

```yaml
# BEGIN ACE
colors:
  primary:
    background: '0x0e0400'
    foreground: '0xf5e6c6'
  cursor:
    text:       '0x0e0400'
    cursor:     '0xf5e6c6'
  normal:
    black:      '0x0e0400'
    red:        '0xBB6E37'
    green:      '0xAE8F38'
    yellow:     '0xC3913F'
    blue:       '0xDBAA4B'
    magenta:    '0xF7C95E'
    cyan:       '0xE3BB87'
    white:      '0xf5e6c6'
  bright:
    black:      '0xaba18a'
    red:        '0xBB6E37'
    green:      '0xAE8F38'
    yellow:     '0xC3913F'
    blue:       '0xDBAA4B'
    magenta:    '0xF7C95E'
    cyan:       '0xE3BB87'
    white:      '0xf5e6c6'
# END ACE
```

## Related Links
- [pywal Issue #37 - Alacritty doesn't seem to be working with wal](https://github.com/dylanaraps/pywal/issues/37)

## Known Issues
- If there isn't ``# BEGIN ACE`` comment, the script wipes out whole config.

## Roadmap
- [ ] Fix critical issues
- [ ] Handle indented lines instead of repeated group names
- [ ] Remove necessity of surrounding comments for not corrupt config
- [ ] Option to disable cursor and selection colors
- [ ] Support for different color databases other than Wal
- [ ] Add subcommands to define input (colors) and output (Alacritty config) path
- [ ] Support for different default config path for different OS
- [ ] An option to clean all possible duplicate color declarations and generate new ones

## Contribution
As I said in the beginning, don't forget to backup config and thank you for your contribution in advance. Any information from testing on different systems would valuable to anyone who interested in this script. Issues and PR's are welcomed.

## License
This software is under [The Do What The Fuck You Want To Public License (WTFPL)](http://www.wtfpl.net/about/).
