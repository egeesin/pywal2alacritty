# Alacritty Color Export

A temporary, Regex based solution to export generated (Wal) colors into Alacritty configuration with one command.

**Warning:** It may corrupt your Alacritty configuration file unless script isn't outdated. Don't forget to backup the config first!

Currently tested on macOS 10.14.6 with Alacritty **0.3.3** and worked as intended.
Sed commands may differ on untested distros and give errors.

## Initial Purpose
Currently there's no easy way to set colors generated via [wal](https://github.com/dylanaraps/pywal/) in macOS systems. So I created this script to automatically update colors.

## Installation
**Dependencies:** bash, grep, sed

You can simply go to raw file and save the file to your script directory or open your terminal emulator:

```sh
git clone https://github.com/egeesin/alacritty-wal-mac
cd alacritty-wal-mac
chmod +x script.sh
```

## Usage
Before executing the script, comment existing color declarations out in order to avoid duplication errors and keep your initial colors.
Also to get colors, you must have run ``wal`` once. if you already did, then...

```sh
# Execute with default config
./script.sh

# Execute with custom path
./script.sh <config>
```

## Example

##### Terminal emulator:

```bash
$ ./script.sh
```

##### .cache/wal/colors:

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

##### alacritty.yml:

```yaml
# BEGIN ACE
colors.normal.black: '0x151718'
colors.normal.red: '0xcd3f45'
colors.normal.green: '0x9fca56'
colors.normal.yellow: '0xe6cd69'
colors.normal.blue: '0x55b5db'
colors.normal.magenta: '0xa074c4'
colors.normal.cyan: '0x55dbbe'
colors.normal.white: '0xd6d6d6'
colors.bright.black: '0x41535b'
colors.bright.red: '0xcd3f45'
colors.bright.green: '0x9fca56'
colors.bright.yellow: '0xe6cd69'
colors.bright.blue: '0x55b5db'
colors.bright.magenta: '0xa074c4'
colors.bright.cyan: '0x55dbbe'
colors.bright.white: '0xffffff'
colors.primary.background: '0x151718'
colors.primary.foreground: '0xd6d6d6'
colors.cursor.text: '0x151718'
colors.cursor.cursor: '0xd6d6d6'
colors.selection.text: '0x151718'
colors.selection.background: '0xd6d6d6'
# END ACE
```

## Related Links
- [pywal - Alacritty doesn't seem to be working with wal #37](https://github.com/dylanaraps/pywal/issues/37)

## Known Issues
- If there's any symlink in config destination, it brokes.
- If there isn't # BEGIN ACE comment, the script wipes out whole config.

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
