#linux #video
ffmpeg video converter

Video file info: `ffprobe -i video_file.mp4`

## Conversions
Convert *full_images.raw* to *.mp4* file:
```shell
ffmpeg -re -y -f rawvideo -vcodec rawvideo -pix_fmt gray8 -video_size 640x400 -i full_images.raw -c:v libx264 full_images.mp4
```

Convert .avi to .mp4: `ffmpeg -i video.avi output_video.mp4`
Set framerate: `ffmpeg -i input.mp4 -r 24 output.mp4`

### stream video over ssh [StkOvrfl](https://unix.stackexchange.com/questions/2302/can-i-pipe-dev-video-over-ssh):
with `ffmpeg` and `mplayer`
```
ssh USERNAME@REMOTEHOST ffmpeg -an -f video4linux2 -s 640x480 -i /dev/video0 -r 10 -b:v 500k -f matroska - | mplayer - -idle -demuxer matroska
```
where
-   `-an` turns off audio encoding. If you want audio, replace `-an` with `-f alsa -ac 1 -i hw:3` (where hw:3 could also be hw:0 or hw:1, … See `arecord -l` for your device). If you want audio only (no video), [use this](https://unix.stackexchange.com/questions/116919/redirect-sound-microphone-via-ssh-how-to-telephone-via-ssh/116921#116921))
-   `-s 640x480` is the size of your video in x and y dimension
-   `-r 10` is the framerate you want to receive (lower makes better images at low bitrates, but looks more bumby)
-   `-b:v 500k` is a bitrate of 500 kilobit/s
You need ffmpeg on the remote host and [[mplayer]] on the local machine installed.

### Split file
[guide](https://www.baeldung.com/linux/ffmpeg-split-video-parts)
#### by size (does not work for ffmpeg 4.2.7 version)
```sh
ffmpeg -i input.mkv -acodec copy -vcodec copy -f segment -segment_size <size_in_bytes> output_%03d.mkv
```
- `-i input.mkv`: specifies the input MKV file.
- `-acodec copy -vcodec copy`: copies the audio and video streams without re-encoding (faster processing).
- `-f segment`: sets the output format to segmented.
- `-segment_size <size_in_bytes>`: defines the desired size for each output segment. You can specify the size in bytes (`B`), kilobytes (`KB`), megabytes (`MB`), or gigabytes (`GB`). For example `50M` or `1024K`.
- `output_%03d.mkv`: defines the output filename pattern. The `%03d` part will be replaced with a sequential number for each segment (e.g., output_001.mkv, output_002.mkv).

> [!NOTE] Data density
> Splitting by size might not result in perfectly equal segments. ffmpeg will create the largest possible segment that fits within the specified size limit. This is because video files often have variable bitrates, meaning the data density can change throughout the video.
- **Estimating File Size:** Keep in mind the potential for slight variations due to variable bitrates.
- **Lossless Splitting:** This method copies the audio and video streams without re-encoding, maintaining the original quality.

#### by time
This will split the file into 600 second parts:
```sh
ffmpeg -i input_file.mp4 -acodec copy -f segment -segment_time 1:00:00 -vcodec copy -reset_timestamps 1 -map 0 output_%d.mp4
```
> [!NOTE] Troubleshoot
> If you get the following error: "Subtitle encoding currently only possible from text to text or bitmap to bitmap"
> Try removing the `-map 0` parameters as it will remove the subtitles from the split.

Alternatively,
```sh
ffmpeg -i input.mkv -acodec copy -vcodec copy -t split_duration output1.mkv
ffmpeg -ss split_duration -i input.mkv -acodec copy -vcodec copy -to -1 output2.mkv
```
- The first command splits the beginning portion of the video with `-t split_duration` option.
- `-ss split_duration`: tells ffmpeg to start processing from the specified position (split duration in seconds).
- `-to -1`: tells ffmpeg to process everything until the end of the file, resulting in the second part.

## Audio
### Formts
You can find a comprehensive list of supported audio codecs and their corresponding filename extensions in the ffmpeg [documentation](https://ffmpeg.org/ffmpeg-codecs.html).
Audio formats:
- **Lossy vs. Lossless:** MP3 and AAC are popular lossy compressed formats, resulting in smaller file sizes but with some potential quality loss. WAV and FLAC are lossless formats that preserve the original audio quality but create larger files.
### Extrac audio
Extract audio from a file:
`ffmpeg -i input.mp4 -vn output.mp3`
 - `-vn` means discard the video (*video no*)
 - To extract to a different format change the output file's extension to desired format: `wav`, `aac`, `flac` etc.
### Increase volume
Increase volume by 5 dB: `ffmpeg -i input.mp4 -af "volume=5" output.mp4`
- `-af`: This tells ffmpeg to apply an audio filter.
- `"volume=X"`: This is the specific filter definition.
	    - `"volume="`: This defines the volume filter.
		    - `X`: This represents the volume level you want to increase to. Here are your options:
	        - **value (e.g., 2, 3.5, -5):** This increases/decreases the volume by the specified value in decibels (dB).
	        - **`volume=1`**: This sets the volume to 0 dB (no change).
> [!Clipping]
Increasing the volume excessively can lead to audio clipping, which creates distortion. It's recommended to raise the volume gradually and monitor the output for clipping.
- **Normalization (Optional):** If your goal is to adjust the overall loudness of the audio without clipping, consider using the `normalize` filter instead of `volume`. Normalization aims to amplify the audio to a certain target level while avoiding clipping. Refer to the ffmpeg [documentation](https://ffmpeg.org/ffmpeg-filters.htm).

### Embed audio into video
This assumes that you have an `.mp4` video file and an `.mp4` audio file, and you want to combine them into a single `.mp4` file:
```sh
ffmpeg -i video.mp4 -i audio.mp4 -c:v copy -c:a aac -strict experimental -b:a 192k output.mp4`
```
- `-i video.mp4`: Specifies the input video file.
- `-i audio.mp4`: Specifies the input audio file.
- `-c:v copy`: Copies the video stream from the input video file without re-encoding.
- `-c:a aac`: Encodes the audio stream in AAC format.
- `-strict experimental`: Allows the use of experimental codecs, necessary for some builds of `ffmpeg` when encoding AAC audio.
- `-b:a 192k`: Sets the audio bitrate to 192 kbps.
- `output.mp4`: The name of the output file.

Alternative parameters:
- If your audio file is in a different format (e.g., `.aac` or `.mp3`), you can still use the same command, just change the input audio file extension.
- The `-c:v copy` option ensures that the video stream is copied directly without re-encoding, which is faster and retains the original video quality. If you need to re-encode the video for any reason, you can specify a different codec with `-c:v`.
- The `-c:a aac` option re-encodes the audio to AAC format, which is common for MP4 files. If your audio is already in the desired format and you want to copy it directly, you can use `-c:a copy`.
