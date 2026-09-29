# admin.md: new topic, forget, structural change

## New topic
Only for a genuinely durable topic, with authorization (command or confirmed proposal). Auto-checkpoint does not cover it.
Topic slug rules (required):
- Convert the human name to lowercase ASCII.
- Replace spaces and any non-alphanumeric character with a single hyphen.
- Collapse consecutive hyphens; trim leading/trailing hyphens.
- Result must be 2–40 characters. If the result is empty or invalid, ask once for a valid name and stop.
Example: “IHSG Stocks” → `ihsg-stocks`
1. Create state/<t>.md with confirmed state and default header:
   Auto-checkpoint: off
   Obsidian: ask
   Obsidian-rules: 
   Last-checkpoint: none
   Last-summarized: none
2. Add index.md row.
3. No other files; the Data file state/<t>.data.md is created later, at the first accepted results.
4. Commit state + index to main in ONE call.
5. Verify (see procedures/write.md).
6. Obsidian per mode (load procedures/obsidian.md only if writing).
7. Report one line: what was created + VERIFIED / PENDING / FAILED.
If the create command also requests research, lists, or results:
- Capture only the goal and constraints in Status / Key decisions / Next step.
- Do not produce or invent any concrete results during topic creation.
- After the topic is verified, treat the research request as the Next step. Present candidates for acceptance; only accepted items may later enter the Data file.


Obsidian header mapping:
- Default remains Obsidian: ask, Obsidian-rules: (empty).
- If the user states a clear preference (“only when I ask for offline note”, “never”, “always log”, etc.), set the mode and one-line rules accordingly.
- Ambiguous preference → leave defaults and note the ambiguity in Open questions.
## Forget [t]
Confirm first. One commit on main:
- Delete state/<t>.md and state/<t>.data.md if present.
- Remove the index.md row.
Leave obsidian and Git history unless the user explicitly asks to delete them too.
Verify the paths are gone (listing + SHA check). Don't recreate without a new authorized checkpoint.
Report: Forgotten + VERIFIED / FAILED.

## Structural change
Merge, split, rename/move, or retire a topic; change a topic's meaning or routing; edit MEMORY.md or procedures.
Only after the user authorizes the underlying change. No new write permission. No unrelated writes.
1. List affected state files, Data files, and obsidian paths.
2. Inspect the obsidian side (listing) before writing.
3. Preserve history. Never rewrite old history to look current. Renames/moves keep content and stay discoverable.
4. Make an obsidian summary only if it helps navigation or provenance.
5. Update index.md and state files for changed routing, status, or meaning. Set Last-checkpoint on any modified state file. One commit on main.
6. Put what changed and why in the commit message. No separate log file.
7. Verify main and (if touched) obsidian paths by SHA/listing. Report briefly.
Missing obsidian path: don't invent history; note the absence in the commit message when useful.