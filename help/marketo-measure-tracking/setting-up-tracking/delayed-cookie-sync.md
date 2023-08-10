---
unique-page-id: 30082018
description: Sincronizzazione cookie ritardata - [!DNL Marketo Measure] - Documentazione del prodotto
title: Sincronizzazione cookie ritardata
exl-id: 394053ed-5642-48e4-b83c-c483a58ebbd7
feature: Tracking
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Sincronizzazione cookie ritardata {#delayed-cookie-sync}

Questa modifica al valore predefinito [!DNL Marketo Measure] JavaScript fornisce [!DNL bizible.js] Supporto API, per consentire di configurare JS per memorizzare temporaneamente le attività degli utenti dei visitatori, ma non per inviare le informazioni al [!DNL Marketo Measure] fino a quando l&#39;utente non dà il consenso per farlo.

## Procedure {#how-to}

Sostituisci il predefinito [!DNL bizible.js] tag script con:

`<script id="bizible-settings" type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="" data-consent-button-id="ConsentButtonId"></script>`

L’attributo data-consent-button-id=&quot;ConsentButtonId&quot; comunica [!DNL bizible.js] per non inviare dati analitici finché non si fa clic su un elemento HTML con tale id.

In alternativa, i clienti possono impostare [!UICONTROL data-consent-button-id] essere qualcosa di inesistente (ad es., &quot;foobar&quot;) e utilizza la seguente API per comunicare [!DNL bizible.js] che l’utente ha acconsentito:

`window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`
`Bizible.Push("Consent", true });`

>[!NOTE]
>
>Il consenso dell’utente viene salvato nel cookie, il che significa che una volta che l’utente ha acconsentito, non è necessario eseguire questa chiamata su alcuna pagina successiva.

## Limitazione {#limitation}

Perché [!DNL bizible.js] salva temporaneamente le attività web non inviate nei cookie di prima parte dei clienti e le dimensioni dei cookie di prima parte sono limitate; è possibile salvare solo tre richieste non inviate in un dato momento.

Se sono già presenti tre richieste in sospeso, tutte le attività successive verranno ignorate; in questo modo verrà mantenuta la prima visualizzazione di pagina, che contiene informazioni preziose sul referente.
