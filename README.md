# Apollo 11 Audio Transcription and Alignment
## Overview

1. Run all audio through speech-to-text recognition to get timestamps for each word.
2. Match timestamps of speech-to-text to existing transcript timestamps and get offsets
3. Find long blocks of silence
    - Use speech-to-text timestamps to find long gaps between words
4. Insert space in the middle of these gaps to align audio files with the existing transcripts.

## Notes

Need to decide whether to produce 1 large file or multiple smaller files. Combining the audio would produce a very large file:

|Bitrate  |File size per hour|Total file size|
|-------- |------------------|---------------|
|96 Kbps  |43.2 MB           |7.8 GB         |
|128 Kbps*|57.6 MB           |10.4 GB        |
|192 Kbps |86.4 MB           |15.6 GB        |
|256 Kbps |115.2 MB          |20.7 GB        |

> *128 Kbps seems to be the best option (for a 16gb sd card)

For smaller files, need to decide where to cut:
- At a set time (4 hours etc.)
- Set file size (100 MB etc.)*
- As the original tapes were
    - this would be tricky as some tapes overlap (no gap in conversation)
- At key moments
    - possibly tricky as can't cut during the moment (don't want audio splice artifacts during launch etc.)

> *Probably the most logical option

## Links

### Resources

> ### Tapes - [ATG (Air to Ground) tapes, 155-AAA to 188-AAA](https://archive.org/details/Apollo11Audio)

> ### Transcript - [Apollo 11 Flight Journal](https://history.nasa.gov/afj/ap11fj/index.html)

### Similar Projects
- Project Apollo 17
    - blog:  [benfeist.com](http://benfeist.com/project-apollo-17/)
    - website: [apollo17.org](http://apollo17.org)
