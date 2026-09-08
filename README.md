# kyron-live

Live video for Kyron.

**There is no system here yet, and that is deliberate.** Live is the one part
of Kyron where the wrong early choice costs real money every month rather than
a refactor, so the decision comes before the code.

Read [`docs/DECISION.md`](docs/DECISION.md) first. It costs the options against
each other with worked numbers, recommends one, and lists the four questions
that need a human before anything is built.

The short version:

- **Broadcast or interactive** decides the vendor, the cost and the client.
  Answer it first; everything else follows.
- Cloudflare Stream charges **per delivered minute regardless of resolution**;
  LiveKit charges **per gigabyte**. At 100 concurrent viewers that is roughly
  $189/month against $288 plus a tier — and the gap widens with every step up
  in quality.
- Self-hosting an SFU looks cheap if you only price the bandwidth. It is the
  part of Kyron that breaks the one-machine assumption holding everywhere else.
- The hardest problem is not cost. **Live video cannot be pre-moderated**, and
  that needs a plan before launch rather than after an incident.

A finished stream is an ordinary video file, so it lands in the media pipeline
the main repo already has: stored, poster cut, re-encoded on a queue.
