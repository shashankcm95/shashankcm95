# Shashank C M

I build the boring layer that makes unreliable systems safe to run — transaction
boundaries, verification gates, and recovery paths around things that fail
non-deterministically (LLM agents, distributed event queues, ingest pipelines).

My north star is a specific engineering claim: **you make failures cheap,
observable, and reversible before you make them rare.**  
Most of my work is about containing the blast radius of a bad write, not pretending 
bad writes won't happen. I design autonomous loops to be inherently 
transparent and recoverable, ensuring they scale reliably with project demands.
By treating LLM outputs as untrusted data and wrapping every action in transaction 
boundaries, I build systems that contain the blast radius of inevitable errors 
rather than relying on the hope that models will eventually stop hallucinating.

---

### What I actually build

- **Agent runtimes that treat the LLM as Byzantine.** Both its outputs *and* its
  inputs are untrusted by construction and checked against external ground truth
  by pure-function gates — no model in the blocking path.
- **Effect containment, not output scoring.** Every agent action is wrapped as a
  transaction: isolated worktree → filesystem delta → verify → promote or roll
  back via a reverse-cherry-pick journal. The unit of truth is the validated
  in-scope delta, not the model's prose.
- **Pipelines that are honest about cost and failure.** Pre-call token-budget
  ceilings, content-addressed caching (SHA-256) for multi-user reuse, structured
  JSONL observability with `domain.subject.action` event names, and documented
  known-overrun vectors instead of hidden ones.
- **Full-stack tooling with real session security.** HMAC-signed anonymous
  sessions, double-submit CSRF, Drizzle ORM schema + migrations, pre-flight
  environment gates that fail closed on placeholder config.

---

### Featured Systems

#### [claude-power-loom](https://claude-power-loom.shashank-cm.dev/) — *a deterministic substrate for stochastic agents*

A loom imposes deterministic structure on stochastic threads; this does the same
for agentic coding. It wraps non-deterministic agent execution in transaction
boundaries and pure-function verification gates so an agent's file edits become
**atomic, replayable, and reversible** — the way a DB transaction manager wraps
unreliable writes.

**The honest version of the pitch:** it makes long-horizon agent failures cheap
and recoverable. It does *not* make the model smarter — and the README says so,
out loud, because overclaiming is the failure mode I'm designing against.

- Microkernel in three layers (Kernel / Runtime / Evolution Lab) with an
  inward-pointing dependency rule enforced by lint + per-file layer markers.
- Detects out-of-scope writes *post-hoc* and treats them as policy violations —
  because Claude Code's `isolation: "worktree"` is a git mechanism, not a
  filesystem sandbox, and `Bash` bypasses tool-layer hooks entirely.
- Shipped as a Claude Code plugin across 12 documented phases, each with a
  signed-off close and an activation ledger naming every built-but-dark capability.

`JavaScript · pure-function gates · reverse-cherry-pick rollback · 583 commits, 50 releases`

#### [textbook-to-tutorial](https://textbook-to-tutorial.shashank-cm.dev/) — *local-first ingest + synthesis pipeline*

Converts textbook PDFs into chapter-by-chapter tutorials with quizzes and SRS
flashcards. Your PDF, your machine, your data.

- Hybrid model pipeline: `gpt-4o` for streaming narrative, `gpt-4o-mini` for
  classification, quiz/flashcard generation, and fidelity scoring.
- Ingest chunks content-addressed by `pdf_sha256` so identical sources are
  reused across users without re-paying ingest cost.
- **Documents its own bugs.** The per-tutorial cost cap has a known
  concurrent-stream overrun (unserialized read-write on the budget check); the
  README states the exact blast radius (~1 chapter's cost) and the three deferred
  hardening paths rather than pretending the cap is a hard wall.

`Next.js 14 · TypeScript · Drizzle/SQLite · S3-compatible store · structured JSONL logs`

#### [Portfolio-Website-Builder](https://portfolio-website-builder.shashank-cm.dev/) — *schema-to-site compiler*

Parses structured resume schemas and reconciles them against live GitHub API
state to compile deployment-ready developer portfolios — a build pipeline, not a
template.

#### [AADI (Arrival-Aware Dine In)](https://aadi.shashank-cm.dev/) — *event-driven service orchestration*

Synchronizes distributed event queues and kitchen ticket fire-times against
real-time location telemetry, so the kitchen fires on *predicted arrival*, not
order time.

---

### Connect

**Portfolio:** [shashank-cm.dev](https://shashank-cm.dev/) ·
**LinkedIn:** [in/shashank-c-m](https://www.linkedin.com/in/shashank-c-m) ·
**Email:** shashankcm95@gmail.com
