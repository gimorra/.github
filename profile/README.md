<p align="center">
  <a href="https://github.com/gimorra"><img alt="Gimorra" src="https://avatars.githubusercontent.com/u/322532366?s=200&v=4" height="140" /></a>
  <br />
  <strong>Gimorra — autonomous offensive security agent</strong>
  <br />
  <em>recon → scan → propose PoC → deterministically prove → report</em>
</p>

---

## What this is

`gimorra` is an autonomous offensive-security platform. Point it at an **authorized** target with a
goal and a scope, and it runs the whole engagement end to end — a human in the loop only where
blast radius requires it.

> [!WARNING]
> Gimorra only operates against targets you are authorized to test.
> No authorization artifact, no active operation — enforced in code, not policy.

## The thesis

Autonomous offense is usually gated by a human on every action, because a mistake reaches out and
touches something it shouldn't. Gimorra's bet is that **autonomy is bought with deterministic
guardrails**: non-AI controls make a run incapable of harming the target, so supervision becomes a
dial rather than a per-action crutch.

- **A non-destructive deterministic validator.** Non-AI code re-proves every finding with the
  least-invasive action. The agent proposes; code disposes. No self-certified bugs.
- **Auto-cleanup and a kill switch.** Anything changed is reverted; a recorded stop makes queued
  work unclaimable and refuses any proof commit after it.
- **A scope guard underneath both.** Deny-wins, ambiguity blocks, evaluated per tool call before
  the autonomy policy is consulted.

The safety and validator packages have **no dependency on the agent, model, or network stack** —
they are pure functions. If the model is prompt-injected, they still hold. That property is the
whole point.

One more half of the design is the operator's: gimorra runs real tools on the machine it was
started on, so the boundary around a run is the environment you started it in — a VM, a disposable
box, a container you launched.

## Getting started

```bash
gimorra doctor                                  # runtimes, toolchain, SDK auth
gimorra scan acme.test                          # auto-scope, auto-authorize, run everything
gimorra scan acme.test -p "focus on IDOR and broken access control"
gimorra findings <engagement-id> -f md          # the report
```

Everything is also runnable as a single container image with the full recon and offensive toolchain
baked in, which doubles as the recommended sandbox.

Want the deterministic half only — no agent, no tokens?

```bash
gimorra scan 'http://127.0.0.1:3000/item?id=1' --no-agent
```

## Around here

- **[gimorra](https://github.com/gimorra/gimorra)** — the platform: CLI, worker, gateway, the
  deterministic spine, and the declarative arsenal of skills, personas and validators.
- The scan engine ships separately as [vigolium](https://github.com/vigolium) and is installed
  alongside gimorra.

## Contact

Built with ♥ by [@j3ssie](https://github.com/j3ssie) · [@j3ssie on X](https://x.com/j3ssie)

Released under the MIT license.
