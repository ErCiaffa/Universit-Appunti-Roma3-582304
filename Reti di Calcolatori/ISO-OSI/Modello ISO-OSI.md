Il modello **ISO/OSI** (*International Organization for Standardization - Open Systems Interconnection*) è lo standard teorico di riferimento per l'architettura delle reti a stratificazione (7 livelli).

### Principi di Progettazione:
- **Astrazione**: Ogni strato fornisce allo strato superiore funzioni ben definite nascondendo i dettagli implementativi.
- **Minimizzazione delle interfacce**: Lo scambio di informazioni tra livelli adiacenti è ridotto al minimo indispensabile.
- **Indipendenza**: Le modifiche all'interno di uno strato non impattano gli altri, purché l'interfaccia resti inalterata.

---

### Mappa Concettuale ISO/OSI:

```mermaid
flowchart TD
    OSI["[[Modello ISO-OSI]]"]

    subgraph Architettura ["📁 Struttura e Livelli"]
        LIV["[[Livelli OSI]]"]
        PDU["[[PDU e Incapsulamento]]"]
    end

    subgraph Interazione ["📁 Interfacce e Servizi"]
        SAP["[[SAP e Primitive]]"]
        SERV["[[Servizi Connessi e Non Connessi]]"]
    end

    OSI --> Architettura
    OSI --> Interazione

    Architettura --> LIV
    Architettura --> PDU
    Interazione --> SAP
    Interazione --> SERV

    classDef main fill:#581c87,stroke:#a855f7,stroke-width:2px,color:#ffffff;
    classDef sub fill:#3b0764,stroke:#c084fc,stroke-width:1px,color:#ffffff;

    class OSI main;
    class LIV,PDU,SAP,SERV sub;
```

---

### Analogia dei Filosofi:
Per comprendere la stratificazione, si consideri due filosofi (uno in Kenya, uno in Indonesia) che comunicano tramite i rispettivi traduttori e ingegneri:
1. **Filosofi (Applicazione)**: Scambiano concetti astratti.
2. **Traduttori (Presentazione/Sessione)**: Traducono il messaggio in una lingua comune condivisa.
3. **Ingegneri (Fisico/Data Link)**: Convertono il testo in segnali (es. codice Morse) trasmessi sul canale.

---

### 🧭 Navigazione Gerarchica
- ⬆️ **Nodo Padre:** [[Rete]]
- ⬅️ **Passo Precedente:** [[Circuito Virtuale]]
- ➡️ **Passo Successivo:** [[Livelli OSI]]
