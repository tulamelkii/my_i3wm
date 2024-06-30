# my_i3wm
programs

- i3
  
- rofi
  
- xcb
  
- xorg-dev
  
- xinit 


#####################keybord###########################################/etc/X11/xorg.conf.d/00-keybord.conf
*show keybord

- setxkbmap -print -verbose 10

localadm@Only:~$ cat /etc/X11/xorg.conf.d/00-keybord.conf

#localectl set-locale en_US.utf8 -no-convert set-x11-kemap layout us,ru  pc105 ,dvorak grp:alt_shift_toggle

Section "InputClass"

        Identifier "system-keyboard"
        
        MatchIsKeyboard "on"
        
        Option "XkbLayout" "us,ru"
        
        Option "XkbModel" "pc105"
        
        Option "XkbOptions" "grp:alt_shift_toggle"
        
EndSection

########################################################################
bindsym $mod+z exec --no-startup-id rofi -show drun

exec --no-startup-id setxbmap -model pc105 -layout us,ru -option grp: alt_shift_toggle

workspace 2 output HDMI-1

workspace 1 output DP-2

exec --no-startup-id xrandr --output eDP-1 --off

exec --no-startup-id xrandr --output DP-2 --primary

exec --no-startup-id xrandr --output DP-2 --left-of HDMI-1

default_border pixel 1

default_floating_border pixel 1

bindsym $mod+Control+l exec "i3lock -c 000000"

exec "xautolock -detectsleep -time 3 -locker \"i3lock -c 000000\""

exec --no-startup-id blueman-applet

exec dbus-launch  startxfce4

exec --no-startup-id picom -b

bindsym $mod+minus move scratchpad

bindsym $mod+plus scratchpad show

#########################################Picom ################################

#inactive-opacity = 1;
#active-opacity = 1;

opacity-rule = ["75:class_g = 'Xfce4-terminal'"];


############################################################################ logon /etc/profile######################

if [[ -z $DISPLAY ]] && [[ $(tty) = /dev/tty1 ]] && [[ $(whoami) = 'your_username' ]]; then
  startx
fi
