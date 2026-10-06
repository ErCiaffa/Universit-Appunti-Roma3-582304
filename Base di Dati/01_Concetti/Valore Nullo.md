# ❓ Valore Nullo (`NULL`)

Rappresenta l'assenza di un valore all'interno di un attributo di una riga.

### Significati del `NULL`:
1. **Dato Sconosciuto:** Il valore esiste nel mondo reale ma non è attualmente noto (es. data di nascita non ancora registrata).
2. **Dato Inapplicabile:** L'attributo non ha senso per quel determinato record (es. numero di patente per chi non guida).

> [!WARNING]
> Non usare mai valori convenzionali ("fantoccio") come `0`, `-1` o stringhe vuote `""` per indicare dati assenti, altrimenti le funzioni aggregate (es. `AVG()`, `COUNT()`) produrranno risultati errati.

---

### 🧭 Navigazione Gerarchica
- ⬆️ **Nodo Padre:** [[Base di Dati]]
- ⬅️ **Passo Precedente:** [[Schema e Istanza]]
- ➡️ **Passo Successivo:** [[Modello Relazionale]]
