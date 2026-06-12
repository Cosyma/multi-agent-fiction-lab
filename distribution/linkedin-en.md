# LinkedIn EN article — draft

> Status: **v0.5 draft** · polish + publish when the lab reaches v0.5 distribution-ready milestone (per [`docs/05-roadmap.md`](../docs/05-roadmap.md)).
> Word count target: 300–500 (excl. hashtags).
> Hero image: TBD (architecture sketch from README + lab badge).

---

## Title (choose one at publish time)

- I built a multi-agent lab for collaborative fiction writing. Here's what I learned about putting humans in the loop.
- Why I went the other way from autonomous AI orchestrators
- A PM's notes from running multi-agent workflows on a 100k-word novel

## Body

In the past three months, I've been running an experiment that sits at an unusual intersection: I'm a PM who builds AI agent platforms by day and writes novels by night. Most AI-fiction tools are built by engineers for writers. I built one as a writer working as a PM on my own workflow — and the result is something I think is genuinely different.

The lab is called **multi-agent-fiction-lab**. It's not a writing tool you install. It's a working methodology for AI-augmented long-form fiction, designed around a counterintuitive principle: **humans should be in the loop, by design**.

While the industry races toward autonomous orchestrators (Devin, Operator, you name it), I went the other way. My agents communicate via persistent markdown files. A human — me — is the messenger between sessions. Why? Because creative judgment doesn't decompose cleanly into prompts. Author taste is the irreplaceable variable; the workflow's job is to preserve it.

Three design choices that surprised me along the way:

1. **Two agent teams, not one** — a 4-agent outline-debate team (divergent thinker, sharp critic, taste-forward aesthete, synthesis-without-flattening captain) plus a 5-agent prose-review team (rhythm gate, blocking, voice, forbidden patterns, captain consolidation). One pipeline is the textbook approach. Two teams that talk to each other is what holds long-form together.

2. **Memory as workflow, not infrastructure** — no vector DB, no RAG. Each session gets a hand-curated input package: locked facts, character profiles, the "do-not-debate" list. Slow but correct. Long-form breaks vector retrieval exactly when it matters most.

3. **A craft baseline that precedes the AI** — most AI-fiction projects skip "what does *good* mean to the author" and train on style without surfacing the craft. My lab uses a hand-written novel as the explicit fidelity target for the multi-agent workflow. The two sit in a deliberate progression: baseline → validation.

The lab also documents what makes this design different from LangGraph / AutoGen / CrewAI — they sit at one abstraction layer; mine sits at another (built from primitives, not on top of another framework's abstractions). This asymmetry is something I plan to write up formally for CHI as a case study.

If you build multi-agent systems, work in PM around AI tooling, or care about HCI in AI-assisted creative work, the lab is fully public:

🔗 **https://github.com/Cosyma/multi-agent-fiction-lab**

It ships v0.1 with methodology docs, workflow templates you can clone, two case-study skeletons, 15 logged decisions with rationale, a dual-license setup, and a CHI / arxiv-friendly citation file.

I'm exploring AI PM opportunities at intersection of product + multi-agent systems + creative tooling, especially in markets outside China. If your team is thinking about humans-in-the-loop for AI workflows — let's talk.

---

#multiagent #llm #productmanagement #humanaicollaboration #aiwriting #hci

---

## Publish checklist (when v0.5 lands)

- [ ] Add hero image (architecture sketch + lab badge)
- [ ] Update word count if too long
- [ ] Final pass for tone (LinkedIn audience expects polished but warm)
- [ ] Add specific recent metric if research/ has any (e.g., "100k+ words produced")
- [ ] Tag relevant people (advisor, ex-colleagues with multi-agent expertise)
- [ ] Cross-post to Twitter / X with short thread version

## Variant: 知乎 ZH (待写)

Different tone, more methodological depth (Chinese readers expect detail). To be drafted closer to v0.5.
