# Neon Defense: Wave Schedule

Questo documento descrive la progressione delle ondate di nemici in *Neon Defense*.

## Struttura delle Ondate

Il gioco utilizza un sistema misto per la generazione delle ondate:
1. **Ondate Fisse:** Ondate specifiche con composizione predefinita.
2. **Ondate Procedurali:** Ondate generate basandosi sul numero dell'ondata (`wave`).

### Ondate Fisse (Hardcoded)

| Ondata | Composizione |
| :--- | :--- |
| **3** | 1x Carrier, 10x Soldier, 5x Tank |
| **4** | 20x Soldier |
| **5** | 10x Scout, 20x Fleet |
| **6** | 1x Carrier, 20x Tank |
| **11** | 35x Soldier |
| **12** | 35x Scout |
| **13** | 10x Soldier, 1x Decoy Tank, 9x Tank |
| **14** | 40x Fleet, 1x Carrier |
| **15** | 20x Tank, 20x Scout |
| **16** | 20x Soldier, 2x Decoy Tank, 5x Tank |
| **17** | 40x Tank, 2x Carrier |
| **18** | 30x Soldier, 30x Scout |
| **19** | 10x Tank, 1x Decoy Tank, 5x Tank, 30x Fleet |
| **21** | 5x Air Soldier, 50x Soldier |
| **22** | 1x Carrier, 70x Scout |
| **23** | 60x Soldier |
| **24** | 10x Air Soldier, 20x Scout, 20x Fleet, 10x Tank |
| **25** | 3x Splitter |

### Ondate Procedurali

Per le ondate non elencate sopra, la composizione viene calcolata in base a `w = wave % 10` e `wt = ((wave - 1) % 3) + 1`.

*   **Boss (w = 0):** 1x Boss
*   **Ondata 7 (w = 7):** 10x Soldier, 10x Scout
*   **Ondata 8 (w = 8):** 25x [Tipo variabile basato su `wt`]
    *   `wt=1`: Soldier
    *   `wt=2`: Scout
    *   `wt=3`: Tank
*   **Ondata 9 (w = 9):** 10x Tank, 14x Soldier, 1x Carrier
*   **Altre Ondate:**
    *   Se `w = 3` o `w = 6`: 1x Carrier, 14x [Tipo variabile basato su `wt`]
    *   Altrimenti: 15x [Tipo variabile basato su `wt`]

*Nota: Il "Tipo variabile" (`type`) segue la rotazione: 1=Soldier, 2=Scout, 3=Tank.*
