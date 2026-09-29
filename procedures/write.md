# write.md: checkpoint, verify, auto, failure

## Checkpoint (when authorized)
1. Use the state file already read this chat. Re-read only if it wasn't read or may have changed.
2. Build the latest confirmed state. Replace superseded info. Keep uncertainty explicit.
3. Update the index.md row only if status, routing, or last-updated changed.
4. Commit state (+ index) to main in ONE call.
5. Verify (below).
6. Obsidian: check the topic's Obsidian: mode. Load procedures/obsidian.md only if you will write.
7. Report one line: what was saved + VERIFIED / PENDING / FAILED.

## Verify
- A success response is not verification.
- Compare each committed blob SHA against a directory listing of main. No content read-back.
- Match: VERIFIED. Mismatch or unavailable: PENDING or FAILED. Don't auto-retry; investigate before another write.
- If the listing gives no SHAs, read the changed file back once.

## Auto-checkpoint
- Off by default. Only the user command "Auto-checkpoint [t] on/off" changes it, by editing that one header line. Needs an existing state file, else say a checkpoint is needed first. Verify.
- While on: may update state/<t>.md and its index row without asking when the change is confirmed, durable, and future-relevant. Confirmed = user stated it or explicitly accepted an AI proposal. Silence is not acceptance.
- Never covers: new topics, Forget, structural changes, edits to MEMORY.md or procedures, removing unsuperseded info, changes that conflict with current state (ask). Obsidian writes only if Obsidian: auto.
- After each auto write, report one line. User correction is the latest statement and replaces the entry at the next checkpoint. Git history is the undo.
- Unverified or failed write: stop auto writes for that topic until resolved.

## Failure
If GitHub access, write, or verification fails: don't claim it saved. Tell the user the checkpoint couldn't be confirmed. Keep the info in chat. Don't auto-retry. Investigate before another write.
