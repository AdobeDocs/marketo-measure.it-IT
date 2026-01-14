---
description: Aggiunta di  [!DNL Marketo Measure] script alle [!DNL Uberflip] linee guida di Forms per gli utenti di Marketo Measure
title: Aggiunta di  [!DNL Marketo Measure] script a [!DNL Uberflip] Forms
exl-id: fb123e15-523d-4931-b4c1-705fe49be3d0
feature: Tracking
source-git-commit: 0299ef68139df574bd1571a749baf1380a84319b
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Aggiunta dello script [!DNL Marketo Measure] a [!DNL Uberflip] Forms {#adding-marketo-measure-script-to-uberflip-forms}

Se stai utilizzando [!DNL Uberflip] per gestire il contenuto, è importante che tu prenda le misure necessarie per assicurarti che [!DNL Marketo Measure] stia tenendo traccia di tali invii di moduli. Anche il tuo Success Manager in [!DNL Uberflip] dovrebbe essere in grado di aiutarti in questo.

1. Aggiungi questo script alla sezione [!DNL Uberflip] di [!UICONTROL Custom Code>HTML].

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Assicurati che questo codice del preambolo [!DNL Marketo Measure] venga attivato sia al caricamento della pagina che al cambiamento della pagina in AJAX. Eseguire questa operazione nella sezione [!UICONTROL Custom Code>JS]

   `window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`

   Aggiungi questo preambolo agli hook dell&#39;evento JavaScript di [!DNL Hubs.onLoad] e [!DNL Hubs.onPageChange] di AJAX di seguito. (Nota: anche in questi hook evento potrebbe essere presente altro codice. Assicurarsi di includere anche il preambolo.)

   `Hubs.onLoad = function () {`

   `window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`

   `}`

   `Hubs.onPageChange = function () {`

   `window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`

   `}`

1. Crea e definisci una funzione che invia i dati a Bizible in seguito all’invio di un CTA modulo. Viene inserita la sezione [!UICONTROL Custom Code>JavaScript]. (Nota: questa funzione richiede solo il parametro ctaData fornito da Uberflip, ma puoi includere gli altri parametri ctaId e ctaName nel caso in cui l’utente desideri personalizzare il proprio codice per trasmettere anche questi dati).

   `function bizibleFormCode(ctaId, ctaData, ctaName) {`
   `var email = ctaData["email"];`
   `if(email){`
   `Bizible.Push('User', {`
   `eMail: email, // required`
   `}); }`

   `}`

1. Quando viene inviato un CTA modulo, assicurarsi che la funzione [!DNL Marketo Measure] venga eseguita come indicato di seguito. Operazione eseguita nella sezione [!UICONTROL Custom Code>JS]. (Nota: potresti avere altro codice all’interno dell’hook dell’evento JavaScript Hubs.onCtaFormSubmitSuccess, assicurati di includere anche questa chiamata alla funzione).

   `Hubs.onCtaFormSubmitSuccess = function (ctaId, ctaData, ctaName) {`
   `bizibleFormCode(ctaId, ctaData, ctaName);`\
   `}`
