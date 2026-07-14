# CKAD Flashcards & Knowledge Graph

Flashcards and a knowledge graph for [CKAD](https://www.cncf.io/certification/ckad/) exam preparation, derived from the exercises in [dgkanatsios/CKAD-exercises](https://github.com/dgkanatsios/CKAD-exercises).

## Files

- **[knowledge-graph.json](knowledge-graph.json)** — the knowledge graph. Nodes are organized as *category → exercise → leaf task*, where every leaf task is a simple task that can be completed with a single command. Each leaf task references its deduplicated flashcard via `flashcardId` (the same command used across several exercises maps to one card).
- **[flashcards.json](flashcards.json)** — the deduplicated flashcard list. Each card has:
  - `front` — task description (markdown)
  - `back` — the command to execute, a short description, and a link to the official Kubernetes docs (markdown)
  - `category` — the CKAD curriculum domain
  - `id` — stable id referenced from the knowledge graph

## Status

| Category | Status |
| --- | --- |
| Core Concepts - 13% | ✅ done (18 exercises, 22 flashcards) |
| Multi-container pods - 10% | ✅ done (2 exercises, 4 new flashcards + 4 reused from Core Concepts) |
| Pod design - 20% | ⬜ todo |
| Configuration - 18% | ⬜ todo |
| Observability - 18% | ⬜ todo |
| Services and networking - 13% | ⬜ todo |
| State persistence - 8% | ⬜ todo |
| helm | ⬜ todo |
| Custom Resource Definitions | ⬜ todo |

## Original prompt (for reference and follow up)

> Please checkout and read then whole repo https://github.com/dgkanatsios/CKAD-exercises.
>
> Build a knowledge graph with different categories, exercises as nodes. As end nodes there should be simple tasks which can be completed using single command.
>
> Based on completed mind graphs leaf nodes build a deduplicated list of flashcards for CKAD exam preparation.
>
> The JSON should be a list of flash cards. where each card should contain.
>
> markdown front text, markdown back text and category (Core Concepts - 13%
> Multi-container pods - 10%
> Pod design - 20%
> Configuration - 18%
> Observability - 18%
> Services and networking - 13%
> State persistence - 8%
> helm
> Custom Resource Definitions). On the back I want to see the answer command I should execute. Description and some Link to Kubernetes official docs.
>
> For now deal only with category "Multi-container pods".
>
> Update status in readme.

Expected JSON schema:

```json
[
  {
    "frontText": "Question (Markdown)",
    "backText": "Answer (Markdown)",
    "category": "Optional category"
  }
]
```
