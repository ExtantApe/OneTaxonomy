<picture><source media="(prefers-color-scheme: dark)" srcset="marks/oneorigin-dark.svg"><img src="marks/oneorigin-light.svg" alt="" width="96" height="96"></picture>

# The OneOrigin suite

**Good tools for understanding where animals come from, without a subscription.**

OneOrigin is a suite of five independent tools from EXTANT APE. Each does one job and works on its own. Use one or several, in whatever combination fits your work. They run from the widest view to the closest:

| Tool | The question it answers | Today |
| --- | --- | --- |
| [OneTaxonomy](https://github.com/ExtantApe/OneTaxonomy) | What do sources claim about how life is organized, and how do we browse it? | Early alpha: npm packages, a Payload plugin and a Mac app |
| [OneLineage](https://github.com/ExtantApe/OneLineage) | How do today's lineages branch from a shared origin? | Coming soon |
| [OnePhylogeny](https://github.com/ExtantApe/OnePhylogeny) | Given DNA, what does the evidence support, and where does this sample fit? | Early alpha: npm packages, a Payload plugin, a command line and a Mac app |
| [OnePedigree](https://github.com/ExtantApe/OnePedigree) | How is this individual related to its known relatives? | Early alpha: npm packages, a Payload plugin and a Mac app |
| [OneFamily](https://github.com/ExtantApe/OneFamily) | Given my DNA matches, how might we be related? | Early: tested on made-up families only, and not released yet |

Every one of them is early. Each repo's README opens with a status note that says what has been tested and what hasn't.

## Why this exists

Too much good work now sits behind a monthly charge. Researchers, keepers, teachers and small conservation groups shouldn't have to rent the tools they rely on, or lose their own work when a payment stops.

So the OneOrigin tools are built differently.

## What we commit to

- **No subscriptions.** The OneOrigin tools don't charge a recurring fee to use them.
- **No account needed.** The Mac apps run on your computer. They use the internet only when you ask for public data or check for updates.
- **Your files stay yours.** Everything is saved as plain, documented files you can open without us. If we vanished tomorrow, your work would still be readable.
- **Your source files aren't touched.** Your extra information lives beside them.
- **The code is open to read and improve.** Anyone can read, change and share it for noncommercial use, with attribution, under [PolyForm Noncommercial](https://polyformproject.org/licenses/noncommercial/1.0.0). A business that wants to use it commercially can ask for a separate license. This license makes the code source-available. It isn't an open source license.
- **Honesty over polish.** The tools say what they don't know and what a result can't tell you. Unknown stays unknown.

These commitments cover the tools. Services that have real ongoing costs, such as lab testing, are separate and priced as what they are.

## Separately or together

No tool needs another. Connections are optional, and they use plain files or a small optional package.

| You use | What you get | Today |
| --- | --- | --- |
| **OneTaxonomy alone** | Curated classifications and trees, with views and lessons | npm packages, a Payload plugin and a Mac app |
| **OnePhylogeny alone** | Fetch records, build reference panels and test samples | npm packages, a Payload plugin, a command line and a Mac app |
| **OnePedigree alone** | Pedigrees for any species, with GEDCOM, CSV and JSON files | npm packages, a Payload plugin and a Mac app |
| **OneFamily alone** | Group your DNA matches, then weigh possible family trees with odds | Built and tested on made-up families; not released |
| **OnePhylogeny + OneTaxonomy** | Trees you build become hypotheses you can check and browse | The export package works. OneTaxonomy's Mac app can't open an exported record yet |
| **OnePhylogeny + OnePedigree** | Check DNA results against recorded maternal lines, and report conflicts for review | The check package works. Neither Mac app uses it yet |
| **OneFamily + OnePedigree** | Family trees drawn with OnePedigree's views | Inside OneFamily's Mac app, on made-up data |
| **OnePedigree + OneTaxonomy** | Pedigrees tied to a curated species list | Planned |
| **OneLineage with the others** | From a species, to its lineages, to a named animal's family and DNA | Coming soon |
| **On a website** | Payload plugins and React views on your own site | OneTaxonomy, OnePhylogeny and OnePedigree, published as alphas |

## One suite, each its own

The tools share a look, a way of behaving and a set of beliefs. Each keeps its own purpose, layout and color. Together they follow the [suite guidelines](guidelines.md), which turn this page into specific rules. The marks are in [marks/](marks/). The Mac apps still use their earlier icons.

## Names

- **OneOrigin** is the name of the suite. It isn't a package or a product you install.
- Each tool keeps its own name and repo, and has or will have its own app.
- Packages stay under each project's scope, such as `@extantape/onephylogeny-core`.
