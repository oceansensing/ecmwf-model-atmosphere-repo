# Decisions

Dated, irreversible-leaning decisions, one entry each, newest last. The
reasoning lives in `PLAN.md`.

**What counts as one-way in a data repository**: a decision that puts bytes in
readers' hands under a shape they will code against; a decision about which
repository owns a product, since moving one costs a migration in two places;
and a decision that forecloses an upstream.

## D1 2026-11-09 ECMWF's products move here from `realtime-data-repo`, their names kept

ECMWF's wind (2026-08-03) and ECWAM's waves (2026-08-12) joined `realtime-data-repo` when it was the only origin; every model since has had its own (the site pipeline's D6 and D10: one upstream, one fault domain, one gigabyte). They move here so their run follows ECMWF's cadence and not the observations' three runs an hour, and so a fault upstream or in a product that remembers its files stops this repository alone. The seven roots keep their names, so every reader that routes by the origins' `status.json` follows them without a change. Both origins publish them for an overlap, then `realtime-data-repo` declares them no more.

## D2 2026-11-22 Two days ahead and one behind, three-hourly; the mean sea-level pressure joins; the contours a product of their own

**The window is 48 hours ahead and 24 behind** (`hours_ahead`, `hours_behind`; the site pipeline's D16, the owner's call of 2026-11-21) for the grids — the wind, both air temperatures, the cloud cover, the 500 hPa heights' grid and the sea-level pressure — and the waves, at the steps the model posts: three-hourly. Every hour is in `moreFrames`, the base among them; no root lists `frames`, as none did.

**The hours ahead are the base's run's**: every run posts all its steps at once, so a run's hours ahead are read the first time it is the freshest and not asked of ECMWF again, the last base's listing saying which it gave. **The hours behind are kept, never fetched**: each is the hour as it stood when it was the base, and a file once behind is never written again. An hour ahead that cannot be read ends its root's list there, said, and the next run asks it again.

**The dated files are R2's alone** (`memory = "r2-kept"`, `<root>.v<time>.json`): none is on Pages or the `published` branch, and R2 keeps one while a root lists it. **The branch moves only after R2 has the files it lists** (the workflow's `remember` job).

**The mean sea-level pressure** (`mslp-ecmwf.json`, hPa) is a new root of the grids' product, R2's alone as a new product is: `msl` from the same step's index, one more range read. **The 500 hPa contours stay one hour**, the product `heights` with no window.

**Measured in rehearsal, nothing published**, from the live branch on 2026-11-22: a new run 225 to 246 seconds, about 785 MB and 133 files to R2; the base moved within a run 37 seconds, 87 MB and 21 files; the window full a day on, no listed hour lacking and no hour behind written again. About a third of a gigabyte a day read from ECMWF, against a tenth before.
