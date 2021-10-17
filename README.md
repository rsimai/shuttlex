Linux userspace app for Contour Design ShuttleXpress
====================================================

Execute shell commands such as xdotool key <keyname> to work with 
video/audio editors and such, see .shuttle-go.json.example.
Code comes from (kudos to!) abourget's shuttle-go which I have stripped
down and made suitable for my needs.

See https://github.com/abourget/shuttle-go for the original.

## Layout

        F5   F6   F7   F8   F9


             (Jog Shuttle)
        S-7 .. S-1  S0  S1 .. S7

#### xdotool

The key names to use in the X11 bindings are found here:
https://www.cl.cam.ac.uk/~mgk25/ucs/keysymdef.h or you can view them
locally in `/usr/include/X11/keysymdef.h` (stripped of the `XK_` prefix).

You need to install the `xdotool` package before using this driver.

Any bindings triggered will execute the corresponding command through
`/bin/bash -c "your command"`

### udev

You'll need at least a one line udev rule like this added to /etc/udev/rules.d/

    ATTRS{name}=="Contour Design ShuttleXpress" MODE="0666" SYMLINK+="input/shuttlexpress"

### build

Run the build.sh script.

## Run

    shuttle-go

It assumes config in ~/.shuttle-go.json and the device to be /dev/input/shuttlexpress.
Modify to your needs:

    shuttle-go -config YOUR_CONF /PATH/TO/YOUR/DEVICE

## License

MIT

