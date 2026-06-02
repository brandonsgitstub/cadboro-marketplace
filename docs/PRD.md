# PRD: Cadboro Marketplace — Skills & README Upload

| | |
|---|---|
| **Status** | Draft |
| **Author** | hello@brandongains.com |
| **Last updated** | 2026-06-02 |
| **Repository** | `brandonsgitstub/cadboro-marketplace` |

---

## 1. Summary

Cadboro Marketplace is a **Claude Code plugin marketplace** focused on product
management. Today the repository contains only a stub `README.md` and a
`LICENSE`. This PRD defines the work required to turn it into a functional,
installable marketplace by (a) uploading an initial set of product-management
skills packaged as Claude Code plugins and (b) authoring a README that lets
users discover, install, and use them.

## 2. Background & Context

Claude Code supports **plugin marketplaces**: git repositories that expose a
catalog of installable plugins. A user adds the marketplace once and can then
install any plugin from it. A plugin may bundle **skills** (model-invoked
capabilities defined by a `SKILL.md`), as well as slash commands, subagents,
hooks, and MCP servers.

Cadboro's niche is **product management** — PRD authoring, roadmap planning,
user-story generation, competitive analysis, and similar workflows. The
marketplace makes these reusable across any repo a PM works in.

## 3. Goals

- **G1** — Establish the canonical marketplace manifest so the repo is
  installable via `/plugin marketplace add brandonsgitstub/cadboro-marketplace`.
- **G2** — Ship an initial catalog of product-management skills, each correctly
  structured and validated.
- **G3** — Provide a README that explains what the marketplace is, how to add
  it, how to install plugins, and how to contribute.
- **G4** — Make contribution repeatable: document the directory layout and
  skill authoring conventions so new skills can be added consistently.

### Non-goals

- Building a hosted web UI or backend — distribution is git-based only.
- Authentication, payments, or telemetry.
- Publishing to any registry outside of this GitHub repo.

## 4. Users & Use Cases

| User | Use case |
|------|----------|
| Product manager | Adds the marketplace and installs the `prd-writer` skill to draft PRDs in-context. |
| PM team lead | Standardizes the team on a shared set of PM skills via one marketplace add. |
| Contributor | Adds a new skill following the documented layout and opens a PR. |

## 5. Requirements

### 5.1 Marketplace manifest (G1)

- **R1.1** — Add `.claude-plugin/marketplace.json` at the repo root.
- **R1.2** — Manifest MUST include a marketplace `name`, `owner`, and a
  `plugins` array listing each plugin with `name`, `source`, and `description`.
- **R1.3** — Plugin `source` paths MUST resolve to directories within this repo.

### 5.2 Skills catalog (G2)

- **R2.1** — Each skill lives under a plugin directory and is defined by a
  `SKILL.md` containing YAML frontmatter with `name` and `description`, plus the
  skill body/instructions.
- **R2.2** — The `description` MUST clearly state *what the skill does* and
  *when to trigger it*, since this drives model invocation.
- **R2.3** — Initial catalog (proposed — to be confirmed in §8):
  - `prd-writer` — draft and refine product requirements documents.
  - `roadmap-planner` — build and prioritize product roadmaps.
  - `user-story-generator` — turn requirements into user stories with acceptance criteria.
  - `competitive-analysis` — structure competitor research and feature comparisons.
- **R2.4** — Each plugin SHOULD include a `plugin.json` manifest with name,
  version, and description.
- **R2.5** — Skills MUST be validated (frontmatter parses, paths resolve, and a
  test install succeeds) before merge.

### 5.3 README (G3)

- **R3.1** — Replace the stub README with sections: Overview, What's inside,
  Installation, Using a skill, Available skills (table), Contributing, License.
- **R3.2** — Installation section MUST show the exact commands:
  - `/plugin marketplace add brandonsgitstub/cadboro-marketplace`
  - `/plugin install <plugin-name>@cadboro-marketplace`
- **R3.3** — The available-skills table MUST stay in sync with the manifest.

### 5.4 Contribution docs (G4)

- **R4.1** — Document the directory layout and the steps to add a new skill
  (either in the README or a `CONTRIBUTING.md`).

## 6. Proposed Repository Layout

```
cadboro-marketplace/
├── .claude-plugin/
│   └── marketplace.json          # marketplace catalog
├── plugins/
│   ├── prd-writer/
│   │   ├── .claude-plugin/plugin.json
│   │   └── skills/prd-writer/SKILL.md
│   ├── roadmap-planner/
│   │   └── ...
│   └── ...
├── docs/
│   └── PRD.md
├── README.md
└── LICENSE
```

## 7. Success Metrics

- Marketplace adds cleanly with no manifest errors.
- Every listed plugin installs and its skill is invocable in a session.
- README enables a new user to go from zero to an installed skill without
  outside help.

## 8. Open Questions

- **Q1** — Is the §5.2 initial skill list correct, or should it match a
  specific set defined in the prior session?
- **Q2** — Should skills be packaged as one plugin per skill, or grouped into a
  single `cadboro-pm` plugin bundling all skills?
- **Q3** — Is GPLv3 (current `LICENSE`) the intended license for distributed
  skills, or should it be more permissive (e.g., MIT)?

## 9. Milestones

1. **M1** — Approve this PRD (resolve open questions).
2. **M2** — Add marketplace manifest + first skill (`prd-writer`); verify install.
3. **M3** — Add remaining skills from the agreed catalog.
4. **M4** — Finalize README and contribution docs.
