Il modello [[Modello ISO-OSI]] suddivide le funzionalità di rete in 7 livelli gerarchici.

### Classificazione nei Nodi:
- **Livelli End-to-End (4, 5, 6, 7)**: Risiedono esclusivamente nei nodi terminali (host di origine e destinazione).
- **Livelli Hop-by-Hop (1, 2, 3)**: Risiedono anche nei nodi intermedi (router e switch).

---

### Mappa dei 7 Livelli:

```mermaid
flowchart LR
    subgraph HostA ["Host A (Terminal Node)"]
        direction TB
        L7_A["7. Applicazione"]
        L6_A["6. Presentazione"]
        L5_A["5. Sessione"]
        L4_A["4. Trasporto"]
        L3_A["3. Rete"]
        L2_A["2. Data Link"]
        L1_A["1. Fisico"]
    end

    subgraph Router ["Router (Intermediate Node)"]
        direction TB
        L3_R["3. Rete (Routing)"]
        L2_R["2. Data Link"]
        L1_R["1. Fisico"]
    end

    subgraph HostB ["Host B (Terminal Node)"]
        direction TB
        L7_B["7. Applicazione"]
        L6_B["6. Presentazione"]
        L5_B["5. Sessione"]
        L4_B["4. Trasporto"]
        L3_B["3. Rete"]
        L2_B["2. Data Link"]
        L1_B["1. Fisico"]
    end

    L1_A <==>|Fisico| L1_R
    L1_R <==>|Fisico| L1_B
    L3_A -.->|Routing| L3_R
    L3_R -.->|Routing| L3_B
    L4_A == Protocollo End-to-End ==> L4_B

    classDef host fill:#0f766e,stroke:#14b8a6,color:#fff;
    classDef router fill:#b45309,stroke:#f59e0b,color:#fff;
    class L7_A,L6_A,L5_A,L4_A,L3_A,L2_A,L1_A,L7_B,L6_B,L5_B,L4_B,L3_B,L2_B,L1_B host;
    class L3_R,L2_R,L1_R router;
```

---

### Descrizione Sintetica dei Livelli:

1. **Fisico (1)**: Trasmissione della sequenza grezza di bit sul mezzo trasmissivo (voltaggi, frequenze).
2. **Data Link (2)**: Trasferimento di frame tra nodi adiacenti, rilevazione e correzione degli errori di trasmissione fisica.
3. **Rete (3)**: Conosce la topologia di rete; responsabile dell'**instradamento** (*routing*) e della commutazione end-to-end.
4. **Trasporto (4)**: Primo livello **End-to-End**. Colma le deficienze della rete garantendo affidabilità, controllo di flusso e gestione della connessione.
5. **Sessione (5)**: Sincronizzazione e gestione del dialogo tra due processi applicativi.
6. **Presentazione (6)**: Gestione della sintassi e codifica dei messaggi (crittografia, compressione, formati dati).
7. **Applicazione (7)**: Interfaccia di rete per le applicazioni utente (es. HTTP, FTP, SMTP).

---

### 🧭 Navigazione Gerarchica
- ⬆️ **Nodo Padre:** [[Rete]]
- ⬅️ **Passo Precedente:** [[Modello ISO-OSI]]
- ➡️ **Passo Successivo:** [[PDU e Incapsulamento]]
