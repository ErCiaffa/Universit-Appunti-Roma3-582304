Il **progetto IEEE 802** è una famiglia di standard sviluppati dall'IEEE che definiscono i livelli Fisico (Livello 1) e Data Link (Livello 2) per reti locali ([[LAN]]), metropolitane (MAN) e personali (PAN), su pacchetti a lunghezza variabile.

### Mappa Concettuale IEEE 802:

```mermaid
flowchart TD
    IEEE["[[Progetto IEEE 802]]"]

    subgraph Sottolivelli ["📁 Scomposizione Livello 2 (Data Link)"]
        LLC["[[Sottolivello LLC]] (802.2)"]
        MAC["[[Sottolivello MAC]]"]
        INDMAC["[[Indirizzi MAC]] (EUI-48)"]
    end

    subgraph Famiglie ["📁 Standard di Rete"]
        E5["802.3 Ethernet"]
        E11["802.11 Wireless LAN (Wi-Fi)"]
        E15["802.15 Wireless PAN (Bluetooth)"]
        E1["802.1 Management & VLAN"]
    end

    IEEE --> Sottolivelli
    IEEE --> Famiglie

    Sottolivelli --> LLC
    Sottolivelli --> MAC
    MAC --> INDMAC

    classDef main fill:#14532d,stroke:#22c55e,stroke-width:2px,color:#ffffff;
    classDef sub fill:#064e3b,stroke:#34d399,stroke-width:1px,color:#ffffff;

    class IEEE main;
    class LLC,MAC,INDMAC,E5,E11,E15,E1 sub;
```

---

### Componenti Principali:
- **802.1**: Network Management, Bridge, VLAN.
- **802.2**: Logical Link Control (LLC).
- **802.3**: Ethernet (Ethernet, Fast Ethernet 802.3u, Gigabit Ethernet 802.3z, 10G 802.3ae).
- **802.11**: Wireless LAN (Wi-Fi).
- **802.15**: Wireless PAN (Bluetooth, ZigBee).

---

### 🧭 Navigazione Gerarchica
- ⬆️ **Nodo Padre:** [[Rete]]
- ⬅️ **Passo Precedente:** [[Servizi Connessi e Non Connessi]]
- ➡️ **Passo Successivo:** [[Sottolivello MAC]]
