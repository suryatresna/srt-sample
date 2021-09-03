# SRT Sample App


# How to run
This project using tilt.dev as development. To run this project you need execute this command
```
tilt up
```

# How to test
You can use ffmpeg to broadcast and ffplay to receive the video

The format will be like this
```
ffmpeg -re -f lavfi -i testsrc=size=720x1280:rate=30 -f lavfi -i sine \
-vf drawtext="text='%{localtime\:%X}':fontsize=20:fontcolor=white:x=7:y=7" \
-vcodec libx264 -vb 2000k -preset ultrafast -x264-params keyint=60 \
-acodec aac -f mpegts 'srt://localhost:9000?pkt_size=1316&maxbw=250000'
```

For receive or play the video, you use this command
```
ffplay 'srt://localhost:6000'
```