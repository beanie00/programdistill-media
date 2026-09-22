# ProgramDistill Mining media

Static browser recordings used by the [ProgramDistill dashboard](https://microsoft.github.io/debug-gym/blog/2026/09/programdistill/dashboard/).

This repository contains 1,969 MP4 recordings and 1,969 PNG previews (about
653 MiB). GitHub Pages serves `main` from `/`, without Jekyll processing:

`https://beanie00.github.io/programdistill-media/media/<source-sha256>.mp4`

The dashboard's Mining catalog remains in `microsoft/debug-gym` at
`docs/figures/programdistill/mining/catalog.json`. It records relative paths,
video sizes, and SHA-256 hashes for both videos and previews. Only media
referenced by that catalog belongs here; source execution records and
unrelated artifacts are not included.

The blog configures this site's root URL as `programdistill_mining_media_base`
in `docs/_config.yml`. Application data and patch files stay on the blog's
own origin; only the configured media location is allowed for recordings.

Publish media before changing the blog's catalog, verify the published file
hashes and HTTP range responses, and retain files referenced by released
catalogs. Do not overwrite an existing URL with different content: use a new
versioned path when re-encoding. GitHub Pages size and bandwidth limits still
apply to this separate site.
