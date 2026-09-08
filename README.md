# forecaster — a Model Meets Reality starter

**says what will happen, by when**

A *model* here is not neural weights. It is a short document stating premises, a
mechanism, at least one falsifiable consequence with a date, and a deletion
clause naming when you would retire it. This repo is a starting point for one of
the eleven kinds.

## What makes this kind a kind

**Premise shape**

```
By <date>, <observable> will <state>, because <mechanism>.
```

**What would prove it wrong:** the date arrives with the observable in another state





**Tier: PROVEN** — a discipline worked out against real instances.

## Agentic reasoning

Models here are not static documents. The engine runs each one against live
sources on a schedule: it searches, reads what it finds, and writes dated claims
that later get graded. Every citation is validated against what the search
actually returned, so a fabricated source is dropped rather than recorded.

What the pass asks is specific to this kind:

> Observe the entity and state what you EXPECT to see by the resolution date. Every claim needs an observable a stranger could check and a date. A claim with no date is not a forecast.

And when a claim comes due:

> The date has arrived. Did the stated observable reach the stated state? Grade hit / partial / miss / unresolvable, and say which.

## Start

```bash
git clone https://github.com/shaelsrv/ModelMeetsReality my-copilot   # the engine (anonymous clone, no gh CLI needed)
cd my-copilot
rm -rf .git               # detach: a clone still points at the engine's remote
git config --global --add safe.directory "$PWD"   # if git says "dubious ownership"
git init && git add -A && git commit -m "main instance"
cp .env.example .env      # set OPENROUTER_API_KEY, or LLM_BACKEND=claude-code

python -m suites.new_model my-model --kind forecaster \
    --title "My Model" --domain "what it models, in a sentence"

# then EDIT ../my-model/watch.json -- the scaffold placeholder is refused
# and write real premises into MODEL.md; the scaffold is empty by design
python -m suites.model_watch --repo my-model --predict
```

The engine refuses to run against the scaffold placeholder, on purpose: running
it as-is spends a web search and returns either nothing or claims about a target
you did not choose.

`rm -rf .git` matters: a fresh clone is already a git repo whose `origin` is the
engine, so without it the `git init` is a no-op and a later `git push` would send
your private premises to the engine repo. Your main should be yours — one initial
commit, no remote.

## Engine

Pinned to `56a33c1` of [ModelMeetsReality](https://github.com/shaelsrv/ModelMeetsReality). The engine
is shared across all eleven kinds; only the discipline above differs. Update
deliberately rather than tracking latest.
