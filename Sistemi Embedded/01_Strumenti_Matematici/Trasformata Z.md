---
aliases:
  - Trasformata Z
  - Z-Transform
tags:
  - università/sistemi-embedded
  - trasformata-z
date: 2026-10-01
---

# 🌀 Trasformata Z — L'Algebra dei Sistemi Discreti

> [!ABSTRACT] Perché Esiste la Trasformata Z a Parole Povere?
> Risolvere un'equazione alle differenze a mano passo per passo ($u_0, u_1, u_2, \dots$) è lungo e noioso.  
> La **Trasformata Z** è un trucco magico: trasforma i ritardi nel tempo in semplici moltiplicazioni algebriche:
> $$\text{Ritardo di 1 passo nel tempo } u_{k-1} \quad \Longleftrightarrow \quad \text{Moltiplicare per } z^{-1}$$
> In questo modo, un'equazione ricorsiva complicata diventa una **semplice frazione tra polinomi di scuola superiore**!

---

## 📐 1. Definizione Visiva

Data una sequenza di campioni $\{x_0, x_1, x_2, x_3, \dots\}$, la sua trasformata Z è la serie di potenze di $z^{-1}$:

$$\mathbf{X(z) = x_0 + x_1 z^{-1} + x_2 z^{-2} + x_3 z^{-3} + \dots = \sum_{k=0}^{\infty} x_k z^{-k}}$$

> [!NOTE] Chi è la variabile $z$?
> È legata alla variabile continua di Laplace $s = \sigma + j\omega$ mediante la relazione fondamentale:
> $$\mathbf{z = e^{s T}}$$
> dove $T$ è il periodo di campionamento.

---

## 🗺️ 2. Grafico: Mappatura dal Piano $s$ al Piano $z$

Questo è il grafico fondamentale per capire la stabilità dei sistemi digitali:

