# 🔗 Integrità Referenziale (`FOREIGN KEY`)

L'**Integrità Referenziale** garantisce la coerenza delle relazioni e dei riferimenti tra tabelle distinte tramite l'uso delle **Chiavi Esterne (`FOREIGN KEY` / FK)**.

### Regola dell'Integrità Referenziale:
Un valore presente nella chiave esterna di una tabella *referenziante* **deve obbligatoriamente esistere** come valore della [[Chiave Primaria]] della tabella *referenziata* (oppure assumere valore [[Valore Nullo]], se consentito).

### Esempio SQL:
```sql
CREATE TABLE Esami (
    ID INT PRIMARY KEY,
    MatricolaStudente INT,
    Voto INT,
    FOREIGN KEY (MatricolaStudente) REFERENCES Studenti(Matricola)
);
```

---

### 🧭 Navigazione Gerarchica
- ⬆️ **Nodo Padre:** [[Base di Dati]]
- ⬅️ **Passo Precedente:** [[Chiave Primaria]]
- ➡️ **Passo Successivo:** [[Comandi Base SQL]]
