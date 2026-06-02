# PRD: Cadboro Labs — Claude Skills Marketplace (Skills & README Upload)

| | |
|---|---|
| **Status** | Draft |
| **Author** | hello@brandongains.com (Brandon Gains, Cadboro Labs) |
| **Last updated** | 2026-06-02 |
| **Repository** | `brandonsgitstub/cadboro-marketplace` |
| **Marketplace name** | `cadboro-labs` |

---

## 1. Summary

Cadboro Labs ships a **Claude Code plugin marketplace** — a one-command install
path for the Cadboro Labs product-management (PM) toolkit. A user adds the
marketplace once and installs any skill as a plugin. Today the repo holds only a
stub `README.md` and a `LICENSE`. This PRD defines the work to populate it: a
marketplace manifest, an initial catalog of PM skills packaged as plugins, and
the project README that lets users add, install, update, and contribute.

`product-roadmap` is already authored and **live**; the remaining seven skills
are vendored in one at a time.

## 2. Background & Context

Claude Code supports **plugin marketplaces**: git repositories exposing a
catalog of installable plugins. A plugin bundles one or more **skills** (defined
by a `SKILL.md` with YAML frontmatter), and may also include commands, agents,
hooks, and MCP servers. Cadboro Labs already maintains standalone skill repos;
this marketplace is the **curated install path** that vendors each skill into a
plugin folder, while the standalone repos remain for direct download.

Install/usage flow for end users:

```bash
/plugin marketplace add brandonsgitstub/cadboro-marketplace   # add once
/plugin install product-roadmap@cadboro-labs                  # install a skill
/product-roadmap:roadmap-generator                            # invoke (or natural language)
/plugin marketplace update cadboro-labs                        # refresh when new skills land
```

## 3. Goals

- **G1** — Marketplace is installable via
  `/plugin marketplace add brandonsgitstub/cadboro-marketplace` under the name
  `cadboro-labs`.
- **G2** — Vendor the eight-skill catalog as one plugin per skill, each
  validated with `claude plugin validate .`.
- **G3** — Ship the project README (add / install / invoke / update / catalog /
  structure / contribution steps).
- **G4** — Make adding the remaining seven skills a repeatable, documented
  procedure.

### Non-goals

- Hosted web UI, backend, auth, payments, or telemetry — distribution is
  git-based only.
- Replacing the standalone skill repos (they stay as the direct-download source
  of truth).

## 4. Users & Use Cases

| User | Use case |
|------|----------|
| Product manager | Adds the marketplace and installs `product-roadmap` to turn a backlog into a sequenced roadmap in-context. |
| PM team | Standardizes on the Cadboro Labs toolkit via one marketplace add. |
| Contributor / maintainer | Vendors a standalone skill repo into a plugin folder following §7 and validates before pushing. |

## 5. Requirements

### 5.1 Marketplace manifest (G1)

- **R1.1** — Add `.claude-plugin/marketplace.json` at the repo root.
- **R1.2** — Manifest declares marketplace `name: cadboro-labs`, owner
  (Brandon Gains / Cadboro Labs), and a `plugins` array.
- **R1.3** — Set `metadata.pluginRoot` to `./plugins`; each entry's `source` is
  `./<plugin-folder>` (resolved relative to `pluginRoot`; the `./` prefix is
  required by `claude plugin validate`).
- **R1.4** — Each `plugins` entry includes `name`, `source`, `description`,
  `version`, `author`, `homepage`, `repository`, `license`, `keywords`, and
  `category`.

### 5.2 Skills catalog (G2)

- **R2.1** — **Packaging: one plugin per skill.** Each plugin directory contains
  `.claude-plugin/plugin.json`, a `README.md`, and `skills/<skill-name>/SKILL.md`
  (plus `references/` if the source skill has them).
- **R2.2** — The skill directory name MUST match the `name:` in that skill's
  `SKILL.md` frontmatter.
- **R2.3** — `SKILL.md` frontmatter `description` MUST state *what it does* and
  *when to trigger it* (drives model invocation).
- **R2.4** — Plugins are **GPLv3-licensed** (per each `plugin.json`), matching
  the repository `LICENSE`.
