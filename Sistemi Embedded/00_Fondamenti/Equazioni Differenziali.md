---
aliases:
  - Equazioni Differenziali
  - Discretizzazione
tags:
  - università/sistemi-embedded
  - fondamenti
date: 2026-10-01
---

# ⚙️ Equazioni Differenziali — Come Diventano Codice

> [!ABSTRACT] Il Problema a Parole Povere
> Nel mondo reale tutto è **continuo e liscio**: la velocità di un motore, la temperatura, la carica di una batteria. Queste grandezze si descrivono con le **derivate** ($dy/dt$).  
> Ma un **microcontrollore non può fare derivate continue**: ha un clock che batte a scatti ogni $T$ secondi.  
> **La soluzione:** Sostituire la derivata con la differenza tra il valore di *adesso* e quello di *prima*.

---

## 📈 1. Grafico: Continuo vs Discreto

Guarda la differenza tra il segnale analogico continuo e ciò che campiona il microcontrollore a passi regolari $T$:

<svg viewBox="0 0 540 240" width="100%" style="background:#0f172a; border-radius:8px; margin: 15px 0;">
  <defs>
    <marker id="arr2" markerWidth="8" markerHeight="8" refX="6" refY="4" orient="auto">
      <path d="M1,1 L7,4 L1,7 Z" fill="#94a3b8" />
    </marker>
  </defs>

  <!-- Assi -->
  <line x1="40" y1="200" x2="500" y2="200" stroke="#475569" stroke-width="2" marker-end="url(#arr2)" />
  <line x1="40" y1="200" x2="40" y2="20" stroke="#475569" stroke-width="2" marker-end="url(#arr2)" />
  <text x="505" y="205" fill="#f8fafc" font-family="system-ui, sans-serif" font-size="12" font-weight="bold">Tempo t</text>
  <text x="40" y="14" fill="#f8fafc" font-family="system-ui, sans-serif" font-size="12" font-weight="bold">y(t)</text>

  <!-- Curva Continua Liscia (Blu) -->
  <path d="M 40,200 Q 150,40 480,45" fill="none" stroke="#38bdf8" stroke-width="3" />
  <text x="320" y="35" fill="#38bdf8" font-family="system-ui, sans-serif" font-size="13" font-weight="bold">Segnale Continuo Reale y(t)</text>

  <!-- Campioni Discreti (Rossi a spillo) -->
  <!-- t=0 -->
  <circle cx="40" cy="200" r="4.5" fill="#f43f5e" />
  <text x="40" y="220" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">0</text>

  <!-- t=T (x=100, y=145) -->
  <line x1="100" y1="200" x2="100" y2="145" stroke="#f43f5e" stroke-width="1.5" stroke-dasharray="3" />
  <circle cx="100" cy="145" r="4.5" fill="#f43f5e" />
  <text x="100" y="220" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">T</text>

  <!-- t=2T (x=160, y=105) -->
  <line x1="160" y1="200" x2="160" y2="105" stroke="#f43f5e" stroke-width="1.5" stroke-dasharray="3" />
  <circle cx="160" cy="105" r="4.5" fill="#f43f5e" />
  <text x="160" y="220" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">2T</text>

  <!-- t=3T (x=220, y=78) -->
  <line x1="220" y1="200" x2="220" y2="78" stroke="#f43f5e" stroke-width="1.5" stroke-dasharray="3" />
  <circle cx="220" cy="78" r="4.5" fill="#f43f5e" />
  <text x="220" y="220" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">3T</text>

  <!-- t=4T (x=280, y=60) -->
  <line x1="280" y1="200" x2="280" y2="60" stroke="#f43f5e" stroke-width="1.5" stroke-dasharray="3" />
  <circle cx="280" cy="60" r="4.5" fill="#f43f5e" />
  <text x="280" y="220" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">4T</text>

  <!-- t=5T (x=340, y=50) -->
  <line x1="340" y1="200" x2="340" y2="50" stroke="#f43f5e" stroke-width="1.5" stroke-dasharray="3" />
  <circle cx="340" cy="50" r="4.5" fill="#f43f5e" />
  <text x="340" y="220" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">5T</text>

  <!-- t=6T (x=400, y=46) -->
  <line x1="400" y1="200" x2="400" y2="46" stroke="#f43f5e" stroke-width="1.5" stroke-dasharray="3" />
  <circle cx="400" cy="46" r="4.5" fill="#f43f5e" />
  <text x="400" y="220" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">6T</text>

  <text x="230" y="160" fill="#f43f5e" font-family="system-ui, sans-serif" font-size="13" font-weight="bold">• Campioni Discreti Letti dal Microcontrollore {y_k}</text>
</svg>

---

## ✂️ 2. Il Trucco della Discretizzazione

La derivata continua $\frac{dy}{dt}$ per definizione matematica è:
$$\frac{dy}{dt} = \lim_{\Delta t \to 0} \frac{y(t) - y(t - \Delta t)}{\Delta t}$$

