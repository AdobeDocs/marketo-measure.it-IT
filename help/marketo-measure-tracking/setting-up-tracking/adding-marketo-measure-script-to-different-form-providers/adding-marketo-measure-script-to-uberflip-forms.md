---
unique-page-id: 18874749
description: Aggiunta [!DNL Marketo Measure] Script per [!DNL Uberflip] Forms - [!DNL Marketo Measure] - Documentazione del prodotto
title: Aggiunta [!DNL Marketo Measure] Script per [!DNL Uberflip] Forms
exl-id: fb123e15-523d-4931-b4c1-705fe49be3d0
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# Aggiunta [!DNL Marketo Measure] Script per [!DNL Uberflip] Forms {#adding-marketo-measure-script-to-uberflip-forms}

Se stai utilizzando [!DNL Uberflip] per gestire i contenuti, è importante adottare le seguenti misure necessarie per garantire che [!DNL Marketo Measure] tiene traccia degli invii dei moduli. Il tuo Success Manager su [!DNL Uberflip] dovrebbe anche essere in grado di aiutarvi con questo.

1. Aggiungi questo script a [!DNL Uberflip]s [!UICONTROL Custom Code>HTML] sezione .

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Assicurati che [!DNL Marketo Measure] il codice di preambolo viene attivato sia al caricamento della pagina che AJAX modifica della pagina. Esegui questa operazione all’interno di [!UICONTROL Custom Code>JS] sezione

   `window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`

   Aggiungerà questo preambolo a entrambi i [!DNL Hubs.onLoad] e [!DNL Hubs.onPageChange] AJAX gli hook dell&#39;evento Javascript per di seguito. (Nota: Puoi avere altri codici anche in questi hook di eventi. Assicurati di includere anche il preambolo).

   `Hubs.onLoad = function () {`

   `window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`

   `}`

   `Hubs.onPageChange = function () {`

   `window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`

   `}`

1. Crea e definisci una funzione che invierà i dati a Bizible in base a un CTA del modulo. Questo entra nel [!UICONTROL Custom Code>Javascript] sezione . (Nota: questa funzione richiede solo il parametro ctaData fornito da Uberflip, ma è possibile includere gli altri parametri ctaId e ctaName nel caso in cui l&#39;utente desideri personalizzare il proprio codice per trasmettere anche questi dati).

   `function bizibleFormCode(ctaId, ctaData, ctaName) {`
   `var email = ctaData["email"];`
   `if(email){`
   `Bizible.Push('User', {`
   `eMail: email, // required`
   `}); }`

   `}`

1. Quando viene inviato un Invito all’azione per i moduli, assicurati che [!DNL Marketo Measure] viene eseguita per sotto. Questa operazione viene eseguita all’interno della [!UICONTROL Custom Code>JS] sezione . (Nota: Potresti avere altro codice all&#39;interno del gancio evento javascript Hubs.onCtaFormSubmitSuccess, assicurati di includere anche questa chiamata alla funzione).

   `Hubs.onCtaFormSubmitSuccess = function (ctaId, ctaData, ctaName) {`
   `bizibleFormCode(ctaId, ctaData, ctaName);`\
   `}`
