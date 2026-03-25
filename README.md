# Neon Defense 🛡️⚡

**Neon Defense** è un Tower Defense esagonale con una forte estetica Cyberpunk/Neon, sviluppato interamente in HTML5 Canvas e JavaScript (senza l'uso di engine esterni). 
Il tuo obiettivo è difendere il Mainframe da ondate di dati corrotti (nemici) posizionando torrette difensive strategiche.

## 🎮 Come Funziona il Gioco

1. **La Griglia Esagonale**: Il campo di battaglia è una griglia esagonale. I nemici entrano da un punto di spawn e cercano di raggiungere l'uscita.
2. **Costruzione e Pathfinding**: Puoi spendere Crediti per piazzare torrette (Laser, Sniper, Flamer) sugli esagoni vuoti. Attenzione: il sistema di sicurezza impedisce di bloccare completamente il percorso dei nemici! Ci deve sempre essere almeno una via d'uscita.
3. **Ondate (Waves)**: Il gioco è strutturato in 50 ondate. Il ciclo dei nemici si ripete ogni 10 ondate, ma la loro salute e velocità aumentano progressivamente.
4. **Boss e Minion**: Ogni 10 ondate appare un Boss. I Boss sono lenti ma estremamente resistenti, generano minion (Void) periodicamente e, se raggiungono l'uscita, infliggono danni massicci (5 punti integrità) alla tua base.
5. **Upgrade**: Le torrette possono essere potenziate fino al Livello 3. Al livello massimo, sbloccano modalità di fuoco speciali (es. danni ad area, proiettili perforanti).

## 💡 Curiosità e Dettagli Tecnici (Dietro le quinte)

Essendo un progetto sviluppato da zero, ci sono alcune scelte tecniche molto interessanti sotto il cofano:

* **Audio Procedurale (Zero Asset Esterni)**: Non ci sono file `.mp3` o `.wav` nel gioco! Tutti gli effetti sonori (spari, esplosioni, UI) e la musica di sottofondo sono generati matematicamente in tempo reale utilizzando la **Web Audio API** del browser (tramite oscillatori *sawtooth*, *square* e *sine*).
* **Coordinate Assiali (q, r)**: Gestire una griglia esagonale è molto più complesso di una griglia quadrata. Il gioco utilizza un sistema di coordinate assiali per calcolare le distanze, le adiacenze e per convertire la posizione del mouse (pixel) nell'esagono corretto.
* **Pathfinding BFS Dinamico**: I nemici non seguono un percorso pre-calcolato statico. Ogni volta che piazzi o vendi una torretta, il gioco esegue un algoritmo di **Breadth-First Search (BFS)** per ricalcolare istantaneamente il percorso più breve per tutti i nemici presenti sulla mappa.
* **Scaling Matematico**: La difficoltà non è "hardcoded" per ogni ondata. Utilizza un moltiplicatore esponenziale: `1.05 ^ (wave - 1)`. Questo significa che all'ondata 50 i nemici avranno statistiche moltiplicate per circa 10.9x rispetto all'ondata 1!
* **Drop Dinamici**: Alcuni nemici speciali (i *Carrier*) non rilasciano crediti, ma sbloccano l'accesso a nuove tecnologie (come lo Sniper Cannon all'ondata 3 o il Flamer all'ondata 6).

---
*Progetto sviluppato per testare le potenzialità del Canvas 2D e del Game Design algoritmico.*
