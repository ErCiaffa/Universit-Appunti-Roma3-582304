---
aliases:
  - Commutazione di Pacchetto
  - Packet Switching
tags:
  - università/reti-di-calcolatori
  - commutazione
date: 2026-09-29
---

# 📦 Commutazione di Pacchetto

Nella **Commutazione di Pacchetto** (*Packet Switching*) i dati vengono suddivisi in blocchi discreti chiamati **pacchetti** (composti da *Header* con le informazioni di controllo e *Payload* con i dati).

> [!INFO] Meccanismi Fondamentali
> - **Store-and-Forward**: Ogni nodo intermedio (router/switch) deve ricevere l'intero pacchetto prima di poterlo ritrasmettere sul collegamento successivo.
> - **Multiplazione Statistica**: Le risorse di rete sono condivise su richiesta (senza prenotazione a priori), ottimizzando l'uso dei canali.
> - **Buffer e Code**: Se l'arrivo dei pacchetti supera la capacità trasmissiva della linea, si generano ritardi di accodamento (*queuing delay*) o perdita di pacchetti (*packet loss*).

```mermaid
flowchart LR
    HOST_A["Host A"] -->|Pacchetto 1| R1["Router 1 (Buffer/Code)"]
    R1 -->|Store-and-Forward| R2["Router 2"]
    R2 --> HOST_B["Host B"]

    classDef host fill:#0f766e,stroke:#14b8a6,color:#fff;
    classDef router fill:#b45309,stroke:#f59e0b,color:#fff;
    class HOST_A,HOST_B host;
    class R1,R2 router;
```

---

### Approcci di Commutazione di Pacchetto:
1. **[[Datagramma]]**: Approccio senza connessione (*connectionless*).
2. **[[Circuito Virtuale]]**: Approccio orientato alla connessione (*connection-oriented*).

---

### 🧭 Navigazione Gerarchica
- ⬆️ **Nodo Padre:** [[Rete]]
- ⬅️ **Passo Precedente:** [[Commutazione di Circuito]]
- ➡️ **Passo Successivo:** [[Datagramma]]
