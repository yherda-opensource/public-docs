# Integrating with Your Tools

The CLI is built to slot into whatever you're already using — not to be its own island. A few ways people plug it into their existing setup.

---

## Scriptable output

Every command supports `--json`, which gives you raw, structured output instead of the formatted table:

```sh
yherda ideas list --json
yherda expression print 4 --json
```

That makes it straightforward to pipe Yherda data into other tools — feed it to `jq`, write a small script that backs up your expressions on a schedule, or generate a status report across all your active projects.

```sh
yherda projects list --json | jq '.[] | select(.status == "active")'
```

## Editor and build integration

Because every command is a normal CLI invocation with predictable exit codes, you can wire it into:

- A build step that exports your manuscript every time you push to a branch
- An editor task/keybinding that runs `yherda expression print` against your current draft
- A pre-commit hook that backs up an idea document before you touch it

There's nothing special required on Yherda's end — it's the same interface you'd use by hand, just called from somewhere else.

## Reading from stdin and files

Commands that take longer text content — like idea documents — read from a file or from stdin, so they compose naturally with whatever's already producing that text:

```sh
yherda doc create --idea 42 --title "Outline" --file outline.md
pandoc outline.docx -t markdown | yherda doc create --idea 42 --title "Outline"
```

## Non-interactive by design

`login` is the one command that needs a browser. Everything else runs entirely from flags and stored context, with no interactive prompts — which is what makes it safe to drop into a script or automation in the first place.

---

A small note for the curious: because every command is scriptable with consistent `--json` output and clean exit codes, the CLI also happens to work well as an integration point for AI coding agents that want to read or modify your project directly. That's a side effect of building a good CLI, not the point of it — but if that's relevant to your workflow, it's there.
