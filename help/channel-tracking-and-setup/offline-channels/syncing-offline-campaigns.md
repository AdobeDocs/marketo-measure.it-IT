---
unique-page-id: 18874600
description: Sincronizzazione delle campagne offline - [!DNL Marketo Measure] - Documentazione del prodotto
title: Sincronizzazione delle campagne offline
exl-id: a6f9e217-ff6e-474d-9f14-c6f6238c9e84
source-git-commit: 02f686645e942089df92800d8d14c76215ae558f
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---

# Sincronizzazione delle campagne offline {#syncing-offline-campaigns}

Può essere difficile tracciare con precisione le campagne offline e capire in che modo si confrontano con le attività di marketing digitale. [!DNL Marketo Measure] consente di tracciare e attribuire i punti di contatto alle campagne offline in [!DNL Salesforce], anche in situazioni in cui [!DNL Salesforce] La campagna viene creata solo poche settimane dopo l’evento.

## Prima della sincronizzazione {#before-you-sync}

Di seguito sono riportati alcuni suggerimenti per un processo di sincronizzazione efficiente:

* Le campagne offline fanno riferimento alle interazioni di marketing che non si verificano online. Questi includono canali di marketing come eventi, webinar e fiere. Includere solo campagne di marketing offline.
* Se desideri includere campagne che hanno tracciato l’attività online prima del momento dell’installazione [!DNL Marketo Measure], assicurati di impostare la data di fine del punto di contatto come data di distribuzione di JavaScript sul tuo sito.
* È utile mantenere [!DNL Marketo Measure] L’app viene aperta nella pagina Canali offline in modo da identificare facilmente i diversi tipi di campagna, insieme al canale di marketing in cui verranno inseriti i punti di contatto.

* Controlla tutto prima di colpire &quot;[!UICONTROL Save]&quot; pulsante!

## Aggiornamento in blocco della data del punto di contatto {#bulk-update-touchpoint-date}

In [!DNL Salesforce], il campo Data creazione nell’oggetto membro della campagna prende nota della data in cui il membro della campagna è stato aggiunto alla campagna. Affinché il processo di sincronizzazione funzioni senza problemi, accertati che il campo Data punto di contatto dell’acquirente abbia la stessa data della data sull’oggetto membro della campagna di Salesforce. Questo passaggio viene eseguito utilizzando &quot;[!UICONTROL Bulk Update Touchpoint Date button]&quot; _prima_ seleziona la [!UICONTROL picklist] nel campo Abilita punti di contatto dell’acquirente .

Perché questo è importante? Immagina per un momento che la tua azienda abbia sponsorizzato uno stand ad una conferenza in gennaio. Alla conferenza, 100 persone hanno mostrato interesse per il tuo prodotto e hanno fornito le loro informazioni di contatto per ricevere aggiornamenti e-mail. Tre settimane dopo, hai finalmente creato una campagna in [!DNL Salesforce] seguire l&#39;esito della conferenza.

La data di caricamento sarà tre settimane dopo la data della conferenza. Per correggere questa differenza, il [!UICONTROL Bulk Update Touchpoint Date] può essere utilizzato per impostare la data appropriata. Il pulsante è illustrato nell&#39;immagine seguente.

![](assets/1-3.png)

In questo caso, la data di caricamento verrebbe retrocompilata di tre settimane. Questo passaggio deve essere fatto prima di impostare &quot;[!UICONTROL Enable Buyer Touchpoints]&quot; campo.

In sintesi, se utilizzi il [!UICONTROL Bulk Update Touchpoint Date] e modificare la data del punto di contatto con la data dell’evento, [!DNL Marketo Measure] genererà punti di contatto per la data effettiva dell’evento, non per la data di caricamento.

Puoi anche aggiornare le date di tutti i membri della campagna su una campagna esistente. In questo modo, assicurati che la data del punto di contatto sia la data dell&#39;interazione del membro. Fai clic su Aggiorna in blocco data punto di contatto dell’acquirente, filtra l’elenco dei membri della campagna in base alle necessità e nella sezione &quot;[!UICONTROL Select Date]&quot; sopra l’elenco dei membri della campagna, aggiungi la stessa data della data in cui si è verificato l’evento.

>[!CAUTION]
>
>Assicurati di aggiornare la data del punto di contatto _prima_ attivate i punti di contatto per tutti i membri della campagna.

![](assets/2-3.png)

## Come creare una campagna e sincronizzare i punti di contatto dell’acquirente {#how-to-create-a-campaign-and-sync-buyer-touchpoints}

Per creare una campagna in [!DNL Salesforce], passa alla [!UICONTROL Campaigns] seleziona &quot;[!UICONTROL New]&quot; come mostrato nell&#39;immagine seguente. A seconda del [!DNL Salesforce] potrebbe essere necessario aggiungere Campagne alla barra superiore facendo clic sull’icona più (+).

![](assets/3-3.png)

Quando crei questa campagna, fai clic su &quot;[!UICONTROL Enable Buyer Touchpoints]&quot; e seleziona una delle seguenti opzioni dalla lista di selezione:

![](assets/4-3.png)

* **Includi tutti i membri della campagna**
   * Questa opzione abilita [!DNL Marketo Measure] per attribuire un punto di contatto a ciascun membro della campagna.

* **Includi i membri della campagna &quot;Rispondi&quot;.**
   * Questa opzione applica i punti di contatto ai membri della campagna con stato &quot;Rispondi&quot;.

* **Escludi tutti i membri della campagna.**
   * Questa opzione non attribuisce i punti di contatto ad alcun membro della campagna e agisce come un flag per cui la campagna è stata deliberatamente esclusa [!DNL Marketo Measure]. Se sincronizzi una campagna con i punti di contatto dell’acquirente in caso di incidente, puoi modificare lo stato in &quot;Escludi tutti i membri della campagna&quot; e i punti di contatto verranno rimossi.

Una volta selezionata una di queste selezioni, [!DNL Marketo Measure] assegnerà a ogni membro della campagna un punto di contatto, se applicabile. Il lead o il contatto che viene aggiunto alla campagna _deve_ dispongono di un indirizzo e-mail associato al record per [!DNL Marketo Measure] per creare un punto di contatto. Senza un indirizzo e-mail, [!DNL Marketo Measure] non assegna un punto di contatto al membro della campagna.

>[!MORELIKETHIS]
>
>[[!DNL Marketo Measure] Università: Mappatura dei canali offline](https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c630eca34d9f0367662b77f)
>
>[[!DNL Marketo Measure] Università: Campi oggetto campagna](https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c63007334d9f0367662b758)
