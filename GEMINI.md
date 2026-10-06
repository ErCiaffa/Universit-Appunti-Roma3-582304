# 📌 Regole di Formattazione e Struttura Vault Obsidian (Università)

Questo file definisce le linee guida vincolanti per la generazione e gestione di tutte le note nel Vault universitario.  
**TUTTI i modelli e agenti devono rigorosamente rispettare queste regole.**

---

## 🏗️ 1. Struttura del Vault ed Architettura delle Materie

Ogni materia ha un **File Principale (Master Hub)** che risiede nella cartella radice della materia e sottocartelle numerate o tematiche:

### 1. Reti di Calcolatori
- **Master Hub:** `Reti di Calcolatori/Rete.md`
- **Sottocartelle:**
  - `Reti/`: Concetti base, LAN, WAN, Banda vs Delay, Mezzi Trasmissivi, Gestione Risorse, Standard.
  - `Commutazioni/`: Commutazione di Circuito, Commutazione di Pacchetto, Datagramma, Circuito Virtuale.
  - `ISO-OSI/`: Modello ISO-OSI, Livelli OSI, PDU e Incapsulamento, SAP e Primitive.
  - `IEEE 802/`: Progetto IEEE 802, Sottolivello MAC, Indirizzi MAC (EUI-48), LLC, SNAP, Repeater e Hub, Bridge e Switch, Spanning Tree Protocol.
  - `Kathara/`: Laboratorio virtuale Kathará, emulazione apparati, routing IP, script startup.

### 2. Base di Dati
- **Master Hub:** `Base di Dati/Base di Dati.md`
- **Sottocartelle:**
  - `01_Concetti/`: Concetti base, modelli dei dati, DBMS, schema vs istanza.
  - `02_Struttura/`: Modello relazionale, schemi, tabelle, strutture nidificate.
  - `03_Vincoli/`: Vincoli di integrità (Primary Key, Foreign Key, Not Null, Check).
  - `04_SQL/`: Linguaggio SQL (DDL, DML, DQL).

### 3. Sistemi Embedded
- **Master Hub:** `Sistemi Embedded/Sistemi Embedded.md`
- **Sottocartelle:**
  - `00_Fondamenti/`: Numeri complessi (Gauss, Eulero), equazioni differenziali continue e discretizzazione.
  - `01_Strumenti_Matematici/`: Equazioni alle differenze, Trasformata Z, proprietà, trasformate notevoli, metodi di antitrasformazione.
  - `02_Campionamento_e_Ricostruzione/`: Campionamento impulsivo, spettro periodico, Teorema di Shannon, aliasing, ricostruttore sinc vs ZOH reale.

### 4. Machine Learning
- **Master Hub:** `Machine Learning/Machine Learning.md`
- **Sottocartelle:**
  - `01_Supervisionato/`: Regressione, classificazione, alberi decisionali, SVM.
  - `02_Non_Supervisionato/`: Clustering (K-Means), PCA, riduzione dimensionalità.
  - `03_Deep_Learning/`: Reti neurali artificiali, CNN, RNN, Transformers, ottimizzatori.

---

## 🎨 2. Palette Cromatica e Gruppi di Colore (Graph View)

I colori devono essere perfettamente sincronizzati tra **Mermaid (`classDef`)** e il **Graph View di Obsidian (`.obsidian/graph.json`)**:

| Corso | Cartella | Colore | Codice Esadecimale | Valore Intero RGB |
|---|---|---|---|---|
| **Reti** | `Reti` | Giallo / Oro | `#eab308` | `15381256` |
| **Reti** | `Commutazioni` | Ciano / Azzurro | `#06b6d4` | `440020` |
| **Reti** | `ISO-OSI` | Viola / Magenta | `#a855f7` | `11031031` |
| **Reti** | `IEEE 802` | Verde Smeraldo | `#22c55e` | `2278750` |
| **Reti** | `Kathara` | Arancione Vivace | `#f97316` | `15990622` |
| **Basi Dati** | `01_Concetti` | Celeste / Blu | `#38bdf8` | `3899638` |
| **Basi Dati** | `02_Struttura` | Verde Boscoso | `#10b981` | `1095809` |
| **Basi Dati** | `03_Vincoli` | Arancione / Rosso | `#f97316` | `15990622` |
| **Basi Dati** | `04_SQL` | Viola Chiaro | `#c084fc` | `16096779` |
| **Sistemi Embedded** | `00_Fondamenti` | Rosa / Corallo | `#f43f5e` | `16007006` |
| **Sistemi Embedded** | `01_Strumenti_Matematici` | Indaco / Elettrico | `#6366f1` | `6514417` |
| **Sistemi Embedded** | `02_Campionamento_e_Ricostruzione` | Teal / Turchese scuro | `#0d9488` | `889992` |
| **Machine Learning** | `01_Supervisionato` | Fucsia Brillante | `#ec4899` | `15485081` |
| **Machine Learning** | `02_Non_Supervisionato` | Ambra / Arancio | `#f59e0b` | `16096779` |
| **Machine Learning** | `03_Deep_Learning` | Viola Profondo | `#8b5cf6` | `9133302` |

