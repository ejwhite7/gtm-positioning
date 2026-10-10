# Marketing Positioning Workshop by GrowthCast

A guided product marketing workshop for Claude Code (and pi). It takes you from customer evidence to positioning and copy, saving one reviewable document per stage:

0. **Evidence and research** (optional): parse your documents, read the links you submit, and search the web for customer language, competitor claims, and market signals.
1. **Jobs-to-be-Done analysis** (`jobs-to-be-done-analysis` skill): core jobs, functional, emotional and social dimensions, forces of progress, true competition, and opportunities.
2. **Positioning statement exercise** (`positioning-statement` skill): competitive alternatives, unique attributes, value, ICP candidates, market category, and a positioning statement per ICP.
3. **ICP product marketing guidance** (`product-marketing-context` skill) for the feature and ICP you choose.
4. **Ad or website copy** (`website-and-ad-copywriter` skill) from a guided brief: copy type, page or platform, funnel stage, angle, conversion action, and constraints.

Every claim traces back to evidence. The skills never invent customers, quotes, metrics, or proof, and they label hypotheses.

Prefer a browser? The hosted version runs at [growthcast.app/resources/positioning-wizard](https://growthcast.app/resources/positioning-wizard).

## Install in Claude Code

```text
/plugin marketplace add ejwhite7/marketing-positioning-workshop
/plugin install marketing-positioning-workshop@growthcast
```

## Use

| Command | What it does |
|---|---|
| `/marketing-positioning-workshop:workshop` | Run the workshop in the terminal. Add a product and feature, or `next`, `status`, or `copy`. |
| `/marketing-positioning-workshop:studio` | Open the local studio: a GrowthCast-branded screen for each stage. |

Outputs land in `output/positioning-workshop/<product-feature>/`, plus a shared `.claude/product-marketing-context.md`. Run state lives in `state.json` in the run folder, so you can resume later.

For web research the workshop uses the Firecrawl skills when they are installed, and Claude Code's WebSearch and WebFetch otherwise.

## Studio

The studio is a local web app at http://127.0.0.1:4710.

- **Projects:** a **workspace** works for any company or product, with no codebase needed; the studio keeps its files in `~/.positioning-workshop/workspaces/`. Or **use a folder** (macOS shows a folder picker).
- **00 Evidence:** upload documents (PDF, DOCX, PPTX, XLSX, CSV, TXT, MD, VTT, up to 50 MB each), add links tagged by type, and write a research brief (review sites, communities, competitors, trends, searches, standard or deep).
- **01 to 04:** fill in each brief and press **Queue for Claude**. Your next message in Claude Code, even just "go", carries the request; the document appears in the studio as soon as Claude saves it.
- **Revisions:** queue revision notes against any saved document.

A `UserPromptSubmit` hook (`hooks/studio-context.mjs`) hands a queued request to Claude once. The server listens on 127.0.0.1 only and reads files only inside each registered project's `output/positioning-workshop/` folder and `.claude/product-marketing-context.md`.

## pi

```bash
pi install git:github.com/ejwhite7/marketing-positioning-workshop
```

Then run `/positioning-workshop` (`next`, `copy`, `status`, `cancel`). pi asks to continue when each stage's file is saved, shows progress in the status bar, and writes `state.json` so pi runs also appear in the studio.

## Layout

```text
.claude-plugin/   Claude Code plugin and marketplace manifests
commands/         workshop and studio commands
hooks/            hands queued studio requests to Claude
skills/           the four skills
studio/           local studio server and UI
extensions/       pi extension
package.json      pi package manifest
```

## Credits

Built by [GrowthCast](https://growthcast.app), GTM Engineering for growth. The studio bundles the Manrope and DM Mono typefaces, both licensed under the SIL Open Font License 1.1.
