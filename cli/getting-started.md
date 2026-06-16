# Getting Started with the CLI

The Yherda CLI (`yherda`) brings your ideas, characters, arcs, and beats into the terminal — so you can work on your story alongside whatever else you already use to write: your editor, your build scripts, your notes.

---

## Install

Download the latest release for your platform from the [yherda-cmd releases page](https://github.com/yherda-opensource/yherda-cmd/releases), and put the binary somewhere on your `PATH`.

Confirm it's working:

```sh
yherda --help
```

---

## Log in

```sh
yherda login
```

This opens your browser to authenticate with your Yherda account. Once you approve it, your credentials are stored locally and used automatically by every other command — you only need to do this once per machine.

---

## Pick a workspace

If you belong to more than one workspace, see which ones are available to you:

```sh
yherda workspacelist
```

Then set the active one:

```sh
yherda workspace acme-publishing
```

Everything you do from here runs against that workspace until you switch again.

---

## Set your active idea

Most of what you do day-to-day happens inside a single idea (a project, novel, or story). List your ideas and set one active:

```sh
yherda ideas list
yherda ideas use 42
```

Once an idea is active, commands like `yherda person list` or `yherda place list` work without you having to pass an `--idea` flag every time — and as you `use` a person, arc, place, or thing, the CLI keeps narrowing its sense of "what you're working on" so each subsequent command needs less typing, not more.

---

## Next

- [Core Concepts](concepts.md) — how ideas, persons, arcs, beats, places, and things map onto the CLI's commands
- [Common Workflows](workflows.md) — task-oriented walkthroughs for things you'll actually want to do
- [Integrating with Your Tools](integrations.md) — scripting, piping, and wiring the CLI into your existing setup
