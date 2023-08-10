---
unique-page-id: 18874749
description: Aggiunta [!DNL Marketo Measure] Script per [!DNL Uberflip] FORMS - [!DNL Marketo Measure] - Documentazione del prodotto
title: Aggiunta [!DNL Marketo Measure] Script per [!DNL Uberflip] Forms
exl-id: fb123e15-523d-4931-b4c1-705fe49be3d0
feature: Tracking
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# Aggiunta [!DNL Marketo Measure] Script per [!DNL Uberflip] Forms {#adding-marketo-measure-script-to-uberflip-forms}

Se si sta utilizzando [!DNL Uberflip] per gestire i contenuti, è importante adottare le misure necessarie per assicurarsi che [!DNL Marketo Measure] tiene traccia di tali invii di moduli. Il tuo Success Manager in [!DNL Uberflip] dovrebbe anche essere in grado di aiutarti in questo.

1. Aggiungi questo script a [!DNL Uberflip]di [!UICONTROL Custom Code>HTML] sezione.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Verifica che [!DNL Marketo Measure] il codice del preambolo viene attivato sia al caricamento della pagina che al cambiamento della pagina AJAX. Esegui questa operazione entro il [!UICONTROL Custom Code>JS] sezione

   `window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`

   Questo preambolo verrà aggiunto a entrambi [!DNL Hubs.onLoad] e [!DNL Hubs.onPageChange] Gli hook dell’evento JavaScript per AJAX di seguito. (Nota: anche in questi hook evento possono essere presenti altri codici. Assicurati di includere anche il preambolo.)

   `Hubs.onLoad = function () {`

   `window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`

   `}`

   `Hubs.onPageChange = function () {`

   `window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`

   `}`

1. Crea e definisci una funzione che invierà i dati a Bizible in seguito all’invio di un CTA modulo. Questo va nel [!UICONTROL Custom Code>Javascript] sezione. (Nota: questa funzione richiede solo il parametro ctaData fornito da Uberflip, ma puoi includere gli altri parametri ctaId e ctaName nel caso in cui l’utente desideri personalizzare il proprio codice per trasmettere anche questi dati).

   `function bizibleFormCode(ctaId, ctaData, ctaName) {`
   `var email = ctaData["email"];`
   `if(email){`
   `Bizible.Push('User', {`
   `eMail: email, // required`
   `}); }`

   `}`

1. Quando viene inviato un CTA modulo, assicurati che il [!DNL Marketo Measure] La funzione viene eseguita come di seguito. Questa operazione viene eseguita all&#39;interno di [!UICONTROL Custom Code>JS] sezione. (Nota: potresti avere altro codice all’interno dell’hook dell’evento JavaScript Hubs.onCtaFormSubmitSuccess; assicurati di includere anche questa chiamata alla funzione).

   `Hubs.onCtaFormSubmitSuccess = function (ctaId, ctaData, ctaName) {`
   `bizibleFormCode(ctaId, ctaData, ctaName);`\
   `}`
