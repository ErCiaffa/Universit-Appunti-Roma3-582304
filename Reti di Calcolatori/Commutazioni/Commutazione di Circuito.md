---
aliases:
  - Commutazione di Circuito
  - Circuit Switching
tags:
  - università/reti-di-calcolatori
  - commutazione
date: 2026-09-29
---

# 📞 Commutazione di Circuito

Nella **Commutazione di Circuito** (*Circuit Switching*) viene stabilito un canale fisico **dedicato ed esclusivo** tra mittente e destinatario prima dell'inizio del trasferimento dati.

> [!INFO] Caratteristiche Principali
> - **Banda riservata** (tramite FDM o TDM): Assenza di contesa e zero ritardo di accodamento (*queuing delay*).
> - **Inefficiente per traffico a raffica (*bursty*)**: Le risorse di rete restano occupate anche durante i periodi di inattività o silenzio tra i nodi.
> - **Esempio per eccellenza**: Rete telefonica tradizionale (PSTN).

```mermaid
sequenceDiagram
    participant A as Mittente
    participant N1 as Nodo Rete 1
    participant N2 as Nodo Rete 2
    participant B as Destinatario

    Note over A,B: 1. Fase di Setup (Riservazione Canale Fisico)
    A->>N1: Richiesta Connessione
    N1->>N2: Allocazione Risorsa
    N2->>B: Connessione Stabilita

    Note over A,B: 2. Trasferimento Dati (Banda Esclusiva)
    A->>B: Flusso di Dati Continuo

    Note over A,B: 3. Abbattimento (Rilascio Risorse)
    A->>B: Chiusura Canale
```

---

### 🧭 Navigazione Gerarchica
- ⬆️ **Nodo Padre:** [[Rete]]
- ⬅️ **Passo Precedente:** [[Standard e Organismi]]
- ➡️ **Passo Successivo:** [[Commutazione di Pacchetto]]
