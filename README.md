# Cartridge Shelf

The public submissions inbox for cartridges to be added to the [cartridges.machinefabric.com](https://cartridges.machinefabric.com/manifest) registry.

If you've built a cartridge and want it included in the canonical manifest that MachineFabric ships with by default, propose it here. We curate every submission by hand. Once we've reviewed a repo and added it to the live manifest, it moves from `submitted.txt` to `accepted.txt`.

## Submitting a cartridge

[**Submit a Cartridge**](../../issues/new?template=add-cartridge.yml)

Anyone can propose a cartridge. There is no quality threshold — as long as the repo meets the requirements below, we'll review it. If you're unsure about any of the requirements, send the submission anyway and we'll work through them together.

### Requirements

- The cartridge repository must be **publicly accessible** (no private repos, no auth-required endpoints).
- The repository URL must include the protocol (usually `https://`) and the `.git` extension, e.g. `https://github.com/<owner>/<name>.git`.
- The repository must have at least one release tagged as a [semantic version](https://semver.org).
- The cartridge must build, install, and run on macOS using the standard MachineFabric cartridge tooling.
- The cartridge must declare valid cap URNs as defined by [`capfab`](https://github.com/machinefabric/capfab) — every cap URN it serves must parse via the `capdag` library and the `in` and `out` tags must reference media URNs that exist in the standard registry, or be defined alongside the cartridge submission via [capfab](https://github.com/machinefabric/capfab/issues/new?template=add-media-spec.yml).
- All repository content must comply with our [code of conduct](#code-of-conduct).

## Removing a cartridge

You can request that an already-accepted cartridge be removed from the registry by opening a [Remove Cartridge](../../issues/new?template=remove-cartridge.yml) issue. Removals are weighed against impact — accepted cartridges are referenced by deployed installs and by users' saved machine notations, so we'll work with you on a deprecation path before pulling anything in active use.

## How this repository works

```
cartridge-shelf/
├── submitted.txt    URLs awaiting maintainer review (one per line, alphabetical)
├── accepted.txt     URLs that have been reviewed and added to the canonical manifest
└── README.md
```

The flow:

1. You open an [Add Cartridge](../../issues/new?template=add-cartridge.yml) issue with one or more repository URLs.
2. A maintainer opens a PR that appends the URL(s) to `submitted.txt`. The issue stays open while we review.
3. Once we've validated the cartridge and added it to the [canonical manifest](https://cartridges.machinefabric.com/manifest), the URL moves from `submitted.txt` to `accepted.txt` and we close the issue with a link to the live entry.
4. If we decide not to accept a submission, we close the issue with a reason. The closed issue is the record — there is no separate rejected list.

There is no automation. Every step happens by hand. PRs that change `submitted.txt` or `accepted.txt` should be opened only by maintainers in response to a corresponding issue.

## Other channels

- [Report a security vulnerability](../../issues/new?template=report-vulnerability.yml) — for issues affecting an accepted cartridge.
- [Bug, feature request, or question](../../issues/new?template=bug-or-feature.yml) — for everything that isn't a cartridge submission.

## Code of conduct

Be kind. Be useful. Don't submit cartridges that exfiltrate data, mine cryptocurrency, or do anything else a reasonable person would object to running on their machine. We will refuse submissions that breach this in obvious ways and remove accepted cartridges that turn out to.

## Part of MachineFabric

Cartridge Shelf is part of the [MachineFabric](https://machinefabric.com) project. The canonical cartridge registry it feeds lives at [cartridges.machinefabric.com](https://cartridges.machinefabric.com/manifest).
