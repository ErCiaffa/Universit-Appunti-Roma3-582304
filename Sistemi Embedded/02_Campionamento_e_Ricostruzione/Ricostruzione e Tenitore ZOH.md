---
aliases:
  - Ricostruzione del Segnale
  - Tenitore ZOH
  - Zero Order Hold
tags:
  - università/sistemi-embedded
  - campionamento
date: 2026-10-01
---

# 🔄 Ricostruzione del Segnale e Tenitore ZOH

> [!ABSTRACT] Il Problema a Parole Povere
> Il microcontrollore ha finito i calcoli e ha prodotto una sequenza di numeri in memoria: $\{u_0, u_1, u_2, \dots\}$.  
> Ma l'attuatore fisico (un motore, una valvola, un altoparlante) **non capisce i numeri astratti: ha bisogno di una tensione elettrica reale continua nel tempo $u(t)$!**  
> Come trasformiamo i numeri in una tensione continua? Questo è il lavoro del convertitore DAC (**Ricostruzione**).

---

## 🏛️ 1. Il Ricostruttore Ideale (Filtro Sinc) e Perché NON Funziona nella Realtà

In teoria, la matematica dice che puoi ricostruire una curva continua perfetta usando la funzione **cardinale sinc**:
$$x(t) = \sum_{k=-\infty}^{+\infty} x(kT) \cdot \text{sinc}\left(\frac{\omega_s (t - kT)}{2}\right)$$

<svg viewBox="0 0 540 180" width="100%" style="background:#0f172a; border-radius:8px; margin: 15px 0;">
  <line x1="30" y1="120" x2="510" y2="120" stroke="#475569" stroke-width="1.5" />
  <line x1="270" y1="150" x2="270" y2="20" stroke="#475569" stroke-width="1.5" />
  <text x="515" y="124" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">t</text>
  <text x="270" y="14" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">sinc(t)</text>

  <!-- Curva Sinc -->
  <path d="M 50,120 Q 80,123 110,120 Q 140,113 170,120 Q 210,140 235,120 Q 255,20 270,20 Q 285,20 305,120 Q 330,140 370,120 Q 400,113 430,120 Q 460,123 490,120" fill="none" stroke="#c084fc" stroke-width="2.5" />

  <circle cx="270" cy="20" r="5" fill="#c084fc" />
  <text x="280" y="25" fill="#c084fc" font-family="system-ui, sans-serif" font-size="12" font-weight="bold">Campione di Adesso</text>
  <text x="140" y="70" text-anchor="middle" fill="#f43f5e" font-family="system-ui, sans-serif" font-size="11" font-weight="bold">← Richiede campioni futuri!</text>
  <text x="400" y="70" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">Campioni passati →</text>
</svg>

> [!CAUTION] Perché è Impossibile nei Sistemi di Controllo Embedded?
> 1. **È NON-CAUSALE:** Per calcolare la tensione del motore in questo istante, la sinc richiede di conoscere **tutti i campioni futuri all'infinito ($k \to +\infty$)**! Nessun microcontrollore può prevedere il futuro.
> 2. Se ritardi il filtro per renderlo causale, introduci un ritardo enorme che destabilizza e fa oscillare il controllo in anello chiuso!

---

## ⚡ 2. Grafico: Il Tenitore di Ordine Zero (ZOH) Reale

La soluzione geniale e semplice adottata in ogni DAC hardware è lo **ZOH (Zero Order Hold)**:  
*"Ricevi un numero dal microcontrollore e mantieni la tensione COSTANTE fino al prossimo campione!"*

