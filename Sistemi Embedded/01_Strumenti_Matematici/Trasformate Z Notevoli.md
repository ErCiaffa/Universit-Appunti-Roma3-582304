---
aliases:
  - Trasformate Z Notevoli
  - Tabella Trasformata Z
tags:
  - università/sistemi-embedded
  - tabelle
date: 2026-10-01
---

# 📋 Trasformate Z Notevoli con Grafici dei Segnali

> [!ABSTRACT] A Cosa Serve Questa Pagina?
> Negli esami non si ricalcolano le trasformate da zero. Si usa questa **tabella dei 5 segnali standard** per convertire al volo ogni segnale dal tempo al dominio Z e viceversa.

---

## 🎨 1. I 5 Segnali Standard Disegnati

### 1️⃣ Impulso di Dirac / Kronecker $\delta_0(kT)$
Un solo colpo all'istante $k=0$, poi zero per sempre:

<svg viewBox="0 0 500 120" width="100%" style="background:#0f172a; border-radius:8px; margin: 10px 0;">
  <line x1="30" y1="90" x2="450" y2="90" stroke="#475569" stroke-width="2" />
  <line x1="60" y1="105" x2="60" y2="20" stroke="#475569" stroke-width="2" />
  <text x="460" y="94" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">k</text>
  <text x="60" y="14" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">x(k)</text>

  <!-- Impulso a k=0 -->
  <line x1="60" y1="90" x2="60" y2="35" stroke="#38bdf8" stroke-width="3" />
  <circle cx="60" cy="35" r="5" fill="#38bdf8" />
  <text x="50" y="38" text-anchor="end" fill="#38bdf8" font-family="system-ui, sans-serif" font-size="12" font-weight="bold">1</text>
  <text x="60" y="105" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">0</text>

  <!-- Zeri successivi -->
  <circle cx="120" cy="90" r="3.5" fill="#38bdf8" /><text x="120" y="105" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">1</text>
  <circle cx="180" cy="90" r="3.5" fill="#38bdf8" /><text x="180" y="105" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">2</text>
  <circle cx="240" cy="90" r="3.5" fill="#38bdf8" /><text x="240" y="105" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">3</text>
  <circle cx="300" cy="90" r="3.5" fill="#38bdf8" /><text x="300" y="105" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">4</text>
</svg>

$$\mathbf{\mathcal{Z}[\delta_0(kT)] = 1}$$

---

### 2️⃣ Gradino Unitario $1(kT)$
Accendi a $k=0$ e rimane costante a $1$ per sempre:

<svg viewBox="0 0 500 120" width="100%" style="background:#0f172a; border-radius:8px; margin: 10px 0;">
  <line x1="30" y1="90" x2="450" y2="90" stroke="#475569" stroke-width="2" />
  <line x1="60" y1="105" x2="60" y2="20" stroke="#475569" stroke-width="2" />
  <text x="460" y="94" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">k</text>

  <!-- Stems di altezza 1 -->
  <line x1="60" y1="90" x2="60" y2="40" stroke="#38bdf8" stroke-width="2" /><circle cx="60" cy="40" r="4" fill="#38bdf8" /><text x="60" y="105" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">0</text>
  <line x1="120" y1="90" x2="120" y2="40" stroke="#38bdf8" stroke-width="2" /><circle cx="120" cy="40" r="4" fill="#38bdf8" /><text x="120" y="105" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">1</text>
  <line x1="180" y1="90" x2="180" y2="40" stroke="#38bdf8" stroke-width="2" /><circle cx="180" cy="40" r="4" fill="#38bdf8" /><text x="180" y="105" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">2</text>
  <line x1="240" y1="90" x2="240" y2="40" stroke="#38bdf8" stroke-width="2" /><circle cx="240" cy="40" r="4" fill="#38bdf8" /><text x="240" y="105" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">3</text>
  <line x1="300" y1="90" x2="300" y2="40" stroke="#38bdf8" stroke-width="2" /><circle cx="300" cy="40" r="4" fill="#38bdf8" /><text x="300" y="105" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">4</text>
  <text x="50" y="44" text-anchor="end" fill="#38bdf8" font-family="system-ui, sans-serif" font-size="12" font-weight="bold">1</text>
</svg>

$$\mathbf{\mathcal{Z}[1(kT)] = \frac{1}{1 - z^{-1}} = \frac{z}{z - 1}}$$
*(Polo singolo sul bordo in $z = 1$)*.

---

### 3️⃣ Rampa Unitaria $x(kT) = k \cdot T$
Un segnale che sale costantemente in proporzione al tempo:

<svg viewBox="0 0 500 130" width="100%" style="background:#0f172a; border-radius:8px; margin: 10px 0;">
  <line x1="30" y1="105" x2="450" y2="105" stroke="#475569" stroke-width="2" />
  <line x1="60" y1="115" x2="60" y2="15" stroke="#475569" stroke-width="2" />
  <text x="460" y="109" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">k</text>

  <circle cx="60" cy="105" r="4" fill="#38bdf8" /><text x="60" y="120" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">0</text>
  <line x1="120" y1="105" x2="120" y2="85" stroke="#38bdf8" stroke-width="2" /><circle cx="120" cy="85" r="4" fill="#38bdf8" /><text x="120" y="120" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">1</text>
  <line x1="180" y1="105" x2="180" y2="65" stroke="#38bdf8" stroke-width="2" /><circle cx="180" cy="65" r="4" fill="#38bdf8" /><text x="180" y="120" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">2</text>
  <line x1="240" y1="105" x2="240" y2="45" stroke="#38bdf8" stroke-width="2" /><circle cx="240" cy="45" r="4" fill="#38bdf8" /><text x="240" y="120" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">3</text>
  <line x1="300" y1="105" x2="300" y2="25" stroke="#38bdf8" stroke-width="2" /><circle cx="300" cy="25" r="4" fill="#38bdf8" /><text x="300" y="120" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">4</text>
