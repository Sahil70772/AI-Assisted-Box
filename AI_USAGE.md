# AI Usage  (TEMPLATE – replace every section with YOUR real experience)

> Be honest. The reviewers want to see your own judgement, not a polished story.

## Tools used
- (e.g. Claude, ChatGPT, Cursor, Copilot – and what each was used for)

## Prompts I gave
1. (paste your real prompts here)

## Output I accepted
- (what you kept as-is and why)

## Output I rejected or modified
- (what you changed and why)

## Mistakes the AI made
- (real bugs/wrong assumptions you found. Example from this scaffold: a first test contained the
  meaningless assertion `assertTrue(x is False or True)` that can never fail – it was caught on review
  and replaced with real assertions. Also, an initial settings edit silently did nothing because
  Django generates double quotes, so `packing` wasn't in INSTALLED_APPS until noticed. Only keep
  these if they are true for YOUR process; add your own.)

## How I verified the final code
- (tests you ran, manual API calls, hand-calculated cases, edge cases you tried)
