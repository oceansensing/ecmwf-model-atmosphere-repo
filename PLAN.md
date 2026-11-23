# ecmwf-model-atmosphere-repo: the founding plan and running record

ECMWF's open forecast data, the atmosphere and the waves. Created on GitHub by the owner and given its documents by the site's
`pipeline/scaffold/new-origin.py`. **Publishing since 2026-11-09**, hourly at :13.

## What it is for

ECMWF's open-data forecast fields at 0.25°, the step nearest the clock from the newest run: the 10 m wind (`wind.json`), the 2 m and 850 hPa air temperatures (`air.json`, `air-850.json`), the total cloud cover (`cloud.json`), the 500 hPa heights as contours (`gh-500.json`) and as a grid (`hgt500-ecmwf.json`, on R2 alone), and ECWAM's significant wave height (`waves.json`). The roots keep the names they had in `realtime-data-repo`, which published them from 2026-08-03 (the wind) and 2026-08-12 (the waves) until this repository took them over.

## Where the data comes from

ECMWF's open data, `https://data.ecmwf.int/forecasts`: the IFS high-resolution forecast (`oper`) and ECWAM (`wave`), four runs a day, three-hourly steps, each message read by a byte range from the run's index. CC BY 4.0, credited as ECMWF's. The fetchers are the site's `scripts/fetch-wind.py` and `scripts/fetch-waves.py`; their docstrings carry the measurements.

## Open

1. The hours either side (D2): the run that moves the base, keeping the last behind, and the first on a new ECMWF run,
   read; the window behind full a day after the first run.

## Record

- **2026-11-09, the first runs**: dispatched at 08:16 EST (run 42623969507), green — its six Pages files
  byte-identical to `realtime-data-repo`'s (the 06Z run's step +6 h), R2 14 files; the second at 08:58 (run
  42630255870), green — seeded 7 files from the first, the step +9 h, both products fresh, R2 12 of 14 uploaded.
  The schedule uncommented then, hourly at :13.
- **2026-11-22, evening: the hours either side and the sea-level pressure** (D2), built in the site's fetchers
  and rehearsed from this branch (four runs, nothing published); this repository's declaration and workflow
  pushed that evening.
- **2026-11-23 (UTC), the first runs with the hours**: the first (run 45090175109, 00:40 UTC) green — the 18Z run's
  base at 00:00 UTC and sixteen hours ahead for each of seven roots, the sea-level pressure among them, nothing dated
  on the branch, R2 equal to the build (135 files), the wind's step 235 s; the second (45093902084, 01:19 UTC) found
  nothing new and R2 kept the 112 hours ahead.
