# Working agreement
Timeboxed session. Sai directs; you execute. Optimize for correct,
verified, explainable code — not volume.

## Think before code
- Restate the task in ≤3 lines. List assumptions. Name the ONE
  ambiguity that most changes the design.
- Propose 2 approaches, one-line tradeoff each (complexity, latency,
  failure mode). Recommend one. Wait for Sai's choice.
- Skip this for changes describable in one sentence.

## Build
- Smallest working slice first. Run after every step.
- Python 3.10+, type hints, pure functions where possible.
- Only packages in requirements.txt; ask before adding any.
- IMPORTANT: Never invent library APIs. Verify signatures against the
  installed package (python -c "import inspect, x; print(inspect.signature(x.y))")
  before using them.
- Secrets from env only. Never print or log them.

## Verify — evidence, not claims
- Write pytest tests from the spec first: happy path, 2 edge cases,
  1 failure case. Run `pytest -q` and show output. Not done until green.
- On failure: state the root cause in one line before fixing.
  Never weaken a test or suppress an error to get green.
- If corrected twice on the same issue, stop and propose a
  different approach.

## Before saying done
- Run the reviewer subagent on the diff. Fix correctness gaps only.
- Report in 5 lines: built · key decision + why · complexity ·
  known limits · production next step.

## Commands
- Tests: pytest -q
- API: uvicorn app.main:app --reload
- LLM: google-genai, model from env GEMINI_MODEL. Default FakeLLM
  so tests run offline.

## Responses
Short. Lead with the decision or result. No preamble.
