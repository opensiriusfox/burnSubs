# burnSubs
You found my burnSubs tool. The goal for this tool is to ease the
conversion of arbitrary video files with soft-subtitles in the SSA/ASS
Substation Alpha format into simple stereo hard-subtitled video files.

## Features
* softsub to hardsub conversion
* embedded font files
* selecting specific audio streams
* selecting specific video streams
* automatic selection of language preferences
* default surround sound to stereo down-mixing
  * opt out CLI flag available
* anti-clobbering default behavior
* auto-cleanup on error

## Prerequisite Tools
Firstly, the tool will yell at you if the tools it needs don't exist.
Feel free to just run the tool, and it will let you know what you're
missing.

* [`ffmpeg`](https://ffmpeg.org/) - the one and only
  * `ffprobe` - usually comes with ffmpeg
* [`jq`](https://stedolan.github.io/jq/) - file/pipe based JSON processor


## How does it work?
`burnSubs` takes an input video file and tries to figure out what
audio streams and subtitle streams exist within the file. It stores
metadata in `/tmp` while it runs. When running it will pull the
streams within the input file, and try to select Japanese language
audio streams, and a non-signs subtitle stream (i.e. a full language
subtitle stream) to add to the output video.

Before transcoding it will then extract the subtitle file to pass into
`ffmpeg`'s subtitle burn in filter, and will try to down-mix any
surround sound input streams to stereo. Downmixing, track selection,
clobbering behavior, and verbosity can all be controlled to a limited
extent by CLI flags.

## Can you make it do *XYZ*.
Give me an enhancement request in github and I'll take a look.