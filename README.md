## Blake Hallisey

Senior Product Manager, AI systems. Eight years across cloud, enterprise
infrastructure, security and AI, at Sephora, Olympix, Dell and Google Cloud, and
a software engineer before that. I write the evals, ship the agents, and own the
call on what is ready for production and what is not.

Most of what I build is private, because it runs my own work. What is public is
here, and it is mostly one thing.

### Six tools for when an agent works and nobody is watching

I ran a coding agent against a real repo overnight, every night, for weeks. Each
of these exists because something went wrong and a note in a document turned out
not to be a control.

| | |
|---|---|
| [curfew](https://github.com/blakehallisey-arch/curfew) | Write-time policy for an unattended agent. Decides what it may write, run and merge, by rule, before the call happens. |
| [breaker](https://github.com/blakehallisey-arch/breaker) | Stops a session that is spinning, spreading across files, looping, or inventing a build nobody asked for. |
| [shipgate](https://github.com/blakehallisey-arch/shipgate) | Refuses a merge until the checks this particular diff needs have actually run. |
| [nightwatch](https://github.com/blakehallisey-arch/nightwatch) | The run rail. A queue, a window, a spend lid, two tiers, and a log that reads git instead of believing the rail. |
| [draftdiff](https://github.com/blakehallisey-arch/draftdiff) | Learns your voice from the edits you make to a draft before you send it. |
| [ledger](https://github.com/blakehallisey-arch/ledger) | Gives stateless subagents a memory of what you actually did with their advice. |

The thread running through all six: **a prompt is a request, and code is a
rule.** Every time the fix was "write it down more clearly," it failed again.
Every time the fix was a hook, it held.

Four of them are the same night at different layers. `nightwatch` picks the work
and holds the window and the lid, `curfew` says what that work may touch,
`breaker` notices when it stops resembling the ask, and `shipgate` refuses to let
it out until it was checked. The other two are about what the loop learns.

Standard library only. No shared dependencies, no imports between them, no
network calls, no telemetry, no accounts. MIT, all six.

If you only open one, open [curfew](https://github.com/blakehallisey-arch/curfew).
The section called "Tiers, and the one idea worth stealing" is the whole thesis in
four paragraphs: the thing that proposes the work is not the thing that
authorizes it.

None of them is a sandbox. A hook lives in the same trust domain as the agent it
watches. They stop an agent taking the shortest path to finishing its job. They
do not stop an attacker. For that, use a container.

### Live

- **[blakehallisey.com](https://blakehallisey.com)** is a portfolio you talk to.
  Ask it something and it answers from my actual work, and it never invents a
  project it cannot point at.
- **[How I use AI](https://blakehallisey.com/how-i-use-ai)** is the long version
  of the paragraph above, including what the six tools came out of.
- **[Uptake](https://uptake-six.vercel.app)** is a daily AI learning feed that
  rebuilds itself at 6am. The gate on it withholds the day's cards until I have
  done the work I am avoiding.

### Also public

Three builds about scoping and governing enterprise agents, kept up because the
arguments still hold:
[first-rung](https://github.com/blakehallisey-arch/first-rung) on why build order is
the strategy,
[agent-blueprint-builder](https://github.com/blakehallisey-arch/agent-blueprint-builder)
for scoping an agent out of a workflow, and
[governed-agent-demo](https://github.com/blakehallisey-arch/governed-agent-demo),
where you ask a question, watch the receipts cross three systems, then ask it again as
someone else and meet a wall.

The case study that goes with them is live at
[compounding-order.vercel.app](https://compounding-order.vercel.app).
