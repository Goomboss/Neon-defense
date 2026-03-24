# Neon Defense - Waves Schema (Alpha 1.0)

Questo documento descrive la configurazione e la composizione delle ondate (waves) nemiche in **Neon Defense**.
Il gioco prevede un totale di **50 ondate**, al termine delle quali si ottiene la Vittoria.

## Regole Generali

- **Nemici per ondata standard:** 15 (`KILLS_PER_WAVE = 15`)
- **Scaling Difficoltà:** Ad ogni ondata, gli HP base dei nemici aumentano del 5% (moltiplicatore `1.05^(wave-1)`). *Nota: dalla patch Alpha 1.0 la velocità è diventata costante, lo scaling si applica solo agli HP.*
- **Ciclo base dei nemici:** Il tipo di nemico base cambia ciclicamente ogni 3 ondate.
  - `wt = 1` -> **Soldier** (Intervallo spawn: 60 tick)
  - `wt = 2` -> **Scout** (Intervallo spawn: 30 tick)
  - `wt = 3` -> **Tank** (Intervallo spawn: 72 tick)

## Dettaglio Ondate (1 - 50)

### Ondate Standard (Cicli regolari)
Le ondate che non sono multiple di 10 seguono il ciclo base:
- **Ondate 1, 4, 7, 11, 14, 17, 21...**: 15x Soldier
- **Ondate 2, 5, 8, 12, 15, 18, 22...**: 15x Scout
- **Ondate 13, 16, 19, 23, 26, 29...**: 15x Tank

### Ondate Speciali "Carrier" (Sblocco Sniper)
Nelle ondate 3, 6 e 9, il primo nemico a spawnare è un **Carrier**. L'uccisione di un Carrier sblocca la possibilità di costruire una torretta Sniper.
- **Ondata 3:** 1x Carrier + 14x Tank
- **Ondata 6:** 1x Carrier + 14x Tank
- **Ondata 9:** 1x Carrier + 14x Tank

*Nota: Dopo l'ondata 9 non ci sono più Carrier programmati nello script attuale.*

### Ondate Boss (Ogni 10 ondate)
Le ondate 10, 20, 30, 40 e 50 sono ondate Boss.
- **Composizione:** 1x Boss
- **Meccanica Boss:** Il Boss ha HP molto elevati (100 base) e si muove lentamente. Ogni 120 tick genera un minion, alternando tra `void_scout` e `void_soldier`.
- **Ricompensa:** L'uccisione del Boss fornisce 5 Crediti e termina l'ondata. I minion del vuoto non forniscono crediti.

## Tabella Riassuntiva (Prime 10 Ondate)

| Ondata | Tipo Nemico Principale | Quantità | Note |
|---|---|---|---|
| 1 | Soldier | 15 | |
| 2 | Scout | 15 | |
| 3 | Carrier + Tank | 1 + 14 | Sblocca 1 Sniper |
| 4 | Soldier | 15 | |
| 5 | Scout | 15 | |
| 6 | Carrier + Tank | 1 + 14 | Sblocca 1 Sniper |
| 7 | Soldier | 15 | |
| 8 | Scout | 15 | |
| 9 | Carrier + Tank | 1 + 14 | Sblocca 1 Sniper |
| 10 | Boss | 1 | Genera Void Minions |

*(Il pattern 1-9 si ripete per le decadi successive, escludendo i Carrier che appaiono solo nelle ondate 3, 6 e 9).*
