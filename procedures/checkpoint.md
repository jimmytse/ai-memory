# Checkpoint Procedure & Write Verification

## Checkpoint Procedure

When a checkpoint is authorized:

1. Read the current `state/<topic>.md` (if it exists).
2. Determine the latest confirmed state. Replace superseded information; do not accumulate a transcript. Preserve uncertainty explicitly.
3. Soft ceiling ≈ 250 words. Condense if needed.
4. Update `index.md` only if status, routing, or last-updated meaningfully changed.
5. Obsidian: follow the topic’s `Obsidian:` setting and `Obsidian-rules:` (see `procedures/obsidian.md`). Append only when useful detail would otherwise be lost.
6. Write the required files once.
7. Read back the exact target file(s) and verify the intended content.
8. Report briefly: what was saved + verification status (VERIFIED / PENDING_VERIFICATION / FAILED).

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