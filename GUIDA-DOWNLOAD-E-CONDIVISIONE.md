# Sfoglia: guida per scaricare, installare e condividere

## 1. Dove trovare la chiave API di Gemini

1. Apri [Google AI Studio — API Keys](https://aistudio.google.com/api-keys) e accedi con il tuo account Google.
2. Premi **Create API key** (o **Crea chiave API**). Se richiesto, seleziona o crea un progetto Google.
3. Copia la chiave e non pubblicarla, non inviarla in chat e non inserirla nei file dell'app.
4. Apri Sfoglia → **Profilo** → incolla la chiave nel campo **Chiave API Gemini** → **Salva chiave**.

Il prototipo conserva la chiave nel browser usato. La richiesta va direttamente a Google. Il livello gratuito di Gemini Flash ha quote/limiti che possono cambiare; nel livello gratuito i prompt possono essere usati per migliorare i prodotti Google. Evita quindi appunti privati o informazioni sensibili.

## 2. Il modo consigliato per installarla sul telefono

Il file ZIP contiene una **PWA**: una piccola app web installabile. Per installarla bene su Android/iPhone, pubblicala prima su un indirizzo HTTPS. Un modo gratuito è GitHub Pages:

Se hai già pubblicato una versione precedente e vuoi aggiornare l'icona, carica nel repository i nuovi `icon-192.png`, `icon-512.png`, `manifest.json` e `sw.js` inclusi nello ZIP, sostituendo i file esistenti. Poi rimuovi e reinstalla la PWA sul dispositivo per aggiornare l'icona.

1. Scarica ed estrai `sfoglia-app.zip` sul computer.
2. Accedi o crea un account su [GitHub](https://github.com/).
3. Crea un nuovo repository, per esempio `sfoglia-app`. Per rendere la pagina pubblica senza costi, scegli **Public**.
4. Dopo l'estrazione, apri la cartella `sfoglia` e carica i suoi file direttamente nella cartella principale del repository: `index.html`, `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png` e i file guida. Non caricare la cartella contenitore come unica sottocartella.
5. Nel repository apri **Settings → Pages**. Sotto **Build and deployment**, scegli **Deploy from a branch**, branch `main`, cartella `/(root)`, quindi **Save**.
6. Attendi la pubblicazione. GitHub mostrerà un indirizzo simile a `https://tuonome.github.io/sfoglia-app/`.
7. Apri quell'indirizzo sul telefono:
   - **Android:** Chrome → menu ⋮ → **Installa app** oppure **Aggiungi a schermata Home**.
   - **iPhone:** apri il link in Safari → pulsante **Condividi** → **Aggiungi alla schermata Home**.

La pubblicazione con repository pubblico rende visibile il codice dell'app: non inserire la chiave API nel repository. La chiave salvata tramite Profilo resta nel browser di ciascuna persona e non è inclusa nel pacchetto.

## 3. Come condividerla

- **Per condividere l'app funzionante:** invia il link HTTPS pubblicato. Chi lo apre può aggiungerlo alla schermata Home.
- **Per condividere i file sorgenti:** invia `sfoglia-app.zip`. Chi lo riceve dovrà estrarlo e pubblicarlo su HTTPS (oppure servirlo da un computer) per installare correttamente la PWA.
- Ogni persona conserva sul proprio dispositivo progressi, salvataggi e la propria chiave API. Non inviare la tua chiave agli altri.

## 4. Se vuoi solo provarla senza pubblicarla

Sul computer, estrai lo ZIP, apri un terminale nella cartella `sfoglia` ed esegui:

```sh
python -m http.server 8000
```

Poi visita `http://localhost:8000`. Questo avvia una prova locale sul computer. Aprire direttamente `index.html` dal file manager del telefono (`file://`) non è il metodo consigliato: installazione PWA, ricerca online e chiamate IA possono non funzionare correttamente.

## 5. Cosa funziona senza connessione

La schermata e i file già memorizzati sul dispositivo possono aprirsi offline dopo il primo caricamento. La ricerca nei cataloghi e la generazione con Gemini richiedono Internet. Il prototipo non sincronizza progressi tra dispositivi e non genera file video: mostra slide animate con voce del telefono.