Ma la CPU non può fare $\Delta t \to 0$. L'intervallo più piccolo che conosce è il suo **passo di campionamento $T$**.  
Sostituiamo quindi la derivata continua con la **differenza finita**:

$$\left. \frac{dy}{dt} \right|_{t=kT} \approx \frac{y_k - y_{k-1}}{T} = \frac{\text{Nuovo Valore} - \text{Vecchio Valore}}{\text{Passo di Tempo } T}$$

---

## 🧪 3. Esempio Pratico: Il Filtro RC Diventa Algoritmo

Prendiamo il circuito filtro passa-basso analogico RC:

<svg viewBox="0 0 520 180" width="100%" style="background:#0f172a; border-radius:8px; margin: 15px 0;">
  <!-- Linea ingresso -->
  <circle cx="40" cy="60" r="4" fill="none" stroke="#38bdf8" stroke-width="2" />
  <text x="30" y="45" fill="#38bdf8" font-family="system-ui, sans-serif" font-size="13" font-weight="bold">e(t)</text>
  <line x1="44" y1="60" x2="110" y2="60" stroke="#f8fafc" stroke-width="2" />

  <!-- Resistenza R -->
  <rect x="110" y="45" width="80" height="30" fill="#1e293b" stroke="#f59e0b" stroke-width="2" rx="4" />
  <text x="150" y="65" text-anchor="middle" fill="#f59e0b" font-family="system-ui, sans-serif" font-size="13" font-weight="bold">R</text>

  <!-- Collegamento intermedio -->
  <line x1="190" y1="60" x2="290" y2="60" stroke="#f8fafc" stroke-width="2" />
  <circle cx="290" cy="60" r="4" fill="#38bdf8" />

  <!-- Uscita u(t) -->
  <line x1="290" y1="60" x2="450" y2="60" stroke="#f8fafc" stroke-width="2" />
  <circle cx="454" cy="60" r="4" fill="none" stroke="#38bdf8" stroke-width="2" />
  <text x="465" y="65" fill="#38bdf8" font-family="system-ui, sans-serif" font-size="13" font-weight="bold">u(t) (Uscita)</text>

  <!-- Condensatore C verso massa -->
  <line x1="290" y1="64" x2="290" y2="105" stroke="#f8fafc" stroke-width="2" />
  <line x1="265" y1="105" x2="315" y2="105" stroke="#10b981" stroke-width="3" />
  <line x1="265" y1="115" x2="315" y2="115" stroke="#10b981" stroke-width="3" />
  <text x="325" y="114" fill="#10b981" font-family="system-ui, sans-serif" font-size="13" font-weight="bold">C</text>
  <line x1="290" y1="115" x2="290" y2="145" stroke="#f8fafc" stroke-width="2" />

  <!-- Massa GND -->
  <line x1="275" y1="145" x2="305" y2="145" stroke="#94a3b8" stroke-width="2" />
  <line x1="280" y1="151" x2="300" y2="151" stroke="#94a3b8" stroke-width="2" />
  <line x1="285" y1="157" x2="295" y2="157" stroke="#94a3b8" stroke-width="2" />
  <text x="290" y="173" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">GND (0V)</text>
</svg>

### I 3 Passaggi Algebrici:
1. **Legge fisica continua:**  
   $$\tau \frac{du(t)}{dt} + u(t) = e(t) \qquad (\text{con } \tau = R \cdot C)$$
2. **Sostituiamo la derivata con la differenza:**  
   $$\tau \left[ \frac{u_k - u_{k-1}}{T} \right] + u_k = e_k$$
3. **Isoliamo l'uscita $u_k$ da calcolare nella CPU:**  
   Moltiplicando per $T$ e raccogliendo:
   $$(\tau + T) u_k = \tau u_{k-1} + T e_k \implies \mathbf{u_k = \alpha \cdot u_{k-1} + (1 - \alpha) \cdot e_k}$$
   *(dove $\alpha = \frac{\tau}{\tau + T}$ è il fattore di smorzamento tra $0$ e $1$)*.

---

## 💻 4. Il Codice in C per Microcontrollore

```c
float alpha = 0.85f;     // Peso della memoria passata
float u_prev = 0.0f;    // Registro RAM che ricorda u_(k-1)

void Step_Controllo(void) {
    float e_k = Leggi_ADC();                            // Lettura analogica
    float u_k = alpha * u_prev + (1.0f - alpha) * e_k; // Equazione alle differenze
    Scrivi_DAC(u_k);                                   // Attuatore
    u_prev = u_k;                                      // Aggiornamento registro
}
```

---

### 🧭 Navigazione
- ⬆️ **Master Hub:** [[Sistemi Embedded]]
- ➡️ **Passo Successivo:** [[Equazioni alle Differenze]]
