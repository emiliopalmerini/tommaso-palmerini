# Guida al Deployment su GitHub Pages

Questa guida ti spiega come pubblicare il sito su GitHub Pages.

## Prerequisiti

- Account GitHub
- Repository creato su GitHub

## Step 1: Crea il Repository su GitHub

1. Vai su [GitHub](https://github.com)
2. Clicca su "New repository"
3. Nome repository: `tommaso-palmerini` (o il nome che preferisci)
4. Lascia il repository **pubblico** (richiesto per GitHub Pages gratuito)
5. **NON** inizializzare con README, .gitignore o licenza (abbiamo già questi file)
6. Clicca su "Create repository"

## Step 2: Collega il Repository Locale a GitHub

Esegui questi comandi nella directory del progetto:

```bash
# Aggiungi il remote (sostituisci USERNAME con il tuo username GitHub)
git remote add origin https://github.com/USERNAME/tommaso-palmerini.git

# Fai il primo commit
git add .
git commit -m "feat(init): initial site setup with Hugo and Blowfish theme"

# Rinomina il branch in main (se necessario)
git branch -M main

# Pusha il codice su GitHub
git push -u origin main
```

## Step 3: Configura GitHub Pages

1. Vai al tuo repository su GitHub
2. Clicca su **Settings** (Impostazioni)
3. Nel menu laterale, clicca su **Pages**
4. Sotto "Build and deployment":
   - **Source**: Seleziona "GitHub Actions"
5. Salva

## Step 4: Deployment Automatico

Il sito verrà automaticamente:
- **Buildato e deployato** ad ogni push sul branch `main`
- Accessibile all'URL: `https://USERNAME.github.io/tommaso-palmerini/`

Puoi anche:
- Vedere il progresso del deployment nella tab **Actions** del repository
- Fare deploy manualmente dalla tab Actions cliccando su "Run workflow"

## Uso di un Dominio Personalizzato (Opzionale)

Se hai un dominio personalizzato (es. `tommasopalmerini.it`):

1. Vai su **Settings** > **Pages**
2. Sotto "Custom domain", inserisci il tuo dominio
3. Configura i DNS del tuo dominio provider:
   - Aggiungi un record `CNAME` che punta a `USERNAME.github.io`
   - Oppure 4 record `A` che puntano agli IP di GitHub Pages:
     ```
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153
     ```

4. Attendi la propagazione DNS (può richiedere fino a 48 ore)
5. Attiva "Enforce HTTPS" nelle impostazioni

### Configurare il dominio personalizzato in Hugo

Se usi un dominio personalizzato, aggiorna il `baseURL` in `config/_default/hugo.toml`:

```toml
baseURL = "https://tuodominio.it"
```

E fai un nuovo push per rifare il deploy.

## Aggiornare il Sito

Per pubblicare modifiche:

```bash
# Modifica i file che vuoi cambiare
# Poi:

git add .
git commit -m "feat(content): update servizi page"
git push
```

Il workflow GitHub Actions farà automaticamente il rebuild e deploy del sito!

## Monitorare il Deployment

1. Vai alla tab **Actions** del repository
2. Vedrai ogni workflow run con il suo stato
3. Clicca su un run per vedere i dettagli e i log

## Troubleshooting

### Il sito non si aggiorna

- Controlla la tab Actions per vedere se ci sono errori
- Assicurati che GitHub Pages sia configurato con source "GitHub Actions"
- Verifica che il workflow sia stato triggerato (tab Actions)

### Errore 404

- Verifica che il repository sia pubblico
- Assicurati che GitHub Pages sia abilitato nelle impostazioni
- Controlla che il baseURL sia corretto

### Il tema non viene caricato

- Assicurati che i submodule siano stati pushati:
  ```bash
  git submodule update --init --recursive
  git push --recurse-submodules=on-demand
  ```

## Link Utili

- [Documentazione GitHub Pages](https://docs.github.com/en/pages)
- [Documentazione Hugo](https://gohugo.io/documentation/)
- [Documentazione Blowfish](https://blowfish.page/docs/)