<svg viewBox="0 0 540 220" width="100%" style="background:#0f172a; border-radius:8px; margin: 15px 0;">
  <line x1="40" y1="180" x2="500" y2="180" stroke="#475569" stroke-width="1.5" />
  <line x1="50" y1="190" x2="50" y2="20" stroke="#475569" stroke-width="1.5" />
  <text x="505" y="184" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">Tempo t</text>
  <text x="50" y="14" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">Tensione (V)</text>

  <!-- Curva Continua Originale (Blu Tratteggiata) -->
  <path d="M 50,180 Q 140,50 480,55" fill="none" stroke="#38bdf8" stroke-width="2" stroke-dasharray="4" />
  <text x="320" y="45" fill="#38bdf8" font-family="system-ui, sans-serif" font-size="12" font-weight="bold">Segnale Continuo Ideale</text>

  <!-- Gradini ZOH Reali (Rosso vivo) -->
  <path d="M 50,180 H 120 V 130 H 190 V 90 H 260 V 68 H 330 V 58 H 400 V 54 H 470" fill="none" stroke="#f43f5e" stroke-width="3" />
  <text x="210" y="150" fill="#f43f5e" font-family="system-ui, sans-serif" font-size="13" font-weight="bold">• Uscita Reale a Gradini dello ZOH (DAC)</text>

  <!-- Etichette temporali T -->
  <text x="50" y="200" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">0</text>
  <text x="120" y="200" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">T</text>
  <text x="190" y="200" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">2T</text>
  <text x="260" y="200" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">3T</text>
  <text x="330" y="200" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">4T</text>
  <text x="400" y="200" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">5T</text>
</svg>

---

## 📐 3. Funzione di Trasferimento dello ZOH

Un singolo gradino di durata $T$ è dato dalla differenza tra un gradino che parte a $t=0$ e uno che si sottrae a $t=T$:
$$g_0(t) = 1(t) - 1(t - T)$$

Facendo la Trasformata di Laplace:
$$\mathcal{L}[1(t) - 1(t - T)] = \frac{1}{s} - \frac{e^{-Ts}}{s} = \frac{1 - e^{-Ts}}{s}$$

La funzione di trasferimento continua dello ZOH è quindi:
$$\mathbf{H_0(s) = \frac{1 - e^{-Ts}}{s}}$$

---

## ⏱️ 4. Grafico: Il Ritardo Medio di Mezzo Passo ($T/2$)

Guarda l'errore tra il gradino piatto dello ZOH e la salita continua del segnale reale:

<svg viewBox="0 0 540 160" width="100%" style="background:#0f172a; border-radius:8px; margin: 15px 0;">
  <line x1="40" y1="120" x2="480" y2="120" stroke="#475569" stroke-width="1.5" />
  <line x1="80" y1="135" x2="80" y2="20" stroke="#475569" stroke-width="1.5" />
  <text x="485" y="124" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">t</text>
  <text x="80" y="14" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">u(t)</text>

  <!-- Salita continua reale (Blu tratteggiata) -->
  <line x1="80" y1="100" x2="380" y2="30" stroke="#38bdf8" stroke-width="2.5" stroke-dasharray="4" />
  <text x="390" y="35" fill="#38bdf8" font-family="system-ui, sans-serif" font-size="11" font-weight="bold">Continuo</text>

  <!-- Gradino ZOH (Rosso continuo) -->
  <path d="M 80,100 H 230 V 65 H 380" fill="none" stroke="#f43f5e" stroke-width="3" />
  <text x="235" y="100" fill="#f43f5e" font-family="system-ui, sans-serif" font-size="11" font-weight="bold">Gradino ZOH</text>

  <!-- Ritardo medio T/2 -->
  <line x1="155" y1="100" x2="155" y2="82" stroke="#f59e0b" stroke-width="2.5" />
  <circle cx="155" cy="82" r="3" fill="#f59e0b" />
  <text x="165" y="93" fill="#f59e0b" font-family="system-ui, sans-serif" font-size="12" font-weight="bold">Ritardo Medio: τ = T/2</text>

  <text x="80" y="138" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">0</text>
  <text x="230" y="138" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">T</text>
  <text x="380" y="138" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">2T</text>
</svg>

> [!IMPORTANT] La Regola d'Oro dello ZOH
> In media, il gradino dello ZOH è in ritardo di **mezzo periodo di campionamento**:
> $$\mathbf{\tau_{delay} = \frac{T}{2}}$$
> Questo ritardo introduce una perdita di fase ($\Delta \phi = -\omega \frac{T}{2}$) che il progettista del controllo deve sempre compensare per non far oscillare il sistema!

---

### 🧭 Navigazione
- ⬅️ **Passo Precedente:** [[Teorema di Shannon e Aliasing]]
- ⬆️ **Torna al Master Hub:** [[Sistemi Embedded]]
