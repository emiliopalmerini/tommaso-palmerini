# Guida: Configurare Google Forms per la Prenotazione

Questa guida ti spiega come configurare il form di prenotazione con Google Forms.

## Step 1: Crea il Google Form

1. Vai su [Google Forms](https://forms.google.com)
2. Clicca su **"Vuoto"** per creare un nuovo form
3. Dai un titolo al form: **"Prenotazione Trattamento Massoterapia"**

## Step 2: Aggiungi i Campi del Form

Crea questi campi nel form (nell'ordine):

1. **Nome e Cognome**
   - Tipo: Risposta breve
   - Obbligatorio: Sì

2. **Email**
   - Tipo: Risposta breve
   - Obbligatorio: Sì
   - Aggiungi validazione: Email

3. **Telefono**
   - Tipo: Risposta breve
   - Obbligatorio: Sì

4. **Data Preferita**
   - Tipo: Data
   - Obbligatorio: Sì

5. **Tipo di Trattamento**
   - Tipo: Scelta multipla
   - Opzioni:
     - Massaggio rilassante
     - Massaggio sportivo
     - Massaggio decontratturante
     - Altro
   - Obbligatorio: No

6. **Note aggiuntive**
   - Tipo: Paragrafo
   - Obbligatorio: No

## Step 3: Ottieni il Form ID e gli Entry IDs

### Ottieni il Form ID:

1. Clicca sul pulsante **"Invia"** in alto a destra
2. Copia l'URL che vedi (sarà simile a: `https://docs.google.com/forms/d/e/1FAIpQLSxxxxxxxxxxxxxxxxxxxxxxxxx/viewform`)
3. Il **FORM_ID** è la parte tra `/d/e/` e `/viewform`

### Ottieni gli Entry IDs:

1. Apri il tuo Google Form in **modalità incognito** (o logout da Google)
2. Clicca con il tasto destro sulla pagina e seleziona **"Ispeziona elemento"** o **"Visualizza sorgente pagina"**
3. Cerca (Ctrl+F o Cmd+F) la parola **"entry."**
4. Troverai codici come `entry.123456789` - questi sono gli Entry IDs!

**Esempio:** Se nel codice HTML vedi:
```html
<input type="text" name="entry.719211028" ...>
```

L'Entry ID per quel campo è: `entry.719211028`

### Metodo Alternativo (più facile):

1. Apri il form in modalità incognito
2. Clicca con il destro sul primo campo (**Nome e Cognome**)
3. Seleziona **"Ispeziona"**
4. Nel codice HTML evidenziato, cerca l'attributo `name="entry.XXXXXXXX"`
5. Ripeti per ogni campo

## Step 4: Aggiorna il File prenota.md

1. Apri il file `content/prenota.md`

2. Sostituisci `INSERISCI_QUI_IL_TUO_FORM_ID` con il tuo Form ID (riga 18)

3. Sostituisci tutti gli `entry.XXXXXXXX` con i tuoi Entry IDs corrispondenti:
   - Riga 25: Nome e Cognome → `entry.XXXXXXXX` (il tuo entry ID)
   - Riga 35: Email → `entry.XXXXXXXX`
   - Riga 45: Telefono → `entry.XXXXXXXX`
   - Riga 55: Data → `entry.XXXXXXXX`
   - Riga 64: Tipo di Trattamento → `entry.XXXXXXXX`
   - Riga 76: Note → `entry.XXXXXXXX`

### Esempio di riga completa:

**Prima:**
```html
<input type="text" name="entry.XXXXXXXX" ...>
```

**Dopo:**
```html
<input type="text" name="entry.719211028" ...>
```

## Step 5: Configura le Notifiche Email

1. Nel tuo Google Form, clicca su **"Risposte"** (tab in alto)
2. Clicca sui tre puntini (⋮) in alto a destra
3. Seleziona **"Ricevi notifiche email per le nuove risposte"**
4. Ora riceverai un'email ogni volta che qualcuno compila il form!

## Step 6: Collega a Google Sheets (Opzionale)

Per tenere traccia di tutte le prenotazioni in un foglio:

1. Nel tab **"Risposte"**, clicca sull'icona di Google Sheets (foglio verde)
2. Scegli **"Crea un nuovo foglio di lavoro"**
3. Clicca **"Crea"**

Ora tutte le risposte saranno automaticamente salvate in un Google Sheet!

## Step 7: Testa il Form

1. Salva le modifiche e fai commit:
   ```bash
   git add .
   git commit -m "feat(form): configure Google Forms booking system"
   git push
   ```

2. Aspetta che GitHub Actions faccia il deployment (1-2 minuti)

3. Visita la pagina `/prenota` sul tuo sito

4. Compila il form di test

5. Controlla che:
   - Il form si invii correttamente
   - Vieni reindirizzato alla pagina "Grazie"
   - La risposta appaia nel tuo Google Form
   - Ricevi la notifica email

## Risoluzione Problemi

### Il form non si invia

- Controlla che il Form ID sia corretto
- Verifica che gli Entry IDs corrispondano ai campi giusti
- Assicurati di aver aperto il form in modalità incognito per ottenere gli Entry IDs

### La pagina "Grazie" non appare

- Verifica che il file `content/grazie.md` esista
- Controlla che l'URL nel codice sia `/grazie` (senza `.md`)

### Non ricevo le notifiche email

- Controlla le impostazioni di notifica nel Google Form
- Verifica la cartella spam
- Assicurati di aver attivato le notifiche (Step 5)

## Link Utili

- [Google Forms](https://forms.google.com)
- [Tutorial originale](https://puvvadi.net/posts/add-contact-form-hugo-google-forms/)