</svg>

$$\mathbf{\mathcal{Z}[kT] = \frac{T z}{(z - 1)^2}}$$
*(Polo DOPPIO in $z = 1$)*.

---

### 4️⃣ Esponenziale Smorzato $e^{-at}$
La scarica di un condensatore o la decelerazione naturale di un motore:

<svg viewBox="0 0 500 120" width="100%" style="background:#0f172a; border-radius:8px; margin: 10px 0;">
  <line x1="30" y1="95" x2="450" y2="95" stroke="#475569" stroke-width="2" />
  <line x1="60" y1="105" x2="60" y2="15" stroke="#475569" stroke-width="2" />
  <text x="460" y="99" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">k</text>

  <!-- Curva tratteggiata di riferimento -->
  <path d="M 60,30 Q 150,85 360,94" fill="none" stroke="#64748b" stroke-dasharray="3" />

  <line x1="60" y1="95" x2="60" y2="30" stroke="#10b981" stroke-width="2" /><circle cx="60" cy="30" r="4" fill="#10b981" /><text x="60" y="110" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">0</text>
  <line x1="120" y1="95" x2="120" y2="56" stroke="#10b981" stroke-width="2" /><circle cx="120" cy="56" r="4" fill="#10b981" /><text x="120" y="110" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">1</text>
  <line x1="180" y1="95" x2="180" y2="72" stroke="#10b981" stroke-width="2" /><circle cx="180" cy="72" r="4" fill="#10b981" /><text x="180" y="110" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">2</text>
  <line x1="240" y1="95" x2="240" y2="81" stroke="#10b981" stroke-width="2" /><circle cx="240" cy="81" r="4" fill="#10b981" /><text x="240" y="110" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">3</text>
  <line x1="300" y1="95" x2="300" y2="86" stroke="#10b981" stroke-width="2" /><circle cx="300" cy="86" r="4" fill="#10b981" /><text x="300" y="110" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">4</text>
</svg>

$$\mathbf{\mathcal{Z}[e^{-akT}] = \frac{1}{1 - e^{-aT} z^{-1}} = \frac{z}{z - e^{-aT}}}$$
*(Polo reale interno in $z = e^{-aT} < 1$, quindi STABILE!)*.

---

### 5️⃣ Sinusoide Discreta $\sin(\omega k T)$
Un'oscillazione armonica campionata:

<svg viewBox="0 0 500 130" width="100%" style="background:#0f172a; border-radius:8px; margin: 10px 0;">
  <line x1="30" y1="65" x2="450" y2="65" stroke="#475569" stroke-width="2" />
  <line x1="60" y1="115" x2="60" y2="15" stroke="#475569" stroke-width="2" />
  <text x="460" y="69" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">k</text>

  <!-- Curva sinusoidale continua di riferimento -->
  <path d="M 60,65 Q 110,15 160,65 T 260,65 T 360,65 T 460,65" fill="none" stroke="#64748b" stroke-dasharray="3" />

  <circle cx="60" cy="65" r="4" fill="#f59e0b" /><text x="60" y="80" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">0</text>
  <line x1="110" y1="65" x2="110" y2="25" stroke="#f59e0b" stroke-width="2" /><circle cx="110" cy="25" r="4" fill="#f59e0b" /><text x="110" y="80" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">1</text>
  <circle cx="160" cy="65" r="4" fill="#f59e0b" /><text x="160" y="80" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">2</text>
  <line x1="210" y1="65" x2="210" y2="105" stroke="#f59e0b" stroke-width="2" /><circle cx="210" cy="105" r="4" fill="#f59e0b" /><text x="210" y="60" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">3</text>
  <circle cx="260" cy="65" r="4" fill="#f59e0b" /><text x="260" y="80" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">4</text>
  <line x1="310" y1="65" x2="310" y2="25" stroke="#f59e0b" stroke-width="2" /><circle cx="310" cy="25" r="4" fill="#f59e0b" /><text x="310" y="80" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">5</text>
</svg>

$$\mathbf{\mathcal{Z}[\sin(\omega kT)] = \frac{z \sin(\omega T)}{z^2 - 2z\cos(\omega T) + 1}}$$
*(Coppia di poli complessi coniugati posizionati sul cerchio unitario $|z|=1$)*.

---

## 📊 Tabella Riassuntiva per l'Esame

| Segnale nel Tempo $x(k)$ | Forma in $z$ (per i poli) | Forma in $z^{-1}$ (per il codice) | Poli nel Piano $z$ |
|---|---|---|---|
| **Impulso $\delta_0$** | $1$ | $1$ | Nessuno |
| **Gradino $1(k)$** | $\dfrac{z}{z - 1}$ | $\dfrac{1}{1 - z^{-1}}$ | $z = 1$ |
| **Rampa $k T$** | $\dfrac{T z}{(z - 1)^2}$ | $\dfrac{T z^{-1}}{(1 - z^{-1})^2}$ | $z = 1$ (doppio) |
| **Esponenziale $e^{-akT}$** | $\dfrac{z}{z - e^{-aT}}$ | $\dfrac{1}{1 - e^{-aT} z^{-1}}$ | $z = e^{-aT} < 1$ |
| **Seno $\sin(\omega kT)$** | $\dfrac{z \sin(\omega T)}{z^2 - 2z\cos(\omega T) + 1}$ | $\dfrac{z^{-1}\sin(\omega T)}{1 - 2z^{-1}\cos(\omega T) + z^{-2}}$ | Coppia complessa su $|z|=1$ |

---

### 🧭 Navigazione
- ⬆️ **Nodo Padre:** [[Trasformata Z]]
