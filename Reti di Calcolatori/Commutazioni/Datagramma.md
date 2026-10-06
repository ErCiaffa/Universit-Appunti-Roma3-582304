---
aliases:
  - Datagramma
  - Datagram
tags:
  - università/reti-di-calcolatori
  - commutazione
date: 2026-09-29
---

# ✉️ Datagramma

Approccio **senza connessione (*connectionless*)** nella [[Commutazione di Pacchetto]].

> [!INFO] Caratteristiche Principali
> - **Nessun Setup**: I pacchetti vengono inviati immediatamente senza preventiva instaurazione di una connessione.
> - **Pacchetti Indipendenti**: Ciascun pacchetto (datagramma) contiene l'indirizzo di destinazione completo e viene trattato autonomamente.
> - **Instradamento Dinamico**: Ogni router decide la rotta pacchetto per pacchetto in base alla propria tabella di routing e allo stato della rete.
> - **Affidabilità Best-Effort**: I pacchetti dello stesso flusso possono seguire percorsi diversi, arrivare **fuori ordine** o essere scartati in caso di congestione.
> - **Esempio per eccellenza**: Protocollo **IP** (Internet Protocol).

```mermaid
flowchart TD
    HOST_A["Host A"] -->|P1 via Ruta 1| R1["Router 1"]
    HOST_A -->|P2 via Ruta 2| R2["Router 2"]
    R1 --> HOST_B["Host B (Può ricevere P1 e P2 fuori ordine)"]
    R2 --> HOST_B

    classDef host fill:#0f766e,stroke:#14b8a6,color:#fff;
    classDef router fill:#b45309,stroke:#f59e0b,color:#fff;
    class HOST_A,HOST_B host;
    class R1,R2 router;
```

---

### 🧭 Navigazione Gerarchica
- ⬆️ **Nodo Padre:** [[Rete]]
- ⬅️ **Passo Precedente:** [[Commutazione di Pacchetto]]
- ➡️ **Passo Successivo:** [[Circuito Virtuale]]
