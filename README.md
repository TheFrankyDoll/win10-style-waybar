# win10-style-waybar
Waybar config to make Windows 10 refugees feel at home. Works well with [Hyprland](https://github.com/hyprwm/Hyprland).

![2024-07-21T15:52:00,421480788+07:00](https://github.com/user-attachments/assets/60a498d3-6989-48e9-b74d-d07242fee288)

### Installation
1. copy `waybar` directory into your `~/.config`
2. relaunch waybar (`pkill waybar`, `waybar & disown`)

> [!NOTE]
> `style.css` of this waybar uses "Segoe UI" font and expects it to be installed. On linux, you probably have to do it manually, for example from [this repo](https://github.com/mrbvrz/segoe-ui-linux).

### Default usage

> [!TIP]
> These are the actions called by the default configuration file. Feel free to change them, even if you are new to waybar, editing the config is very easy. Refer to the [wiki](https://github.com/Alexays/Waybar/wiki) for options.

* Click on OS button to try running `wofi --show drun`
* Scroll on workspaces buttons to move through them. It calls `hyprctl dispatch workspace r±1`, works in Hyprland only.
* Click on taskbar button to switch to app, middle-click to close it.
* Click on speaker sign to try running [pwvucontrol](https://github.com/saivert/pwvucontrol) - pipewire version of [pavucontrol](https://github.com/pulseaudio/pavucontrol)
* Clock's tooltip will expose waybar's calendar - it's not the prettiest, but it does it job!

### Bluring background! (on Hyprland)
Waybar uses GTK3 and does not provide any way add blur by default. ([unless you're from the future and use GTK4](https://github.com/Alexays/Waybar/issues/2815))

However, on Hyprland you can add this:
```
layerrule = blur, waybar # Add blur to waybar
layerrule = blurpopups, waybar # Blur waybar popups too!
layerrule = ignorealpha 0.2, waybar # Make it so transparent parts are ignored
```
in your `hyprland.conf` to add blur to your waybar. Blur options are controlled by `decoration:blur` (see https://wiki.hyprland.org/Configuring/Variables/#blur)

### Trivia
* `style.css` has most of it's colors exposed as variables at the very top of the file, making it easy to change them as you wish.
Waybar may also use some variables from your GTK theme, put `* { all: unset; }` in your `style.css` if you want to design everything from scratch.

* For some reason selection doesn't work if you put mouse at the very bottom of the screen - to fix this, I used a dirty hack of making waybar 1 pixel larger (41px total) and setting `"margin-bottom": -1` in the `config` file. This works fine - still weird you have to do this.

* Unfortunately I couldn't find a way to limit taskbar's elements length, so opening to many apps will push all of the right elements out of screen.
