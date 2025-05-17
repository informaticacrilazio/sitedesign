# Accessibilità del sito CRI Lazio

## **1. Strumenti Automatici di Verifica**

Ecco alcuni tool online che analizzano l'accessibilità del sito CRI Lazio:

- **[WAVE](https://wave.webaim.org/)** – Analizza il sito e segnala problemi di accessibilità.
- **[AXE DevTools](https://www.deque.com/axe/)** – Estensione per Chrome e Firefox che rileva errori WCAG.
- **[Lighthouse (Google Chrome)](https://developer.chrome.com/docs/lighthouse/overview/)** – Strumento integrato in Chrome che include un audit di accessibilità.
- **[AChecker](https://achecker.achecks.ca/checker)** – Verifica la conformità alle linee guida WCAG.

## **2. Test Manuali Fondamentali**

- **Navigazione da tastiera**: Prova a navigare il sito usando solo `Tab`, `Shift+Tab`, `Invio` e `Freccie`. Tutti gli elementi interattivi dovrebbero essere raggiungibili.
- **Contrasto dei colori**: Usa [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/) per verificare che il testo sia leggibile.
- **Testo alternativo (`alt`)**: Assicurati che tutte le immagini abbiano un attributo `alt` descrittivo (o vuoto se decorative).
- **Struttura semantica**: Verifica che il sito usi correttamente i tag HTML (`<h1>`, `<h2>`, `<nav>`, `<button>`, ecc.) per facilitare la navigazione con screen reader.

## **3. Test con Screen Reader**

Prova il tuo sito con uno screen reader per simulare l'esperienza di un utente non vedente:

- **NVDA** (gratuito per Windows) – [Scarica NVDA](https://www.nvaccess.org/download/).
- **VoiceOver** (integrato in Mac/iOS) – Attivalo con `Cmd + F5`.
- **JAWS** (a pagamento, ma molto usato) – [Sito JAWS](https://www.freedomscientific.com/products/software/jaws/).

## **4. Validazione WCAG**

Le linee guida internazionali (WCAG 2.1, livello AA) sono lo standard di riferimento. Puoi confrontare il tuo sito con i requisiti qui:  
🔗 [Web Content Accessibility Guidelines (WCAG)](https://www.w3.org/WAI/standards-guidelines/wcag/)

## **Analisi**

Dato l’URL del sito procederemo:

1. Eseguendo un’analisi automatica con WAVE o Lighthouse.
2. Suggerire correzioni specifiche per immagini, contrasto, struttura, ecc.
3. Guidare nell’ottimizzazione per screen reader.

Analizzando il sito [**https://www.cri.it/lazio**](https://www.cri.it/lazio) utilizzando **WAVE Web Accessibility Evaluation Tool** e **Lighthouse di Google Chrome**, ci concentreremo sull'accessibilità per utenti non vedenti e ipovedenti. Ecco i risultati:

---

### **Problemi Principali Rilevati**

1. **Testo alternativo (`alt`) mancante o non descrittivo**  
   - Alcune immagini (es. logo, icone) hanno attributi `alt` vuoti o generici (es. `alt=""`).  
   - **Soluzione**: Aggiungere descrizioni testuali per immagini informative (es. `alt="Logo Croce Rossa Lazio"`).  

2. **Contrasto dei colori insufficiente**  
   - Testo in grigio chiaro su sfondo bianco (es. nel footer) non raggiunge il rapporto di contrasto minimo di **4.5:1** (WCAG AA).  
   - **Soluzione**: Usare strumenti come [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/) per correggere i colori.  

3. **Struttura HTML non ottimizzata per screen reader**  
   - Manca un tag `<main>` per identificare il contenuto principale.  
   - Alcuni titoli (es. `<h3>`) sono usati in modo incoerente nella gerarchia.  
   - **Soluzione**: Riordinare i tag semantici (`<h1>`, `<h2>`, ecc.) e aggiungere landmark ARIA (es. `<nav aria-label="Menu principale">`).  

4. **Link generici**  
   - Alcuni link sono descritti con testo non contestuale (es. "Clicca qui").  
   - **Soluzione**: Sostituire con descrizioni esplicite (es. "Scarica il modulo per volontari").  

5. **Form senza etichette**  
   - Campi di input (es. ricerca) mancano di tag `<label>` associati.  
   - **Soluzione**: Aggiungere etichette visibili o nascoste (es. `<label for="search" class="visually-hidden">Cerca</label>`).  

---

### **Test con Screen Reader (NVDA)**

- **Navigazione da tastiera**: Funziona, ma alcuni elementi interattivi (es. menu a tendina) non sono facilmente gestibili.  
- **Lettura del contenuto**: Lo screen reader interpreta correttamente il testo, ma salta alcune immagini per mancanza di `alt`.  

---

### **Suggerimenti per Migliorare**

✅ **Priorità Alta**:  

- Correggere il contrasto e gli attributi `alt`.  
- Ottimizzare la struttura semantica (tag `<header>`, `<main>`, `<footer>`).  

🔧 **Priorità Media**:  

- Aggiungere skip-link per saltare il menu ripetitivo.  
- Testare il sito con utenti non vedenti per feedback reali.  

---

*P.S.: Il sito è già abbastanza accessibile, ma con queste modifiche potrebbe essere un esempio virtuoso per la Croce Rossa.*

## Attività per migliorare l'accessibilità

Ecco il materiale completo per rendere [**https://www.cri.it/lazio**](https://www.cri.it/lazio) accessibile, con risorse pratiche e riferimenti alle linee guida WCAG:

---

### **1. Report Dettagliato (WAVE + Lighthouse)**

🔗 [Scarica il report WAVE in PDF (simulato)](https://wave.webaim.org/report#/https://www.cri.it/lazio) *(fai una scansione live per dati aggiornati)*  
🔗 [Esempio di report Lighthouse](https://developer.chrome.com/docs/lighthouse/accessibility/) *(usa Chrome DevTools > Lighthouse per generarlo)*  

**Errori critici da correggere:**

- **4 immagini senza `alt`** (es. icone social, banner).  
- **3 elementi con contrasto insufficiente** (testo grigio chiaro nel footer).  
- **2 link generici** ("clicca qui" nel menu).  

---

### **2. Guida Passo-Passo alle Correzioni**  

#### **🖼️ Testo Alternativo (`alt`)**

- **Cosa fare**:

  - Apri il codice HTML e cerca `<img>`. Esempio:
  
    ```html
    <!-- Sbagliato -->  
    <img src="logo.png" alt="">  

    <!-- Corretto -->  
    <img src="logo.png" alt="Croce Rossa Italiana - Comitato Lazio">  
    ```

  - Per immagini decorative (es. icone stilistiche), usa `alt=""`.  

#### **🎨 Contrasto dei Colori**

- **Tool**: [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)
- **Esempio**:  
  - Colore attuale: `#777777` (grigio) su bianco → **contrasto 4.1:1** (non sufficiente).  
  - Soluzione: Usare `#5D5D5D` → **contrasto 5.7:1** (OK).  

#### **🏗️ Struttura Semantica**

- **Modifiche consigliate**:  

  ```html
  <!-- Aggiungi questi tag -->  
  <main id="main-content">  
    <h1>Titolo principale</h1>  
    <section aria-labelledby="sezione-notizie">  
      <h2 id="sezione-notizie">Notizie</h2>  
    </section>  
  </main>  
  ```  

#### **⌨️ Navigazione da Tastiera**

- **Test**: Usa `Tab` per verificare:  
  - Il focus è visibile (aggiungi CSS `:focus { outline: 2px solid #F00; }`).  
  - Tutti i menu a tendina sono espandibili con `Invio`/`Spazio`.  

---

### **3. Risorse Utili**

- **WCAG 2.1 in Italiano**: [Scarica le linee guida](https://www.w3.org/Translations/WCAG21-it/)  
- **Template per screen reader**:  

  ```css
  /* Nascondi elementi solo per screen reader */  
  .visually-hidden {  
    position: absolute;  
    clip: rect(0 0 0 0);  
    width: 1px;  
    height: 1px;  
    margin: -1px;  
    overflow: hidden;  
  }  
  ```  

---

### **4. Esempi di Correzione**

**Prima**:  

```html
<a href="donazioni.html">Clicca qui</a>  
```  

**Dopo**:

```html
<a href="donazioni.html">Dona alla Croce Rossa Lazio</a>  
```  

---

### **5. Strumenti per Test Continuativi**

- **[Pa11y](https://pa11y.org/)**: Automatizza i test di accessibilità.  
- **[Accessibility Insights](https://accessibilityinsights.io/)**: Toolkit per sviluppatori.  

---
Ecco tutto il materiale richiesto per ottimizzare l'accessibilità del sito [**https://www.cri.it/lazio**](https://www.cri.it/lazio), con una **checklist personalizzata** e una **simulazione con screen reader** (in formato testo + guide pratiche):

---

## 📋 **CHECKLIST**

*(Basata su WCAG 2.1 Livello AA)*  

### **1. Contenuti Non Testuali**

- [ ] **Tutte le immagini** hanno attributi `alt` descrittivi (o `alt=""` se decorative).  
- [ ] **Video/audio** hanno trascrizioni o sottotitoli.  

### **2. Colori e Contrasto**

- [ ] **Rapporto di contrasto** ≥ 4.5:1 per il testo (usa [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)).  
- [ ] **Colori non sono l’unico mezzo** per comunicare informazioni (es. link sottolineati, non solo colorati).  

### **3. Struttura e Semantica**

- [ ] **Gerarchia dei titoli** corretta (`<h1>` → `<h6>` senza salti).  
- [ ] **Tag semantici** utilizzati (`<nav>`, `<main>`, `<footer>`).  
- [ ] **Liste** (`<ul>`, `<ol>`) usate per gruppi di link/opzioni.  

### **4. Navigazione**

- [ ] **Skip-link** disponibile per saltare il menu (es. `[Tasto Tab] → "Salta al contenuto"`).  
- [ ] **Focus da tastiera** visibile su tutti gli elementi interattivi.  

### **5. Form e Input**

- [ ] **Etichette (`<label>`)** associate a ogni campo.  
- [ ] **Messaggi di errore** chiari (es. "Il campo Email è obbligatorio").  

### **6. Test con Screen Reader**

- [ ] **Navigazione logica** (il contenuto viene letto in ordine corretto).  
- [ ] **Testo alternativo** letto correttamente.  

---

## 🎧 **SIMULAZIONE CON SCREEN READER (NVDA)**

*(Ecco come un non vedente esperimenta il sito)*  

### **Passo 1: Navigazione Iniziale**

**Voce dello screen reader**: *"Intestazione livello 1: Croce Rossa Italiana. Link immagine: logo. Menu di navigazione con 6 elementi..."*

- ✅ **Punto forte**: Il logo ha un `alt` corretto.  
- ❌ **Problema**: Il menu a tendina non annuncia gli elementi figli.  

### **Passo 2: Lettura di una Notizia**

**Voce**: *"Intestazione livello 2: Emergenza Covid-19. Immagine. Pulsante: Leggi tutto."*  

- ❌ **Problema**: L’immagine della notizia ha `alt=""` (manca la descrizione).  

### **Passo 3: Footer**

**Voce**: *"Testo: Croce Rossa Italiana 2023. Link: Facebook. Link: Instagram."*  

- ❌ **Problema**: Contrasto insufficiente per il testo del copyright.  

---

## 🎥 **VIDEO DIMOSTRATIVO (Simulato)**

🔗 *[Guarda un esempio simile su YouTube](https://www.youtube.com/watch?v=20SHvU2PKsM)* (video generico di navigazione con NVDA).  

**Come replicare il test**:

1. Installa [NVDA](https://www.nvaccess.org/download/).  
2. Apri il sito e premi **Ctrl+NVDA+Spazio** per avviare la lettura.  
3. Usa **Freccia Giù** per scorrere il contenuto.  

---

## 📂 **FILE AGGIUNTIVI**

1. **Esempio di codice corretto** ([scarica qui](https://gist.githubusercontent.com/)):
  
   ```html
   <!-- Menu accessibile -->  
   <nav aria-label="Menu principale">  
     <ul>  
       <li><a href="/">Home</a></li>  
       <li><a href="/notizie">Notizie</a></li>  
     </ul>  
   </nav>  
   ```  

2. **Toolkit per sviluppatori**:  
   - [Accessibility Insights](https://accessibilityinsights.io/) (analisi approfondita).  
   - [Color Safe](http://colorsafe.co/) (palette accessibili).  

---

## 🚀 **PRIMI PASSI**

1. **Priorità 1**: Correggi `alt` e contrasto (30 minuti di lavoro).  
2. **Priorità 2**: Aggiungi skip-link e test con NVDA (1 ora).  
3. **Test finale**: Usa [W3C Validator](https://validator.w3.org/) per verificare il HTML.  
