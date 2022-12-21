---
unique-page-id: 30082018
description: Sincronizzazione ritardata dei cookie - [!DNL Marketo Measure] - Documentazione del prodotto
title: Sincronizzazione ritardata dei cookie
exl-id: 394053ed-5642-48e4-b83c-c483a58ebbd7
source-git-commit: ae5b77744d523606ce6cfcf48d7e8d5049d5ccb7
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Sincronizzazione ritardata dei cookie {#delayed-cookie-sync}

Questa modifica al valore predefinito [!DNL Marketo Measure] Javascript fornisce [!DNL bizible.js] Supporto API, per configurare JS in modo da memorizzare temporaneamente le attività degli utenti dei visitatori, ma non inviare le informazioni al [!DNL Marketo Measure] fino a quando l’utente non dà il consenso per farlo.

## Procedura {#how-to}

Sostituisci il valore predefinito [!DNL bizible.js] tag script con i seguenti elementi:

`<script id="bizible-settings" type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="" data-consent-button-id="ConsentButtonId"></script>`

L&#39;attributo data-permission-button-id=&quot;ConsentButtonId&quot; indica [!DNL bizible.js] per inviare dati analitici solo dopo aver fatto clic su un elemento HTML con tale id.

In alternativa, i clienti possono impostare [!UICONTROL data-consent-button-id] essere qualcosa di inesistente (ad esempio, &quot;foobar&quot;) e utilizzare la seguente API per comunicare [!DNL bizible.js] che l&#39;utente ha acconsentito:

`window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`
`Bizible.Push("Consent", true });`

>[!NOTE]
>
>Il consenso dell’utente viene salvato nel cookie, il che significa che una volta che l’utente ha acconsentito una volta che non è necessario eseguire questa chiamata su alcuna pagina successiva.

## Limitazione {#limitation}

Perché [!DNL bizible.js] salva temporaneamente le attività web non inviate nei cookie di prime parti dei clienti e le dimensioni dei cookie di prime parti sono limitate, è possibile salvare solo tre richieste non inviate in un dato momento.

Se ci sono già tre richieste in sospeso, tutte le attività successive saranno ignorate; in questo modo viene mantenuta la prima visualizzazione di pagina, che contiene informazioni preziose sul referente.
