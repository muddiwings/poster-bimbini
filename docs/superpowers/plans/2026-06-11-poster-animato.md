# Poster Animato Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Creare una pagina HTML singola con il poster animato, pronta per ricevere animazioni su richiesta del designer.

**Architecture:** Unico file `index.html` contenente SVG inline, CSS animazioni, e JavaScript di controllo. Il JS trova i gruppi per ID e applica animazioni a tutti i personaggi con sfasamento.

**Tech Stack:** HTML5, CSS3 (keyframes), Vanilla JavaScript

---

### Task 1: Creare index.html con SVG del poster principale

**Files:**
- Create: `index.html`

- [ ] **Step 1: Leggere il SVG del poster principale e creare la struttura HTML**

Il file HTML conterrà:
- DOCTYPE html, viewport meta, charset UTF-8
- L'SVG completo dal file `poster principale.svg` (tutti i 741 lines) inserito direttamente nell'HTML
- Un `<style>` tag vuoto pronto per le animazioni
- Un `<script>` tag vuoto pronto per il JavaScript
- Sfondo nero o comunque scuro per far risaltare il poster

- [ ] **Step 2: Verificare che il file si apra correttamente**

Aprire `index.html` in un browser e verificare che il poster si veda correttamente con tutti i personaggi.

---

### Task 2: Sistema base animazioni CSS + JavaScript

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Aggiungere il JavaScript base**

Il JS deve:
1. Selezionare i gruppi personaggio noti: `viola`, `verde`, `blu`, `arancione`, `rosso`, `giallo`
2. Fornire una funzione `applicaAnimazione(nomeGruppo, nomeAnimazione, sfasamento)` che:
   - Trova il gruppo di partenza (es. `viola`)
   - Applica la classe CSS con quell'animazione a TUTTI i gruppi
   - Aggiunge un `animation-delay` progressivo (sfasamento) tipo 0s, 0.3s, 0.6s, 0.9s, 1.2s, 1.5s
3. Le animazioni hanno `animation-iteration-count: infinite` di default

- [ ] **Step 2: Aggiungere esempio animazione CSS di test**

```css
@keyframes dondola {
  0%, 100% { transform: rotate(0deg); }
  25% { transform: rotate(-3deg); }
  75% { transform: rotate(3deg); }
}

.anim-dondola {
  animation: dondola 2s ease-in-out infinite;
}
```

E chiamare `applicaAnimazione('viola', 'dondola')` all'avvio per testare.

- [ ] **Step 3: Aprire in browser e verificare**

Tutti i personaggi devono dondolare leggermente con uno sfasamento l'uno dall'altro, e il loop deve essere infinito.

---

### Task 3: Struttura pronta per nuove animazioni

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Predisporre il sistema per ricevere nuove animazioni senza modificare il JS**

Il JS esporrà una funzione globale `aggiungiAnimazione(nome, keyframesCSS)` in modo che io possa aggiungere nuove animazioni semplicemente chiamandola dalla console o aggiungendo righe.

- [ ] **Step 2: Aggiungere animazioni base pronte**

- `fluttua`: movimento su e giù
- `ruota`: rotazione leggera
- `rimpicciolisci`: scala che diminuisce e torna
- `oscilla`: combinazione di rotazione e traslazione
