# 🛡️ Vincoli di Integrità

Un **vincolo di integrità** è una regola espressa tramite un predicato booleano che l'istanza della base di dati deve sempre soddisfare per essere ritenuta corretta.

### Tipologie di Vincoli:

1. **Vincoli Intrarelazionali (Singola Tabella):**
   - **Vincolo di Dominio:** Limita i valori ammissibili di un singolo attributo (es. `Età >= 18`).
   - **Vincolo di Ennupla:** Regola tra più attributi della stessa riga (es. `Lode` ammessa solo se `Voto = 30`).
   - **Vincoli di Chiave:** Garantiscono l'univocità delle righe tramite [[Chiave Primaria]].

2. **Vincoli Interrelazionali (Più Tabelle):**
   - [[Integrità Referenziale]] (`FOREIGN KEY`): Mantiene coerenti i legami e i riferimenti tra tabelle diverse.

---

### 🧭 Navigazione Gerarchica
- ⬆️ **Nodo Padre:** [[Base di Dati]]
- ⬅️ **Passo Precedente:** [[Strutture Nidificate]]
- ➡️ **Passo Successivo:** [[Chiave Primaria]]
