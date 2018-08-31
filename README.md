# Apollo 11 Audio Transcription and Alignment
## Overview

1. Run all audio through speech-to-text recognition to get timestamps for each word.
2. Match timestamps of speech-to-text to existing transcript timestamps and get offsets
3. Find long blocks of silence
    - Use speech-to-text timestamps to find long gaps between words
4. Insert space in the middle of these gaps to align audio files with the existing transcripts.

## Links

### Resources

> ### Tapes - [ATG (Air to Ground) tapes, 155-AAA to 188-AAA](https://archive.org/details/Apollo11Audio)

> ### Transcript - [Apollo 11 Flight Journal](https://history.nasa.gov/afj/ap11fj/index.html)

### Similar Projects
- Project Apollo 17
    - blog:  [benfeist.com](http://benfeist.com/project-apollo-17/)
    - website: [apollo17.org](http://apollo17.org)