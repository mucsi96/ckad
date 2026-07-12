# CKAD Flashcard Generator

Generates deduplicated flashcards for CKAD exam preparation from
[dgkanatsios/CKAD-exercises](https://github.com/dgkanatsios/CKAD-exercises),
by first modeling each domain as a knowledge graph and then deriving one
flashcard per single-command leaf task.

## Layout

- `mindmaps/` — per-category knowledge graphs (`category → topic → leaf task`).
- `flashcards/` — per-category flashcard JSON derived from the graph leaf nodes.

Each flashcard is `{ front, back, category }`, where `back` contains the answer
command, a short description, and a link to the official Kubernetes docs.

## Status

- [x] Core Concepts (13%)
- [ ] Multi-container pods (10%)
- [ ] Pod design (20%)
- [ ] Configuration (18%)
- [ ] Observability (18%)
- [ ] Services and networking (13%)
- [ ] State persistence (8%)
- [ ] Helm
- [ ] Custom Resource Definitions

## Prompt (for follow-up and reference)

> Please checkout and read then whole repo https://github.com/dgkanatsios/CKAD-exercises.
>
> Build a knowledge graph with different categories, exercises as nodes. As end nodes there should be simple tasks which can be completed using single command.
>
> Based on completed mind graphs leaf nodes build a deduplicated list of flashcards for CKAD exam  preparation.
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
> For now deal only with category "Core Concepts"
