# Audio File Splitter
Vinyl &amp; Tape Audio File Splitter is a single-file browser tool for:
- splitting recordings into individual tracks, 
- tagging them with metadata, and 
- exporting them as WAV files or FFmpeg scripts.

No installation. 
No uploads. 
Runs in the browser. 
Optional song recognition requires third-party connection.

## 1. Add an audio file.
(MP3, WAV, FLAC, OGG, M4A). Large VBR MP3s handled via chunked decoding.

## 2. Waveform viewer and split editor. 
- A zoomable view of the audio file.  
- Splits can be added, deleted, and moved.
- Audio can be played/stopped from any location with right-click.
- Optional view as spectrogram.

## 3. Detection.
### Automated detection using a simple process.
Looks for "silence" of a minimum length below a certain volumn threshold.  Default theshholds based upon album recording type.
### Automated detection using a more complex process.
Additional analysis for detecting tracks where typical silence is less reliable.  See below for more details.
### Apply splits from a manual list.
Paste a list of tracks and times using one of several formats.
### Apply splits based upon information of individual song tracks.
Search for an album and apply metadata and split information from MusicBrainz database or Discogs database.  
Results are often off by a few seconds. Users can choose to "click-to" the promising detection and manually adjust each split in the waveform.

## 4. Review and tagging of identified tracts.
- Ability to look-up albums using MusicBrainz or Discogs.
- Ability to manually add track information.  
- Ability to play each tract.
- Ability to review each proposed split location and confirm.

All metadata search uses the [MusicBrainz](https://musicbrainz.org) public API (CC0 licence). No key required. Requests identify themselves as `VinylSplitter/1.0` per MusicBrainz's usage guidelines.

## 5. Identify unknown tracks and add metadata.
Using your own API key, sending an audio sample to [Shazam via RapidAPI](https://rapidapi.com/apidojo/api/shazam), AcoustID, or [AudD](https://audd.io) 
Add BPM metadata.

## 6. Export 
### Formats
- **FFmpeg Script** .sh (macOS/Linux): Place in the same folder as your audio file, run chmod +x script.sh && ./script.sh. Produces fully-tagged MP3s. Get FFmpeg ↗
- **FFmpeg Script** .bat (Windows): Place in the same folder as your audio file, then double-click or run from a command prompt. Requires FFmpeg on your PATH.
- **WAV (Lossless)**: Exports each track as a WAV file. Use Mp3tag or Kid3 to add ID3 tags afterwards.
- **Cue Sheet**: A single .cue file describing all split points — use with your audio player or ripper.
- **Metadata JSON**: A structured JSON file with all track metadata for use in custom workflows.

Opening page:
<img width="825" height="1046" alt="VS1" src="https://github.com/user-attachments/assets/b1f9ca54-a0da-4f3d-8890-ca3682e4a1fc" />

Dark Mode with splits detected:
<img width="818" height="1147" alt="VS2" src="https://github.com/user-attachments/assets/e9992dd9-4711-4971-ad17-92aef5632ab5" />

Two-columns optional:
<img width="1245" height="1159" alt="VS3" src="https://github.com/user-attachments/assets/cf6f868b-b548-4fca-a56b-5825734ad18f" />

## Automated detection using a more complex process. 
A more detailed description.

After identifying cadidates, applies audio analysis signals. Takes longer but may handle drum solos, fades, and ambiguous silences more reliably than simple threshold detection.

- **Silence / Energy** — Detects track boundaries by finding quiet regions where the audio amplitude drops below a fixed threshold. Gaps with deeper silence and lengths matching the expected inter-track gap score higher; a built-in beat guard suppresses false positives caused by drum solos or sparse sections.
- **Spectral Flux** — Measures how much the overall frequency content of the audio changes across a candidate boundary. A large spectral shift between the seconds before and after a gap is strong evidence that two different songs surround it.
- **High-Freq Drop** — Tracks the level of high-frequency content on either side of a gap. Track endings typically roll off treble content as a song fades, while new tracks open with a brighter sound.
- **BPM / Rhythm** — Estimates tempo using autocorrelation over 10-second windows and compares the dominant beat before and after a gap. A significant tempo change across the boundary raises the boundary score.
- **Hi-Pass BPM** — Works like BPM detection but first filters the audio above ~1 kHz to focus on snare and hi-hat transients, which often give a cleaner and more stable rhythm estimate than the full-band signal.
- **Onset Density** — Counts the rate of musical note events (onsets) in the audio and looks for a drop or surge across a candidate boundary. A song ending produces fewer and fewer onsets; a new song starting brings a burst of new activity.
- **Spectral Centroid** — Measures the average "brightness" of the audio on each side of a gap. A significant shift in the centre of spectral mass suggests a change in instrumentation or production style between two songs.
- **Key / Chroma** — Analyses the 12-note pitch-class distribution (chroma) of the audio on either side of a boundary. A change in tonal centre or key is a reliable indicator that a different song has begun.
- **Dynamic Range** — Measures the crest factor (peak-to-RMS ratio) of the audio. A fade-out at the end of a track compresses dynamics before the gap; a new track typically opens with greater dynamic contrast.

