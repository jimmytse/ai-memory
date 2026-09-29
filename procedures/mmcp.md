# Major Memory Change Protocol (MMCP)

A **major memory change** is a structural or semantic change that can make existing memory harder to find, misroute a topic, or leave the authoritative and historical sides out of alignment.

## Triggers

Run MMCP when any of these occurs:
- two or more state topics are merged;
- one state topic is split into multiple topics;
- a state topic is renamed or moved;
- a state topic is deleted or retired;
- a topic's meaning, routing, or ownership changes materially;
- `MEMORY.md`, `SYSTEM.md`, or the memory architecture changes.

Routine updates inside an existing topic do **not** trigger MMCP unless they also change structure or meaning.

## Procedure

After the user authorizes the underlying memory change:

1. Identify every affected authoritative state file and corresponding Obsidian topic/history.
2. Inspect the Obsidian side before writing.
3. Preserve historical material; never rewrite old history merely to make it appear current.
4. Reorganize Obsidian paths when needed so historical material remains discoverable under the new topic structure. Renames/moves must preserve the historical content.
5. Create or update an Obsidian summary only when it materially improves navigation or preserves useful provenance.
6. Update `index.md` and authoritative state files when routing, status, or topic meaning changed.
7. Record the structural change as a concise maintenance milestone in `state/memory-system-redesign.md`.
8. Verify both the authoritative `main` paths and all affected Obsidian paths by read-back.
9. Report the change and verification status briefly.

## Authorization and safety

MMCP does not create a new permission to write. The user's authorization for the underlying memory change authorizes the required MMCP maintenance for that same change. Do not use MMCP to make unrelated memory writes.

If an affected Obsidian history path does not exist, do not invent history. Record only that the path was absent when useful for the maintenance milestone.