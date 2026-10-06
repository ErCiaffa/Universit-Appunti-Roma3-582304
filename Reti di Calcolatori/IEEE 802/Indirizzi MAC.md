Gli **Indirizzi MAC** (*Medium Access Control Addresses*) identificano univocamente le interfacce fisiche di rete sul sottolivello MAC.

### Formato e Standard EUI-48:
Gli indirizzi sono codificati su **6 byte (48 bit)** e rappresentati in notazione esadecimale (es. `00:25:9E:3C:07:9A`).

```mermaid
bitfield
    0-23: "OUI - Organization Unique Identifier (3 Byte assegnati da IEEE)"
    24-47: "Definito dal Costruttore (3 Byte numero di serie)"
```

- **Primi 3 byte**: **OUI** (*Organization Unique Identifier*), attribuiti dall'IEEE direttamente al costruttore hardware (es. `00:25:9E` è registrato da Huawei).
- **Secondi 3 byte**: Assegnati autonomamente dal produttore per ogni singola scheda di rete prodotta.

---

### Tipologie di Indirizzi MAC:
1. **Unicast**: Identificano una singola scheda di rete.
   - *Regola*: Se l'ultimo bit del primo byte ha valore **`0`**, l'indirizzo è unicast.
2. **Multicast**: Identificano un gruppo di schede di rete.
   - *Regola*: Se l'ultimo bit del primo byte ha valore **`1`**, l'indirizzo è multicast.
3. **Broadcast**: Destinato a tutte le schede della rete locale.
   - *Valore*: `FF:FF:FF:FF:FF:FF`.

---

### Indirizzi Globali vs Locali:
- **Penultimo bit del primo byte = 0**: L'indirizzo è **unico a livello mondiale** (amministrato via OUI dall'IEEE).
- **Penultimo bit del primo byte = 1**: L'indirizzo è **amministrato localmente** (utilissimo per assegnare indirizzi MAC personalizzati a macchine virtuali e schede di rete virtualizzate).

---

### 🧭 Navigazione Gerarchica
- ⬆️ **Nodo Padre:** [[Rete]]
- ⬅️ **Passo Precedente:** [[Sottolivello MAC]]
- ➡️ **Passo Successivo:** [[Sottolivello LLC]]
