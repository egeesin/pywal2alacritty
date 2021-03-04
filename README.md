# Alacritty Color Export

A temporary, Regex based solution to export generated (Wal) colors into Alacritty config with one command.

Tested on macOS (10.14.6, 10.15.2, 11.2.1) with Alacritty (0.3.3, 0.4.2-dev, **0.6.0**) and works as intended.
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

## Example

##### Terminal emulator:

```bash
$ ./script.sh
```

##### Input (~/.cache/wal/colors.sh):

```
...
color0='#0a0c0a'
color1='#514739'
color2='#6B4F39'
color3='#776338'
color4='#5E5747'
color5='#936843'
color6='#75936F'
color7='#d6c6a6'
color8='#958a74'
color9='#514739'
color10='#6B4F39'
color11='#776338'
color12='#5E5747'
color13='#936843'
color14='#75936F'
color15='#d6c6a6'
...
```

##### Output (~/.config/alacritty/alacritty.yml):

```yaml
...
# BEGIN ACE
colors:
  primary:
    background: '#0a0c0a'
    foreground: '#d6c6a6'
  cursor:
    text:       '#0a0c0a'
    cursor:     '#d6c6a6'
  normal:
    black:      '#0a0c0a'
    red:        '#514739'
    green:      '#6B4F39'
    yellow:     '#776338'
    blue:       '#5E5747'
    magenta:    '#936843'
    cyan:       '#75936F'
    white:      '#d6c6a6'
  bright:
    black:      '#958a74'
    red:        '#514739'
    green:      '#6B4F39'
    yellow:     '#776338'
    blue:       '#5E5747'
    magenta:    '#936843'
    cyan:       '#75936F'
    white:      '#d6c6a6'
# END ACE
```

## Known Issues
- ~~If there isn't ``# BEGIN ACE`` comment, the script wipes out whole config.~~

## Roadmap
- [x] Fix critical issues
- [ ] Make use of config import
  - [ ] Remove necessity of surrounding comments for not corrupt config
- [ ] Handle indented lines instead of repeated group names
- [ ] Option to disable cursor and selection colors
- [ ] Add subcommands to define input (colors) and output (Alacritty config) path
- [ ] Support for different default config path for different OS
- [ ] An option to clean all possible duplicate color declarations and generate new ones

## Related Links
- [pywal Issue #37 - Alacritty doesn't seem to be working with wal](https://github.com/dylanaraps/pywal/issues/37)

## Contribution
Don't forget to backup config and thank you for your contribution in advance. Any information from testing on different systems would valuable to anyone who interested in this script. Issues and PR's are welcomed.

## License
This software is under [The Do What The Fuck You Want To Public License (WTFPL)](http://www.wtfpl.net/about/).
