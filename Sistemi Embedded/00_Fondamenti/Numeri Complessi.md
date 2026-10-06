---
aliases:
  - Numeri Complessi
  - Piano Complesso
  - Formula di Eulero
tags:
  - università/sistemi-embedded
  - fondamenti
date: 2026-10-01
---

# 🎯 Numeri Complessi — Guida Visiva per Ingegneria

> [!ABSTRACT] Cos'è un numero complesso a parole povere?
> È semplicemente una **freccia sul piano bidimensionale**.  
> Ci serve perché con un solo numero possiamo tenere insieme due informazioni fisiche vitali:  
> 1. **Quanto è forte il segnale** (Lunghezza della freccia = **Modulo** o Ampiezza $\rho$).
> 2. **Come sta oscillando** (Direzione della freccia = **Angolo** o Fase $\theta$).

In ingegneria usiamo la lettera **$j$** ($j^2 = -1$) per non confonderla con la corrente $i$.

---

## 📊 1. Grafico: Il Piano Complesso di Gauss

Un numero complesso può essere scritto come coordinate cartesiane ($a + jb$) o polari ($\rho e^{j\theta}$):

<svg viewBox="0 0 520 260" width="100%" style="background:#0f172a; border-radius:8px; margin: 15px 0;">
  <defs>
    <marker id="arr" markerWidth="8" markerHeight="8" refX="6" refY="4" orient="auto">
      <path d="M1,1 L7,4 L1,7 Z" fill="#94a3b8" />
    </marker>
    <marker id="arr-blue" markerWidth="8" markerHeight="8" refX="6" refY="4" orient="auto">
      <path d="M1,1 L7,4 L1,7 Z" fill="#38bdf8" />
    </marker>
    <marker id="arr-purple" markerWidth="8" markerHeight="8" refX="6" refY="4" orient="auto">
      <path d="M1,1 L7,4 L1,7 Z" fill="#c084fc" />
    </marker>
  </defs>

  <!-- Assi -->
  <line x1="50" y1="130" x2="480" y2="130" stroke="#475569" stroke-width="2" marker-end="url(#arr)" />
  <line x1="120" y1="240" x2="120" y2="20" stroke="#475569" stroke-width="2" marker-end="url(#arr)" />
  <text x="490" y="135" fill="#f8fafc" font-family="system-ui, sans-serif" font-size="13" font-weight="bold">Re (Reale)</text>
  <text x="120" y="14" text-anchor="middle" fill="#f8fafc" font-family="system-ui, sans-serif" font-size="13" font-weight="bold">Im (Immaginario)</text>

  <!-- Linee tratteggiate coordinate -->
  <line x1="320" y1="130" x2="320" y2="50" stroke="#64748b" stroke-width="1.5" stroke-dasharray="4" />
  <line x1="120" y1="50" x2="320" y2="50" stroke="#64748b" stroke-width="1.5" stroke-dasharray="4" />
  <line x1="320" y1="130" x2="320" y2="210" stroke="#64748b" stroke-width="1.5" stroke-dasharray="4" />
  <line x1="120" y1="210" x2="320" y2="210" stroke="#64748b" stroke-width="1.5" stroke-dasharray="4" />

  <!-- Etichette coordinate a, b, -b -->
  <text x="320" y="148" text-anchor="middle" fill="#38bdf8" font-family="system-ui, sans-serif" font-size="13" font-weight="bold">a</text>
  <text x="105" y="55" text-anchor="end" fill="#38bdf8" font-family="system-ui, sans-serif" font-size="13" font-weight="bold">b</text>
  <text x="105" y="215" text-anchor="end" fill="#c084fc" font-family="system-ui, sans-serif" font-size="13" font-weight="bold">-b</text>

  <!-- Arco fase theta -->
  <path d="M 180,130 A 60 60 0 0 0 172,106" fill="none" stroke="#f59e0b" stroke-width="2" />
  <text x="190" y="112" fill="#f59e0b" font-family="system-ui, sans-serif" font-size="13" font-weight="bold">θ (Fase)</text>

  <!-- Vettore z -->
  <line x1="120" y1="130" x2="315" y2="52" stroke="#38bdf8" stroke-width="3" marker-end="url(#arr-blue)" />
  <circle cx="320" cy="50" r="5" fill="#38bdf8" />
  <text x="330" y="45" fill="#38bdf8" font-family="system-ui, sans-serif" font-size="14" font-weight="bold">z = a + jb = ρ · e^(jθ)</text>
  <text x="210" y="75" fill="#38bdf8" font-family="system-ui, sans-serif" font-size="12" font-style="italic">ρ (Modulo)</text>

  <!-- Vettore Coniugato z* -->
  <line x1="120" y1="130" x2="315" y2="208" stroke="#c084fc" stroke-width="2.5" stroke-dasharray="6" marker-end="url(#arr-purple)" />
  <circle cx="320" cy="210" r="4.5" fill="#c084fc" />
  <text x="330" y="215" fill="#c084fc" font-family="system-ui, sans-serif" font-size="13" font-weight="bold">z* = a - jb (Coniugato)</text>
</svg>

A parole:
- **Forma Cartesiana ($z = a + j b$):** ti dice le coordinate cartesiane. Comoda per fare **somme** e **sottrarre** segnali.
- **Forma Polare ($z = \rho e^{j\theta}$):** ti dice la lunghezza $\rho = \sqrt{a^2 + b^2}$ e l'angolo $\theta = \arctan(b/a)$. Comoda per **moltiplicare** e capire le **rotazioni**.

---

## 🔄 2. La Regola d'Oro: Moltiplicare = Far Ruotare la Freccia!

