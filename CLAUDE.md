# Design Taste System

This is a personal design taste feedback loop. `design-taste.md` is a living document that evolves as new examples are analyzed.

## Auto-apply

For any design review, UI critique, or aesthetic suggestion — read `design-taste.md` first to load the taste framework before responding.

## Workflow

1. Drop screenshots into `examples/bad-ui/`, `examples/good-ui/`, or `examples/best-ui/`
2. Run `/taste-update` — Claude visually analyzes new images and updates `design-taste.md`
3. Run `/taste-review` from any project to apply the taste framework to its UI

## Available commands

- `/taste-update` — scan new example images, extract patterns, update `design-taste.md`
- `/taste-review` — apply taste framework to a project's UI design
