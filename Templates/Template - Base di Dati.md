---
aliases:
  - {{title}}
tags:
  - università/base-di-dati
  - database
  - {{modulo_tag}}
date: {{date}}
---

# 🗄️ {{title}}

Definizione sintetica del concetto, vincolo o costrutto all'interno dei sistemi per la gestione di basi di dati (DBMS).

---

## 🎯 1. Concetto Teorico e Formalizzazione Relazionale

Spiegazione formale con notazione relazionale (schemi, domini, tuple):

> [!INFO] Definizione
> Sia $R(A_1, A_2, \dots, A_n)$ uno schema di relazione.  
> Un'istanza $r$ di $R$ è un insieme finito di ennuple (tuple) definite sul prodotto cartesiano dei rispettivi domini.

### Vincoli di Integrità Associati
- **Vincolo Intra-relazionale:** ...
- **Vincolo Inter-relazionale (Foreign Key):** ...

---

## 📊 2. Esempio Pratico su Tabella

Rappresentazione tabellare concreta per visualizzare il comportamento dei dati:

| ID (PK) | Nome | Cognome | Matricola | Dipartimento_ID (FK) |
|---|---|---|---|---|
| `1` | Mario | Rossi | `012345` | `10` |
| `2` | Laura | Bianchi | `012346` | `20` |

---

## 💻 3. Sintassi e Query SQL di Riferimento

Costrutti SQL (DDL per creare/modificare tabelle o DQL/DML per interrogare):

```sql
-- Esempio SQL commentato
SELECT 
    S.Nome, 
    S.Cognome, 
    D.NomeDipartimento
FROM 
    Studenti S
JOIN 
    Dipartimenti D ON S.Dipartimento_ID = D.ID
WHERE 
    S.Matricola LIKE '012%'
ORDER BY 
    S.Cognome ASC;
```

> [!TIP] Ottimizzazione / Best Practice
> Considerazioni sugli indici (B-Tree/Hash), costo temporale del piano di esecuzione o gestione dei valori NULL.

---

## 🧭 Navigazione Gerarchica

- ⬆️ **Nodo Padre:** [[Nome_Hub_o_Modulo]]
- ➡️ **Passo Successivo:** [[Prossimo_Argomento]]
