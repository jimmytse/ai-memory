# admin.md: new topic, forget, structural change

## New topic
Only for a genuinely durable topic, with authorization (command or confirmed proposal). Auto-checkpoint does not cover it.
1. Create state/<t>.md (confirmed state, default header). 2. Add index.md row. 3. No other files; the Data file state/<t>.data.md is created later, at the first accepted results. 4. Obsidian per mode.

## Forget [t]
Confirm first. One commit on main: delete state/<t>.md and state/<t>.data.md if present, remove index row. Leave obsidian and Git history unless the user explicitly asks to delete them too. Verify the paths are gone. Don't recreate without a new authorized checkpoint.

## Structural change
Merge, split, rename/move, or retire a topic; change a topic's meaning or routing; edit MEMORY.md or procedures.
Only after the user authorizes the underlying change. No new write permission. No unrelated writes.
1. List affected state files, Data files, and obsidian paths.
2. Inspect the obsidian side (listing) before writing.
3. Preserve history. Never rewrite old history to look current. Renames/moves keep content and stay discoverable.
4. Make an obsidian summary only if it helps navigation or provenance.
5. Update index.md and state files for changed routing, status, or meaning. One commit on main.
6. Put what changed and why in the commit message. No separate log file.
7. Verify main and obsidian paths by SHA/listing. Report briefly.
Missing obsidian path: don't invent history; note the absence in the commit message when useful.

## Retired
projects/ and inbox/: never recreate.
