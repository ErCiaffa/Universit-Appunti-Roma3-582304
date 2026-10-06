---
aliases:
  - Base di Dati
  - Basi di Dati
  - Master Hub Base di Dati
tags:
  - università/base-di-dati
  - hub
date: 2026-10-01
---

# 🗄️ Base di Dati — Master Hub

> [!ABSTRACT] 📌 File Principale & Master Hub del Corso
> Questa nota rappresenta il **File Principale** del corso di **Base di Dati**.  
> Funge da guida sintetica per l'esame: per ciascun tema trovi il **concetto fondamentale**, la **formalizzazione relazionale** e il link diretto alla relativa nota di dettaglio.

---

## 🏗️ 1. Architettura a Tre Livelli di un DBMS

I moderni Database Management System (DBMS) separano la visione dell'utente dalla memorizzazione fisica su disco tramite l'architettura a 3 livelli ANSI/SPARC:

```mermaid
flowchart TD
    subgraph EXT ["Livello Esterno (Viste Utente)"]
        V1["Vista Applicazione Web"]
        V2["Vista Amministrazione"]
    end

    subgraph LOG ["Livello Logico (Modello Relazionale)"]
        direction TB
        SCH["<b>[[Modello dei Dati|Schemi delle Tabelle]]</b><br/>Tabelle, Colonne, Domini"]
        VINC["<b>[[Vincoli di Integrità|Vincoli]]</b>: [[Chiave Primaria|PK]] & [[Integrità Referenziale|FK]]"]
        SQL["<b>[[Comandi Base SQL|Linguaggio SQL]]</b>: DDL, DML, DQL"]
    end

    subgraph PHYS ["Livello Fisico (Storage su Disco)"]
        STOR["File su File System, B-Tree, Pagine e Blocchi Disco"]
    end

    EXT ==>|"Mapping Esterno/Logico"| LOG
    LOG ==>|"Mapping Logico/Fisico"| PHYS

    classDef extNode fill:#0369a1,stroke:#38bdf8,stroke-width:2px,color:#e0f2fe;
    classDef logNode fill:#064e3b,stroke:#34d399,stroke-width:2px,color:#ecfdf5;
    classDef physNode fill:#1e293b,stroke:#94a3b8,stroke-width:2px,color:#f8fafc;

    class V1,V2 extNode;
    class SCH,VINC,SQL logNode;
    class STOR physNode;
```

---

## 📋 2. Quadro Sinottico: Cosa C'è da Sapere per Ogni Argomento

| Modulo | Argomento & Nota | 🎯 Concetto Chiave da Sapere | 📌 Regola Fondamentale / Esempio | 💡 Significato Pratico |
|---|---|---|---|---|
| **01** | **[[Modello dei Dati]]** | Definizione formale di modello logico vs concettuale. | Dati strutturati vs non strutturati | Permette l'indipendenza fisica dei dati dalle applicazioni. |
| **01** | **[[Schema e Istanza]]** | Schema (intensione invariante) vs Istanza (estensione temporale). | Schema = DDL (`CREATE`)<br/>Istanza = tuple attuali | Lo schema cambia raramente; l'istanza muta ad ogni `INSERT`/`DELETE`. |
| **01** | **[[Valore Nullo]]** | Il valore `NULL` denota assenza di valore, valore sconosciuto o inapplicabile. | Logica a tre valori (True, False, Unknown) | `NULL` non è né zero né stringa vuota: richiede predicati `IS NULL`. |
| **02** | **[[Modello Relazionale]]** | Relazione come sottoinsieme del prodotto cartesiano dei domini. | Tuple ordinate per nome attributo | Righe non ordinate, tuple distinte (nessun duplicato formale). |
| **02** | **[[Strutture Nidificate]]** | Modello relazionale piatto (1NF) vs strutture complesse/XML/JSON. | Prima Forma Normale: valori atomici | Tutti i campi devono contenere un valore elementare indivisibile. |
| **03** | **[[Vincoli di Integrità]]** | Predicati booleani che ogni istanza valida deve obbligatoriamente soddisfare. | Vincoli intra-relazionali vs inter-relazionali | Impediscono la corruzione dei dati a livello di DBMS. |
| **03** | **[[Chiave Primaria]]** | Insieme minimale di attributi che identifica univocamente ogni tupla. | `PRIMARY KEY` (Univoca + `NOT NULL`) | Identità della riga; impedisce duplicati logici nella tabella. |
| **03** | **[[Integrità Referenziale]]** | Vincolo che lega una chiave esterna (FK) alla chiave primaria di un'altra tabella. | `FOREIGN KEY (d) REFERENCES T(id)` | Impedisce tuple "orfane"; politiche `CASCADE` o `SET NULL` su cancellazione. |
| **04** | **[[Comandi Base SQL]]** | I tre sottoinsiemi: DDL (definizione), DML (manipolazione), DQL (interrogazione). | `SELECT ... FROM ... WHERE ... GROUP BY` | Standard universale dichiarativo: descrivi *cosa* vuoi, non *come* estrarlo. |

---

## 🌳 3. Mappa Concettuale Ramificata ad Albero Puro

```mermaid
flowchart TD
    BD["🗄️ <b>BASE DI DATI</b><br/>(Master Hub)"]

    subgraph C1 ["📁 01_CONCETTI FONDAMENTALI (Celeste)"]
        direction TB
        MD["[[Modello dei Dati]]"]
        SI["[[Schema e Istanza]]"]
        VN["[[Valore Nullo]]"]
    end

    subgraph C2 ["📁 02_STRUTTURA RELAZIONALE (Verde)"]
        direction TB
        MR["[[Modello Relazionale]]"]
        SN["[[Strutture Nidificate]]"]
    end

    subgraph C3 ["📁 03_VINCOLI DI INTEGRITÀ (Arancione)"]
        direction TB
        VI["[[Vincoli di Integrità]]"]
        PK["[[Chiave Primaria]]"]
        FK["[[Integrità Referenziale]]"]
    end

    subgraph C4 ["📁 04_LINGUAGGIO SQL (Viola)"]
        direction TB
        SQL["[[Comandi Base SQL]]"]
    end

    %% ALBERO GERARCHICO
    BD ==> C1
    BD ==> C2
    BD ==> C3
    BD ==> C4

    C1 --> MD
    MD --> SI
    SI --> VN

    C2 --> MR
    MR --> SN

    C3 --> VI
    VI --> PK
    PK --> FK

    C4 --> SQL

    %% STILI VISIVI
    classDef hubNode fill:#0f172a,stroke:#38bdf8,stroke-width:4px,color:#f8fafc;
    classDef c1Node fill:#0369a1,stroke:#38bdf8,stroke-width:2px,color:#e0f2fe;
    classDef c2Node fill:#064e3b,stroke:#34d399,stroke-width:2px,color:#ecfdf5;
    classDef c3Node fill:#7c2d12,stroke:#fb923c,stroke-width:2px,color:#ffedd5;
    classDef c4Node fill:#581c87,stroke:#c084fc,stroke-width:2px,color:#faf5ff;

    class BD hubNode;
    class MD,SI,VN c1Node;
    class MR,SN c2Node;
    class VI,PK,FK c3Node;
    class SQL c4Node;
```