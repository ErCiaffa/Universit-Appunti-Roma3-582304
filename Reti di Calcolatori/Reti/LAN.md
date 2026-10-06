---
aliases:
  - LAN
  - Local Area Network
tags:
  - università/reti-di-calcolatori
  - reti
date: 2026-09-29
---

# 🏠 LAN — Local Area Network

La **LAN** (*Local Area Network* o Rete Locale) interconnette risorse di calcolo situate nello stesso edificio o in edifici vicini.

> [!INFO] Caratteristiche Principali
> - **Distanza geografica**: $d < 5\text{ km}$
> - **Larghezza di banda tipica**: da $10\text{ Mbit/s}$ a $100\text{ Gbit/s}$
> - **Ritardo (Delay)**: Molto basso (distanze contenute)
> - **Tasso di errore**: Molto basso rispetto alle reti geografiche

```mermaid
flowchart LR
    HOST1["Computer A"] <--> SWITCH["Switch LAN (IEEE 802.3 / 802.11)"]
    HOST2["Computer B"] <--> SWITCH
    SERVER["Server Locale"] <--> SWITCH

    classDef host fill:#0f766e,stroke:#14b8a6,color:#fff;
    classDef dev fill:#713f12,stroke:#eab308,color:#fff;
    class HOST1,HOST2,SERVER host;
    class SWITCH dev;
```

---

### Tecnologia di Riferimento:
Le reti LAN sono standardizzate principalmente dal **[[Progetto IEEE 802]]**:
- **Ethernet (IEEE 802.3)** per le reti cablate.
- **Wi-Fi (IEEE 802.11)** per le reti wireless.

---

### 🧭 Navigazione Gerarchica
- ⬆️ **Nodo Padre:** [[Rete]]
- ➡️ **Passo Successivo:** [[WAN]]
