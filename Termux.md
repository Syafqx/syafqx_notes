## bashrc
It's on `~/../usr/etc/bash.bashrc`. Declare some variable and function.

---
The update function
```bash
update() {
    pkg update -y && pkg upgrade -y && pip install -U yt-dlp
}
```

---
yt-dlp format variable (though I probably should use yt-dlp.conf for this)
```
F="(298/136/135/134/bv)+(140-40/140-39/140-38/140-37/140-36/140-35/140-34/140-33/140-32/140-31/140-30/140-29/140-28/140-27/140-26/140-25/140-24/140-23/140-22/140-21/140-20/140-19/140-18/140-17/140-16/140-15/140-14/140-13/140-12/140-11/140-10/140-9/140-8/140-7/140-6/140-5/140-4/140-3/140-2/140-1/140/ba)"
```

---
yt-dlp playlist title
```
O="%(playlist_index)s %(title)s.%(ext)s"
```

---
Then add `/storage/emulated/0/` as a variable for easier access (quicker way to cd to home dir)

## Things to install
* python
* wget
* file
* ffmpeg
* qrencode
* git
* pip yt-dlp

```
pkg install -y python wget file ffmpeg qrencode git && pip install yt-dlp
```