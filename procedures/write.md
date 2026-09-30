# write.md: checkpoint, verify, auto, failure

## Checkpoint (when authorized)
1. Use the state file already read this chat. Re-read only if it wasn't read or may have changed.
2. Build the latest confirmed state. Replace superseded info. Keep uncertainty explicit. Check it against State file format (header, four sections, size) before committing.
3. Results: if the user accepted results this session, or explicitly asked to save an in-progress draft, replace state/<t>.data.md in full, in the format defined in MEMORY.md. Set the state header line Data: state/<t>.data.md. Other unaccepted candidates stay in chat.
4. Update the index.md row only if status or routing changed.
5. Set Last-checkpoint to today's date (platform date if known).
6. Commit state (+ data, index) to main in ONE call; if the tool writes one file per call, use the write order in MEMORY.md.
7. Verify (below).
8. Obsidian: check the topic's Obsidian: mode. Load procedures/obsidian.md only if you will write.
9. Report one line: what was saved + VERIFIED / PENDING / FAILED.

## Verify
- A success response from the write tool is not verification.
- Required steps (do exactly, in order):
  1. List the changed paths and their SHAs (directory listing or equivalent).
  2. Re-read each changed file once.
  3. Confirm content matches what was intended and each state file still has the full header and sections.
- Verification outcomes (use exactly one per changed file):
  - `VERIFIED <path> <short-sha>`
    Full check succeeded: listing returned the path + SHA, re-read matched intended content, and state files still have the complete header + four sections.
  - `PENDING <path> (no-sha | partial-listing)`
    Re-read of the file succeeded and content matches what was intended (including header/sections for state files), but SHA was unavailable or the directory listing was incomplete. Do not invent a SHA.
  - `FAILED — <reason>`
    Content mismatch, inability to re-read, or any other hard failure.
- Report format (first line of the post-write report must be exactly one of these):
  `VERIFIED <path> <short-sha>` for each file
  or
  `PENDING <path> (no-sha | partial-listing)` for each file
  or
  `FAILED — <reason>`
- Match on all changed files → VERIFIED.
- Any PENDING or FAILED → treat Auto-checkpoint for that topic as off until the user explicitly re-enables it. Keep the new information in chat only. Do not treat a PENDING write as authoritative for future sessions until a later VERIFIED write confirms it.
- Unverified or failed write: treat Auto-checkpoint for that topic as off until the user explicitly re-enables it. Keep the new information in chat only.
- Do not auto-retry. Investigate before another write.

## Auto-checkpoint
- Off by default. Only the user command "Auto-checkpoint [t] on/off" changes it, by editing that one header line. Needs an existing state file, else say a checkpoint is needed first. Verify.
- While on: may update state/<t>.md, its Data file, and its index row without asking when the change is confirmed, durable, and future-relevant. Confirmed = user stated it or explicitly accepted an AI proposal. Silence is not acceptance.
- Never covers: new topics, Forget, structural changes, edits to MEMORY.md or procedures, removing unsuperseded info, changes that conflict with current state (ask). Obsidian writes only if Obsidian: auto.
- After each auto write, report one line including the verification result. User correction is the latest statement and replaces the entry at the next checkpoint. Git history is the undo.
- Unverified or failed write: stop auto writes for that topic until the user re-enables Auto-checkpoint.

## Failure
If GitHub access, write, or verification fails: don't claim it saved. Tell the user the checkpoint could not be confirmed. Keep the info in chat. Don't auto-retry. Investigate before another write.