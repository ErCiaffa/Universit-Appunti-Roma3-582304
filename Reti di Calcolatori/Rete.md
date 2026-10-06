---
aliases:
  - Rete
  - Reti di Calcolatori
  - Master Hub Reti
tags:
  - università/reti-di-calcolatori
  - hub
date: 2026-10-01
---

# 🌐 Reti di Calcolatori — Master Hub

> [!ABSTRACT] 📌 File Principale & Master Hub del Corso
> Questa nota rappresenta il **File Principale** del corso di **Reti di Calcolatori**.  
> Funge da guida sintetica per l'esame: per ciascun tema trovi il **concetto fondamentale**, la **formula di ritardo o standard** e il link diretto alla relativa nota di dettaglio.

Interconnessione di risorse di calcolo autonome per scambiare informazioni e condividere risorse, con trasmissione seriale dei dati.

---

## 🏗️ 1. Architettura a Livelli: ISO/OSI vs Standard IEEE 802

I sistemi di telecomunicazione operano a strati gerarchici, ciascuno con una specifica unità dati (**PDU**):

```mermaid
flowchart LR
    subgraph OSI ["Modello ISO/OSI (7 Livelli)"]
        direction TB
        L7["7. Applicazione"] --> L6["6. Presentazione"]
        L6 --> L5["5. Sessione"]
        L5 --> L4["4. Trasporto (Segmento)"]
        L4 --> L3["3. [[Commutazione di Pacchetto|Rete]] (Pacchetto)"]
        L3 --> L2["2. [[Modello ISO-OSI|Collegamento]] (Frame)"]
        L2 --> L1["1. [[Mezzi Trasmissivi|Fisico]] (Bit)"]
    end

    subgraph IEEE ["Progetto IEEE 802 (Livelli 1 e 2)"]
        direction TB
        LLC["<b>[[Sottolivello LLC|LLC (802.2)]]</b><br/>Controllo Flusso & [[SNAP]]"]
        MAC["<b>[[Sottolivello MAC|MAC]]</b> & <b>[[Indirizzi MAC|EUI-48]]</b><br/>Accesso al Mezzo"]
        PHY["<b>Fisico IEEE 802</b><br/>802.3 Ethernet / 802.11 Wi-Fi"]
        LLC --> MAC --> PHY
    end

    L2 -.->|"Standardizzato da"| LLC
    L1 -.->|"Standardizzato da"| PHY

    classDef osiNode fill:#581c87,stroke:#c084fc,stroke-width:2px,color:#faf5ff;
    classDef ieeeNode fill:#064e3b,stroke:#34d399,stroke-width:2px,color:#ecfdf5;

    class L7,L6,L5,L4,L3,L2,L1 osiNode;
    class LLC,MAC,PHY ieeeNode;
```

---

## 📋 2. Quadro Sinottico: Cosa C'è da Sapere per Ogni Argomento

