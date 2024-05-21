# my_i3wm
programs
- i3
- rofi
- xcb
- xorg-dev 
- xinit 


bindsym $mod+z exec --no-startup-id rofi -show drun
exec --no-startup-id setxbmap -model pc105 -layout us,ru -option grp: alt_shift_toggle
workspace 2 output HDMI-1
workspace 1 output DP-2

exec --no-startup-id xrandr --output eDP-1 --off
exec --no-startup-id xrandr --output DP-2 --primary
exec --no-startup-id xrandr --output DP-2 --left-of HDMI-1

