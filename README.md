# CKAD Flashcards & Knowledge Graph

Flashcards and a knowledge graph for [CKAD](https://www.cncf.io/certification/ckad/) exam preparation, derived from the exercises in [dgkanatsios/CKAD-exercises](https://github.com/dgkanatsios/CKAD-exercises).

## Files

- **[knowledge-graph.json](knowledge-graph.json)** — the knowledge graph. Nodes are organized as *category → exercise → leaf task*, where every leaf task is a simple task that can be completed with a single command. Each leaf task references its deduplicated flashcard via `flashcardId` (the same command used across several exercises maps to one card).
- **[flashcards.json](flashcards.json)** — the deduplicated flashcard list. Each card has:
  - `frontText` — a single atomic question (markdown)
  - `backText` — starts with a code block containing the **one-line answer** (a command, a field name, or a short fact), followed by a short explanation and a link to the official Kubernetes docs (markdown)
  - `category` — the CKAD curriculum domain
  - `id` — stable id referenced from the knowledge graph

## Status

| Category | Status |
| --- | --- |
| Core Concepts - 13% | ✅ done (18 exercises, 23 flashcards) |
| Multi-container pods - 10% | ✅ done (2 exercises, 8 new flashcards + 4 reused from Core Concepts) |
| Pod design - 20% | ✅ done (51 exercises, 53 new flashcards + 7 reused from Core Concepts) |
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
> For now deal only with category "Pod design".
>
> Update status in readme.

### Flashcard rules (append to every follow-up prompt)

> Every flashcard must be **atomic** and answerable by typing a **single line of text** into one input field:
>
> - One card = one question = one answer. Never combine alternatives on a card ("e.g. X, or Y", "and also…") — split them into separate cards instead.
> - `backText` must **start with a fenced code block containing exactly the one-line answer**, followed by a short explanation and a link to the official Kubernetes docs. YAML snippets, alternatives and verification commands belong in the explanation, never in the answer block.
> - Pick the answer type by task kind:
>   - imperative task → the single `kubectl ...` command (```` ```bash ````)
>   - YAML-editing task → don't ask for the manifest; ask *which field* achieves it, and the answer is the field name/path (e.g. `spec.initContainers`, `completions`). Show the full YAML example in the explanation.
>   - concept question → a short one-line fact (e.g. "No — it only permits scheduling there").
> - The front must contain every concrete value the answer needs (names, images, labels, numbers) so exactly one answer is correct.
> - Deduplicate across exercises via the knowledge graph's `flashcardId`. Keep existing card ids stable; new cards continue the category's numbering (`cc-`, `mc-`, `pd-`, …).

Expected JSON schema:

```json
[
  {
    "id": "Stable unique id (required)",
    "frontText": "Question (Markdown)",
    "backText": "Answer (Markdown)",
    "category": "Optional category"
  }
]
```
