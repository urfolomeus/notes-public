## Todos

- [ ] Install
  - [ ] Slack
  - [ ] Zoom
  - [ ] python
  - [ ] chrome
  - [ ] vscode
  - [ ] tmux
- [ ] Configuration
  - [ ] nvim
  - [ ] zsh
  - [ ] tmux

## Keyboard

### How to setup VP3 Keyboard

<https://www.reddit.com/r/MechanicalKeyboards/comments/35uy60/guide_howto_program_your_pok3r_programming_layers/>

I also have the following set on the red layer (Fn .)

| Name | Was  | Now  |
|---|---|---|
| PgUp | Fn+u | Fn+y |
| Home | Fn+h | Fn+u |
| LArr | Fn+j | Fn+h |
| UArr | Fn+i | Fn+k |
| DArr | Fn+k | Fn+j |

### Remap caps lock to ctrl

Use Tweak tool (install using Gnome extensions in browser)

<https://opensource.com/article/18/11/how-swap-ctrl-and-caps-lock-your-keyboard>

### Remap other keys
    

## Notes

### Setting up the keyboard

See this [blog post](http://www.fascinatingcaptain.com/projects/remap-keyboard-keys-for-ubuntu/)

### Terminal

* You can change the default keybindings for copy and paste in the terminal by opening the preferences and then changing the keybindings. Note the defaults are ctrl-shift-* rather than ctrl-*

### Sound

* When pairing the Bose QC35s over bluetooth the sound was initially really quiet. If you open the sound settings there was an option to set the volume over 100%. I noticed no noticable loss of audio quality.

### If RAM has swapped and you want to do things to reclaim the memory

See <>

tl;dr I now have an alias `reclaim` that will get memory back from swap into RAM. **However** before running this I should run `vmstat 1` to ensure that there is not still data swapping in and out. Also, close as many programs as possible in case any are swapping.

If you want to see the progress of the data moving you can use `watch free -h`.

### System tray for icons in top right

<https://github.com/ubuntu/gnome-shell-extension-appindicator>

### Other handy extensions/customisations

<https://support.system76.com/articles/customize-gnome/>

## Helpful apps

[Dash to dock](https://support.system76.com/articles/dash-to-dock/)