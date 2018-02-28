# Classic Rock

This folder contains the data behind the story [Why Classic Rock Isn’t What It Used To Be](https://fivethirtyeight.com/features/why-classic-rock-isnt-what-it-used-to-be/).

`radio.py` is a Python script which scrapes the song data from radio sites.  
`compiling_radio.py` is a Python script which processes `radio.py`'s output into one file per station.

The following table provides a definition for each data field in `classic-rock-raw-data.csv`:

Data Field      | Definition
----------------|------------
`SONG RAW`      | The song's raw title which is scraped from the radio station
`Song Clean`    | The song's title after processing the raw song title
`ARTIST RAW`    | The song's raw artist's name which is scraped from the radio station
`ARTIST CLEAN`  | The song's artist's name after processing the raw artist name
`CALLSIGN`      | The call sign of the radio station which played the song
`TIME`          | The time (in _seconds_) at which the radio station played the song (note, Python measures time in _seconds_ beginning from January 1, 1970)
`UNIQUE_ID`     | The unique ID that is assigned to each song. The unique ID is formed by combining the radio's call sign with a four-digit number. `0001` represents the last song that the radio station played. The largest unique ID represents the first song that the radio station played.
`COMBINED`      | The combination of `Song Clean` and `ARTIST CLEAN` which can be used to connect `classic-rock-raw-data.csv` to `classic-rock-song-list.csv`.
`First?`        | Indicates if this is the first occurence of the song in the data (`1` if this is the first occurence, `0` otherwise)

The following table provides a definition for each data field in `classic-rock-song-list.csv`:

Data Field      | Definition
----------------|------------
`Song Clean`    | The song's title
`ARTIST CLEAN`  | The song's artist's name
`Release Year`  | The song's release year that is obtained from SongFacts. If no year is provided, then the song did not have an entry in SongFacts.
`COMBINED`      | The combination of `Song Clean` and `ARTIST CLEAN` which can be used to connect `classic-rock-song-list.csv` to `classic-rock-raw-data.csv`.
`First?`        | This value is always 1. Since all entries of a particular song in `classic-rock-raw-data.csv` are represented by a single entry in `classic-rock-song-list.csv`, there is only one occurence of the song in `classic-rock-song-list.csv`.
`Year?`         | Indicates if the song's `Release Year` was detected (`1` if `Release Year` was detected, `0` otherwise)
`PlayCount`     | The number of times the song was played by radio stations. This value corresponds to the total number of entries for the song in `classic-rock-raw-data.csv`.
`F*G`| _If_ `Year?` is `1`, this field indicates the number of times the song was played by radio stations. 