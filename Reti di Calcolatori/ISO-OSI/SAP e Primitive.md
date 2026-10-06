Nel [[Modello ISO-OSI]], l'interazione tra strati adiacenti e tra entità dello stesso livello avviene tramite punti di accesso logici e primitive standardizzate.

### Service Access Point (SAP):
Il **SAP** è il punto logico in cui uno strato $N$ eroga i propri servizi allo strato superiore $N+1$.
- Garantisce l'**indipendenza funzionale**: lo strato $N+1$ non deve conoscere il funzionamento interno dello strato $N$, ma solo la sua interfaccia tramite il SAP.

---

### Flusso delle Primitive di Servizio:

```mermaid
sequenceDiagram
    participant U1 as Entità Utente A (N+1)
    participant S1 as Entità Strato N (Mittente)
    participant S2 as Entità Strato N (Destinatario)
    participant U2 as Entità Utente B (N+1)

    U1->>S1: 1. Request (Richiesta via SAP)
    S1->>S2: Protocollo di Strato N (N-PDU)
    S2->>U2: 2. Indication (Indicazione via SAP)
    U2->>S2: 3. Response (Risposta via SAP)
    S2->>S1: Consegna Risposta
    S1->>U1: 4. Confirm (Conferma via SAP)
```

### Le 4 Primitive:
1. **Richiesta (*Request*)**: L'utente $N+1$ invoca l'esecuzione di un servizio dallo strato sottostante $N$.
2. **Indicazione (*Indication*)**: Lo strato $N$ notifica all'utente destinatario $N+1$ l’arrivo di una richiesta di servizio.
3. **Risposta (*Response*)**: L'utente destinatario $N+1$ fornisce la risposta al servizio richiesto.
4. **Conferma (*Confirm*)**: Lo strato $N$ notifica all'utente mittente $N+1$ l'esito della richiesta originaria.

---

### 🧭 Navigazione Gerarchica
- ⬆️ **Nodo Padre:** [[Rete]]
- ⬅️ **Passo Precedente:** [[PDU e Incapsulamento]]
- ➡️ **Passo Successivo:** [[Servizi Connessi e Non Connessi]]
