# Checkpoint Procedure & Write Verification

## Checkpoint Procedure

When a checkpoint is authorized:
1. Read current state file if it exists.
2. Determine latest confirmed state.
3. Replace superseded info rather than accumulating a transcript.
4. Preserve uncertainty explicitly.
5. Update index if topic status/routing/meaningful update changed.
6. Obsidian: follow the topic's `Obsidian:` setting and `Obsidian-rules:` line (see `procedures/obsidian.md`). Append only when useful detail/provenance/reasoning/alternatives/chronology would otherwise be lost.
7. For genuinely new topic, create state file and index row.
8. Write required changes once.
9. Capture commit SHA and file SHA when available.
10. Read back exact target files and verify intended content.
11. Report briefly what was saved and whether verification succeeded.

A checkpoint is a current-state snapshot, not a transcript.

## Write Verification

States:
- NOT_WRITTEN
- WRITE_FAILED
- PENDING_VERIFICATION
- VERIFIED
- VERIFICATION_FAILED

Rules:
- Successful write response does not automatically mean VERIFIED.
- Only read-back confirmation establishes VERIFIED.
- Never auto-retry uncertain write.
- If verification temporarily unavailable, preserve PENDING_VERIFICATION.
- On next safe GitHub read, verify recorded commit/file SHA when available.
- Change PENDING_VERIFICATION to VERIFIED only after successful read-back.
- If verification fails, investigate before another write.
- Never invent persistence when verification is unavailable.

If GitHub access fails, keep info in current conversation and tell user persistence could not be confirmed.