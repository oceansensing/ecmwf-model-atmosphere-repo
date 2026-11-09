# ecmwf-model-atmosphere-repo: the founding plan and running record

ECMWF's open forecast data, the atmosphere and the waves. Created on GitHub by the owner and given its documents by the site's
`pipeline/scaffold/new-origin.py`. **Nothing is published yet.**

## What it is for

ECMWF's open-data forecast fields at 0.25°, the step nearest the clock from the newest run: the 10 m wind (`wind.json`), the 2 m and 850 hPa air temperatures (`air.json`, `air-850.json`), the total cloud cover (`cloud.json`), the 500 hPa heights as contours (`gh-500.json`) and as a grid (`hgt500-ecmwf.json`, on R2 alone), and ECWAM's significant wave height (`waves.json`). The roots keep the names they had in `realtime-data-repo`, which published them from 2026-08-03 (the wind) and 2026-08-12 (the waves) until this repository took them over.

## Where the data comes from

ECMWF's open data, `https://data.ecmwf.int/forecasts`: the IFS high-resolution forecast (`oper`) and ECWAM (`wave`), four runs a day, three-hourly steps, each message read by a byte range from the run's index. CC BY 4.0, credited as ECMWF's. The fetchers are the site's `scripts/fetch-wind.py` and `scripts/fetch-waves.py`; their docstrings carry the measurements.

## Open

1. The first dispatched run, read against `realtime-data-repo`'s copy, and then the schedule.
2. The overlap with `realtime-data-repo`, then its declarations removed.
