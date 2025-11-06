# Tommaso Palmerini - Sito Web

Sito web professionale per Tommaso Palmerini, massoterapista laureato in Scienze Motorie.

## Tecnologie

- **Hugo**: Generatore di siti statici
- **Blowfish**: Tema Hugo moderno e professionale
- **Lingua principale**: Italiano

## Struttura del Sito

- **Home** (`/`): Pagina principale
- **Chi Sono** (`/chi-sono`): Informazioni su Tommaso e la sua formazione
- **Servizi** (`/servizi`): Descrizione dei trattamenti offerti
- **Prenota** (`/prenota`): Form di prenotazione tramite Google Forms

## Sviluppo Locale

### Avviare il server di sviluppo

```bash
hugo server
```

Il sito sarà disponibile su: http://localhost:1313/

### Fermare il server

Premi `Ctrl+C` nel terminale dove sta girando Hugo.

## Integrazione Google Forms

Per aggiungere il form di prenotazione:

1. Crea un Google Form con i campi necessari (nome, email, data, tipo di trattamento, etc.)
2. In Google Forms, clicca su "Invia" e seleziona l'opzione "Embed"
3. Copia il codice iframe
4. Apri il file `content/prenota.md`
5. Sostituisci il commento con il codice embed del tuo Google Form

Esempio:
```html
<iframe src="https://docs.google.com/forms/d/e/YOUR_FORM_ID/viewform?embedded=true" width="100%" height="800" frameborder="0" marginheight="0" marginwidth="0">Caricamento…</iframe>
```

## Personalizzazione

### Modificare i contenuti

I file di contenuto si trovano in `content/`:
- `_index.md`: Home page
- `chi-sono.md`: Pagina Chi Sono
- `servizi.md`: Pagina Servizi
- `prenota.md`: Pagina Prenotazione

### Configurazione del sito

I file di configurazione si trovano in `config/_default/`:
- `hugo.toml`: Configurazione generale
- `languages.it.toml`: Configurazione lingua italiana e informazioni autore
- `menus.it.toml`: Menu di navigazione
- `params.toml`: Parametri del tema

### Aggiungere immagini

Puoi aggiungere:
- Logo del sito
- Foto di Tommaso
- Immagini dei trattamenti

Le immagini vanno in `static/img/` e poi vanno referenziate nei file di configurazione.

## Build di Produzione

Per creare la versione statica del sito:

```bash
hugo
```

I file generati saranno in `public/` e possono essere caricati su qualsiasi servizio di hosting statico (Netlify, Vercel, GitHub Pages, etc.).

## Documentazione

- [Hugo Documentation](https://gohugo.io/documentation/)
- [Blowfish Theme Documentation](https://blowfish.page/docs/)
