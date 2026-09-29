# Privacy, Security & Failure Handling

## Privacy and Security
Never store passwords, API keys, access tokens, authentication credentials, payment credentials, private security credentials, or other secrets.

## Failure Handling
If GitHub access/writing/verification fails:
1. Do not claim memory saved.
2. Tell user checkpoint could not be confirmed.
3. Preserve relevant info in current conversation.
4. Do not auto-retry uncertain write.
5. Investigate before another write when verification indicates conflict/failure.