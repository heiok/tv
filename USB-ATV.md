Model|OS|Video|Audio|Rec|Player
-|-|-|-|-|-
Gadmei UTV330+|WinXP SP3|OK|OK|OK|TVHome3.Potplayer
Gadmei UTV330+|Win10 Ent|OK|No|No|TVHome3.Potplayer
Gadmei UTV330+|Win8 pro|OK|No|No|TVHome3.Potplayer
Gadmei UTV330+|Ubuntu 16.04|OK|OK|OK|tvtime
Gadmei UTV330+|Ubuntu 14.04|No|No|No|tvtime

1. validate audio device name with audacity;
2. v4l2-ctl -l -d /dev/video1;
3. v4l2-ctl -c mute=0 -d /dev/video1;
4. sudo ffmpeg -f v4l2 -i /dev/video1 -thread_queue_size 4096 -f alsa -thread_queue_size 4096 -i hw:2 -f mpegts -c:v mpeg2video -c:a mp3 -y -threads 8 23.mpg -async 1 -vsync 1
5. use tvheadend with pipe mux no sound : pipe:///usr/bin/ffmpeg -r 25 -f v4l2 -i /dev/video1 -f mpegts -c:v mpeg2video pipe:1
6. compile new tvheadend ok ver:HTS Tvheadend 4.3-1695~gb17dcf9

