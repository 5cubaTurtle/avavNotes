The non-interactive network downloader

download a page: `wget https://linuxhandbook.com/change-echo-output-color/`
```sh
wget --user-agent="Mozilla" <URL>
```

### options
- The `-b` option allows you to run `wget` in the background, freeing up your terminal.
- Set user agent: `wget --user-agent="Mozilla" <URL>`.
- If a download is interrupted, the `-c` option allows you to resume it.
- `-P <download/here>` Set the path where the file will be saved to. The default is the current directory.
- The `-r` option enables recursive downloading, useful for downloading an entire website. The default maximum depth is 5.