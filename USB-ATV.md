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
4. sudo ffmpeg -f v4l2 -i /dev/video1 -thread_queue_size 4096 -f alsa -thread_queue_size 4096 -i hw:2 -f mpegts -c:v mpeg2video -c:a mp3 -y -threads 8 23.mpg -async 1 -vsync 1
5. use tvheadend with pipe mux no sound : pipe:///usr/bin/ffmpeg -r 25 -f v4l2 -i /dev/video1 -f mpegts -c:v mpeg2video pipe:1
