Nel [[Modello ISO-OSI]], per tutti i livelli superiori al primo sono previste due modalità operative di comunicazione.

### 1. Servizio Connesso (*Connection-Oriented*):
- **Analogia**: Telefonata.
- **Fasi**:
  1. Instaurazione della connessione (Primitive per presentarsi).
  2. Scambio di messaggi/dati ordinato.
  3. Abbattimento della connessione (Primitive per salutare e rilasciare risorse).

### 2. Servizio Non Connesso (*Connectionless*):
- **Analogia**: E-mail / Lettera postale.
- **Funzionamento**: Ciascun messaggio è inviato separatamente, contenendo l'indirizzo completo del destinatario. Nessun setup preventivo.

---

### Multiplexing tra Livelli:

```mermaid
flowchart TD
    subgraph MultiApp ["Più applicazioni L(N+1) su 1 connessione LN"]
        APP1["App 1 (es. Student Manager)"]
        APP2["App 2 (es. Exam Manager)"]
        CONN1["Connessione di Livello N (es. TCP)"]
        APP1 --> CONN1
        APP2 --> CONN1
    end

    subgraph MultiConn ["1 applicazione L(N+1) su più connessioni LN"]
        FTP["FTP (Servizio Trasferimento File)"]
        C_DATA["Connessione L4 - Dati"]
        C_CTRL["Connessione L4 - Comandi"]
        FTP --> C_DATA
        FTP --> C_CTRL
    end
```

---

### 🧭 Navigazione Gerarchica
- ⬆️ **Nodo Padre:** [[Rete]]
- ⬅️ **Passo Precedente:** [[SAP e Primitive]]
- ➡️ **Passo Successivo:** [[Progetto IEEE 802]]
