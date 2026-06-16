# Common Workflows

Task-oriented walkthroughs for things you'll actually want to do. For the full flag reference on any command, run `yherda <command> --help` — this page sticks to the common path.

---

## Read your current draft

```sh
yherda ideas use 42
yherda expression list
yherda expression print 4
```

`print` walks the expression's segment tree in reading order and prints the content straight to your terminal — the fastest way to read a draft without exporting a file.

## Export your manuscript

```sh
yherda expression export --expression 4 --format scriv
```

This writes a file in the requested format (defaulting to `<expression-id>.<ext>` in your current directory). Run `yherda expression export --help` to see which formats are currently supported, and pass `--output` to choose your own filename:

```sh
yherda expression export --expression 4 --format scriv --output draft.scrivx
```

## Switch between projects

```sh
yherda ideas list
yherda ideas use 17
```

Switching ideas clears your active person, arc, place, and thing — they're scoped to whichever idea you were just in.

## Build out a character's arc

```sh
yherda person create --name "Detective Marlowe" --idea 42
yherda identity create --name "The Cynic" --person 7
yherda arc create --want "to stop caring" --person 7
yherda beat create --description "He takes the case anyway" --arc 9
yherda beat list --arc 9
```

## Capture research or worldbuilding notes

Idea documents are freeform notes attached to an idea — for anything that doesn't fit the structured story model.

```sh
yherda doc create --idea 42 --title "Worldbuilding notes" --file notes.md
yherda doc list --idea 42
yherda doc show 19
```

You can also pipe content in directly instead of writing a file first:

```sh
echo "The harbor town runs on fish and rumor." | yherda doc create --idea 42 --title "Setting notes"
```

## Check on a project's status

```sh
yherda projects list
yherda projects show 3
```

---

For scripting these into something larger — CI, an editor command, a build step — see [Integrating with Your Tools](integrations.md).
