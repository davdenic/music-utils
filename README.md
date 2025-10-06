# 📀 Music Utils

A collection of Bash scripts to maintain your music library efficiently. Tested on macOS, should also work on Linux.

## Setup

1. Download the scripts to a preferred location, e.g., your home directory.
2. Ensure they are executable:

```bash
chmod +x /path/to/music-utils/*
```

### Requirements

install flac
```bash
brew install flac
```

install ffmpeg 
```bash
brew install ffmpeg
```

install mp3info (for mp3lowlog)
```bash
brew install mp3info
```

## FLAC CD Quality

Convert FLAC files from high-resolution (e.g., 24-bit/96kHz) to CD quality (16-bit/44.1kHz or 48kHz).

The script detects the sample rate of each file and converts it to the nearest multiple of 44.1kHz or 48kHz:

* 96kHz → 48kHz
* 192kHz → 48kHz
* 88.2kHz → 44.1kHz

### Why CD Quality?

* 16-bit gives 96dB of dynamic range.
* 44.1kHz covers 0Hz to 22,050Hz, covering human hearing.
* High-resolution audio benefits recording and production, but for playback, differences are inaudible.

## Recursive FLAC to MP3 320kbps

Converts FLAC files to MP3 at 320kbps recursively while preserving folder structure.

```bash
cd /your/Music/Artist1/
/path/to/flac2mp3
```

Creates a new `mp3` folder containing album subfolders with MP3 files while keeping original FLAC folders:

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

## FLAC Rename According to CUE File

When splitting a single album FLAC or APE file into tracks, filenames often appear as:

```
split-track-01.flac
split-track-02.flac
```

This script reads the accompanying `.cue` file and renames tracks accordingly:

```
01 Mojo Pin.flac
02 Grace.flac
```

### Usage

```bash
cd /your/splitted/album/
/path/to/flacrename
```

## Find MP3 Low Bitrate

Finds MP3 files with bitrate lower than 320kbps recursively. You can specify a different threshold (e.g., 256kbps):

```bash
mp3lowlog 256
```

### Usage

```bash
cd /your/Music/root/
/path/to/mp3lowlog 256
```

Generates a log file `lowbitrate.log` with all files below the threshold.

## Notes

* Always backup your music before running these scripts.
* Ensure `ffmpeg`, `mp3info`, and other dependencies are installed and available in your PATH.
* Scripts preserve origina