<svg viewBox="0 0 540 240" width="100%" style="background:#0f172a; border-radius:8px; margin: 15px 0;">
  <defs>
    <radialGradient id="stableZ" cx="50%" cy="50%" r="50%">
      <stop offset="0%" stop-color="#10b981" stop-opacity="0.3" />
      <stop offset="100%" stop-color="#10b981" stop-opacity="0.1" />
    </radialGradient>
    <marker id="arr-map" markerWidth="8" markerHeight="8" refX="6" refY="4" orient="auto">
      <path d="M1,1 L7,4 L1,7 Z" fill="#38bdf8" />
    </marker>
  </defs>

  <!-- PIANO S (Sinistra) -->
  <g transform="translate(10, 20)">
    <text x="90" y="0" text-anchor="middle" fill="#f8fafc" font-family="system-ui, sans-serif" font-size="12" font-weight="bold">PIANO CONTINUO (Laplace s)</text>
    <!-- Zona stabile verde a sinistra -->
    <rect x="10" y="20" width="80" height="170" fill="#10b981" fill-opacity="0.18" />
    <!-- Assi -->
    <line x1="10" y1="105" x2="170" y2="105" stroke="#64748b" stroke-width="1.5" />
    <line x1="90" y1="190" x2="90" y2="20" stroke="#64748b" stroke-width="2" />
    <text x="175" y="109" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">σ</text>
    <text x="90" y="14" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">jω</text>
    <!-- Etichette -->
    <text x="50" y="45" text-anchor="middle" fill="#10b981" font-family="system-ui, sans-serif" font-size="11" font-weight="bold">STABILE</text>
    <text x="50" y="58" text-anchor="middle" fill="#10b981" font-family="system-ui, sans-serif" font-size="9">(σ &lt; 0)</text>
    <text x="130" y="45" text-anchor="middle" fill="#f43f5e" font-family="system-ui, sans-serif" font-size="11" font-weight="bold">INSTABILE</text>
    <!-- Poli s1, s1* -->
    <circle cx="55" cy="70" r="4" fill="#10b981" />
    <circle cx="55" cy="140" r="4" fill="#10b981" />
    <text x="45" y="73" text-anchor="end" fill="#10b981" font-family="system-ui, sans-serif" font-size="10">s₁</text>
  </g>

  <!-- Freccia di trasformazione al centro -->
  <line x1="195" y1="125" x2="275" y2="125" stroke="#38bdf8" stroke-width="3" marker-end="url(#arr-map)" />
  <text x="235" y="115" text-anchor="middle" fill="#38bdf8" font-family="system-ui, sans-serif" font-size="13" font-weight="bold">z = e^(sT)</text>

  <!-- PIANO Z (Destra) -->
  <g transform="translate(290, 20)">
    <text x="130" y="0" text-anchor="middle" fill="#f8fafc" font-family="system-ui, sans-serif" font-size="12" font-weight="bold">PIANO DISCRETO (Z)</text>
    <!-- Disco Stabile Interno -->
    <circle cx="130" cy="105" r="70" fill="url(#stableZ)" />
    <!-- Assi -->
    <line x1="30" y1="105" x2="230" y2="105" stroke="#64748b" stroke-width="1.5" />
    <line x1="130" y1="190" x2="130" y2="20" stroke="#64748b" stroke-width="1.5" />
    <text x="235" y="109" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">Re</text>
    <text x="130" y="14" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">Im</text>
    <!-- Cerchio unitario -->
    <circle cx="130" cy="105" r="70" fill="none" stroke="#38bdf8" stroke-width="2.5" />
    <text x="185" y="45" fill="#38bdf8" font-family="system-ui, sans-serif" font-size="11" font-weight="bold">|z| = 1</text>
    <text x="130" y="110" text-anchor="middle" fill="#10b981" font-family="system-ui, sans-serif" font-size="11" font-weight="bold">STABILE (|z| &lt; 1)</text>
    <text x="210" y="170" fill="#f43f5e" font-family="system-ui, sans-serif" font-size="10" font-weight="bold">INSTABILE</text>
    <!-- Poli z1, z1* -->
    <circle cx="160" cy="80" r="4" fill="#10b981" />
    <circle cx="160" cy="130" r="4" fill="#10b981" />
    <text x="170" y="83" fill="#10b981" font-family="system-ui, sans-serif" font-size="10">z₁</text>
  </g>
</svg>

> [!IMPORTANT] Il Criterio di Stabilità nei Sistemi Embedded
> Tutto il semipiano sinistro continuo ($\text{Re}(s) < 0$) viene compresso **ALL'INTERNO del cerchio unitario** ($|z| < 1$).  
> Un sistema a microcontrollore è **asintoticamente stabile** se e solo se **tutti i poli cadono rigorosamente dentro il cerchio unitario**!

---

## 🎯 3. Grafico: Perché i Poli Fuori Fanno Esplodere il Sistema?

La risposta temporale dovuta a un polo $p$ è proporzionale a $(p)^k$:

