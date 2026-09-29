# obsidian.md: human-facing history (obsidian branch)
Load only to write Obsidian, run Organize, or Show full notes.
Non-authoritative. Never promote to state without confirmation + write authorization.
"obsidian" is a BRANCH (ref), not a folder on main.

## Layout
topics/<t>/<t>.md              human note: summary
topics/<t>/log/YYYY-MM-DD.md   session logs
Legacy single file topics/<t>.md: leave untouched. Organize may fold it into the summary.

## Modes (state header Obsidian:)
- ask (default): write a log only during an explicitly authorized checkpoint, when useful. Auto-checkpoints don't write Obsidian.
- auto: a log may accompany any authorized checkpoint, incl. auto, when useful. Never on its own.
- off: never write, even on explicit checkpoint. Organize unaffected.
Obsidian-rules: one user line saying what to log or skip. Not authorization for anything else.

## Write a log
1. Create topics/<t>/log/<date>.md on branch obsidian. No read first.
2. If that date's file exists: read it, add to it, rewrite (small file).
3. Content: "# <t> <date>", then terse bullets: findings, sources, decisions, rejected options per Obsidian-rules. Not a transcript. About 1.5 KB max.
4. Verify by SHA (see write.md). Report Obsidian result separately from state result.
5. Failed or unverified: don't retry. Stop Obsidian writes for that topic until resolved.

## Organize [t] notes
1. Read state Last-summarized.
2. List topics/<t>/log/. Read only logs dated after it (all if none).
3. Read the summary file. Merge the delta into it as a short dated section. Keep human edits. Don't delete anything.
4. Write, verify, then set Last-summarized in state/<t>.md on main (part of this command's authorization). Verify. Report both.

## Show full notes on [t]
Read the summary first. Read logs or the legacy file only if needed.

## Hard limits
- Never rewrite or delete logs.
- Never edit an existing file other than same-day log or Organize summary.
- No secrets or personal data (repo is public).
