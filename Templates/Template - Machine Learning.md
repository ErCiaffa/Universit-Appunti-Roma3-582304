---
aliases:
  - {{title}}
tags:
  - università/machine-learning
  - ai
  - {{categoria_tag}}
date: {{date}}
---

# 🤖 {{title}}

Definizione sintetica del modello, algoritmo di apprendimento o tecnica di ottimizzazione (supervisionato, non supervisionato, reinforcement learning).

---

## 💡 1. Intuizione Geometrica e Obiettivo del Modello

Cosa cerca di fare l'algoritmo nello spazio delle feature:

```mermaid
flowchart LR
    DATA["Dataset (X, y)<br/>Train & Val"] --> PRE["Pre-processing<br/>Scaling & Encoding"]
    PRE --> MODEL["<b>Algoritmo / Rete Neurale</b><br/>Parametri W, b"]
    MODEL --> LOSS["Funzione di Costo J(θ)<br/>Calcolo Errore"]
    LOSS --> OPT["Ottimizzatore (es. Adam, SGD)<br/>Aggiornamento Pesi"]

    classDef mlNode fill:#1e1b4b,stroke:#6366f1,stroke-width:2px,color:#fff;
    class DATA,PRE,MODEL,LOSS,OPT mlNode;
```

> [!INFO] Scheda del Modello
> - **Tipo:** Supervisionato / Non Supervisionato
> - **Compito:** Regressione / Classificazione / Clustering / Riduzione Dimensionalità
> - **Spazio di Ipotesi:** Lineare / Albero / Rete Neurale Profonda

---

## 📐 2. Formulazione Matematica: Loss & Ottimizzazione

Funzione obiettivo da minimizzare o massimizzare:

$$\mathcal{L}(\theta) = \frac{1}{N} \sum_{i=1}^N \ell(y_i, f_\theta(x_i)) + \lambda \Omega(\theta)$$

- **Termine di Fitting (Loss):** Misura l'errore di predizione sui dati di training.
- **Termine di Regolarizzazione $\Omega(\theta)$:** Previene l'overfitting ($L_1$ Lasso, $L_2$ Ridge/Weight Decay).

### Regola di Aggiornamento dei Parametri (Discesa del Gradiente):
$$\theta^{(t+1)} = \theta^{(t)} - \eta \nabla_\theta \mathcal{L}(\theta)$$

---

## 🐍 3. Implementazione Python (Scikit-Learn / PyTorch)

Codice minimale, leggibile e commentato:

```python
import numpy as np
import torch
import torch.nn as nn

# Esempio di definizione o utilizzo del modello
```

---

## 🧭 Navigazione Gerarchica

- ⬆️ **Nodo Padre:** [[Nome_Hub_o_Modulo]]
- ➡️ **Passo Successivo:** [[Prossimo_Argomento]]
