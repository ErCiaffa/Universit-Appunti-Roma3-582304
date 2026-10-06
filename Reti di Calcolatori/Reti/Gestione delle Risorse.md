---
aliases:
  - Gestione delle Risorse
tags:
  - università/reti-di-calcolatori
  - sistemi
date: 2026-09-29
---

# ⚙️ Gestione delle Risorse e Tolleranza ai Guasti

Una rete di calcolatori può essere modellata come un insieme di risorse interconnesse (host, storage, stampanti, switch, router).

### Attività di Controllo:
1. **Verifica dei diritti di accesso**.
2. **Sequenziamento delle operazioni**.
3. **Esecuzione delle operazioni disponibili**.

---

### Modalità di Gestione:

```mermaid
flowchart TD
    GR["Gestione delle Risorse"]
    
    GR --> GA["Autocratica\n1 unico gestore centralizzato"]
    GR --> GM["Multilaterale\nPiù gestori per la stessa risorsa"]

    GM --> GMP["Partizionata\nOgni attività gestita da 1 solo processo"]
    GM --> GMS["Successiva\nTutte le attività svolte a turno"]
    GM --> GMR["Replicata\nTutti i gestori partecipano alle attività"]

    GMR --> DEM["Democratica / Peer-to-Peer\nConsenso esplicito negoziato tra pari"]

    classDef main fill:#1e293b,stroke:#cbd5e0,color:#fff;
    classDef sub fill:#0f766e,stroke:#14b8a6,color:#fff;
    class GR main;
    class GA,GM,GMP,GMS,GMR,DEM sub;
```

> [!IMPORTANT] Resilienza ai Guasti (*Fault Tolerance*)
> - La resistenza ai guasti è **elevata** se è alto il numero di gestori che partecipano ad ogni attività con uguaglianza nelle responsabilità (gestione democratica/replicata).
> - Nei sistemi distribuiti è diffuso l'uso di **meccanismi elettorali** per la designazione dinamica del coordinatore/gestore.

---

### 🧭 Navigazione Gerarchica
- ⬆️ **Nodo Padre:** [[Rete]]
- ⬅️ **Passo Precedente:** [[Mezzi Trasmissivi]]
- ➡️ **Passo Successivo:** [[Standard e Organismi]]
