# Audio File Splitter
Vinyl &amp; Tape Audio File Splitter is a single-file browser tool for splitting vinyl and cassette recordings into individual tracks, tagging them with metadata from MusicBrainz, and exporting them as WAV files or FFmpeg scripts.

No installation. No uploads. Runs in the browser. Optional song recognition requires third-party connection.

The tool is divided into 5 sections.

## 1. Add an audio file.
(MP3, WAV, FLAC, OGG, M4A). Large VBR MP3s are handled via chunked decoding.

## 2. Waveform viewer and split editor. 
A zoomable view of the audio file.  Splits can be added, deleted, and moved.  Audio can be played/stopped from any location with right-click.

## 3. Detection.
### Automated detection using a simple process.
Looks for "silence" of a minimum length below a certain volumn threshold.  Default theshholds based upon album recording type.
### Automated detection using a more complex process.
Applying nine types of analysis to assist in detecting tracks more reliably, but takes longer.
### Apply splits from a manual list.
Paste a list of tracks and times using one of several formats.
### Apply splits based upon information of individual song tracks.
Search for an album and apply metadata and split information from MusicBrainz database.  Because the result is often off by a few seconds, the user can either manually adjust each split, or choose to "click-to" the promising detection made by the simple detection method.

## 4. Review and tagging of identified tracts.
Ability to look-up albums using MusicBrainz.  
Ability to manually add track information.  
Ability to play each tract.
Ability to review each proposed split location to listen to three seconds before and after the split.

All metadata search uses the [MusicBrainz](https://musicbrainz.org) public API (CC0 licence). No key required. Requests identify themselves as `VinylSplitter/1.0` per MusicBrainz's usage guidelines.

## 5. Identify unknown tracks by sending an audio sample to [AudD](https://audd.io) or [Shazam via RapidAPI](https://rapidapi.com/apidojo/api/shazam). Requires your own API key.

## 6. Export 
### Formats
**FFmpeg Script** .sh (macOS/Linux): Place in the same folder as your audio file, run chmod +x script.sh && ./script.sh. Produces fully-tagged MP3s. Get FFmpeg ↗
**FFmpeg Script** .bat (Windows): Place in the same folder as your audio file, then double-click or run from a command prompt. Requires FFmpeg on your PATH.
**WAV (Lossless)**: Exports each track as a WAV file. Use Mp3tag or Kid3 to add ID3 tags afterwards.
**Cue Sheet**: A single .cue file describing all split points — use with your audio player or ripper.
**Metadata JSON**: A structured JSON file with all track metadata for use in custom workflows.

Opening page:
<img width="825" height="1046" alt="VS1" src="https://github.com/user-attachments/assets/b1f9ca54-a0da-4f3d-8890-ca3682e4a1fc" />

Dark Mode with splits detected:
<img width="818" height="1147" alt="VS2" src="https://github.com/user-attachments/assets/e9992dd9-4711-4971-ad17-92aef5632ab5" />

Two-columns optional:
<img width="1245" height="1159" alt="VS3" src="https://github.com/user-attachments/assets/cf6f868b-b548-4fca-a56b-5825734ad18f" />
