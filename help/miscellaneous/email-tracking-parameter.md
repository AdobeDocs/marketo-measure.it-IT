---
description: Guida ai parametri di tracciamento e-mail per gli utenti di Marketo Measure
title: Parametro di tracciamento e-mail
exl-id: e2cfd59e-ce4a-4cbb-b64a-828d1db7410f
feature: Tracking
source-git-commit: 0299ef68139df574bd1571a749baf1380a84319b
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 2%

---

# Parametro di tracciamento e-mail {#email-tracking-parameter}

Il parametro di tracciamento e-mail [!DNL Marketo Measure] consente agli addetti al marketing di trattare i clic sulle e-mail come invii di moduli, in modo che vengano generati punti di contatto per tali azioni. Senza utilizzare un parametro di tracciamento e-mail, i click-through da un’e-mail vengono trattati solo come &quot;visite web&quot; fino a quando l’utente non si impegna effettivamente con il sito tramite l’invio di un modulo o una chat web.

## Casi d’uso  {#use-cases}

**Registrazione webinar**: il team Marketing invia un invito e-mail con un solo pulsante per registrarsi a un webinar. Poiché l’e-mail contiene già le informazioni della persona, il singolo clic le registra automaticamente. La pagina di destinazione contiene il parametro di tracciamento e-mail in modo che, quando il click-through viene visualizzato nella pagina di conferma, [!DNL Marketo Measure] possa acquisire l&#39;indirizzo e-mail e considerare il click-through come un modulo di compilazione, generando un punto di contatto.

**Download del contenuto**: il team di marketing dei contenuti desidera promuovere un eBook recente pubblicato con un collegamento di download diretto da un&#39;e-mail. Quando viene creato il modello di e-mail, la pagina di conferma del download contiene il parametro di tracciamento e-mail in modo che, quando fanno clic, [!DNL Marketo Measure] possa acquisire l&#39;indirizzo e-mail. Senza dover compilare un modulo sul sito, [!DNL Marketo Measure] può generare un punto di contatto per il download del contenuto. Questo perché l’e-mail li ha inseriti nella pagina di conferma con il parametro di tracciamento e-mail.

## Come funziona {#how-it-works}

Quando un visitatore arriva sul tuo sito, [!DNL Marketo Measure] prevede di trovare una pagina di destinazione con un indirizzo e-mail o un ID [!DNL Salesforce], in modo che possiamo associare la visita a un &quot;invio modulo&quot; e generare un punto di contatto per tale attività.

In qualità di cliente, puoi creare un modello e-mail come faresti normalmente. Una volta che è il momento di aggiungere nella pagina di destinazione l’azione di cui desideri tenere traccia, devi determinare il token, il tag di variabile o la macro accettata dalla piattaforma di automazione marketing per visualizzare dinamicamente il valore per ogni singolo utente.

Marketo Measure accetta i seguenti valori: Indirizzo e-mail, ID lead Salesforce o ID contatto Salesforce.

## Esempi di tag {#tag-examples}

| Automazione del marketing | Token/Tag/Macro | Esempio | Materiale di supporto |
| --- | --- | --- | --- |
| Marketo | {{lead.Email Address}} | <https://engage.marketo.com/rs/460-TDH-945/images/BZ-B2B-Marketing-Attribution-101-ebook.pdf?mailId={{lead.EmailAddress}}> | [Panoramica dei token](https://experienceleague.adobe.com/docs/marketo/using/product-docs/demand-generation/landing-pages/personalizing-landing-pages/tokens-overview.html?lang=it) |
| Pardot | %%email%% o %%user_crm_id%% | <https://engage.marketo.com/rs/460-TDH-945/images/BZ-B2B-Marketing-Attribution-101-ebook.pdf?mailId=%%email%%> | [Riferimento tag variabili Pardot](https://help.salesforce.com/s/articleView?language=en_US&id=pardot_variable_tags_reference.htm&type=5) |
| Hubspot | (inserito tramite Editor) | n/d | [Contenuto personalizzato da HubSpot](https://knowledge.hubspot.com/website-pages/personalize-your-content) |
| Agire il | (inserito tramite Compositore messaggi) | n/d | [Personalizzazione del contenuto delle e-mail con attivazione](https://connect.act-on.com/hc/en-us/articles/360033436074-How-to-Personalize-Email-Content-with-CRM-Data) |

Infine, in [!DNL Marketo Measure], devi specificare il parametro di tracciamento in modo che [!DNL Marketo Measure] possa individuare il valore dell&#39;e-mail o dell&#39;ID. Il valore predefinito è &quot;mailId&quot;, come illustrato negli esempi precedenti e nella schermata seguente. Immettere il valore nelle impostazioni in [!DNL Marketo Measure], quindi fare clic su **[!UICONTROL Save]**.

![](assets/one-one-1.png)
