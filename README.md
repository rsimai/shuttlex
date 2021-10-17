Linux userspace app for Contour Design ShuttleXpress
====================================================

Execute shell commands such as xdotool key <keyname> to work with 
video/audio editors and such, see .shuttle-go.json.example.
Code comes from (kudos to!) abourget's shuttle-go which I have stripped
down and made suitable for my needs. To specify the whole command gives
more flexibility, for some app features you'll need "keydown" and "keyup"
instead of just "key", which wasn't possible.

See https://github.com/abourget/shuttle-go for the original.

### ShuttleXpress layout

             F6   F7   F8
        F5                  F9

           (Dial norm/slow)
             (Jog Shuttle)

      S-7 .. S-1  S0  S+1 .. S+7

### window matching

This tool supports window matching, you may have config sections specific to the
focused window.

### xdotool

You need to install the `xdotool` package before using this driver, or
anything similar to create keyboard events.

The key names to use with xdotool can be found here:
https://gitlab.com/cunidev/gestures/-/wikis/xdotool-list-of-key-codes

Any bindings triggered will execute the corresponding command through
`/bin/bash -c "your command"`

where "your command" would typically be something like

"xdotool key KEYNAME"

See the .shuttle-go.json.example for more.

### udev

You'll need at least a one line udev rule like this added to /etc/udev/rules.d/

    ATTRS{name}=="Contour Design ShuttleXpress" MODE="0666" SYMLINK+="input/shuttlexpress"

### build

Run the build.sh script.

### run

    shuttle-go

It assumes config in ~/.shuttle-go.json and the device to be /dev/input/shuttlexpress.
Modify to your needs:

    shuttle-go -config YOUR_CONF /PATH/TO/YOUR/DEVICE

### unwanted mouse device

For me the shuttleXpress appears as a keyboard (wanted) and also as mouse device
where the jog produces mousewheel events (unwanted). Use the `shuttle` script
to disable the mouse device using xinput and start up shuttle-go.

### license

MIT

