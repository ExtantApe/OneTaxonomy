<picture><source media="(prefers-color-scheme: dark)" srcset="brand/oneorigin/marks/onetaxonomy-dark.svg"><img src="brand/oneorigin/marks/onetaxonomy-light.svg" alt="" width="96" height="96"></picture>

# OneTaxonomy

A source-available framework for importing, curating, browsing and publishing **scientifically faithful** taxonomic classifications and phylogenetic trees: for developers, and for teachers, museums, researchers and animal keepers who don't write code.

Part of the [OneOrigin suite](https://github.com/ExtantApe/OnePhylogeny/blob/main/docs/oneorigin/README.md): five independent tools, with no subscriptions, that work alone or together. OneTaxonomy is the widest view, followed by [OneLineage](https://github.com/ExtantApe/OneLineage) (coming soon), [OnePhylogeny](https://github.com/ExtantApe/OnePhylogeny), [OnePedigree](https://github.com/ExtantApe/OnePedigree) and [OneFamily](https://github.com/ExtantApe/OneFamily).

> **Status: early alpha.** The five `onetaxonomy-*` packages and the Payload plugin are on npm as `0.1.0-alpha.4`, and the Mac app is 0.2.0 on GitHub Releases. 633 automated tests pass: 249 in the Payload plugin, 132 in the React views, 111 in core, 68 in the Mac app, 63 in the importers and the rest in layout and lessons. The NEXUS and phyloXML readers are tested on hand-written files, not on exports from MrBayes, BEAST or other programs. The plugin has run in the example site on one machine, never on a deployed site or on Postgres. No screen reader has been tried. The Mac app isn't notarized and can't update itself yet. See [limitations](docs/architecture/limitations.md) and [the phase plan](docs/architecture/phase-plan.md).

## Principles

- **Science and display are separate.** Data lives in immutable, checksummed snapshots; views only project it.
- **A classification is not a phylogeny.** Ranks and names are never treated as evidence of common ancestry.
- **Only supported clades are called clades.** Monophyly is `monophyletic`, `not-monophyletic` or `indeterminate`, always relative to a named hypothesis, with reasons and caveats.
- **Missing stays missing.** Unmapped taxa, unresolved polytomies, unrooted trees, partial sampling and unknown status are reported, never guessed.
- **Your sources, your choice.** OneTaxonomy ships adapters for the sources you pick, and no data of its own.

The full rules are in [scientific invariants](docs/architecture/scientific-invariants.md).

## Packages

| Package | What it does | Status |
| --- | --- | --- |
| [`@extantape/onetaxonomy-core`](packages/core) | Records, validation, bounded traversal, MRCA, tri-state monophyly, curated selections, coverage reports, snapshot checksums and diffs, views (actions, undo/redo, filters, highlights, projection), JSON Schema. No dependencies; runs anywhere. | Working |
| [`@extantape/onetaxonomy-import`](packages/import) | Source adapters (CSV/TSV, Darwin Core Archive, JSON, Newick, NEXUS, phyloXML), reconciliation, selective imports, community presets | Working |
| [`@extantape/onetaxonomy-layout`](packages/layout) | Rectangular, phylogram/time (only when valid), radial and sunburst layouts as plain coordinates | Working |
| [`@extantape/onetaxonomy-react`](packages/react) | Server-renderable SVG tree, accessible keyboard outline, explorer (undo/redo, drag, overlays, inspector, clade selector, SVG/PNG/JSON exports), lesson player | Working |
| [`@extantape/onetaxonomy-education`](packages/education) | Lesson decks (scenes, cameras, annotations, reveals) and worksheets with answers computed from the data | Working |
| [`@extantape/payload-plugin-onetaxonomy`](packages/payload) | Payload plugin: sealed snapshots checked by checksum, staged and published, views pinned to them, import jobs that turn source files into staged snapshots, people's own proposals that a curator can accept into a new staged version, a bounded read API (name search, ancestors, descendants, MRCA, coverage, projected views, exports) behind the host's access rules, with optional tenant scope, and admin panels for publishing, import progress and deciding on proposals | Early alpha, on npm: tested on Payload with an in-memory MongoDB and in the example site on one machine, not yet on a deployed site |
| [`apps/studio`](apps/studio) | OneTaxonomy for Mac (Tauri 2): open checklists, Darwin Core Archives, Newick, NEXUS and phyloXML trees and snapshots; browse them; collapse weak branches, add a tree to an open checklist and link its tips to taxa (proposed by exact name, confirmed by you), compare two trees, and reroot or midpoint-root as a new tree; save views and sealed snapshots (never over the file that was opened), and save and open `.onetaxonomy` bundles (a documented ZIP with a manifest and checksums) | 0.2.0 on GitHub Releases. Not notarized, and it can't update itself yet |
| [`apps/payload-example`](apps/payload-example) | A small Payload and Next.js site that uses the plugin: two roles, public pages that draw published views on the server, and proposals that record people by id, with a public handle shown beside it. Runs on your machine with a throwaway in-memory database | An example. Checked over HTTP by its smoke test; nobody has clicked through its admin yet |

## Try it

```bash
pnpm install
pnpm build
pnpm test
pnpm --filter @extantape/onetaxonomy-examples start
```

```js
import { assessTaxon, indexDataset } from '@extantape/onetaxonomy-core'

const data = indexDataset(snapshot)
const result = assessTaxon(data.classification('traditional'), 'c:reptilia', data.phylogeny('archelosauria'))
// { status: 'not-monophyletic', reason: 'missing-descendants', missing: ['t-aves'], hypothesis: { id: 'archelosauria', version: '1' }, … }
```

Curate a selective import from a checklist (see `examples/selective-import.mjs`):

```js
import { csvAdapter, selectiveImport, toSnapshot } from '@extantape/onetaxonomy-import'

const read = await csvAdapter({ source: mySource }).read(csvText)        // Darwin Core column names by default
const full = toSnapshot(read, { id: 'my-checklist', version: '2026-03', createdAt })
const { snapshot, coverage } = selectiveImport(full, {
  id: 'my-selection', title: 'Kept groups', version: '1', classification: full.classifications[0].id,
  roots: [{ concept: turtlesId, policy: { kind: 'rank', ranks: ['species', 'subspecies'] } }],
}, { id: 'curated', version: '1', createdAt })
// snapshot: chosen taxa + ancestor paths only; coverage: what was left out, per root
```

## Install the Mac app

Download the latest `.dmg` from this repository's [Releases](https://github.com/ExtantApe/OneTaxonomy/releases) page (tags `desktop-v*`) and drag OneTaxonomy to Applications. The app isn't notarized, so macOS blocks the first launch. Use either way past the warning:

- **System Settings:** try to open the app once, then go to System Settings > Privacy & Security, scroll down, click **Open Anyway**, and click **Open** when the warning comes back. Apple says to do this only for an app you trust.
- **Terminal:** `xattr -dr com.apple.quarantine "/Applications/OneTaxonomy.app"`

## Documentation

- [Architecture](docs/architecture/architecture.md), [data schema](docs/architecture/data-schema.md), [decisions (ADRs)](docs/architecture/adr/README.md)
- [Phase plan](docs/architecture/phase-plan.md), [backlog](docs/architecture/backlog.md), [limitations](docs/architecture/limitations.md)
- [Fixtures](fixtures/README.md), [releasing](RELEASING.md)

## Citing

If OneTaxonomy helps your research, cite it from `CITATION.cff`. GitHub's **Cite this repository** button reads the same file. There's no DOI yet.

## License

[PolyForm Noncommercial 1.0.0](https://polyformproject.org/licenses/noncommercial/1.0.0) for the software: free for noncommercial use, with attribution; commercial use needs a separate license from EXTANT APE. This license makes OneTaxonomy source-available. It isn't an open source license. Versions published under MIT before the license changed stay under MIT. Data you import keeps its own license; OneTaxonomy records it with every snapshot.
