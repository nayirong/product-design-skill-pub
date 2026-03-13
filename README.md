# design-taste

A self-improving design taste system for Claude Code. Drop screenshots → run a command → your taste skill evolves. Install once and Claude auto-applies it to every design it generates.

## What this is

`design-taste.md` is a living design framework that grows smarter as you feed it examples. The more screenshots you add — good, bad, and exceptional — the more precisely Claude can critique and improve UI design.

The system uses Claude Code's native command and Skills system. No Python, no external dependencies. Just screenshots and Claude.

## How it works

```
examples/bad-ui/    ← screenshots of generic, vibe-coded designs
examples/good-ui/   ← screenshots of solid, distinctive designs
examples/best-ui/   ← screenshots of exceptional, award-worthy designs
```

1. Drop screenshots into the appropriate folder
2. Run `/taste-update` — Claude visually analyzes each image and updates `design-taste.md`
3. Review `analysis_cache/update-summary-latest.md`
4. Deploy: `cp versions/design-taste-vX.X.X.md design-taste.md`
5. Commit and push

## Setup

### 1. Clone the repo

```bash
git clone https://github.com/YOUR_USERNAME/design-taste.git ~/design-taste
```

### 2. Install the Skill (auto-invocation globally)

This is the key step. Once installed, Claude automatically applies the taste framework whenever it generates UI or you ask for design feedback — in **any** project on your machine.

1. Open Claude Code
2. Go to **Customize > Skills**
3. Install `taste-review-skill.zip` from this repo
4. Open the installed `Skill.md` and update the `design-taste.md` path to your local absolute path:
   ```
   Read ~/design-taste/design-taste.md to load the full design taste criteria...
   ```

### 3. Open in Claude Code

```bash
claude ~/design-taste
```

The `CLAUDE.md` file tells Claude to auto-load `design-taste.md` for any design work within this repo.

### 4. Install commands globally (optional — for explicit `/taste-review`)

```bash
cp .claude/commands/taste-update.md ~/.claude/commands/
cp .claude/commands/taste-review.md ~/.claude/commands/
```

Update the `design-taste.md` reference in `~/.claude/commands/taste-review.md` to your absolute path.

## Usage

### Auto-triggered (after Skill install)

Just work on any UI project. When Claude generates a component, creates styles, or you mention design — the taste framework is automatically applied.

### Update the skill with new examples

```bash
# Drop screenshots into the right folder
cp ~/Downloads/nice-site.png examples/best-ui/
cp ~/Downloads/generic-saas.png examples/bad-ui/

# Open Claude Code and run
/taste-update
```

Claude visually analyzes each new image, writes a `.json` analysis next to it, updates `design-taste.md`, and creates a versioned snapshot.

### Manually trigger a review

From any project directory in Claude Code:

```bash
/taste-review
```

## Versioning

| Examples added | Version change |
|---|---|
| 1–5 | patch (1.0.0 → 1.0.1) |
| 6–15 | minor (1.0.0 → 1.1.0) |
| 16+ | major (1.0.0 → 2.0.0) |

All versions are saved in `versions/` so you can diff and track how your taste evolves.

## Philosophy

Earth tones over purple gradients. Editorial layouts over centered landing pages. Serif type over all-sans. Data as design over decoration. Calm over urgent.

The full criteria live in `design-taste.md` — read it to understand what this system considers good taste, and update it by feeding it more examples.

## Forking for your own taste

Fork it, feed it your own examples, and let `design-taste.md` evolve to reflect *your* aesthetic — not anyone else's.

```bash
# Weekly routine
cp ~/Screenshots/design-*.png examples/best-ui/
# Open Claude Code → /taste-update → review → commit
git add . && git commit -m "Week N batch"
```

## Files

```
design-taste/
├── design-taste.md                          ← the active taste framework (deploy target)
├── CLAUDE.md                         ← auto-loads design-taste.md for design work in this repo
├── taste-review-skill/
│   └── Skill.md                      ← official Skill definition (auto-invocation)
├── taste-review-skill.zip            ← install via Customize > Skills
├── .claude/commands/
│   ├── taste-update.md               ← /taste-update command
│   └── taste-review.md               ← /taste-review command (explicit)
├── examples/
│   ├── bad-ui/
│   ├── good-ui/
│   └── best-ui/
├── versions/                         ← versioned design-taste.md snapshots
└── analysis_cache/
    ├── processed_files.json
    ├── update-summary-latest.md
    └── changelog-vX.X.X.md
```
