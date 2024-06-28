#stream #video #ssh 
#### [StkOvrflw](https://unix.stackexchange.com/a/483328)
```
ssh user@host "ffmpeg  -r 14 -s 640x480 -f video4linux2 -i /dev/video0 -f matroska -" | mplayer - -idle
```

This has the benefit of it being encoded, so you save bandwidth as a bonus. Nothing else on any forum/website was working for me on a [[Debian]] machine.

---

Combine with [tee](https://superuser.com/questions/1356841/what-is-the-purpose-of-tee) and you can watch and record at the same time:
```
ssh user@host "ffmpeg  -r 14 -s 640x480 -f video4linux2 -i /dev/video0 -f matroska -" | tee $(date +%Y-%m-%d_%H-%M-%S)_recording.mkv | mplayer - -idle
```

This will open [[mplayer]] for live streaming and save it to a file containing the current datetime at the same time (example filename: `2018-11-22_01-22-10_recording.mkv`).

##### [more detailed version](https://unix.stackexchange.com/a/117352)
#### [python streamer-viewer scripts](https://stackoverflow.com/a/55432139/5273667)
