---
aliases:
  - Spettro del Segnale Campionato
  - Repliche Spettrali
tags:
  - università/sistemi-embedded
  - campionamento
date: 2026-10-01
---

# 📊 Spettro del Segnale Campionato — Perché Nascono le Repliche?

> [!ABSTRACT] Il Fenomeno a Parole Povere
> Quando campioni un segnale continuo nel tempo a intervalli regolari di passo $T$, nel dominio della frequenza succede una cosa pazzesca:  
> **Lo spettro originale non cambia forma, ma viene COPIATO E INCOLLATO ALL'INFINITO ad ogni multiplo della pulsazione di campionamento $\omega_s = \frac{2\pi}{T}$!**

---

## 🎨 1. Grafico: Lo Spettro si Moltiplica all'Infinito!

Guarda cosa succede alle frequenze del segnale prima e dopo il campionatore:

<svg viewBox="0 0 540 260" width="100%" style="background:#0f172a; border-radius:8px; margin: 15px 0;">
  <!-- 1. SPETTRO CONTINUO ORIGINALE -->
  <g transform="translate(40, 20)">
    <text x="0" y="0" fill="#38bdf8" font-family="system-ui, sans-serif" font-size="12" font-weight="bold">1. Spettro Continuo Originale |X(jω)|</text>
    <line x1="20" y1="80" x2="440" y2="80" stroke="#475569" stroke-width="1.5" />
    <line x1="230" y1="90" x2="230" y2="15" stroke="#475569" stroke-width="1.5" />
    <text x="445" y="84" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">ω</text>

    <!-- Triangolo banda base -->
    <polygon points="170,80 230,25 290,80" fill="#38bdf8" fill-opacity="0.25" stroke="#38bdf8" stroke-width="2.5" />
    <text x="230" y="96" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">0</text>
    <text x="170" y="96" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">-ωc</text>
    <text x="290" y="96" text-anchor="middle" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="10">+ωc</text>
    <text x="230" y="60" text-anchor="middle" fill="#38bdf8" font-family="system-ui, sans-serif" font-size="10" font-weight="bold">Banda Base</text>
  </g>

  <!-- 2. SPETTRO CAMPIONATO (PERIODICO) -->
  <g transform="translate(40, 140)">
    <text x="0" y="0" fill="#10b981" font-family="system-ui, sans-serif" font-size="12" font-weight="bold">2. Spettro Campionato |X*(jω)| — Repliche Periodiche</text>
    <line x1="20" y1="80" x2="440" y2="80" stroke="#475569" stroke-width="1.5" />
    <line x1="230" y1="90" x2="230" y2="15" stroke="#475569" stroke-width="1.5" />
    <text x="445" y="84" fill="#94a3b8" font-family="system-ui, sans-serif" font-size="11">ω</text>

    <!-- Replica Sinistra n=-1 (a -omega_s = x=90) -->
    <polygon points="30,80 90,25 150,80" fill="#14b8a6" fill-opacity="0.2" stroke="#14b8a6" stroke-width="2" />
    <text x="90" y="96" text-anchor="middle" fill="#14b8a6" font-family="system-ui, sans-serif" font-size="10">-ωs</text>
    <text x="90" y="60" text-anchor="middle" fill="#14b8a6" font-family="system-ui, sans-serif" font-size="9">Copia -1</text>

    <!-- Banda Base n=0 (a 0 = x=230) -->
    <polygon points="170,80 230,25 290,80" fill="#38bdf8" fill-opacity="0.3" stroke="#38bdf8" stroke-width="2.5" />
    <text x="230" y="96" text-anchor="middle" fill="#38bdf8" font-family="system-ui, sans-serif" font-size="10">0</text>
    <text x="230" y="60" text-anchor="middle" fill="#38bdf8" font-family="system-ui, sans-serif" font-size="9" font-weight="bold">Banda Base</text>

    <!-- Replica Destra n=+1 (a +omega_s = x=370) -->
    <polygon points="310,80 370,25 430,80" fill="#14b8a6" fill-opacity="0.2" stroke="#14b8a6" stroke-width="2" />
    <text x="370" y="96" text-anchor="middle" fill="#14b8a6" font-family="system-ui, sans-serif" font-size="10">+ωs</text>
    <text x="370" y="60" text-anchor="middle" fill="#14b8a6" font-family="system-ui, sans-serif" font-size="9">Copia +1</text>
  </g>
</svg>

Formula matematica dello spettro campionato:
$$\mathbf{X^*(j\omega) = \frac{1}{T} \sum_{n=-\infty}^{+\infty} X(j(\omega - n \omega_s))}$$

A parole:
- Per $n = 0$: è la **banda base** (il segnale originale pulito, scalato di $1/T$).
- Per $n = \pm 1, \pm 2, \dots$: sono le **infinite repliche periodiche** centrate su $\pm \omega_s, \pm 2\omega_s, \dots$.

---

## 🔍 2. Perché Succede? (La Dimostrazione in 3 Passaggi)

1. Il treno di impulsi $\delta_T(t)$ è periodico. Per la **Serie di Fourier** è formato dalla somma di infinite sinusoidi a frequenze multiple di $\omega_s$:
   $$\delta_T(t) = \frac{1}{T} \sum_{n=-\infty}^{+\infty} e^{j n \omega_s t}$$
2. Il segnale campionato è il prodotto nel tempo:
   $$x^*(t) = x(t) \cdot \delta_T(t) = \frac{1}{T} \sum_{n=-\infty}^{+\infty} x(t) \cdot e^{j n \omega_s t}$$
3. Ricordando che moltiplicare per $e^{j n \omega_s t}$ nel tempo significa **traslare la frequenza di $n\omega_s$**, ogni termine genera una copia identica posizionata su $n\omega_s$:
   $$X^*(j\omega) = \frac{1}{T} \sum_{n=-\infty}^{+\infty} X(j(\omega - n \omega_s)) \quad \blacksquare$$

> [!IMPORTANT] La Morale per l'Ingegnere
> Finché queste repliche rimangono separate tra loro, il segnale è integro al 100%!  
> Ma se campioni troppo piano, le repliche si scontrano ed entra in gioco l'**[[Teorema di Shannon e Aliasing|Aliasing]]**.

---

### 🧭 Flusso di Elaborazione
- ⬅️ **Passo Precedente:** [[Campionamento Impulsivo]]
- ➡️ **Passo Successivo:** [[Teorema di Shannon e Aliasing]]
