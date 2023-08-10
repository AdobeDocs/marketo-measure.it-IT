---
unique-page-id: 18874600
description: Sincronizzazione delle campagne offline - [!DNL Marketo Measure] - Documentazione del prodotto
title: Sincronizzazione delle campagne offline
exl-id: a6f9e217-ff6e-474d-9f14-c6f6238c9e84
feature: Channels
source-git-commit: e01738222e8845112892c0258cb084a4f0ebb257
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 0%

---

# Sincronizzazione delle campagne offline {#syncing-offline-campaigns}

Può essere difficile tracciare con precisione le campagne offline e capire in che modo si confrontano con le tue attività di marketing digitale. [!DNL Marketo Measure] consente di tenere traccia e attribuire punti di contatto alle campagne offline in [!DNL Salesforce], anche in situazioni in cui [!DNL Salesforce] la campagna viene creata solo poche settimane dopo l’evento.

>[!NOTE]
>
>Questo articolo riguarda un processo obsoleto. Invitiamo gli utenti a utilizzare [processo in-app nuovo e migliorato](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md){target="_blank"}.

## Prima della sincronizzazione {#before-you-sync}

Di seguito sono riportati alcuni suggerimenti per un processo di sincronizzazione efficiente:

* Le campagne offline si riferiscono alle interazioni di marketing che non si verificano online. tra cui canali di marketing come eventi, webinar e fiere commerciali. Includi solo campagne di marketing offline.
* Se desideri includere campagne che hanno tracciato l’attività online prima di quando hai installato [!DNL Marketo Measure], assicurati di impostare la data di fine del punto di contatto come data in cui il nostro JavaScript è stato distribuito sul tuo sito.
* È utile mantenere [!DNL Marketo Measure] L’app viene aperta sulla pagina Canali offline, in modo da poter identificare facilmente i diversi tipi di campagna e in quale canale di marketing verranno inseriti i punti di contatto.

* Controlla nuovamente tutto prima di premere il tasto &quot;[!UICONTROL Save]&quot;!

## Data punto di contatto per aggiornamento in blocco {#bulk-update-touchpoint-date}

In entrata [!DNL Salesforce], il campo Data di creazione nell’oggetto membro della campagna indica la data in cui il membro della campagna è stato aggiunto alla campagna. Affinché il processo di sincronizzazione si svolga senza problemi, assicurati che il campo Data punto di contatto acquirente abbia la stessa data dell’oggetto membro della campagna Salesforce. Questo passaggio viene eseguito utilizzando il comando &quot;[!UICONTROL Bulk Update Touchpoint Date button],&quot; _prima di_ selezioni il [!UICONTROL picklist] nel campo Abilita punti di contatto buyer.

Perché è importante? Immagina per un momento che la tua azienda abbia sponsorizzato uno stand ad una conferenza in gennaio. Alla conferenza, 100 persone hanno mostrato interesse per il prodotto e hanno fornito le loro informazioni di contatto per ricevere gli aggiornamenti via e-mail. Tre settimane dopo, hai finalmente creato una campagna in [!DNL Salesforce] seguire l&#39;esito della conferenza.

La data di caricamento sarebbe tre settimane dopo la data della conferenza. Per correggere questa differenza, [!UICONTROL Bulk Update Touchpoint Date] per impostare la data appropriata. Il pulsante è illustrato nell&#39;immagine seguente.

![](assets/1-3.png)

In questo caso, la data di caricamento verrebbe retrocompilata di tre settimane. Questo passaggio deve essere eseguito prima di impostare il &quot;[!UICONTROL Enable Buyer Touchpoints]&quot;.

In sintesi, se utilizzi il [!UICONTROL Bulk Update Touchpoint Date] e cambia la data del punto di contatto con la data dell’evento, [!DNL Marketo Measure] genera punti di contatto per la data effettiva dell’evento, non per la data di caricamento.

Puoi anche aggiornare le date per tutti i membri della campagna su una campagna esistente. Quando si esegue questa operazione, assicurarsi che la data del punto di contatto sia la data dell&#39;interazione del membro. Fai clic sulla Data in cui viene aggiornato il punto di contatto dell’acquirente, filtra l’elenco dei membri della campagna in base alle esigenze e nella sezione &quot;[!UICONTROL Select Date]&quot; sopra l’elenco dei membri della campagna, aggiungi la stessa data in cui si è verificato l’evento.

>[!CAUTION]
>
>Assicurati di aggiornare la data del punto di contatto _prima di_ abiliti i punti di contatto per tutti i membri della campagna.

![](assets/2-3.png)

## Come creare una campagna e sincronizzare i punti di contatto dell’acquirente {#how-to-create-a-campaign-and-sync-buyer-touchpoints}

Per creare una campagna in [!DNL Salesforce], passare alla [!UICONTROL Campaigns] e seleziona &#39;[!UICONTROL New]&quot; come illustrato nell’immagine seguente. A seconda del [!DNL Salesforce] , potrebbe essere necessario aggiungere Campagne alla barra superiore facendo clic sull&#39;icona più (+).

![](assets/3-3.png)

Quando crei questa campagna, fai clic su &quot;[!UICONTROL Enable Buyer Touchpoints]&quot; e seleziona una delle seguenti opzioni dall’elenco a discesa:

![](assets/4-3.png)

* **Includi tutti i membri della campagna**
   * Questa opzione abilita [!DNL Marketo Measure] per attribuire un punto di contatto a ciascun membro della campagna.

* **Includi i membri della campagna &quot;Rispondenti&quot;.**
   * Questa opzione applica i punti di contatto ai membri della campagna che hanno lo stato &quot;Risposta&quot;.

* **Escludi tutti i membri della campagna.**
   * Questa opzione non attribuisce punti di contatto a nessun membro della campagna e funge da flag da cui la campagna è stata deliberatamente esclusa [!DNL Marketo Measure]. Se sincronizzi una campagna con i punti di contatto dell’acquirente per errore, puoi cambiare lo stato in &quot;Escludi tutti i membri della campagna&quot; e i punti di contatto verranno rimossi.

Una volta selezionata una di queste selezioni, [!DNL Marketo Measure] assegnerà a ciascun membro della campagna un punto di contatto, se applicabile. Il lead o il contatto aggiunto alla campagna _deve_ hanno un indirizzo e-mail associato al loro record per poter [!DNL Marketo Measure] per creare un punto di contatto. Senza un indirizzo e-mail, [!DNL Marketo Measure] non assegnerà un punto di contatto al membro della campagna.

>[!MORELIKETHIS]
>
>[[!DNL Marketo Measure] University: mappatura dei canali offline](https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c630eca34d9f0367662b77f)
>
>[[!DNL Marketo Measure] Università: Campi oggetto della campagna](https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c63007334d9f0367662b758)
