# 🧱 Strutture Nidificate

Il **Modello Relazionale** classico ammette unicamente **tabelle piatte** (Prima Forma Normale — 1NF). 

Non è possibile inserire tabelle dentro altre tabelle o attributi multivalore/nidificati direttamente nella stessa riga.

---

## 🛠️ Come si gestiscono le strutture nidificate?

Per rappresentare relazioni gerarchiche o dati nidificati (ad esempio una **Ricevuta Fiscale** composta da un'intestazione e multiple righe di dettaglio), si applica la **scomposizione in più tabelle** collegate tramite [[Integrità Referenziale]].

---

## 📊 Esempio Pratico: Ricevuta Fiscale

Anziché nidificare la lista dei prodotti dentro la ricevuta, si creano **due tabelle correlate**:

### 1. Tabella Testata: `Ricevute`
| Numero (PK) | Data | Totale |
| :---: | :---: | :---: |
| **1235** | 12/10/2024 | € 39,20 |

### 2. Tabella Dettaglio: `RigheDettaglio`
| NumeroRicevuta (PK, FK) | NumRiga (PK) | Descrizione | Quantità | Importo |
| :---: | :---: | :--- | :---: | :---: |
| **1235** | 1 | Coperto | 3 | € 3,00 |
| **1235** | 2 | Antipasto | 1 | € 6,20 |
| **1235** | 3 | Primo | 3 | € 12,00 |

---

## 💻 Rappresentazione in SQL

```sql
-- Tabella Principale (Testata)
CREATE TABLE Ricevute (
    Numero INT PRIMARY KEY,
    Data DATE NOT NULL,
    Totale DECIMAL(10,2) NOT NULL
);

-- Tabella Nidificata/Scomposta (Dettaglio)
CREATE TABLE RigheDettaglio (
    NumeroRicevuta INT,
    NumRiga INT,
    Descrizione VARCHAR(100) NOT NULL,
    Quantita INT NOT NULL,
    Importo DECIMAL(10,2) NOT NULL,
    PRIMARY KEY (NumeroRicevuta, NumRiga),
    FOREIGN KEY (NumeroRicevuta) REFERENCES Ricevute(Numero) ON DELETE CASCADE
);
```

---

### 🧭 Navigazione Gerarchica
- ⬆️ **Nodo Padre:** [[Base di Dati]]
- ⬅️ **Passo Precedente:** [[Modello Relazionale]]
- ➡️ **Passo Successivo:** [[Vincoli di Integrità]]
