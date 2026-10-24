# Architektura: SLM + LLM + LangGraph

Rozwiązanie łączy dwa modele:

- **SLM seq2seq** (własny, POC): wątek mailowy → JSON ze zdarzeniami kalendarzowymi. Szybki, lokalny, wyspecjalizowany.
- **Duży LLM**: mózg decyzyjny, który planuje, korzysta z narzędzi i dokumentów firmy, a następnie przygotowuje wynik dla człowieka.

Całość orkiestruje **LangGraph**. Zlecenia przychodzą z chatu (człowiek) albo przez FastAPI (maszyna). SLM, IMAP, kalendarz i inne systemy są dostępne jako narzędzia MCP, a dokumenty firmy przez RAG.

## Dokumenty

| # | Dokument | Zawartość |
|---|---|---|
| 00 | [SLM](diagrams/00-slm.md) | model seq2seq: wyniki, kontrakt input/output, przykład, zakres POC |
| 01 | [Overview](diagrams/01-overview.md) | architektura z LangGraph w centrum, scenariusz „Hotel Senior nieczynny w lipcu 2027” |

Diagramy są w formacie [Mermaid](https://mermaid.js.org) (otwarty standard tekstowy, renderowany w GitHub/GitLab i w podglądzie Markdown w VS Code).

## Legenda

- 🟩 **zielone** — SLM, główny element rozwiązania
- 🟦 **niebieskie** — duży LLM, mózg decyzyjny
