# 📀 Music Utils

A bunch of scripts that I run very often to maintain my library.
Tested on macOs, but should works also on linux.

## Flac CD quality

Convert flac 24/96 to CD quality 16/48-44.1

The script read the current file and find if is multiple of 44.1kHz or 48kHz, and converts to those.
for example
96 -> 48
192 -> 48
88.2 -> 44.1

### Why?

16/44.1 is the redbook standard that was chosen for CDs. It wasn't picked randomly, it was selected because it covers (well, exceeds) the range of human hearing.

16-bits gives 96dB of dynamic range, 44.1KHz covers 0Hz to 22050Hz. When young with perfect hearing, you'll hear 20Hz to 20000Hz.

Trained listeners have heard differences between 16/44.1 and high res when listening in controlled test environments, using headphones and test tones. Real world, with music, you have no chance of hearing any difference. A million times more so when listening through speakers as you'll have 30-40dB noise floor in a quiet room.

There are genuine benefits for recording and producing music at higher sample rates and bit depth, but no benefit for music playback.

If you can hear differences between high res and 16/44.1 versions of a song, they will be different masters.

---

## Recursive Flac to mp3 320kbps

Converts flac to mp3 at 320kbps recursive keeping the folder structure

```
cd /your/Music/Artist1/
/path/to/flac2mp3
````

It creates a new `mp3` folder with inside each album subfolders with mp3 files
It keeps the original flac folders:

```
Music/
├── Artist1/
│   ├── 1998 - Album 1/
│   │   └── *.flac
│   ├── 2000 - Album 2/
│   │   └── *.flac
│   └── mp3/
│       ├── 1998 - Album 1/
│       │   └── *.mp3
│       └── 2000 - Album 2/
│           └── *.mp3

```


---

## Flac rename according to cue file

When splitting a single album flac or ape to separated tracks it happen they names are like 
`split-track-01.flac`
`split-track-02.flac`

This script read the cue file and rename the tracks accordingly.

`01 Mojo Pin.flac`
`02 Grace.flac`

### Usage

enter the folder that contains split-track-* files and a .cue file

```
cd /your/splitted/album/
/path/to/flacrename
```

---

## Find Mp3 low bit rate

mp3lowlog find recursively mp3 files with low bitrate, by default lower than 320kbps
run it with a parameter to find lower than that, for example

`mp3lowlog 256`

### usage

1. download the script where do you prefer, for example your home dir
2. ensure it's executable

`chmod +x /path/to/mp3lowlog`

```
cd /your/Music/root/
/path/to/mp3lowlog 256
```

It save a log file lowbitrate.log