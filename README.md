# Sfoglia — prototipo microlearning

Web app mobile-first con feed verticale; dentro ogni micro-lezione le schede si sfogliano orizzontalmente come un carosello fotografico, senza avanzamento automatico. Ogni slide include un'illustrazione SVG animata; un mini quiz aiuta a fissare i concetti. La voce del browser si può mettere in pausa e riprendere sullo stesso punto. Include ricerca libri, salvataggi e progressi sul dispositivo. Le lezioni sono create dall'app; gli utenti non caricano video.

## Avvio

Apri `index.html` per consultare il prototipo. Per la PWA/service worker usa HTTPS o localhost. Dalla cartella `sfoglia`:

```sh
python -m http.server 8000
```

Poi visita `http://localhost:8000`.

## Installazione su telefono e condivisione

Il progetto è una PWA. Per installarlo correttamente su Android o iPhone, pubblica i file su HTTPS (per esempio GitHub Pages) e apri il link sul telefono; poi scegli **Installa app/Aggiungi alla schermata Home**. Vedi [GUIDA-DOWNLOAD-E-CONDIVISIONE.md](GUIDA-DOWNLOAD-E-CONDIVISIONE.md) per i passaggi guidati e per la chiave Gemini. Lo ZIP include icone PNG adatte all'installazione mobile.

## Cercare e generare su un capitolo

1. Premi **Crea** e scrivi titolo o autore: l'app prova a trovare le edizioni su Google Books e usa Open Library come alternativa se il primo catalogo non risponde.
2. Scegli l'edizione giusta (oppure inserisci titolo/autore a mano).
3. Scrivi il nome/numero del capitolo o l'argomento. I cataloghi servono a identificare il libro, non forniscono automaticamente il testo integrale del capitolo.
4. Facoltativamente aggiungi appunti brevi tuoi (massimo 2.500 caratteri) per ancorare la spiegazione al materiale corretto.
5. Con una chiave Gemini, genera le micro-lezioni. Senza chiave, l'app produce una guida demo generica e la indica come tale: non spaccia una guida per riassunto fedele.

## Costi, privacy e limiti

- Gemini Flash nell'API Google AI Studio ha un livello gratuito soggetto a quote e limiti, non illimitato. Le condizioni possono cambiare. I prompt del livello gratuito possono essere usati da Google per migliorare i prodotti: il prototipo mostra questa informazione prima della generazione.
- La chiave Gemini viene salvata nel localStorage del browser e le richieste vanno direttamente a Google. Non è una configurazione sicura per un servizio pubblico multiutente: in produzione la chiave va protetta lato server e serve verificare i termini aggiornati.
- La ricerca dei libri usa Google Books e, se necessario, Open Library; risultati, disponibilità e quote dipendono dai servizi. Se i cataloghi non rispondono, puoi inserire il titolo a mano.
- Il modello riceve titolo, capitolo, metadati/descrizione trovati e gli appunti che aggiungi. Non riceve automaticamente il libro completo: quando mancano informazioni sul capitolo può rifiutarsi di inventare. Le sintesi IA vanno comunque verificate.
- Gli appunti sono per brevi note personali, non per caricare capitoli completi. La generazione non deve sostituire il libro o riprodurre lunghi estratti.
- Il prototipo crea micro-lezioni testuali animate con narrazione vocale del dispositivo, non veri filmati generativi. Progressi e libri restano locali e non si sincronizzano.
