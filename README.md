# ecmwf-model-atmosphere-repo

ECMWF's open forecast data, the atmosphere and the waves: a data repository of the oceansensing ocean map system, with its own
Pages site, its own schedule and its own gigabyte, and no code of its own.

**Nothing is published yet.** `PLAN.md` is the founding plan; `CLAUDE.md` carries what must not be
got wrong and the shared doc doctrine.

## What it publishes

ECMWF's open-data forecast fields at 0.25°, the step nearest the clock from the newest run: the 10 m wind (`wind.json`), the 2 m and 850 hPa air temperatures (`air.json`, `air-850.json`), the total cloud cover (`cloud.json`), the 500 hPa heights as contours (`gh-500.json`) and as a grid (`hgt500-ecmwf.json`, on R2 alone), and ECWAM's significant wave height (`waves.json`). The roots keep the names they had in `realtime-data-repo`, which published them from 2026-08-03 (the wind) and 2026-08-12 (the waves) until this repository took them over.

These products are drawn on the website's map.

## Where the data comes from

ECMWF's open data, `https://data.ecmwf.int/forecasts`: the IFS high-resolution forecast (`oper`) and ECWAM (`wave`), four runs a day, three-hourly steps, each message read by a byte range from the run's index. CC BY 4.0, credited as ECMWF's. The fetchers are the site's `scripts/fetch-wind.py` and `scripts/fetch-waves.py`; their docstrings carry the measurements.

## How it runs

The orchestrator (the site's private `pipeline/`), the fetchers and the
published-file contract all come from `oceansensing.github.io`, checked out at
run time. This repository carries `pipeline/products.toml` and its publish
workflow, and nothing else executable. Each run publishes to GitHub Pages and
to Cloudflare R2 from one build. Related repositories: `realtime-data-repo` (the observations, which published these products until 2026-11-09), `gfs-model-atmosphere-repo` (NOAA's GFS, the same quantities from another model).

**Which document gets what, and what "update docs" means across all
thirty-four repositories, is the doctrine block at the top of `CLAUDE.md`**: the
same text in all thirty-four, held equal by the site's `check:docs`.

## Structure

```
README.md       what this is
CLAUDE.md       what must not be got wrong, and the shared doc doctrine
PLAN.md         the founding plan and running record
DECISIONS.md    dated one-way decisions, D1 onward
pipeline/       products.toml, the declaration the orchestrator reads
.github/        the publish workflow
```
