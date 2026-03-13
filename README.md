# design-taste

A self-improving design taste system for Claude Code. Drop screenshots → run a command → your taste skill evolves.

## What this is

`SKILL.md` is a living design framework that grows smarter as you feed it examples. The more screenshots you add — good, bad, and exceptional — the more precisely Claude can critique and improve UI design.

The system uses Claude Code's native command system. No Python, no external dependencies. Just screenshots and Claude.

## How it works

```
examples/bad-ui/    ← screenshots of generic, vibe-coded designs
examples/good-ui/   ← screenshots of solid, distinctive designs
examples/best-ui/   ← screenshots of exceptional, award-worthy designs
```

1. Drop screenshots into the appropriate folder
2. Run `/taste-update` in Claude Code — Claude visually analyzes each image, extracts colors/typography/layout patterns, and updates `SKILL.md`
3. Review `analysis_cache/update-summary-latest.md`
4. Deploy: `cp versions/SKILL-vX.X.X.md SKILL.md`
5. Commit and push

## Setup

### 1. Clone the repo

```bash
git clone https://github.com/YOUR_USERNAME/design-taste.git ~/design-taste
cd ~/design-taste
```

### 2. Open in Claude Code

```bash
claude .
```

The `CLAUDE.md` file tells Claude to auto-load `SKILL.md` for any design work within this repo.

### 3. Install commands globally (for use in other projects)

To use `/taste-review` from any project on your machine:

```bash
# Copy commands to global Claude commands folder
cp .claude/commands/taste-update.md ~/.claude/commands/
cp .claude/commands/taste-review.md ~/.claude/commands/
```

Then edit `~/.claude/commands/taste-review.md` — find the line that reads `SKILL.md` and update it to your absolute path:

```
Read ~/design-taste/SKILL.md to load the full design taste criteria...
```

## Usage

### Update the skill with new examples

```bash
# 1. Drop screenshots into the right folder
cp ~/Downloads/nice-site.png examples/best-ui/
cp ~/Downloads/generic-saas.png examples/bad-ui/

# 2. Open Claude Code and run
/taste-update
```

Claude will visually analyze each new image, write a `.json` analysis file next to it, update `SKILL.md` with extracted patterns, and create a versioned snapshot.

### Review a project's design

From any project directory in Claude Code:

```bash
/taste-review
```

Claude loads `SKILL.md`, audits every section of the UI, scores it across five dimensions, and produces a prioritized transformation roadmap with working code.

## Versioning

Version bumps are automatic based on how many new examples you add:

| Examples added | Version change |
|---|---|
| 1–5 | patch (1.0.0 → 1.0.1) |
| 6–15 | minor (1.0.0 → 1.1.0) |
| 16+ | major (1.0.0 → 2.0.0) |

All versions are saved in `versions/` so you can diff and track how your taste evolves.

## Philosophy

Earth tones over purple gradients. Editorial layouts over centered landing pages. Serif type over all-sans. Data as design over decoration. Calm over urgent.

The full criteria live in `SKILL.md` — read it to understand what this system considers good taste, and update it by feeding it more examples.

## Forking for your own taste

This repo is a starting point. Fork it, feed it your own examples, and let `SKILL.md` evolve to reflect *your* aesthetic sensibility — not anyone else's.

```bash
# Weekly routine
cp ~/Screenshots/design-*.png examples/best-ui/
# Open Claude Code → /taste-update → review → commit
git add . && git commit -m "Week N batch"
```

## Files

```
design-taste/
├── SKILL.md                          ← the active taste framework (deploy target)
├── CLAUDE.md                         ← auto-loads SKILL.md for design work
├── .claude/commands/
│   ├── taste-update.md               ← /taste-update command
│   └── taste-review.md               ← /taste-review command
├── examples/
│   ├── bad-ui/                       ← generic/vibe-coded designs
│   ├── good-ui/                      ← solid, distinctive designs
│   └── best-ui/                      ← exceptional, award-worthy designs
├── versions/                         ← versioned SKILL.md snapshots
└── analysis_cache/
    ├── processed_files.json          ← deduplication cache (never re-processes)
    ├── update-summary-latest.md      ← last update summary
    └── changelog-vX.X.X.md          ← per-version changelogs
```
