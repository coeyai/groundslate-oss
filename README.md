# GroundSlate: open-source components

GroundSlate is a proprietary product of COEY. This repository exists so that the open-source
libraries GroundSlate ships with can be obtained from the same place as GroundSlate itself, as
their licences require.

## What is here

Nothing in this repository is COEY-authored code, and no COEY code is licensed by its presence
here. Every release carries source that belongs to its upstream project, under that project's own
licence.

Each release corresponds to a component GroundSlate bundles:

| Release | Component | Licence |
|---|---|---|
| `ffmpeg-<version>` | The exact FFmpeg source a GroundSlate build was compiled from, the configure line used, and the licence text | LGPL-2.1-or-later |

## FFmpeg

GroundSlate bundles FFmpeg as dynamically linked, unrenamed shared libraries, built
`--disable-gpl --disable-nonfree` with no libx264 and no libx265, so the build is
LGPL-2.1-or-later. H.264 and HEVC encoding is done by Apple's VideoToolbox, an OS framework rather
than a linked library. The shipped binary says so itself: `ffmpeg -L` prints the LGPL notice and
`ffmpeg -version` prints the configure line.

Each `ffmpeg-<version>` release contains:

* `ffmpeg-<version>.tar.xz`, the pristine upstream release exactly as fetched from ffmpeg.org
* `ffmpeg-<version>.tar.xz.sha256`, so you can verify that it is untouched
* `groundslate-ffmpeg-<version>-src.tar.xz`, the same source with `GROUNDSLATE-BUILD.txt` added at
  its root, carrying the exact configure line used
* `COPYING.LGPLv2.1`, the licence text

Because the libraries are dynamic and unrenamed, you can build your own compatible FFmpeg from
this source and replace the copies inside `GroundSlate.app/Contents/Frameworks`.

## Anything else

If you believe a component GroundSlate ships is missing from here, or you want source we have not
published, write to opensource@coey.com and we will get it to you.
