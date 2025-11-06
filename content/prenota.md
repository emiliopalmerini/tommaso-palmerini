---
title: "Prenota"
description: "Prenota il tuo appuntamento"
---

## Prenota un Appuntamento

Compila il form qui sotto per prenotare il tuo trattamento di massoterapia.

{{< rawhtml >}}

<link rel="stylesheet" href="/css/form.css">

<script type="text/javascript">var submitted=false;</script>
<iframe name="hidden_iframe" id="hidden_iframe" style="display:none;"
        onload="if(submitted) {window.location='/grazie';}"></iframe>

<form id="contact-form" action="https://docs.google.com/forms/d/e/INSERISCI_QUI_IL_TUO_FORM_ID/formResponse"
      method="post" target="hidden_iframe" onsubmit="submitted=true;">

  <div class="form-group">
    <label for="name">Nome e Cognome <span class="required">*</span></label>
    <input type="text"
           id="name"
           name="entry.XXXXXXXX"
           class="form-input"
           placeholder="Il tuo nome completo"
           required>
  </div>

  <div class="form-group">
    <label for="email">Email <span class="required">*</span></label>
    <input type="email"
           id="email"
           name="entry.XXXXXXXX"
           class="form-input"
           placeholder="tua@email.it"
           required>
  </div>

  <div class="form-group">
    <label for="phone">Telefono <span class="required">*</span></label>
    <input type="tel"
           id="phone"
           name="entry.XXXXXXXX"
           class="form-input"
           placeholder="3XX XXX XXXX"
           required>
  </div>

  <div class="form-group">
    <label for="date">Data Preferita <span class="required">*</span></label>
    <input type="date"
           id="date"
           name="entry.XXXXXXXX"
           class="form-input"
           required>
  </div>

  <div class="form-group">
    <label for="treatment">Tipo di Trattamento</label>
    <select id="treatment"
            name="entry.XXXXXXXX"
            class="form-input">
      <option value="">Seleziona un trattamento</option>
      <option value="Massaggio rilassante">Massaggio rilassante</option>
      <option value="Massaggio sportivo">Massaggio sportivo</option>
      <option value="Massaggio decontratturante">Massaggio decontratturante</option>
      <option value="Altro">Altro</option>
    </select>
  </div>

  <div class="form-group">
    <label for="message">Note aggiuntive</label>
    <textarea id="message"
              name="entry.XXXXXXXX"
              class="form-input"
              rows="5"
              placeholder="Eventuali richieste o informazioni aggiuntive..."></textarea>
  </div>

  <div class="form-group">
    <button type="submit" class="submit-btn">Invia Prenotazione</button>
  </div>

</form>

{{< /rawhtml >}}

---

**Nota:** Riceverai una conferma via email. Ti contatterò al più presto per confermare la disponibilità.