---

## 🔗 3. Regola Aurea sui Collegamenti (Graph Pulito e Gerarchico)

> [!CAUTION] DIVIETO DI COLLEGAMENTI DEBOLI / A RAGNATELA
> - **MAI** inserire sezioni generiche di "Voci Correlate" che collegano file a caso tra capitoli lontani. Questo distrugge la leggibilità del Graph View.
> - I collegamenti tra note devono essere **esclusivamente gerarchici o strettamente propedeutici**:
>   1. **Dall'Hub ai moduli/capitoli principali.**
>   2. **Dal nodo foglia al proprio nodo padre (Hub o modulo).**
>   3. **Da un concetto al suo immediato prerequisito o passo successivo** (es. `Campionamento Impulsivo` $\to$ `Spettro del Segnale Campionato`).

In calce a ogni nota atomica inserire la sezione standard di **Navigazione Gerarchica**:
```markdown
### 🧭 Navigazione Gerarchica
- ⬆️ **Nodo Padre:** [[Nome_Hub_o_Modulo]]
- ➡️ **Passo Successivo:** [[Prossimo_Argomento]]
```

---

## 🎓 4. Standard Pedagogico di Scrittura per Ingegneria

1. **Comprensibile senza essere banale:**
   - Iniziare sempre con **l'intuizione fisica o il problema pratico** (perché serve all'ingegnere, cosa succede nell'hardware o nel mondo reale).
   - Non dare per scontate nozioni matematiche: spiegare a parole cosa significa ogni operatore prima di usarlo.
2. **Dimostrazioni passo-passo commentate:**
   - Ogni passaggio algebrico deve avere una **giustificazione esplicita** (es. *"applicando la serie geometrica", "raccogliendo per z^-1", "per la linearità"*).
3. **Grafici ad Alta Definizione (TikZJax & Excalidraw Cisco):**
   - **TikZJax (````tikz ... ````):** **OBBLIGATORIO** per tutti i grafici matematici, fisici, segnali nel tempo, spettri in frequenza, piano complesso, cerchio unitario e schemi circuitali. **VIETATO l'uso di schemi ASCII grezzi.**
   - **Excalidraw (Icone Cisco per Reti):** Per le topologie di rete, usare diagrammi Excalidraw incorporati (`![[nome.excalidraw]]`) con le icone ufficiali Cisco Network (Router, Switch, Firewall, Server, Cloud) installabili dalla libreria di Excalidraw.
   - **Mermaid:** Usare per diagrammi di sequenza temporale di protocolli (`sequenceDiagram`), alberi gerarchici dei Master Hub (`flowchart TD/LR`) e schemi Entità-Relazione (`erDiagram`).
4. **Implementazione Software Reale:**
   - Fornire frammenti di codice concreti:
     - **Sistemi Embedded:** firmware C per MCU (routine ISR timer, registri, interrupt).
     - **Basi di Dati:** DDL/DQL SQL formattato e commentato.
     - **Reti:** formati frame PDU, comandi di rete (socket, ping, traceroute).
     - **Machine Learning:** PyTorch / Scikit-Learn.
5. **Callout Obsidian:**
   - `> [!ABSTRACT]` — Riquadro riassuntivo in testa all'Hub.
   - `> [!INFO]` — Definizioni formali e schede tecniche.
   - `> [!NOTE]` — Dimostrazioni e passaggi algebrici.
   - `> [!IMPORTANT]` — Regole d'oro, teoremi e criteri di stabilità.
   - `> [!TIP]` — Trucchi per l'esame e best practice ingegneristiche.
   - `> [!CAUTION]` / `> [!WARNING]` — Condizioni di errore, aliasing, instabilità.
6. **Formule Matematiche LaTeX:**
   - In linea con `$formula$` (es. $\omega_s \ge 2\omega_c$).
   - In blocco con `$$formula$$` per equazioni e passaggi di dimostrazione. Nelle tabelle markdown usare $\lvert z \rvert < 1$ (mai il pipe grezzo che rompe le colonne).

---

## 📑 5. Modelli (Templates) Disponibili nel Vault

Nella cartella `Templates/` sono memorizzati i file modello pronti all'uso:
1. `Templates/Template - Master Hub.md` — Modello universale per il File Principale di qualsiasi materia (quadro sinottico tabellare + albero puro).
2. `Templates/Template - Sistemi Embedded.md` — Modello con intuizione, dimostrazione passo-passo, firmware C e navigazione.
3. `Templates/Template - Reti di Calcolatori.md` — Modello con schede ISO/OSI, formato PDU, sequence diagram e formule di ritardo.
4. `Templates/Template - Base di Dati.md` — Modello con schema relazionale, tabelle di esempio, query SQL e vincoli.
5. `Templates/Template - Machine Learning.md` — Modello con intuizione geometrica, funzione di costo, gradient descent e snippet Python.
