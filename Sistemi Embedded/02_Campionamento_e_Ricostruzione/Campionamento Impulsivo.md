---
aliases:
  - Campionamento Impulsivo
  - Treno di Impulsi
  - Pettine di Dirac
tags:
  - università/sistemi-embedded
  - campionamento
date: 2026-10-01
---

# ⏱️ Campionamento Impulsivo — Scattare Foto al Segnale

> [!ABSTRACT] Cos'è il Campionamento a Parole Povere?
> È come scattare una **fotografia col flash** al segnale analogico una volta ogni $T$ secondi.  
> Tra una foto e l'altra, il campionatore non guarda cosa succede: cattura solo il valore istantaneo $x(kT)$ e lo passa al convertitore ADC del microcontrollore.

---

## 📸 1. Grafico: Come Funziona il Campionatore Ideale

Possiamo modellare matematicamente il campionamento come il prodotto tra il segnale continuo $x(t)$ e un **pettine di impulsi di Dirac** $\delta_T(t)$:

<svg viewBox="0 0 540 280" width="100%" style="background:#0f172a; border-radius:8px; margin: 15px 0;">
  <!-- 1. Segnale continuo x(t) -->
  <g transform="translate(20, 15)">
    <text x="0" y="10" fill="#38bdf8" font-family="system-ui, sans-serif" font-size="11" font-weight="bold">1. Segnale Continuo x(t)</text>
    <line x1="0" y1="55" x2="230" y2="55" stroke="#475569" stroke-width="1.5" />
    <path d="M 0,55 Q 60,10 115,40 T 230,55" fill="none" stroke="#38bdf8" stroke-width="2.5" />
  </g>

  <!-- Simbolo Moltiplicazione -->
  <text x="265" y="55" text-anchor="middle" fill="#f8fafc" font-family="system-ui, sans-serif" font-size="20" font-weight="bold">✖</text>

  <!-- 2. Pettine di impulsi delta_T(t) -->
  <g transform="translate(290, 15)">
    <text x="0" y="10" fill="#a855f7" font-family="system-ui, sans-serif" font-size="11" font-weight="bold">2. Pettine di Dirac δ_T(t)</text>
    <line x1="0" y1="55" x2="230" y2="55" stroke="#475569" stroke-width="1.5" />
    <line x1="20" y1="55" x2="20" y2="20" stroke="#a855f7" stroke-width="2" />
    <line x1="65" y1="55" x2="65" y2="20" stroke="#a855f7" stroke-width="2" />
    <line x1="110" y1="55" x2="110" y2="20" stroke="#a855f7" stroke-width="2" />
    <line x1="155" y1="55" x2="155" y2="20" stroke="#a855f7" stroke-width="2" />
    <line x1="200" y1="55" x2="200" y2="20" stroke="#a855f7" stroke-width="2" />
    <text x="20" y="68" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="9">0</text>
    <text x="65" y="68" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="9">T</text>
    <text x="110" y="68" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="9">2T</text>
    <text x="155" y="68" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="9">3T</text>
  </g>

  <!-- Freccia verso il basso -->
  <line x1="270" y1="85" x2="270" y2="120" stroke="#64748b" stroke-width="2" />
  <polygon points="270,126 265,118 275,118" fill="#64748b" />

  <!-- 3. Segnale Campionato x*(t) -->
  <g transform="translate(70, 140)">
    <text x="200" y="0" text-anchor="middle" fill="#10b981" font-family="system-ui, sans-serif" font-size="13" font-weight="bold">3. Segnale Campionato x*(t) = ∑ x(kT) · δ(t - kT)</text>
    <line x1="20" y1="85" x2="380" y2="85" stroke="#475569" stroke-width="2" />
    <line x1="40" y1="85" x2="40" y2="10" stroke="#64748b" stroke-width="1.5" />

    <!-- Impulsi pesati -->
    <!-- k=0 (y=55) -->
    <line x1="40" y1="85" x2="40" y2="85" stroke="#10b981" stroke-width="2.5" />
    <circle cx="40" cy="85" r="3.5" fill="#10b981" />
    <text x="40" y="100" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">0</text>

    <!-- k=1 (y=45) -->
    <line x1="100" y1="85" x2="100" y2="35" stroke="#10b981" stroke-width="2.5" />
    <circle cx="100" cy="35" r="4" fill="#10b981" />
    <text x="100" y="100" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">T</text>

    <!-- k=2 (y=30) -->
    <line x1="160" y1="85" x2="160" y2="40" stroke="#10b981" stroke-width="2.5" />
    <circle cx="160" cy="40" r="4" fill="#10b981" />
    <text x="160" y="100" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">2T</text>

    <!-- k=3 (y=20) -->
    <line x1="220" y1="85" x2="220" y2="60" stroke="#10b981" stroke-width="2.5" />
    <circle cx="220" cy="60" r="4" fill="#10b981" />
    <text x="220" y="100" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">3T</text>

    <!-- k=4 (y=10) -->
    <line x1="280" y1="85" x2="280" y2="75" stroke="#10b981" stroke-width="2.5" />
    <circle cx="280" cy="75" r="4" fill="#10b981" />
    <text x="280" y="100" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">4T</text>
  </g>
</svg>

Formula matematica:
$$\mathbf{x^*(t) = x(t) \cdot \delta_T(t) = \sum_{k=0}^{\infty} x(kT) \cdot \delta(t - kT)}$$

---

## 🌉 2. Da Laplace a Z: La Dimostrazione Più Bella dell'Ingegneria

Ti sei mai chiesto da dove salta fuori la formula $z = e^{sT}$?  
Ecco la dimostrazione in 2 righe:

1. **Facciamo la Trasformata di Laplace del segnale campionato $x^*(t)$:**  
   $$X^*(s) = \mathcal{L}[x^*(t)] = \sum_{k=0}^{\infty} x(kT) \cdot \mathcal{L}[\delta(t - kT)]$$
   Ricordando che la delta di Dirac ritardata di $kT$ ha trasformata $e^{-kTs}$:
   $$X^*(s) = \sum_{k=0}^{\infty} x(kT) \cdot e^{-kTs} = \sum_{k=0}^{\infty} x(kT) \cdot (e^{sT})^{-k}$$

2. **Guarda bene questa sommatoria:**  
   Se al posto di $e^{sT}$ scrivi la lettera **$z$**:
   $$\mathbf{X(z) = \sum_{k=0}^{\infty} x(kT) \cdot z^{-k}}$$

> [!IMPORTANT] L'Intuizione Chiave
> **La Trasformata Z non è altro che la Trasformata di Laplace del segnale campionato**, in cui abbiamo semplicemente rinominato $e^{sT}$ con la lettera $z$!

---

### 🧭 Flusso di Elaborazione
- ➡️ **Prossimo Passo (Cosa Succede alle Frequenze):** [[Spettro del Segnale Campionato]]
