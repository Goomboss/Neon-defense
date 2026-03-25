# Neon Defense - Schema Ondate (Wave Schema)

Questo documento descrive la composizione delle ondate e le regole di spawn dei nemici in Neon Defense.

## Regole Generali
- Le ondate avanzano in cicli di 3 tipi di nemici base: **Soldier**, **Scout**, **Tank**.
- Ogni 10 ondate (10, 20, 30, 40, 50) viene generato un **Boss**.
- Ad ogni ondata, gli HP e la velocità dei nemici aumentano del **5%** (moltiplicatore `1.05 ^ (wave - 1)`).
- Se non diversamente specificato, un'ondata standard è composta da **15 nemici** dello stesso tipo.

## Schema Dettagliato (Ciclo 1-10)
Questo ciclo si ripete ogni 10 ondate (es. la 11 è come la 1, la 12 come la 2, ecc.) fino alla 50.

| Ondata | Tipo Nemici | Quantità | Note / Drop |
|--------|-------------|----------|-------------|
| **1, 11, 21...** | Soldier | 15 | Ondata standard |
| **2, 12, 22...** | Scout | 15 | Ondata standard |
| **3, 13, 23...** | Carrier + Tank | 1 Carrier, 14 Tank | Il Carrier droppa **1 Sniper Cannon** |
| **4, 14, 24...** | Soldier | 15 | Ondata standard |
| **5, 15, 25...** | Scout | 15 | Ondata standard |
| **6, 16, 26...** | Carrier + Tank | 1 Carrier, 14 Tank | Il Carrier droppa **1 Flamer** |
| **7, 17, 27...** | Soldier / Scout | 20 (10 per tipo) | Spawn alternato (Soldier, Scout, Soldier...) |
| **8, 18, 28...** | Scout | 25 | Ondata sciame |
| **9, 19, 29...** | Mista | 25 | 5 Tank, 7 Soldier, 1 Carrier, 5 Tank, 7 Soldier. Il Carrier droppa **1 Sniper Cannon** |
| **10, 20...**| Boss | 1 | Genera Void Scout e Void Soldier periodicamente |

## Ondate Successive (11-50)
- Il ciclo di 10 ondate si ripete identico, ma i nemici diventano progressivamente più forti (+5% HP e velocità per ondata).
- **Vittoria**: Il gioco termina con successo completando l'ondata 50 (Boss Finale).

## Dettaglio Unità
- **Soldier**: HP medi, velocità media.
- **Scout**: HP bassi, velocità alta.
- **Tank**: HP alti, velocità bassa.
- **Carrier**: HP molto alti, velocità bassa. Rilascia ricompense alla distruzione.
- **Boss**: HP estremi, velocità bassa. Genera minion (Void) ogni 2 secondi. Se raggiunge l'uscita, infligge **5 danni** all'integrità.
- **Void Scout / Void Soldier**: Minion generati dal Boss. Non forniscono crediti.
