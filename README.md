# ProgramDistill media and patches

Static browser recordings used by the [ProgramDistill dashboard](https://microsoft.github.io/debug-gym/blog/2026/09/programdistill/dashboard/).

This repository contains 1,969 MP4 recordings and 1,969 PNG previews (about
653 MiB), plus 3,703 gzip-compressed mask patches (about 12 MiB). GitHub Pages
serves `main` from `/`, without Jekyll processing:

`https://beanie00.github.io/programdistill-media/media/<source-sha256>.mp4`

The dashboard's Mining catalog remains in `microsoft/debug-gym` at
`docs/figures/programdistill/mining/catalog.json`. It records relative paths,
video sizes, and SHA-256 hashes for both videos and previews. Only media
referenced by that catalog belongs here; source execution records and
unrelated artifacts are not included.

The blog configures this site's root URL as `programdistill_mining_media_base`
in `docs/_config.yml`. Application JSON stays on the blog's own origin.

## Code patches

Published patches use
`https://beanie00.github.io/programdistill-media/patches/<sha256>.diff.gz`.
The filename is the SHA-256 of the uncompressed original diff; compressed bytes
are copied unchanged from the approved dashboard export. The 3,703 unique files
serve 3,846 task references. Unavailable or withheld patches are not published.

The blog sets `programdistill_patch_base` to this site's `patches/` directory.
Application JSON retains its relative patch paths, byte counts and hashes.
The dashboard accepts only hash-named files within that configured HTTPS
directory, fetches on demand with credential-free CORS, and decompresses them
in the browser. JSON still loads from the blog, and local patch copies are
excluded from its deployment. Verify HTTP success, CORS access, compressed
bytes, uncompressed hashes and actual browser rendering before switching the
blog to newly published patches.

Publish media before changing the blog's catalog, verify the published file
hashes and HTTP range responses, and retain files referenced by released
catalogs and task descriptors. Publish patches before referencing them and
retain released hash-named files unchanged. Do not overwrite an existing URL
with different content: use a new versioned path when re-encoding media.
GitHub Pages size and bandwidth limits still apply to this separate site.
