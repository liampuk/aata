# Apollo 11 Audio Transcription and Alignment
## Overview

1. Run all audio through speech-to-text recognition to get timestamps for each word.
2. Match timestamps of speech-to-text to existing transcript timestamps and get offsets
3. Find long blocks of silence
    - Use speech-to-text timestamps to find long gaps between words
4. Insert space in the middle of these gaps to align audio files with the existing transcripts.