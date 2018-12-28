Model|OS|Video|Audio|Rec|Player
-|-|-|-|-|-
Gadmei UTV330+|WinXP SP3|OK|OK|OK|TVHome3.Potplayer
Gadmei UTV330+|Win10 Ent|OK|No|No|TVHome3.Potplayer
Gadmei UTV330+|Win8 pro|OK|No|No|TVHome3.Potplayer
Gadmei UTV330+|Ubuntu 16.04|OK|No|No|tvtime
Gadmei UTV330+|Ubuntu 14.04|No|No|No|tvtime

1. validate audio device name with audacity;
2. v4l2-ctl -l -d /dev/video1;
3. v4l2-ctl -c mute=0 -d /dev/video1;
4. sudo ffmpeg -r 30000/1001 -f v4l2 -i /dev/video1 -f alsa -ac 2 -ar 48000 -i hw:2,0 -f mpegts -c:v mpeg2video -b:v 8000k -filter:v yadif=0:-\1:0 -c:a ac3 -b:a 224k -y tvb.mpg
