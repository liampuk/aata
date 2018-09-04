# Apollo 11 Audio Transcription and Alignment
## Overview

<img align="right" src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/27/Apollo_11_insignia.png/238px-Apollo_11_insignia.png">

After watching Apollo 13 (for maybe the 13th time) I thought it might be cool to create a modern day version of the *squawk boxes* that the families of astronauts were given to listen into the Air to Ground communications in real time. Obviously I can't listen into Apollo missions in real time, but I thought it would be close enough (+/- 50 years) to play the tapes back on the right date and time, starting at 1:32pm on the 16th July and finishing with the splashdown at 4:50pm on the 24th July.

Although NASA has uploaded the original tapes in their entierty to [archive.org](https://archive.org/details/Apollo11Audio), they are completely raw as recorded, with many cuts and jumps. This means in order to play the audio back in 'real time', a huge amount of editing would be required.  [ben feist](http://benfeist.com/project-apollo-17/) has already done this for apollo 17, which took over 3 years (for a project much larger in scope mind). Ideally, I'd like to get this done in a year, so automating the editing of audio seems to be the way to go.

## Aims

1. Run all audio through speech-to-text recognition to get timestamps for each word.
2. Match timestamps of speech-to-text to existing transcript timestamps and get offsets
3. Find long blocks of silence
    - Use speech-to-text timestamps to find long gaps between words
4. Insert space in the middle of these gaps to align audio files with the existing transcripts.

## Notes

Need to decide whether to produce 1 large file or multiple smaller files. Combining the audio would produce a very large file:

|Bitrate  |File size per hour|Total file size|
|-------- |------------------|---------------|
|96 Kbps  |43.2 MB           |8.4 GB         |
|128 Kbps*|57.6 MB           |11.2 GB        |
|192 Kbps |86.4 MB           |16.8 GB        |
|256 Kbps |115.2 MB          |22.5 GB        |

> *128 Kbps seems to be the best option (for a 16gb sd card)

For smaller files, need to decide where to cut:
- At a set time (4 hours etc.)
- Set file size (100 MB etc.)*
- As the original tapes were
    - this would be tricky as some tapes overlap (no gap in conversation)
- At key moments
    - possibly tricky as can't cut during the moment (don't want audio splice artifacts during launch etc.)

> *Probably the most logical option

***

Various speech-to-text services are available online, but the cost is prohibitively expensive.

- $280 quoted by [Google Cloud](https://cloud.google.com/speech-to-text/) and [Amazon AWS](https://aws.amazon.com/transcribe/), at $0.0004/second
    - Max length of Google Cloud is 180 minutes
- $214 quoted by [IBM Watson](https://www.ibm.com/watson/services/speech-to-text/), at $0.02/minute (first 1000 minutes free)
    - Most accurate of the 4
    - [Watson Docs](https://www.ibm.com/watson/developercloud/speech-to-text/api/v1/curl.html?curl#introduction)
- $187 quoted by [Microsoft Bing Speech](https://azure.microsoft.com/en-us/services/cognitive-services/speech/), at $4/15 seconds

Therefore running the transcription locally seems to be the way to go.

## Links

### Resources

> ### Tapes - [ATG (Air to Ground) tapes, 155-AAA to 188-AAA](https://archive.org/details/Apollo11Audio)

> ### Transcript - [Apollo 11 Flight Journal](https://history.nasa.gov/afj/ap11fj/index.html)

> ### Event Timestamps - [Apollo 11 Timeline](https://history.nasa.gov/SP-4029/Apollo_11i_Timeline.htm)

### Services

- Speech-to-Text
    - [IBM Watson vs Google Cloud](https://dague.net/2017/06/12/comparing-speech-recognition-for-transcripts/)
    - [Recognising Speech for Fun and Profit](https://blog.rebased.pl/2016/12/08/speech-recognition-1.html)
    - [List of speech-to-text apis](https://www.programmableweb.com/category/all/apis?keyword=speech%20recognition)
    - [CMUSphinx](https://github.com/liampuk/aata.git)
      - Linux only
- [ffmpeg](https://www.ffmpeg.org/download.html) for processing audio files 

### Similar Projects
- Project Apollo 17
    - blog:  [benfeist.com](http://benfeist.com/project-apollo-17/)
    - website: [apollo17.org](http://apollo17.org)
