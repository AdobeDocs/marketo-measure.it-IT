---
description: "[!DNL Marketo Measure] Installazione e configurazione dei pacchetti Salesforce - [!DNL Marketo Measure] - Documentazione del prodotto"
title: "[!DNL Marketo Measure] [!DNL Salesforce] Installazione e configurazione dei pacchetti"
exl-id: ed58bc1e-cfb0-48db-aa53-96204e12de2e
feature: Installation, Salesforce
source-git-commit: 68eb5bf83d589c9161490b1772551ed46a9ce444
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 0%

---

# [!DNL Marketo Measure] Installazione e configurazione del pacchetto Salesforce {#marketo-measure-salesforce-package-installation-and-set-up}

Prima di installare [!DNL Marketo Measure] [!DNL Salesforce] pacchetto base, è necessario determinare se verrà installato per la prima volta in un [!DNL Salesforce] prima di passare all’istanza di produzione Salesforce.

>[!NOTE]
>
>Una volta [!DNL Marketo Measure] account connesso a un [!DNL Salesforce] nell&#39;istanza di produzione, non è possibile spostarsi all&#39;indietro e connettersi a una sandbox. Inoltre, un [!DNL Marketo Measure] l&#39;account può essere connesso a un solo [!DNL Salesforce] istanza di produzione.

Il [!DNL Marketo Measure] Il pacchetto base contiene:

* 7 Personalizzato [!DNL Marketo Measure] Oggetti
* Personalizzato [!DNL Marketo Measure] Campi
* 25 [!DNL Stock] Rapporti

[!DNL Marketo Measure] è in grado di leggere standard [!DNL Salesforce] Oggetti, campi e record, [!DNL Marketo Measure] non aggiornerà mai o invierà loro dati. Tutti i dati raccolti da [!DNL Marketo Measure] Javascript verrà visualizzato nella [!DNL Marketo Measure] Oggetti e campi personalizzati.

Per installare il [!DNL Marketo Measure Salesforce] pacchetto di base.

1. Utilizzando un browser in incognito, vai al [Salesforce Appexchange](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3000000B3KLuEAN){target="_blank"} e accedi.

1. Installare in [!DNL Marketo Measure] in sandbox o produzione.

1. Accedi a [!DNL Salesforce] come Amministratore.

1. Seleziona **[!UICONTROL Install]per tutti gli utenti**.

   ![](assets/marketo-measure-salesforce-package-installation-and-set-up-1.png)

1. Una volta completata l’installazione, puoi visualizzarla.

   ![](assets/marketo-measure-salesforce-package-installation-and-set-up-2.png)

Dopo aver completato l&#39;installazione, è possibile aggiornare [[!DNL Salesforce] layout di pagina](/help/configuration-and-setup/marketo-measure-and-salesforce/page-layout-instructions.md){target="_blank"} con [!DNL Marketo Measure] campi, se necessario.

>[!NOTE]
>
>Leggi informazioni su [!DNL Marketo Measure] Set di autorizzazioni creati e [come verranno utilizzati](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md){target="_blank"}.

## Creazione di un [!DNL Marketo Measure] Profilo e utente {#creating-a-marketo-measure-profile-and-user}

[!DNL Marketo Measure] invia e riceve dati tramite una connessione [!DNL Salesforce] utente all&#39;interno di [!DNL Marketo Measure] app.

Per inviare i dati del punto di contatto al tuo [!DNL Salesforce] , l&#39;utente connesso deve avere accesso a [!DNL Marketo Measure] oggetti personalizzati (ad esempio punto di contatto buyer e punto di contatto attribuzione buyer) e standard [!DNL Salesforce] oggetti quali lead e contatti.

Creare un [!DNL Marketo Measure] profilo per garantire che non si verifichino errori di convalida durante il push dei dati in Salesforce.

Passaggio 1: creare un [!DNL Marketo Measure] profilo

1. Assegna le seguenti autorizzazioni:

* &quot;[!DNL Marketo Measure] Set di autorizzazioni amministratore&quot;
   * Il set di autorizzazioni gestite consente a un amministratore SFDC di creare, leggere, scrivere ed eliminare record da [!DNL Marketo Measure] oggetti.
* &quot;Visualizza e modifica set di autorizzazioni lead convertiti&quot;
   * Ciò consente [!DNL Marketo Measure] per decorare i lead dopo la conversione in contatti. Se questo set di autorizzazioni non è abilitato, possono verificarsi significative lacune nel tracciamento dei dati.

>[!NOTE]
>
>Questo profilo può essere un clone di un profilo amministratore di sistema.

Passaggio 2: creare un [!DNL Marketo Measure] in modo da poter tenere traccia dell&#39;impatto di [!DNL Marketo Measure] sul tuo [!DNL Salesforce] istanza

1. Assegna il nuovo [!DNL Marketo Measure] Profilo per tale utente.

1. Abilita &quot;Utente marketing&quot; come autorizzazione a livello di utente.

* Il [!UICONTROL Marketing User] La casella di controllo consente all’utente di creare campagne e utilizzare l’Importazione guidata campagne. Se questa opzione non è selezionata, l’utente può solo visualizzare le campagne e la configurazione avanzata della campagna, modificare la cronologia della campagna per un singolo lead o contatto ed eseguire i rapporti sulle campagne. [!DNL Marketo Measure] deve essere in grado di leggere e scrivere sull’oggetto campaign.

Passaggio 3: escludere questo profilo da tutti i trigger, i flussi di lavoro e i processi

Passaggio 4: accedere al [!DNL Marketo Measure] Account e autorizzazione [!DNL Salesforce] connessione con il nuovo utente

1. Vai a apps.bizible.com e accedi con il nuovo utente di produzione [!DNL Salesforce] credenziali.

1. Seleziona **[!UICONTROL Settings]** all&#39;interno del **[!UICONTROL My Account]** a discesa.

1. Seleziona **[!UICONTROL Connections]** all&#39;interno del **[!UICONTROL Integrations]** raggruppamento.

1. Fare clic sull&#39;icona a destra della connessione corrente [!DNL Salesforce] e seleziona per **Autorizza di nuovo con la produzione**. Accedere nuovamente con le nuove credenziali utente (se richieste).

>[!MORELIKETHIS]
>
>[Installazione di Adobe Admin Console](/help/configuration-and-setup/getting-started-with-marketo-measure/adobe-admin-console-setup.md){target="_blank"}
