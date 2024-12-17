# Changelog

## [v2.0.0] - 2024-12-17

### Improvements & Fixes
- Fixed a number of utterance onset/offset in the video annotations.
- Multiple recording, subrecording, region boundaries were "trimmed" to match the audio file that was annotated.

### New Features
- Added surplus (time that was annotated beyond what we planned to annotate) duration to recordings.csv.
- Added new columns such as `audio_video`, `child`, `month`, `region_id`, and `sub_recording_id` to all tables for more comprehensive data tracking.
- Introduced human-readable duration formats (hh:mm:ss) alongside millisecond-precision timings for easier interpretation of recording lengths.

### Changes
- Updated how recording durations are calculated in order to harmonize listened-to and surplus definitions for months 6 and 7 vs. months 8-17.
- Unified formatting across CSV files by standardizing capitalization and the representation of empty values.

### Documentation
- Added this changelog.

## [v1.0.0] - 2023-03-08 - initial release
