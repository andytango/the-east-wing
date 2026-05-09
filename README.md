# 🇺🇸 The East Wing

> **Heads up:** this is a humour project. This plugin generates parody content
> that imitates the *style* of a well-known public-figure's social media posts. They
> are for personal amusement only and are not affiliated with, endorsed by, or
> representative of any real person, party, or organisation.

## Plugins

| Plugin | What it does |
| --- | --- |
| `trump-tweets-output-style` | Adds hyperbolic, self-aggrandising "Post" commentary alongside Claude's normal coding work. Every post ends with `MAKE CODING GREAT AGAIN!` |

## Install

Inside Claude Code:

```text
/plugin marketplace add andytango/the-east-wing
/plugin install trump-tweets-output-style@the-east-wing
```

Or, if you've cloned the repo locally:

```text
/plugin marketplace add ~/git/github/the-east-wing
/plugin install trump-tweets-output-style@the-east-wing
```

To turn it off later: `/plugin disable trump-tweets-output-style@the-east-wing`.

## How it works

Each plugin is a thin `SessionStart` hook that injects an `additionalContext`
string into the session's system prompt — the same mechanism Anthropic's
[`explanatory-output-style`](https://github.com/anthropics/claude-code/tree/main/plugins/explanatory-output-style)
plugin uses. The personality lives entirely in `hooks-handlers/session-start.sh`
inside each plugin's directory.

Layout:

```text
the-east-wing/
├── .claude-plugin/marketplace.json   # marketplace manifest
└── plugins/
    └── trump-tweets/
        ├── .claude-plugin/plugin.json
        ├── hooks/hooks.json          # registers the SessionStart hook
        └── hooks-handlers/session-start.sh
```

## Costs

These plugins extend the default system prompt and encourage longer, more
flavourful responses, so they will use more tokens than a plain session. Don't
install them on workflows where token cost matters.

## License

MIT.