| Modulo | Argomento & Nota | 🎯 Concetto Chiave da Sapere | 📌 Formula / Standard Chiave | 💡 Significato Ingegneristico |
|---|---|---|---|---|
| **Reti** | **[[LAN]]** | Rete locale confinata a un edificio ($d < 5\text{ km}$); banda alta, delay basso. | $10\text{ Mbps} \div 100\text{ Gbps}$ | Basso tasso di errore, controllo totale dell'infrastruttura. |
| **Reti** | **[[WAN]]** | Rete geografica su scala globale; interconnette LAN tramite router e ISP. | Scala continentale/mondiale | Ritardi elevati, canali condivisi, necessità di instradamento complesso. |
| **Reti** | **[[Banda e Delay]]** | Differenza tra capacità del canale ($R$) e ritardo di propagazione ($T_{prop}$). | $T_{tot} = \frac{L}{R} + \frac{d}{v}$ | Banda = larghezza della strada; Delay = velocità limite della luce nel mezzo. |
| **Reti** | **[[Mezzi Trasmissivi]]** | Supporti fisici: doppino in rame (UTP/STP), fibra ottica (monomodale/multimodale), wireless. | Velocità $v \approx 2 \cdot 10^8\text{ m/s}$ | Fibra = altissima banda e immunità elettromagnetica; rame = economico. |
| **Reti** | **[[Gestione delle Risorse]]** | Multiplexing FDM (frequenza), TDM (tempo statica), Statistico (a pacchetti). | Multiplazione Statistica | La multiplazione a pacchetti massimizza l'efficienza sui picchi di traffico. |
| **Reti** | **[[Standard e Organismi]]** | Standard de jure (ISO, IEEE, ITU-T) vs de facto (IETF RFC di Internet). | Standard aperti | Permettono l'interoperabilità tra apparati di costruttori diversi. |
| **Comm** | **[[Commutazione di Circuito]]** | Riserva dedicata di risorse (canale continuo) per l'intera durata della sessione. | Fasi: Setup $\to$ Dati $\to$ Teardown | Zero ritardo di accodamento durante la chiamata, ma spreco di banda se inattivi. |
| **Comm** | **[[Commutazione di Pacchetto]]** | I dati sono spezzati in pacchetti con header instradati nodo per nodo (*Store and Forward*). | Multiplazione Statistica | Massima efficienza del canale, ma introduce ritardi di accodamento variabili (jitter). |
| **Comm** | **[[Datagramma]]** | Pacchetti indipendenti e non connessi; ogni pacchetto contiene IP sorgente e destinazione. | Instradamento dinamico (*Connectionless*) | I pacchetti possono seguire strade diverse e arrivare disordinati. |
| **Comm** | **[[Circuito Virtuale]]** | Connessione logica stabilita prima del trasferimento (header con VCI numerico breve). | Connesso con instradamento fisso | Pacchetti sempre ordinati; instradamento calcolato solo al setup. |
| **OSI** | **[[Modello ISO-OSI]]** | Architettura teorica di riferimento a 7 livelli indipendenti con interfacce SAP. | 7 Strati Logici | Ogni livello fornisce servizi al livello superiore nascondendo i dettagli. |
| **OSI** | **[[Livelli OSI]]** | Dettaglio dei singoli compiti da Livello 1 (Fisico) a Livello 7 (Applicazione). | Fisico, Data Link, Rete, Trasporto... | Separazione delle responsabilità architetturali. |
| **OSI** | **[[PDU e Incapsulamento]]** | Ogni livello incapsula la PDU superiore aggiungendo il proprio Header: $PDU = PCI + SDU$. | Frame $\supset$ Pacchetto $\supset$ Segmento | Meccanismo a matrioska alla base della trasmissione dati. |
| **OSI** | **[[SAP e Primitive]]** | Punti di accesso al servizio (SAP); 4 primitive: Request, Indication, Response, Confirm. | Chiamate di servizio tra livelli | Interfaccia formale tra strati adiacenti sullo stesso host. |
| **OSI** | **[[Servizi Connessi e Non Connessi]]** | Connessi (affidabili con handshake e ACK) vs Non Connessi (*Best Effort* veloce). | TCP (connesso) vs UDP (non conn.) | Trade-off fondamentale tra affidabilità e latenza. |
| **802** | **[[Progetto IEEE 802]]** | Standardizzazione della LAN; suddivide il Livello 2 OSI in due sottolivelli: MAC e LLC. | Famiglia 802.x | Ethernet cablata (802.3), Wi-Fi wireless (802.11). |
| **802** | **[[Sottolivello MAC]]** | Controllo di accesso al mezzo fisico condiviso (CSMA/CD per Ethernet, CSMA/CA per Wi-Fi). | Arbitraggio collisioni | Decide chi può trasmettere sul canale comune e quando. |
| **802** | **[[Indirizzi MAC]]** | Indirizzo fisico univoco a 48 bit (EUI-48); prime 3 coppie esadecimali = OUI costruttore. | `XX:XX:XX:YY:YY:YY` (6 Byte) | Indirizzamento a livello locale per recapitare i frame allo switch. |
| **802** | **[[Sottolivello LLC]]** | LLC (IEEE 802.2): indipendenza dal mezzo trasmissivo, controllo d'errore e multiplazione. | Servizi LLC tipo 1, 2, 3 | Fornisce al livello IP un'interfaccia uniforme indipendentemente da rame o fibra. |
| **802** | **[[SNAP]]** | Estensione dell'header LLC per supportare identificatori di protocollo EtherType a 16 bit. | Header SNAP (5 Byte) | Permette il trasporto di protocolli IP legacy sopra frame IEEE 802. |
| **802** | **[[Repeater e Hub]]** | Apparati L1 (Fisico); rigenerazione bit e segnali elettrici; non separano i domini di collisione. | Livello 1 Fisico | Estende la distanza fisica del cavo senza alcuna intelligenza o filtraggio MAC. |
| **802** | **[[Bridge e Switch]]** | Interconnessione L2 (MAC); Filtering, Store & Forward, Backward Learning, Full Speed (14.880 pps), Pause Frame 802.3x. | IEEE 802.1D, 802.3x | Segmenta la LAN eliminando collisioni ed instradando frame in modo trasparente. |
| **802** | **[[Spanning Tree Protocol]]** | Protocollo distributed per eliminare cicli e tempeste di broadcast su LAN con topologie ridondanti. | BPDU (`01:80:C2:00:00:00`), IEEE 802.1D | Mantiene collegamenti di backup attivi commutando su guasto in modo aciclico. |
| **Lab** | **[[Kathará]]** | Emulatore di rete virtuale basato su container Docker; configurazione apparati, routing IP e test. | `lab.conf`, `iproute2` | Laboratorio virtuale per emulare LAN, router e protocolli senza hardware fisico. |

