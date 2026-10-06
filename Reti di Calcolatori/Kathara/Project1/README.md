# 🧪 Laboratorio Kathará: Due PC e un Router (Project1)

Questo è un laboratorio pratico minimale e funzionante pronto all'uso, progettato per apprendere le basi del routing IP in **Kathará**.

---

## 🗺️ Topologia della Rete

```
[ pc1 ] (192.168.1.1/24)
   | eth0
===+================= Dominio "A" (LAN 1: 192.168.1.0/24)
   | eth0
[ router ] (eth0: 192.168.1.254/24  |  eth1: 192.168.2.254/24)
   | eth1
===+================= Dominio "B" (LAN 2: 192.168.2.0/24)
   | eth0
[ pc2 ] (192.168.2.1/24)
```

---

## 🚀 Come Avviare il Laboratorio

1. Apri un terminale in questa cartella (`Project1`).
2. Avvia la rete con il comando:
   ```bash
   kathara lstart
   ```
   *Verranno aperti automaticamente 3 terminali grafici, uno per ciascuna macchina virtuale (`pc1`, `router`, `pc2`).*

3. **Verifica della connettività:**
   Dentro il terminale di `pc1`, prova a raggiungere `pc2` con il ping:
   ```bash
   ping 192.168.2.1
   ```
   *Dovresti vedere le risposte con `ttl=63` (il router ha scalato 1 hop).*

4. **Tracciamento del percorso:**
   Sempre dentro `pc1`, esegui:
   ```bash
   traceroute -n 192.168.2.1
   ```
   *Noterai l'hop intermedio sul router `192.168.1.254` e poi l'arrivo su `192.168.2.1`.*

5. **Spegnimento pulito:**
   Quando hai finito, torna nel terminale del tuo PC e digita:
   ```bash
   kathara lclean
   ```

---

## 📂 File del Progetto

- `lab.conf`: Mappa delle connessioni fisiche (chi è attaccato a cosa).
- `pc1.startup`: Configurazione IP e default gateway per `pc1`.
- `router.startup`: Configurazione delle due schede (`eth0`, `eth1`) e abilitazione del forwarding IP (`net.ipv4.ip_forward=1`).
- `pc2.startup`: Configurazione IP e default gateway per `pc2`.
