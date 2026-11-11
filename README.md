# wine-engine

The Wine engine that my Mac game apps download when they install:
[GW2 on Mac](https://github.com/jdrly/gw2-on-mac), SWTOR on Mac and SWGL on Mac.

I don't build these engines. This repository keeps a copy of the exact files the apps were made
and tested against, so an install keeps working when the original download moves. The files are
in the [releases](https://github.com/jdrly/wine-engine/releases), one release per engine.

## cx-26.3.0-8

| File | Size in bytes | sha256 |
|---|---|---|
| `wine-cx-26.3.0-8-macos-x86_64.tar.xz` | 234,978,748 | `1976c3310a1f8be2f8e9a46fcb524f77b4316df3d281d94af2c8542bef60456d` |
| `wine-d23b39774528237cafe49f9a073286f854b779c0-source.tar.gz` | 53,981,897 | `7002111d61bbf28e88cc2504080747d27d074907a7e278f6c78cf6cefe09746e` |

The engine is Wine 11.0 from CodeWeavers' CrossOver 26.3 sources with athei's patches, built for
x86_64, so it runs under Rosetta. athei built it and published it as release `cx-26.3.0-8` of
`athei/wine-build`. That repository is now [athei/mach9](https://github.com/athei/mach9), which
ships an arm64 Wine, and on 2026-11-11 the `cx-*` releases were no longer there. The archive here
is byte for byte the file from that release.

The source archive is the Wine tree it was built from:
[athei/wine](https://github.com/athei/wine) at commit `d23b39774528237cafe49f9a073286f854b779c0`,
as GitHub archives that commit. The build recipe is in athei/mach9 at its tag
[`cx-26.3.0-8`](https://github.com/athei/mach9/tree/cx-26.3.0-8) (`build-wine.sh`,
`bundle-wine.sh`).

The apps check the size and the sha256 before they unpack the engine. To check a download
yourself:

```sh
shasum -a 256 wine-cx-26.3.0-8-macos-x86_64.tar.xz
```

## What is in the engine, and its licences

- **Wine** is LGPL-2.1-or-later. Its source is the archive above. CodeWeavers publishes the
  CrossOver sources at <https://www.codeweavers.com/crossover/source>.
- **What athei bundled with it** is in the archive as he published it: libraries in
  `wine/lib/external`, DXMT v0.80, mtld3d, x87sidecar, and Apple's D3DMetal (Game Porting
  Toolkit) with its licence in `wine/lib/external/D3DMetal-License.rtf`. Each part keeps its own
  licence.
- **My changes to Wine are not in this file.** Each app replaces a few of the engine's files with
  its own builds and ships the patches and notices for them. For GW2 on Mac those are in
  [`patches/`](https://github.com/jdrly/gw2-on-mac/tree/main/patches) and
  [`THIRD_PARTY_NOTICES.md`](https://github.com/jdrly/gw2-on-mac/blob/main/THIRD_PARTY_NOTICES.md).
