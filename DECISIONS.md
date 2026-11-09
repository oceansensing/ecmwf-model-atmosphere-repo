# Decisions

Dated, irreversible-leaning decisions, one entry each, newest last. The
reasoning lives in `PLAN.md`.

**What counts as one-way in a data repository**: a decision that puts bytes in
readers' hands under a shape they will code against; a decision about which
repository owns a product, since moving one costs a migration in two places;
and a decision that forecloses an upstream.

## D1 2026-11-09 ECMWF's products move here from `realtime-data-repo`, their names kept

ECMWF's wind (2026-08-03) and ECWAM's waves (2026-08-12) joined `realtime-data-repo` when it was the only origin; every model since has had its own (the site pipeline's D6 and D10: one upstream, one fault domain, one gigabyte). They move here so their run follows ECMWF's cadence and not the observations' three runs an hour, and so a fault upstream or in a product that remembers its files stops this repository alone. The seven roots keep their names, so every reader that routes by the origins' `status.json` follows them without a change. Both origins publish them for an overlap, then `realtime-data-repo` declares them no more.
