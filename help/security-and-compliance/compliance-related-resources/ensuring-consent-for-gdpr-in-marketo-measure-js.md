---
unique-page-id: 35586069
description: Garantire il consenso per il RGPD in Marketo Measure Js - Marketo Measure - Documentazione del prodotto
title: Garantire il consenso per il RGPD in Marketo Measure Js
exl-id: 9afc5e4d-cf97-4c49-b9ee-ee1cc99c1f90
source-git-commit: c7d3bbce1f0c6a99409822c06c43961c93cd9458
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# Garantire il consenso per il RGPD in Marketo Measure Js {#ensuring-consent-for-gdpr-in-marketo-measure-js}

Il Regolamento generale sulla protezione dei dati (RGPD) è una normativa dell’Unione Europea entrata in vigore il 25 maggio 2018.

## Panoramica {#overview}

L’obiettivo del RGPD è rafforzare i diritti delle persone interessate all’interno dell’Unione europea (UE) e dello Spazio economico europeo (SEE) per quanto riguarda il modo in cui i loro dati personali vengono utilizzati e protetti. Per &quot;dati personali&quot; si intendono tutte le informazioni relative a una persona fisica identificata o identificabile. Il RGPD si applica a qualsiasi organizzazione all’interno o all’esterno dell’UE che commercializza beni o servizi e/o tiene traccia del comportamento degli interessati all’interno dell’UE e del SEE. Se si tratta di persone interessate in Europa che si occupano del trattamento dei loro dati personali, questa legislazione si applica a voi. Le sanzioni in caso di inosservanza sono significative, con ingenti ammende per i soggetti che violano il regolamento; l&#39;importo massimo dell&#39;ammenda per una singola violazione è di 20 milioni di euro o di 4% del fatturato mondiale annuo, a seconda di quale sia il valore più elevato.

Per impostazione predefinita, [!DNL bizible.js] raccoglie i dati analitici degli utenti a meno che non sia configurato in modo specifico per attendere il consenso. Quando [!DNL bizible.js] è configurato in attesa del consenso dell’utente, non creerà cookie o invierà dati di analisi finché non viene raggiunto il consenso.

## Come attendere il consenso {#how-to-wait-for-consent}

Esistono due modi per impostare [!DNL bizible.js] per attendere il consenso.

Opzione 1 - Sostituire l&#39;impostazione predefinita [!DNL bizible.js] tag script con:

`<script id="bizible-settings" type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="" data-consent-button-id="ConsentButtonId"></script>`

**Se utilizzi [!DNL Google Tag Manager] per installare lo script**, ricorda che GTM rimuove gli attributi dei dati, quindi utilizza invece il seguente script:

`<span id="bizible-settings" data-consent-button-id="ConsentButtonId"></span>`
`<script type="text/javascript" src=https://cdn.bizible.com/scripts/bizible.js async=""></script>`

>[!NOTE]
>
>In questo caso, [!DNL bizible.js] allega un evento on-click all’elemento HTML con id &quot;ConsentButtonId&quot;.

Quando fai clic su questo elemento HTML, [!DNL bizible.js] crea un cookie per ricordare che il consenso dell’utente è stato ricevuto e inizia a raccogliere i dati di analisi come di consueto.

**-oppure-**

Opzione 2 - Sostituire l&#39;impostazione predefinita [!DNL bizible.js] tag script con:

`<script id="bizible-settings" type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="" data-requires-user-consent="true"></script>`

Questo è [!DNL bizible.js] per non tenere traccia finché non viene raggiunto il consenso, che può essere fatto con la seguente API JS:

*finestra[&#39;Bizible&#39;] = finestra[&#39;Bizible&#39;] || {_queue: [], Push: function (o, p) { this._queue.push({ tipo: o, dati: p }); };*

*Bizible.Push(&#39;Consent&#39;, true);*

**Se utilizzi [!DNL Google Tag Manager] per installare lo script**, ricorda che GTM rimuove gli attributi dei dati, quindi utilizza invece il seguente script:

`<span id="bizible-settings" data-requires-user-consent="true"></span>`
`<script type="text/javascript" src=https://cdn.bizible.com/scripts/bizible.js async=""></script>`

>[!NOTE]
>
>bizible.js creerà un cookie per ricordare che il consenso dell&#39;utente è stato ricevuto e inizierà a raccogliere i dati di analisi come di consueto solo dopo la chiamata dell&#39;API JS.

Al contrario, i clienti possono anche utilizzare questa API per revocare il consenso dell’utente:

`window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) { this._queue.push({ type: o, data: p }); } };`

`Bizible.Push('Consent', false);`

Quando questo codice viene eseguito, elimina tutti i cookie che [!DNL bizible.js] creato in precedenza e riprenderà la raccolta dei dati di analytics solo se l’utente riacconsente.
