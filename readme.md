# cut-radio-records

A Perl tool to trim, encode, and tag recorded radio broadcasts based on event metadata from the **[calcms](https://github.com/rapilodev/racalmas)** backend.

## Quick Usage

```bash
$ ./cut-radio-records --config <config_file> [--force] <DATE|EVENT_ID>
```

- `<DATE>`: Format `YYYY-MM-DD`
- `<EVENT_ID>`: Numeric calcms event ID

### Examples

```bash
# Process a specific date
$ ./cut-radio-records --config settings.conf 2025-04-06

# Force reprocess a specific event
$ ./cut-radio-records --config settings.conf --force 12345
```

## Features

- Event metadata is fetched from a configured calcms backend.
- Merge & trim WAV files with `sox`
- Encode to MP3 using `lame`
- Add metadata & cover image via `eyeD3`
- Normalize volume with `mp3gain`
- Works with both date- and ID-based lookups

## Config (`.conf` file)

```ini
events_url       = https://piradio.de/agenda/events/&location=piradio
images_url       = https://piradio.de/images/
source_dir       = /srv/audio/piradio/recording/
target_dir       = /srv/audio/piradio/cutted/
image_target_dir = /srv/audio/piradio/cutted/images/
timezone         = Europe/Berlin
offset           = 4.0
```
