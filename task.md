# Daily AI Update Task

You are generating a daily AI digest. Follow the steps below exactly: first collect broadly, then reason and re-rank, then write the report.

Save the final report to `reports/YYYY-MM-DD.md` (use today's actual date). Create the `reports/` directory if it doesn't exist.

---

## Reader interest profile

Use this profile as the scoring lens at every re-ranking step.

**Strong signal — ask these questions:**
- Does this change how a practitioner thinks about building or running agent systems? (new architectures, new patterns, things that break existing assumptions)
- Does this change how a practitioner thinks about training models — makes it cheaper, faster, more data-efficient, or reveals something surprising about how models learn? The specific technique doesn't matter; what matters is whether a senior ML engineer would update their mental model after reading it.
- Does this show how a real team shipped or operates an AI system in production? (case studies, post-mortems, engineering decisions with tradeoffs explained)
- Does this offer a credible, well-reasoned perspective on where LLMs or agents are heading — from someone who builds, not just opines?
- Does this benchmark or eval reveal something genuinely surprising about model capabilities or failure modes?

**Recently engaged with (use as positive exemplars):**
Mem0 (persistent memory layer for agents), RAGFlow (end-to-end RAG system), on-policy distillation papers, Hugging Face Hub weekly CI/CD blog (AI infra in practice), Andrej Karpathy's talk on the loopy/agentic era of AI.

**Did not engage with (use as negative exemplars):**
Vibe-Trading (AI trading bot), video-use (video editing via agents), strix (AI pen-testing tool).

**Weak signal (deprioritize unless it passes the questions above):**
- Demos, product announcements, or launch posts with no technical substance
- Beginner tutorials or "intro to X" content
- Pure business/funding news
- Repos or papers that apply AI to a narrow vertical without generalizable insight

---

## Step 1 — Collect (broad, exhaustive)

Do all four fetches in parallel. Collect more than you need — you will filter in Step 2.

### 1a. Trending GitHub Repositories
Search: `github trending repositories AI today` and `site:github.com trending artificial intelligence`
- Collect 15–20 candidates with recent star momentum (not just high total stars)
- Note the domain for each: agents / RAG / LLM infra / training / diffusion / vision / other

### 1b. Trending arXiv Papers
Search: `arxiv cs.AI cs.LG cs.CL new papers today` and check `https://huggingface.co/papers` for community-upvoted papers
- Collect 10–15 candidates
- Note the core contribution type: new method / benchmark / survey / analysis

### 1c. Blog Posts and Articles
Check recent posts (last 3–5 days) from these sources:
- Simon Willison's blog (simonwillison.net)
- Latent Space (latent.space)
- Interconnects by Nathan Lambert (newsletter.interconnects.ai)
- Import AI by Jack Clark (importai.substack.com)
- Hugging Face Blog (huggingface.co/blog)
- Google DeepMind Blog (deepmind.google/blog)
- Sebastian Raschka's newsletter (magazine.sebastianraschka.com)
- The Batch by deeplearning.ai (deeplearning.ai/the-batch)

### 1d. YouTube Videos
Check for videos published in the last 7 days, starting with these channels as candidates (not a mandatory list):
- Andrej Karpathy (youtube.com/@AndrejKarpathy)
- AI Explained (youtube.com/@aiexplained-official)
- Yannic Kilcher (youtube.com/c/YannicKilcher)
- AI Engineer / ai.engineer (youtube.com/@aiDotEngineer)
- 3Blue1Brown (youtube.com/c/3blue1brown)
- Two Minute Papers (youtube.com/@TwoMinutePapers)

Verify the actual upload date before including anything — don't assume a channel is active or describe old content as "recent." If a listed channel hasn't posted anything new in the lookback window, drop it. Don't stretch a stale upload to fill the section or invent a plausible-sounding recent date. Instead, search for other high-signal videos/talks published in the window (any channel, including ones not listed above) that others are visibly engaging with, and use those. It's fine for this section to end up with fewer than 5 items if that's genuinely all that's out there.

---

## Step 2 — Reason and re-rank (do this explicitly before writing)

For each section, output a brief internal ranking before writing the final section. Format:

```
[RANKING — <Section Name>]
Candidates considered: <count>
Scoring against interest profile:
- <Item>: <score 1-5> — <one-line reason>
- ...
Top 5 selected: <list>
```

Scoring criteria:
- 5: Directly in the interest profile sweet spot (agents, RAG, training, infra in practice)
- 4: Tangentially relevant with high practitioner value
- 3: Interesting but off-profile or too general
- 2: Weak signal, beginner-level, or hype-driven
- 1: Not relevant

Only carry forward items scoring 3 or above, then take the top 5.

---

## Step 3 — Write the report

Use only the top 5 from each section. Format each item with three lines:

```
**<Name/Title>** — <link>
<One sentence: what it is.>
*Why it matters for practitioners:* <One sentence on the concrete implication for someone building agents or LLM systems.>
```

Always name the specific title of the piece you're recommending, even if you can't find its direct URL. Prefer linking straight to the specific repo/paper/article/video; if you can't find that direct link, it's fine to fall back to the homepage/section page as the link — just make sure the title itself is specific enough that the reader can search for it or navigate to it from there.

Report structure:

```markdown
# Daily AI Update — YYYY-MM-DD

## Trending GitHub Repositories
...

## Trending Papers
...

## Blog Posts & Articles
...

## YouTube
...

---
*Generated by daily-ai-update routine*
```

Save to: `/Users/meetparekh/Code/daily-ai-update/reports/YYYY-MM-DD.md`
