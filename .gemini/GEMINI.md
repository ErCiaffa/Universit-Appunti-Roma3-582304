# 📌 Regole di Formattazione e Struttura Vault Obsidian (Università)

Questo file definisce le linee guida per la generazione e gestione delle note nei corsi dell'Università (es. **Reti di Calcolatori** e **Base di Dati**).

---

## 🏗️ 1. Struttura del Vault ed Architettura delle Note

### Reti di Calcolatori
- **File Principale (Master Hub)**: `Reti di Calcolatori/Rete.md`
- **Sottocartelle di Dettaglio**:
  - `Reti di Calcolatori/Reti/`: Concetti base, LAN, WAN, Banda vs Delay, Mezzi Trasmissivi, Gestione Risorse, Standard.
  - `Reti di Calcolatori/Commutazioni/`: Commutazione di Circuito, Commutazione di Pacchetto, Datagramma, Circuito Virtuale.
  - `Reti di Calcolatori/ISO-OSI/`: Modello ISO-OSI, Livelli OSI, PDU e Incapsulamento, SAP e Primitive, Servizi Connessi/Non Connessi.
  - `Reti di Calcolatori/IEEE 802/`: Progetto IEEE 802, Sottolivello MAC, Indirizzi MAC (EUI-48), Sottolivello LLC, SNAP.

### Base di Dati
- **File Principale (Master Hub)**: `Base di Dati/Base di Dati.md`
- **Sottocartelle di Dettaglio**:
  - `Base di Dati/01_Concetti/`: Concetti base, modelli dei dati, DBMS.
  - `Base di Dati/02_Struttura/`: Modello relazionale, schemi, istanze, tabelle.
  - `Base di Dati/03_Vincoli/`: Vincoli di integrità (chiave primaria, FK, not null).
  - `Base di Dati/04_SQL/`: Linguaggio SQL (DDL, DML, DQL).

---

## 🎨 2. Palette Cromatica e Gruppi di Colore (Graph View)

Mantenere la sincronizzazione dei colori sia nei **diagrammi Mermaid** sia nel **Graph View di Obsidian**:

| Corso | Cartella | Colore | Codice Esadecimale / RGB |
|---|---|---|---|
| **Reti** | `Reti` | Giallo / Oro | `#eab308` (RGB: `15381256`) |
| **Reti** | `Commutazioni` | Ciano / Azzurro | `#06b6d4` (RGB: `440020`) |
| **Reti** | `ISO-OSI` | Viola / Magenta | `#a855f7` (RGB: `11031031`) |
| **Reti** | `IEEE 802` | Verde Smeraldo | `#22c55e` (RGB: `2278750`) |
| **Basi Dati** | `01_Concetti` | Celeste / Blu | `#38bdf8` (RGB: `3899638`) |
| **Basi Dati** | `02_Struttura` | Verde Boscoso | `#10b981` (RGB: `1095809`) |
| **Basi Dati** | `03_Vincoli` | Arancione / Rosso | `#f97316` (RGB: `15990622`) |
| **Basi Dati** | `04_SQL` | Viola Chiaro | `#c084fc` (RGB: `16096779`) |

---

## 📝 3. Standard di Scrittura delle Note

1. **Header YAML (Frontmatter)**:
   ```yaml
   ---
   aliases:
     - Nome Alias
   tags:
     - università/reti-di-calcolatori
     - appunti
   date: YYYY-MM-DD
   ---
   ```
2. **Callout Obsidian**: Usare sempre callout formattati (`> [!NOTE]`, `> [!INFO]`, `> [!IMPORTANT]`, `> [!TIP]`, `> [!QUESTION]`, `> [!ABSTRACT]`).
3. **Wikilink (`[[...]]`)**: Collegare sempre ogni concetto alla rispettiva nota atomica.
4. **Diagrammi Mermaid**: Inserire schemi concettuali `flowchart TD` o `sequenceDiagram` ad alta visibilità con `classDef` nei file principali e di approfondimento.
5. **Formule Matematiche**: Usare LaTeX con `$...$` per formule in linea e `$$...$$` per blocchi a sé stanti.