- **R2.5** — Every plugin MUST pass `claude plugin validate .` before merge.
- **R2.6** — Catalog (all vendored from `github.com/brandonsgitstub`; plugin
  folder and skill folder differ where the source skill's `name:` differs):

  | Plugin | Skill (`name:`) | Source repo | What it does | Status |
  |--------|------------------|-------------|--------------|--------|
  | `product-roadmap` | `roadmap-generator` | `product-roadmap-skill` | Backlog/prioritization → structured roadmap with sequencing rationale | ✅ Live |
  | `prd-generator` | `prd-generator` | `prd-skill` | Rough ideas → engineering-ready PRDs | ✅ Live |
  | `user-story-generator` | `user-story-generator` | `user-story-skill` | Features → dev-ready user stories with acceptance criteria | ✅ Live |
  | `feature-prioritization` | `feature-prioritization` | `feature-prio-skill` | Backlog → ranked RICE scorecard + brief | ✅ Live |
  | `jtbd-research` | `jtbd-interview-guide` | `jtbd-skill` | Jobs-to-be-Done interview guides + synthesis | ✅ Live |
  | `anti-ai-design` | `frontend-design` | `anti-ai-design-skill` | Distinctive, non-generic frontend interfaces | ✅ Live |
  | `saas-metrics` | `saas-metrics-analyzer` | `saas-metrics-skill` | SaaS metrics → scenario-modeled financial analysis | ✅ Live |
  | `saas-pricing` | `saas-pricing-analyzer` | `saas-pricing-skill` | Subscription data → pricing tier analysis | ✅ Live |

### 5.3 README (G3)

- **R3.1** — Publish the project README with sections: Add the marketplace,
  Install a skill, Invoke, Update, What's in the catalog (table), Repo structure,
  Adding the other seven skills, Checklist, credits.
- **R3.2** — Commands shown verbatim:
  - `/plugin marketplace add brandonsgitstub/cadboro-marketplace`
  - `/plugin install <plugin>@cadboro-labs`
  - `/<plugin>:<skill>` and natural-language invocation
  - `/plugin marketplace update cadboro-labs`
- **R3.3** — The catalog table MUST stay in sync with `marketplace.json`.

### 5.4 Contribution procedure (G4)

- **R4.1** — Document the per-skill add procedure (§7) in the README, including
  the `plugin.json` and `marketplace.json` entry templates and the validate step.
- **R4.2** — Document the **no-vendoring alternative**: reshape each standalone
  repo into plugin layout and point the marketplace entry at a `github` source
  instead of a relative path (avoids duplication, at the cost of reshaping repos).

## 6. Repository Layout

```
cadboro-marketplace/
├── .claude-plugin/
│   └── marketplace.json          # the catalog — one entry per plugin
├── plugins/                       # metadata.pluginRoot = ./plugins
│   └── product-roadmap/
│       ├── .claude-plugin/plugin.json
│       ├── README.md
│       └── skills/
│           └── roadmap-generator/ # dir name = SKILL.md `name:`
│               ├── SKILL.md
│               └── references/
├── docs/
│   └── PRD.md
├── README.md
└── LICENSE
```

## 7. Procedure: Adding a Skill (per plugin)

1. **Create folders** under `plugins/<plugin-name>/`: `.claude-plugin/plugin.json`
   and `skills/<skill-name>/SKILL.md` (+ `references/` if any). `<skill-name>`
   must match the `name:` in the skill's `SKILL.md` frontmatter.
2. **Add `plugin.json`** (name, description, version, author, homepage,
   repository, GPLv3 license).
3. **Add a `marketplace.json` entry** in the `plugins` array (`source` = folder
   name, plus keywords + `category: product-management`).
4. **Validate**: `claude plugin validate .`
5. Update the README catalog table and checklist.

## 8. Success Metrics

- `/plugin marketplace add` succeeds with no manifest errors; marketplace
  resolves as `cadboro-labs`.
- Every listed plugin installs and its skill is invocable (slash command and
  natural language).
- `claude plugin validate .` passes for the repo.
- A new user can go from zero → installed skill using only the README.

## 9. Milestones

1. **M1 ✅** — Manifest (`cadboro-labs`, `pluginRoot: ./plugins`) landed; all
   eight skills vendored from their `brandonsgitstub` source repos.
2. **M2 ✅** — Project README published (catalog table + contribution procedure).
3. **M3 ✅** — `claude plugin validate .` passes; skill folders match each
   `SKILL.md` `name:`; all JSON valid.
4. **M4** — Review and merge the PR; tag a release.

## 10. Decisions (resolved)

- **Packaging** → one plugin per skill.
- **Marketplace name** → `cadboro-labs`; `pluginRoot` → `./plugins`.
- **Plugin license** → GPLv3, matching the repository `LICENSE` (every
  `plugin.json` declares `"license": "GPL-3.0-or-later"`).
- **Source strategy** → vendor skills into plugin folders (curated install
  path), with the `github`-source approach documented as an alternative.
