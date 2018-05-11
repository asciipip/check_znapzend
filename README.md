# check_znapzend

Nagios plugins to check the functioning of [znapzend][].

  [znapzend]: http://www.znapzend.org

## Prerequisites

Python 2 or 3.

Python modules:

 * isodate
 * enum34 (Python 2 only)
 * future (Python 2 only)

## Usage

### check_znapzend_age

Runs on the znapzend _destination_ system.  Give it a dataset name and
time intervals for warning and critical conditions.  If you're not
using the default timestamp format for znapzend, pass that, too, using
the `--tsformat` parameter.

The time intervals use [ISO 8601 durations][].  They designate age
thresholds.  e.g. `PT30M` represents 30 minutes, so it would trigger
if the most recent snapshot was more than 30 minutes ago.

  [ISO 8601 durations]: https://en.wikipedia.org/wiki/ISO_8601#Durations

Example, with a condensed tsformat, warn after two hours, and critical
after one day:

    check_znapzend_age --tsformat %Y%m%dT%H%M%S --warn PT2H --crit P1D tank/example