---

## 🌳 3. Mappa Concettuale Ramificata ad Albero Puro

```mermaid
flowchart TD
    RETE["🌐 <b>RETI DI CALCOLATORI</b><br/>(Master Hub)"]

    %% RAMO 1: RETI BASE
    subgraph R1 ["📁 CONCETTI BASE RETI (Giallo)"]
        direction TB
        LAN["[[LAN]]"]
        WAN["[[WAN]]"]
        BD["[[Banda e Delay]]"]
        MEZ["[[Mezzi Trasmissivi]]"]
        GES["[[Gestione delle Risorse]]"]
        STD["[[Standard e Organismi]]"]
    end

    %% RAMO 2: COMMUTAZIONI
    subgraph R2 ["📁 COMMUTAZIONI (Ciano)"]
        direction TB
        CC["[[Commutazione di Circuito]]"]
        CP["[[Commutazione di Pacchetto]]"]
        DG["[[Datagramma]]"]
        CV["[[Circuito Virtuale]]"]
    end

    %% RAMO 3: ISO/OSI
    subgraph R3 ["📁 MODELLO ISO/OSI (Viola)"]
        direction TB
        OSI["[[Modello ISO-OSI]]"]
        LOSI["[[Livelli OSI]]"]
        PDU["[[PDU e Incapsulamento]]"]
        SAP["[[SAP e Primitive]]"]
        SC["[[Servizi Connessi e Non Connessi]]"]
    end

    %% RAMO 4: IEEE 802
    subgraph R4 ["📁 PROGETTO IEEE 802 (Verde)"]
        direction TB
        IEEE["[[Progetto IEEE 802]]"]
        MAC["[[Sottolivello MAC]]"]
        IMAC["[[Indirizzi MAC]]"]
        LLC["[[Sottolivello LLC]]"]
        SNAP["[[SNAP]]"]
        REP["[[Repeater e Hub]]"]
        BRG["[[Bridge e Switch]]"]
        STP["[[Spanning Tree Protocol]]"]
    end

    %% RAMO 5: LABORATORIO KATHARA
    subgraph R5 ["📁 LABORATORIO VIRTUALE (Arancio)"]
        direction TB
        KAT["[[Kathará]]"]
    end

    %% ALBERO GERARCHICO
    RETE ==> R1
    RETE ==> R2
    RETE ==> R3
    RETE ==> R4
    RETE ==> R5

    R1 --> LAN
    LAN --> WAN
    LAN --> BD
    BD --> MEZ
    MEZ --> GES
    GES --> STD

    R2 --> CC
    R2 --> CP
    CP --> DG
    CP --> CV

    R3 --> OSI
    OSI --> LOSI
    OSI --> PDU
    OSI --> SAP
    SAP --> SC

    R4 --> IEEE
    IEEE --> MAC
    MAC --> IMAC
    IEEE --> LLC
    LLC --> SNAP
    SNAP --> REP
    REP --> BRG
    BRG --> STP

    R5 --> KAT

    %% STILI VISIVI GRAPH-ALIGNED
    classDef mainNode fill:#0f172a,stroke:#38bdf8,stroke-width:4px,color:#f8fafc;
    classDef reteNode fill:#78350f,stroke:#fbbf24,stroke-width:2px,color:#fef3c7;
    classDef commNode fill:#164e63,stroke:#22d3ee,stroke-width:2px,color:#ecfeff;
    classDef osiNode fill:#581c87,stroke:#c084fc,stroke-width:2px,color:#faf5ff;
    classDef ieeeNode fill:#064e3b,stroke:#34d399,stroke-width:2px,color:#ecfdf5;
    classDef labNode fill:#7c2d12,stroke:#fb923c,stroke-width:2px,color:#fff7ed;

    class RETE mainNode;
    class LAN,WAN,BD,MEZ,GES,STD reteNode;
    class CC,CP,DG,CV commNode;
    class OSI,LOSI,PDU,SAP,SC osiNode;
    class IEEE,MAC,IMAC,LLC,SNAP,REP,BRG,STP ieeeNode;
    class KAT labNode;
```