Cosa succede se moltiplichi un numero complesso per un esponenziale immaginario $e^{j\Delta\theta}$?
$$( \rho e^{j\theta} ) \cdot e^{j\Delta\theta} = \rho \cdot e^{j(\theta + \Delta\theta)}$$

- **La lunghezza $\rho$ rimane identica.**
- **L'angolo aumenta di $\Delta\theta$ (la freccia ruota in senso antiorario)!**

> [!TIP] L'Intuizione Fisica
> Un'onda sinusoidale nel tempo non è altro che **una freccia a lunghezza fissa che continua a ruotare in tondo** sul piano complesso alla velocità angolare $\omega$.

---

## 🌊 3. La Formula di Eulero

La celebre formula di Eulero dice a parole: *"un esponenziale complesso rotante è la somma di una coordinata orizzontale (coseno) e una verticale (seno)"*:

$$e^{j\theta} = \cos(\theta) + j\sin(\theta)$$

### Formule Inverse di Eulero (Indispensabili per calcolare le trasformate):
$$\cos(\theta) = \frac{e^{j\theta} + e^{-j\theta}}{2} \qquad \sin(\theta) = \frac{e^{j\theta} - e^{-j\theta}}{2j}$$

---

## ⭕ 4. Grafico: Il Cerchio Unitario e il Criterio di Stabilità

Nei sistemi digitali discreti a microcontrollore, la variabile è $z = e^{sT}$.  
La posizione dei poli rispetto al **Cerchio Unitario ($|z| = 1$)** decide il destino del sistema:

<svg viewBox="0 0 520 280" width="100%" style="background:#0f172a; border-radius:8px; margin: 15px 0;">
  <defs>
    <radialGradient id="stableGrad" cx="50%" cy="50%" r="50%">
      <stop offset="0%" stop-color="#10b981" stop-opacity="0.3" />
      <stop offset="100%" stop-color="#10b981" stop-opacity="0.1" />
    </radialGradient>
  </defs>

  <!-- Assi -->
  <line x1="40" y1="140" x2="480" y2="140" stroke="#475569" stroke-width="2" marker-end="url(#arr)" />
  <line x1="260" y1="260" x2="260" y2="20" stroke="#475569" stroke-width="2" marker-end="url(#arr)" />
  <text x="490" y="145" fill="#f8fafc" font-family="system-ui, sans-serif" font-size="13" font-weight="bold">Re</text>
  <text x="260" y="14" text-anchor="middle" fill="#f8fafc" font-family="system-ui, sans-serif" font-size="13" font-weight="bold">Im</text>

  <!-- Disco Stabile Interno -->
  <circle cx="260" cy="140" r="95" fill="url(#stableGrad)" />

  <!-- Circonferenza Unitaria -->
  <circle cx="260" cy="140" r="95" fill="none" stroke="#38bdf8" stroke-width="3" />
  <text x="365" y="135" fill="#38bdf8" font-family="system-ui, sans-serif" font-size="12" font-weight="bold">+1</text>
  <text x="145" y="135" fill="#38bdf8" font-family="system-ui, sans-serif" font-size="12" font-weight="bold">-1</text>
  <text x="268" y="40" fill="#38bdf8" font-family="system-ui, sans-serif" font-size="12" font-weight="bold">+j</text>
  <text x="268" y="248" fill="#38bdf8" font-family="system-ui, sans-serif" font-size="12" font-weight="bold">-j</text>
  <text x="325" y="70" fill="#38bdf8" font-family="system-ui, sans-serif" font-size="13" font-weight="bold">|z| = 1</text>

  <!-- Testo e Polo Stabile -->
  <circle cx="210" cy="115" r="5" fill="#10b981" />
  <text x="260" y="175" text-anchor="middle" fill="#10b981" font-family="system-ui, sans-serif" font-size="14" font-weight="bold">ZONA STABILE (|z| &lt; 1)</text>
  <text x="200" y="105" text-anchor="end" fill="#10b981" font-family="system-ui, sans-serif" font-size="12" font-weight="bold">Polo OK (si spegne)</text>

  <!-- Testo e Polo Instabile -->
  <circle cx="390" cy="80" r="5" fill="#f43f5e" />
  <text x="400" y="75" fill="#f43f5e" font-family="system-ui, sans-serif" font-size="12" font-weight="bold">Polo KO (esplode!)</text>
  <text x="430" y="230" text-anchor="middle" fill="#f43f5e" font-family="system-ui, sans-serif" font-size="14" font-weight="bold">ZONA INSTABILE (|z| &gt; 1)</text>

  <!-- Polo Oscillante sul bordo -->
  <circle cx="260" cy="45" r="5" fill="#f59e0b" />
  <text x="270" y="50" fill="#f59e0b" font-family="system-ui, sans-serif" font-size="12" font-weight="bold">Oscillazione continua</text>
</svg>

- **Poli DENTRO al cerchio ($|z| < 1$):** ad ogni passo temporale la potenza $(z)^k$ rimpicciolisce verso zero $\implies$ **STABILE**.
- **Poli SUL cerchio ($|z| = 1$):** la risposta oscilla perennemente senza mai fermarsi $\implies$ **LIMITE DI STABILITÀ**.
- **Poli FUORI dal cerchio ($|z| > 1$):** ad ogni passo la potenza $(z)^k$ cresce verso l'infinito $\implies$ **INSTABILE**.

---

### 🧭 Navigazione
- ⬆️ **Master Hub:** [[Sistemi Embedded]]
- ➡️ **Passo Successivo:** [[Equazioni Differenziali]]
