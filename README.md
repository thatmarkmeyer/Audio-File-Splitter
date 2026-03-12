# Audio File Splitter
Vinyl &amp; Tape Audio File Splitter is a single-file browser tool for splitting vinyl and cassette recordings into individual tracks, tagging them with metadata from MusicBrainz, and exporting them as WAV files or FFmpeg scripts.

No installation. No uploads. Runs in the browser. Optional song recognition requires third-party connection.

The tool is divided into 5 sections.

1. Add an audio file (MP3, WAV, FLAC, OGG, M4A). Large VBR MP3s are handled via chunked decoding.

2. Waveform viewer and split editor. A zoomable view of the audio file.  Splits can be added, deleted, or moved.  Audio can be played from any location.

3. Detection.
3a. Automated detection using a simple and more complex process.
3b. Applying splits from a manual list.
3c. Applying splits based upon information of individual song tracks.

All metadata search uses the [MusicBrainz](https://musicbrainz.org) public API (CC0 licence). No key required. Requests identify themselves as `VinylSplitter/1.0` per MusicBrainz's usage guidelines.

4. Review and tagging of identified tracts. Ability to look-up albums using MusicBrainz.  Ability to manually add track information.  Ability to review each proposed split location.

5. Identify unknown tracks by sending an audio sample to [AudD](https://audd.io) or [Shazam via RapidAPI](https://rapidapi.com/apidojo/api/shazam). Requires your own API key (see below).

6. **Export Formats**
*FFmpeg Script* (.sh) (.bat); *.wav* and *cue sheet*; *metadata json*

<img width="825" height="1046" alt="VS1" src="https://github.com/user-attachments/assets/b1f9ca54-a0da-4f3d-8890-ca3682e4a1fc" />

<img width="818" height="1147" alt="VS2" src="https://github.com/user-attachments/assets/e9992dd9-4711-4971-ad17-92aef5632ab5" />

<img width="1245" height="1159" alt="VS3" src="https://github.com/user-attachments/assets/cf6f868b-b548-4fca-a56b-5825734ad18f" />
