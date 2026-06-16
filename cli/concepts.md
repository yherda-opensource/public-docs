# Core Concepts, in CLI Terms

The CLI mirrors the same model you work with everywhere else in Yherda. If you already know the platform, this is mostly a map of which command touches which piece. If you're new, this is the shape of the whole thing.

---

## Idea

The top-level container for a story. Everything below belongs to one idea.

```sh
yherda ideas list
yherda ideas create --name "The Long Way Home"
yherda ideas use 42
```

## Person

A role in your story — the slot a character fills. A person can hold one or more identities over the course of the story.

```sh
yherda person list
yherda person create --name "Detective Marlowe" --idea 42
```

## Identity

A belief system a person holds — the lens they see through at a given point in the story. Identities can shift over an arc.

```sh
yherda identity list --person 7
yherda identity create --name "The Skeptic" --person 7
```

See [Belief Systems](../concepts/belief-systems.md) for the underlying model.

## Arc

A person's want, and the sequence of beats that pursue it.

```sh
yherda arc list --person 7
yherda arc create --want "to be believed" --person 7
```

## Beat

A single story moment within an arc — one step toward, or away from, the want.

```sh
yherda beat list --arc 9
yherda beat create --description "She finds the letter" --arc 9
```

## Place and Setting

A place is a location in your story; a setting is a specific configuration of that place at a point in time — how it looks or feels.

```sh
yherda place list --idea 42
yherda setting list --place 12
```

## Thing and Disposition

A thing is a notable object; its disposition is its state at a given point in the story.

```sh
yherda thing list --idea 42
yherda disposition list --thing 5
```

## Expression and Format

An expression is your idea rendered into a specific template — the manuscript, screenplay, or one-sheet you actually read and export. A format defines the structure that template uses.

```sh
yherda format list
yherda expression list --idea 42
yherda expression export --expression 4 --format scriv
```

See [Common Workflows](workflows.md) for what you'll actually do with these day to day.

## Project

The dashboard view of a piece of writing in progress — links a project template to its content template, with phase status.

```sh
yherda projects list
```

---

## Active context

Most commands accept an explicit ID flag (`--idea 42`), but you rarely need to. As you `use` an idea, person, arc, place, or thing, the CLI remembers it in a `.yherda` file in your current directory and uses it as the default for anything that needs it. Switching idea, person, or place clears whatever was scoped underneath it — you won't end up with a stale arc pointing at the wrong person.
