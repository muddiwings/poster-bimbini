# Poster Animato — Specifica di Design

## Overview

Poster per bambini animato in HTML a partire da file SVG creati in Illustrator. L'utente (designer) indica quali gruppi animare, e l'animazione viene applicata automaticamente a tutti i personaggi del poster in loop.

## File SVG

### poster principale.svg
6 personaggi con gruppi identificati da `id`:
- `viola` — personaggio viola (in alto)
- `verde` — personaggio verde (in alto)
- `blu` — personaggio blu (al centro)
- `arancione` — personaggio arancione (al centro)
- `rosso` — personaggio rosso (in alto)
- `giallo` — personaggio giallo (in basso)

Contiene anche testo e decorazioni in gruppi senza id specifico.

### poster secondario.svg
Versioni modificate degli stessi personaggi (sembrano "schiacciati"):
- `viola_schiacciato`, `verde_schiacciato`, `blu_schiacciato`, `arancione_schiacciato`, `rosso_schiacciato`, `giallo_schiacciato`
- Elementi aggiuntivi: cerchi decorativi, barra inferiore

## Architettura

Singolo file `index.html` contenente:
1. **SVG inline** — il poster principale copiato direttamente nell'HTML
2. **CSS animazioni** — classi CSS con `@keyframes` per ogni tipo di movimento
3. **JavaScript leggero** — che gestisce:
   - Applicazione delle animazioni ai gruppi
   - Sfasamento temporale tra personaggi (`animation-delay`)
   - Loop infinito (`animation-iteration-count: infinite`)
   - Aggiunta/rimozione di elementi su richiesta
   - Selezione di tutti i gruppi con un colpo solo: l'utente indica un gruppo, il JS applica a tutti

## Flusso di lavoro

1. Poster visibile subito al caricamento della pagina
2. L'utente dice "fai X al gruppo viola"
3. Lo sviluppatore scrive il CSS `@keyframes` per quell'animazione
4. Il JS applica l'animazione a tutti i 6 personaggi con uno sfasamento
5. L'animazione loopa all'infinito
6. Quando serve, l'utente chiede di aggiungere/togliere elementi dal poster secondario

## Tipi di animazione previsti

- **Movimenti**: traslazione (su/giù, destra/sinistra), rotazione
- **Distorsioni**: scala non uniforme, skew, deformazioni
- **Combinate**: più trasformazioni in sequenza

## Loop

Tutte le animazioni hanno `infinite` come iterazione. Quando serve una sequenza complessa, si usa `animation-delay` su più fasi o una timeline JavaScript.

## Prossimi passi

Scrivere l'HTML con il poster principale incorporato e il sistema base JavaScript/CSS pronto per ricevere animazioni.
