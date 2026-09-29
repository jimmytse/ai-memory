# SYSTEM.md - Memory Operating Rules

Defines how the AI uses the GitHub repository as long-term memory while keeping normal conversation discussion-first and preventing accidental writes.

Detailed procedures live in the `procedures/` folder. Load only the file needed for the current command.

## 1. Structure

main:
  MEMORY.md
  SYSTEM.md
  index.md
  state/<topic>.md
  procedures/*.md

obsidian:
  topics/<topic>.md
  topics/<topic>.summary.md

- `main` is authoritative AI memory.
- `obsidian` is non-authoritative detailed history/research.
- `state/<topic>.md` is the current authoritative checkpoint for that topic.
- Obsidian history must never silently become authoritative state.
- `projects/` and `inbox/` are retired. Never recreate or depend on them.

## 2. Discussion First

Normal conversation is not automatically memory.

Keep brainstorming, exploration, tentative ideas, rejected alternatives, speculation, and unresolved discussion in chat.

Never convert an AI suggestion into a user decision.

The normal lifecycle is:

Discussion
  → Clarification
  → Confirmed user decision or requirement
  → Is it durable + future-relevant?
      → Yes → Checkpoint proposal (or auto-checkpoint if already on)
      → No  → Stay in chat
  → User authorization (explicit command, explicit confirmation, or standing auto-checkpoint)
  → GitHub write
  → Read-back verification

## 3. Write Authorization

Only the user authorizes memory writes. Authorization takes one of three forms:

1. Explicit command: "Save a checkpoint for [topic]".
2. Explicit confirmation of a checkpoint proposal.
3. Standing authorization: "Auto-checkpoint [topic] on" (see `procedures/auto-checkpoint.md`).

If confirmed, durable, future-relevant information appears and none of the above applies, propose once and briefly:

> Checkpoint-worthy: <one line>. Save?

A qualifying state change is **not** itself permission to write, unless auto-checkpoint is on for that topic.

Context-risk levels are separate from authorization.
- LOW - continue normally.
- MEDIUM - a checkpoint may be useful.
- HIGH - recommend a checkpoint before continuing when practical.

A warning or recommendation never writes memory. Only an authorization above does.

## 4. Procedure Map

| Action | Load this file |
|--------|----------------|
| Checkpoint / Save / Write verification | `procedures/checkpoint.md` |
| Auto-checkpoint on/off behavior | `procedures/auto-checkpoint.md` |
| Obsidian history rules & settings | `procedures/obsidian.md` |
| Any command (Continue, Forget, Organize, etc.) | `procedures/commands.md` |
| Structural / rename / merge / architecture change | `procedures/mmcp.md` |
| Durable-state rules, state schema, contradictions | `procedures/authority.md` |
| Privacy or write failure | `procedures/failure.md` |

## 5. Core Principles

1. Discussion before persistence.
2. Confirmed state before durable memory.
3. Material future relevance before checkpointing.
4. User authorization (explicit command, explicit confirmation, or standing auto-checkpoint) before writing.
5. Current authoritative state over historical transcripts.
6. Minimum sufficient memory.
7. Context-risk warnings never authorize writes.
8. User-controlled checkpoint commands provide explicit control.
9. Never silently convert uncertainty into fact.
10. Never claim persistence without verification.
11. When uncertain, ask rather than guess.
12. Never recreate retired memory structures.