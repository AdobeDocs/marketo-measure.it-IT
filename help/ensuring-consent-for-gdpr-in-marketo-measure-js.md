---
description: Mostra come configurare bizible.js per attendere il consenso degli utenti per il RGPD prima di impostare i cookie o inviare i dati
title: Assicurare il consenso per il RGPD in Marketo Measure Js
exl-id: 9afc5e4d-cf97-4c49-b9ee-ee1cc99c1f90
feature: Tracking
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# Assicurare il consenso per il RGPD in Marketo Measure Js {#ensuring-consent-for-gdpr-in-marketo-measure-js}

Il Regolamento generale sulla protezione dei dati (RGPD) è una normativa dell’Unione Europea entrata in vigore il 25 maggio 2018.

## Panoramica {#overview}

L’obiettivo del RGPD è rafforzare i diritti degli interessati all’interno dell’Unione europea (UE) e dello Spazio economico europeo (SEE) per quanto riguarda le modalità di utilizzo e protezione dei loro dati personali. Per &quot;dati personali&quot; si intendono tutte le informazioni relative a una persona fisica identificata o identificabile. Il RGPD si applica a qualsiasi organizzazione all’interno o all’esterno dell’UE che commercializza beni o servizi e/o tiene traccia dei comportamenti degli interessati all’interno dell’UE e del SEE. Se svolgi attività commerciali con persone interessate in Europa che comportano il trattamento dei loro dati personali, questa legislazione si applica al tuo caso. Le sanzioni per inadempienza sono significative, con pesanti ammende per chi viola il regolamento; l&#39;ammenda massima per una singola violazione è di 20 milioni di euro o il 4% del fatturato mondiale annuo, a seconda di quale dei due è maggiore.

Per impostazione predefinita, [!DNL bizible.js] raccoglie i dati analitici degli utenti, a meno che non sia configurato per attendere il consenso. Quando [!DNL bizible.js] è configurato per attendere il consenso dell&#39;utente, non creerà cookie né invierà dati di analisi fino al raggiungimento del consenso.

## Come attendere il consenso {#how-to-wait-for-consent}

Esistono due modi per impostare [!DNL bizible.js] per attendere il consenso.

Opzione 1 - Sostituire il tag di script predefinito [!DNL bizible.js] con:

`<script id="bizible-settings" type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="" data-consent-button-id="ConsentButtonId"></script>`

**Se si utilizza [!DNL Google Tag Manager] per installare lo script**, tenere presente che GTM rimuove gli attributi dei dati, quindi utilizzare il seguente script:

`<span id="bizible-settings" data-consent-button-id="ConsentButtonId"></span>`
`<script type="text/javascript" src=https://cdn.bizible.com/scripts/bizible.js async=""></script>`

>[!NOTE]
>
>In questo caso, [!DNL bizible.js] allega un evento al clic all&#39;elemento HTML con ID &quot;ConsentButtonId&quot;.

Quando si fa clic su questo elemento di HTML, [!DNL bizible.js] crea un cookie per ricordare che il consenso dell&#39;utente è stato ricevuto e inizia a raccogliere i dati di analisi come di consueto.

**o-**

Opzione 2 - Sostituire il tag di script predefinito [!DNL bizible.js] con:

`<script id="bizible-settings" type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="" data-requires-user-consent="true"></script>`

Questo comunica a [!DNL bizible.js] di non tenere traccia finché non viene raggiunto il consenso, operazione che può essere eseguita con la seguente API JS:

*finestra[&#39;Bizible&#39;] = finestra[&#39;Bizible&#39;] || { _queue: [], Push: function (o, p) { questo._queue.push({ tipo: o, dati: p }); } };*

*Bizible. Push(&#39;Consent&#39;, true);*

**Se si utilizza [!DNL Google Tag Manager] per installare lo script**, tenere presente che GTM rimuove gli attributi dei dati, quindi utilizzare il seguente script:

`<span id="bizible-settings" data-requires-user-consent="true"></span>`
`<script type="text/javascript" src=https://cdn.bizible.com/scripts/bizible.js async=""></script>`

>[!NOTE]
>
>bizible.js creerà un cookie per ricordare che il consenso dell’utente è stato ricevuto e inizierà a raccogliere i dati di analisi come di consueto solo dopo la chiamata all’API JS.

Al contrario, i clienti possono utilizzare questa API anche per revocare il consenso dell’utente:

`window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) { this._queue.push({ type: o, data: p }); } };`

`Bizible.Push('Consent', false);`

Durante l&#39;esecuzione, il codice elimina tutti i cookie creati in precedenza da [!DNL bizible.js] e riprende la raccolta dei dati di analisi solo se l&#39;utente dà nuovamente il consenso.
