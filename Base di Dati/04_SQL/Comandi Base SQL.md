# 💻 Comandi Base SQL — Prontuario Rapido

Guida essenziale ai comandi SQL fondamentali per la creazione, gestione e interrogazione di una Base di Dati.

---

## 🛠️ 1. Definizione dei Dati (DDL - Data Definition Language)

### 🔹 Creare una Tabella (`CREATE TABLE`)
```sql
CREATE TABLE Studenti (
    Matricola INT PRIMARY KEY,
    Cognome VARCHAR(50) NOT NULL,
    Nome VARCHAR(50) NOT NULL,
    Email VARCHAR(100) UNIQUE,
    DataIscrizione DATE DEFAULT CURRENT_DATE
);
```

### 🔹 Creare una Tabella con Chiave Esterna (`FOREIGN KEY`)
```sql
CREATE TABLE Esami (
    ID INT PRIMARY KEY AUTO_INCREMENT,
    MatricolaStudente INT,
    Materia VARCHAR(50) NOT NULL,
    Voto INT CHECK (Voto >= 18 AND Voto <= 30),
    FOREIGN KEY (MatricolaStudente) REFERENCES Studenti(Matricola) ON DELETE CASCADE
);
```

### 🔹 Modificare o Eliminare una Tabella (`ALTER` / `DROP`)
```sql
-- Aggiungere una colonna
ALTER TABLE Studenti ADD COLUMN Telefono VARCHAR(15);

-- Eliminare una tabella
DROP TABLE Esami;
```

---

## ✏️ 2. Manipolazione dei Dati (DML - Data Manipulation Language)

### 🔹 Inserire Dati (`INSERT INTO`)
```sql
INSERT INTO Studenti (Matricola, Cognome, Nome, Email)
VALUES (6554, 'Rossi', 'Mario', 'mario.rossi@email.com');
```

### 🔹 Aggiornare Dati (`UPDATE`)
```sql
UPDATE Studenti
SET Email = 'mario.rossi.new@email.com'
WHERE Matricola = 6554;
```

### 🔹 Eliminare Dati (`DELETE`)
```sql
DELETE FROM Studenti
WHERE Matricola = 6554;
```

---

## 🔍 3. Interrogazione dei Dati (DQL - Data Query Language)

### 🔹 Selezionare e Filtrare (`SELECT`, `WHERE`)
```sql
-- Selezionare tutte le colonne
SELECT * FROM Studenti;

-- Selezionare solo cognome e nome degli studenti specifici
SELECT Cognome, Nome 
FROM Studenti 
WHERE DataIscrizione >= '2023-01-01';
```

### 🔹 Ordinare i Risultati (`ORDER BY`)
```sql
SELECT * FROM Studenti 
ORDER BY Cognome ASC, Nome ASC;
```

### 🔹 Unire Tabelle (`JOIN`)
```sql
SELECT S.Matricola, S.Cognome, S.Nome, E.Materia, E.Voto
FROM Studenti S
JOIN Esami E ON S.Matricola = E.MatricolaStudente
WHERE E.Voto >= 24;
```

### 🔹 Raggruppare e Aggregare (`GROUP BY`, `HAVING`, Funzioni aggregate)
Funzioni principali: `COUNT()`, `AVG()`, `SUM()`, `MAX()`, `MIN()`.

```sql
-- Calcolare la media dei voti per ogni studente
SELECT MatricolaStudente, AVG(Voto) AS MediaVoti, COUNT(*) AS NumeroEsami
FROM Esami
GROUP BY MatricolaStudente
HAVING AVG(Voto) >= 27;
```

---

## 💡 Summary Grafico Sintesi SQL

| Categoria | Comando | Descrizione |
| :--- | :--- | :--- |
| **DDL** | `CREATE TABLE` | Crea una nuova tabella con vincoli e tipi di dati |
| **DDL** | `ALTER TABLE` | Modifica la struttura di una tabella esistente |
| **DDL** | `DROP TABLE` | Elimina definitivamente una tabella e i suoi dati |
| **DML** | `INSERT INTO` | Inserisce nuovi record nella tabella |
| **DML** | `UPDATE` | Modifica record esistenti in base a una condizione |
| **DML** | `DELETE` | Elimina record in base a una condizione |
| **DQL** | `SELECT ... FROM` | Recupera dati da una o più tabelle |
| **DQL** | `WHERE` | Filtra le righe prima del raggruppamento |
| **DQL** | `JOIN` | Collega due o più tabelle tramite chiavi (`PK`/`FK`) |
| **DQL** | `GROUP BY / HAVING` | Raggruppa i dati e applica filtri sui gruppi |

---

### 🧭 Navigazione Gerarchica
- ⬆️ **Nodo Padre:** [[Base di Dati]]
- ⬅️ **Passo Precedente:** [[Integrità Referenziale]]