2018-12-30 18:14:48.359 mpegts: AAA in TVB - tuning on IPTV #1
2018-12-30 18:14:48.360 epggrab: AAA in TVB - registering mux for OTA EPG
2018-12-30 18:14:48.360 spawn: Executing "/usr/bin/ffmpeg"
2018-12-30 18:14:48.360 subscription: 0001: "scan" subscribing to mux "AAA", weight: 5, adapter: "IPTV #1", network: "TVB", service: "Raw PID Subscription"
2018-12-30 18:14:48.433 spawn: ffmpeg version 2.8.15-0ubuntu0.16.04.1 Copyright (c) 2000-2018 the FFmpeg developers
2018-12-30 18:14:48.433 spawn:   built with gcc 5.4.0 (Ubuntu 5.4.0-6ubuntu1~16.04.10) 20160609
2018-12-30 18:14:48.433 spawn:   configuration: --prefix=/usr --extra-version=0ubuntu0.16.04.1 --build-suffix=-ffmpeg --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --cc=cc --cxx=g++ --enable-gpl --enable-shared --disable-stripping --disable-decoder=libopenjpeg --disable-decoder=libschroedinger --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmodplug --enable-libmp3lame --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-librtmp --enable-libschroedinger --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxvid --enable-libzvbi --enable-openal --enable-opengl --enable-x11g
2018-12-30 18:14:48.433 spawn:   libavutil      54. 31.100 / 54. 31.100
2018-12-30 18:14:48.433 spawn:   libavcodec     56. 60.100 / 56. 60.100
2018-12-30 18:14:48.433 spawn:   libavformat    56. 40.101 / 56. 40.101
2018-12-30 18:14:48.433 spawn:   libavdevice    56.  4.100 / 56.  4.100
2018-12-30 18:14:48.433 spawn:   libavfilter     5. 40.101 /  5. 40.101
2018-12-30 18:14:48.433 spawn:   libavresample   2.  1.  0 /  2.  1.  0
2018-12-30 18:14:48.433 spawn:   libswscale      3.  1.101 /  3.  1.101
2018-12-30 18:14:48.433 spawn:   libswresample   1.  2.101 /  1.  2.101
2018-12-30 18:14:48.433 spawn:   libpostproc    53.  3.100 / 53.  3.100
2018-12-30 18:14:48.887 spawn: [video4linux2,v4l2 @ 0x8cc5a0] The driver does not permit changing the time per frame
2018-12-30 18:14:49.011 spawn: Input #0, video4linux2,v4l2, from '/dev/video1':
2018-12-30 18:14:49.011 spawn:   Duration: N/A, start: 3859.880217, bitrate: 165888 kb/s
2018-12-30 18:14:49.011 spawn:     Stream #0:0: Video: rawvideo (YUY2 / 0x32595559), yuyv422, 720x576, 165888 kb/s, 25 fps, 25 tbr, 1000k tbn, 1000k tbc
2018-12-30 18:14:49.012 spawn: Home directory not accessible: Permission denied
2018-12-30 18:14:49.014 spawn: Guessed Channel Layout for  Input Stream #1.0 : stereo
2018-12-30 18:14:49.014 spawn: Input #1, alsa, from 'hw:2,0':
2018-12-30 18:14:49.014 spawn:   Duration: N/A, start: 1546164889.013507, bitrate: 1536 kb/s
2018-12-30 18:14:49.014 spawn:     Stream #1:0: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
2018-12-30 18:14:49.018 spawn: No pixel format specified, yuv422p for MPEG-2 encoding chosen.
2018-12-30 18:14:49.018 spawn: Use -pix_fmt yuv420p for compatibility with outdated media players.
2018-12-30 18:14:49.018 spawn: -async is forwarded to lavfi similarly to -af aresample=async=1:min_hard_comp=0.100000:first_pts=0.
2018-12-30 18:14:49.022 spawn: Output #0, mpegts, to 'pipe:':
2018-12-30 18:14:49.022 spawn:   Metadata:
2018-12-30 18:14:49.022 spawn:     encoder         : Lavf56.40.101
2018-12-30 18:14:49.022 spawn:     Stream #0:0: Video: mpeg2video, yuv422p, 720x576, q=2-31, 8000 kb/s, 25 fps, 90k tbn, 25 tbc
2018-12-30 18:14:49.022 spawn:     Metadata:
2018-12-30 18:14:49.022 spawn:       encoder         : Lavc56.60.100 mpeg2video
2018-12-30 18:14:49.022 spawn:     Stream #0:1: Audio: ac3, 48000 Hz, stereo, fltp, 224 kb/s
2018-12-30 18:14:49.022 spawn:     Metadata:
2018-12-30 18:14:49.022 spawn:       encoder         : Lavc56.60.100 ac3
2018-12-30 18:14:49.022 spawn: Stream mapping:
2018-12-30 18:14:49.022 spawn:   Stream #0:0 -> #0:0 (rawvideo (native) -> mpeg2video (native))
2018-12-30 18:14:49.022 spawn:   Stream #1:0 -> #0:1 (pcm_s16le (native) -> ac3 (native))
2018-12-30 18:14:49.022 spawn: Press [q] to stop, [?] for help
2018-12-30 18:14:49.183 spawn: [alsa @ 0x8ce880] Thread message queue blocking; consider raising the thread_queue_size option (current value: 8)
2018-12-30 18:14:49.525 spawn: frame=   12 fps=0.0 q=26.0 size=    2181kB time=00:00:00.41 bitrate=43508.5kbits/s    
2018-12-30 18:14:50.030 spawn: frame=   25 fps= 25 q=24.8 size=    3131kB time=00:00:00.92 bitrate=27799.0kbits/s    
2018-12-30 18:14:50.531 spawn: frame=   37 fps= 25 q=24.8 size=    4001kB time=00:00:01.40 bitrate=23369.5kbits/s    
2018-12-30 18:14:51.040 spawn: frame=   50 fps= 25 q=24.8 size=    4943kB time=00:00:01.92 bitrate=21092.0kbits/s    
2018-12-30 18:14:51.541 spawn: frame=   63 fps= 25 q=24.8 size=    5835kB time=00:00:02.44 bitrate=19589.0kbits/s    
2018-12-30 18:14:52.045 spawn: frame=   75 fps= 25 q=24.8 size=    6768kB time=00:00:02.93 bitrate=18867.9kbits/s    
2018-12-30 18:14:52.550 spawn: frame=   88 fps= 25 q=31.0 size=    7694kB time=00:00:03.45 bitrate=18265.5kbits/s    
2018-12-30 18:14:53.071 spawn: frame=  101 fps= 25 q=24.8 size=    8564kB time=00:00:03.96 bitrate=17716.8kbits/s    
2018-12-30 18:14:53.359 mpegts: AAA in TVB scan complete
2018-12-30 18:14:53.359 subscription: 0001: "scan" unsubscribing
2018-12-30 18:15:21.818 service-mapper: TVB/AAA/Service01: success
