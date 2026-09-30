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
9. Report one line: what was saved + VERIFIED / FAILED.

## Verify
- A success response from the write tool is not verification.
- Steps, in order:
  1. Re-read each changed file from main (explicit ref). Do not reuse the write response.
  2. Confirm content matches what was intended, and each state file still has the full header and four sections.
  3. If the tool can list paths, confirm each changed path is present and note its short SHA. Never invent a SHA.
- Outcome, one line per changed file:
  - `VERIFIED <path> <short-sha|no-sha>`: the re-read matched.
  - `FAILED — <reason>`: mismatch, cannot re-read, or any hard failure.
- The first line of the post-write report is these outcome lines.
- Any FAILED: treat Auto-checkpoint for that topic as off until the user explicitly re-enables it. Keep the new information in chat only. Do not auto-retry; investigate before another write.

## Auto-checkpoint
- Off by default. Only the user command "Auto-checkpoint [t] on/off" changes it, by editing that one header line. Needs an existing state file, else say a checkpoint is needed first. Verify.
- While on: may update state/<t>.md, its Data file, and its index row without asking when the change is confirmed, durable, and future-relevant. Confirmed = user stated it or explicitly accepted an AI proposal. Silence is not acceptance.
- Never covers: new topics, Forget, structural changes, edits to MEMORY.md or procedures, removing unsuperseded info, changes that conflict with current state (ask). Obsidian writes only if Obsidian: auto.
- After each auto write, report one line including the verification result. User correction is the latest statement and replaces the entry at the next checkpoint. Git history is the undo.
- Unverified or failed write: stop auto writes for that topic until the user re-enables Auto-checkpoint.

## Failure
If GitHub access or a write fails: don't claim it saved, keep the info in chat, don't auto-retry. Verification failures follow Verify.