<svg viewBox="0 0 540 180" width="100%" style="background:#0f172a; border-radius:8px; margin: 15px 0;">
  <!-- Grafico Sinistra: Stabile |p| = 0.6 -->
  <g transform="translate(30, 20)">
    <text x="100" y="0" text-anchor="middle" fill="#10b981" font-family="system-ui, sans-serif" font-size="12" font-weight="bold">Polo Dentro (|p| = 0.6 &lt; 1)</text>
    <line x1="20" y1="120" x2="200" y2="120" stroke="#64748b" stroke-width="1.5" />
    <line x1="20" y1="120" x2="20" y2="15" stroke="#64748b" stroke-width="1.5" />
    <text x="205" y="124" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">k</text>

    <!-- Stems decaying -->
    <line x1="20" y1="120" x2="20" y2="30" stroke="#10b981" stroke-width="2" />
    <circle cx="20" cy="30" r="3.5" fill="#10b981" />

    <line x1="50" y1="120" x2="50" y2="66" stroke="#10b981" stroke-width="2" />
    <circle cx="50" cy="66" r="3.5" fill="#10b981" />

    <line x1="80" y1="120" x2="80" y2="88" stroke="#10b981" stroke-width="2" />
    <circle cx="80" cy="88" r="3.5" fill="#10b981" />

    <line x1="110" y1="120" x2="110" y2="101" stroke="#10b981" stroke-width="2" />
    <circle cx="110" cy="101" r="3.5" fill="#10b981" />

    <line x1="140" y1="120" x2="140" y2="109" stroke="#10b981" stroke-width="2" />
    <circle cx="140" cy="109" r="3.5" fill="#10b981" />

    <line x1="170" y1="120" x2="170" y2="114" stroke="#10b981" stroke-width="2" />
    <circle cx="170" cy="114" r="3.5" fill="#10b981" />

    <text x="100" y="145" text-anchor="middle" fill="#10b981" font-family="system-ui, sans-serif" font-size="11" font-weight="bold">Decade a Zero (STABILE)</text>
  </g>

  <!-- Grafico Destra: Instabile |p| = 1.4 -->
  <g transform="translate(300, 20)">
    <text x="100" y="0" text-anchor="middle" fill="#f43f5e" font-family="system-ui, sans-serif" font-size="12" font-weight="bold">Polo Fuori (|p| = 1.4 &gt; 1)</text>
    <line x1="20" y1="120" x2="200" y2="120" stroke="#64748b" stroke-width="1.5" />
    <line x1="20" y1="120" x2="20" y2="15" stroke="#64748b" stroke-width="1.5" />
    <text x="205" y="124" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">k</text>

    <!-- Stems exploding -->
    <line x1="20" y1="120" x2="20" y2="110" stroke="#f43f5e" stroke-width="2" />
    <circle cx="20" cy="110" r="3.5" fill="#f43f5e" />

    <line x1="55" y1="120" x2="55" y2="100" stroke="#f43f5e" stroke-width="2" />
    <circle cx="55" cy="100" r="3.5" fill="#f43f5e" />

    <line x1="90" y1="120" x2="90" y2="80" stroke="#f43f5e" stroke-width="2" />
    <circle cx="90" cy="80" r="3.5" fill="#f43f5e" />

    <line x1="125" y1="120" x2="125" y2="50" stroke="#f43f5e" stroke-width="2" />
    <circle cx="125" cy="50" r="3.5" fill="#f43f5e" />

    <line x1="160" y1="120" x2="160" y2="15" stroke="#f43f5e" stroke-width="2" />
    <circle cx="160" cy="15" r="3.5" fill="#f43f5e" />

    <text x="100" y="145" text-anchor="middle" fill="#f43f5e" font-family="system-ui, sans-serif" font-size="11" font-weight="bold">Esplode all'Infinito (INSTABILE)</text>
  </g>
</svg>

---

## 🧮 4. Funzioni Razionali Fratte

Nella pratica, le funzioni nel dominio Z sono rapporti tra polinomi:
$$X(z) = \frac{N(z)}{D(z)} = \frac{b_0 z^m + b_1 z^{m-1} + \dots + b_m}{z^n + a_1 z^{n-1} + \dots + a_n}$$
- Le radici del denominatore ($D(z) = 0$) sono i **POLI** (decidono se il sistema è stabile o instabile).
- Le radici del numeratore ($N(z) = 0$) sono gli **ZERI** (modificano l'ampiezza delle oscillazioni).

---

### 🧭 Ramificazioni
- 🌿 **Proprietà e Teoremi:** [[Proprieta e Teoremi della Trasformata Z]]
- 🌿 **Tavola dei Segnali Notevoli:** [[Trasformate Z Notevoli]]
- 🌿 **Come Tornare al Tempo (Antitrasformare):** [[Antitrasformata Z]]
