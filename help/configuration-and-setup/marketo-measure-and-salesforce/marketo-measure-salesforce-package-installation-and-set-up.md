---
description: Installazione e configurazione del pacchetto Salesforce [!DNL Marketo Measure] - [!DNL Marketo Measure]
title: '[!DNL Marketo Measure] [!DNL Salesforce] Installazione e configurazione del pacchetto'
exl-id: ed58bc1e-cfb0-48db-aa53-96204e12de2e
feature: Installation, Salesforce
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# Installazione e configurazione del pacchetto Salesforce [!DNL Marketo Measure] {#marketo-measure-salesforce-package-installation-and-set-up}

Prima di installare il pacchetto di base [!DNL Marketo Measure] [!DNL Salesforce], è necessario determinare se si sta installando in una sandbox [!DNL Salesforce] prima di passare all&#39;istanza di produzione di Salesforce.

>[!NOTE]
>
>Una volta che l&#39;account [!DNL Marketo Measure] è connesso a un&#39;istanza di produzione [!DNL Salesforce], non è possibile spostarsi all&#39;indietro e connettersi a una sandbox. Inoltre, un account [!DNL Marketo Measure] può essere connesso a una sola istanza di produzione [!DNL Salesforce].

Il pacchetto di base [!DNL Marketo Measure] contiene:

* 7 Oggetti [!DNL Marketo Measure] personalizzati
* [!DNL Marketo Measure] campi personalizzati
* 25 [!DNL Stock] report

[!DNL Marketo Measure] è in grado di leggere oggetti, campi e record [!DNL Salesforce] standard. Tuttavia, [!DNL Marketo Measure] non aggiornerà né invierà mai dati a tali oggetti. Tutti i dati raccolti dal JavaScript [!DNL Marketo Measure] verranno visualizzati negli oggetti e nei campi personalizzati [!DNL Marketo Measure].

Per installare il pacchetto di base [!DNL Marketo Measure Salesforce], attenersi alla procedura riportata di seguito.

1. Utilizzando un browser in incognito, vai a [Salesforce AppExchange](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3000000B3KLuEAN){target="_blank"} e accedi.

1. Eseguire l&#39;installazione nel pacchetto [!DNL Marketo Measure] in sandbox o produzione.

1. Accedere a [!DNL Salesforce] come amministratore.

1. Selezionare **[!UICONTROL Install]per tutti gli utenti**.

   ![](assets/marketo-measure-salesforce-package-installation-and-set-up-1.png)

1. Una volta completata l’installazione, puoi visualizzarla.

   ![](assets/marketo-measure-salesforce-package-installation-and-set-up-2.png)

Dopo aver completato l&#39;installazione, puoi aggiornare i [[!DNL Salesforce] layout di pagina](/help/configuration-and-setup/marketo-measure-and-salesforce/page-layout-instructions.md){target="_blank"} con i campi [!DNL Marketo Measure], se necessario.

>[!NOTE]
>
>Scopri i set di autorizzazioni [!DNL Marketo Measure] creati e [come vengono utilizzati](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md){target="_blank"}.

## Creazione di un profilo e di un utente [!DNL Marketo Measure] {#creating-a-marketo-measure-profile-and-user}

[!DNL Marketo Measure] invia e riceve dati tramite un utente [!DNL Salesforce] connesso all&#39;interno dell&#39;app [!DNL Marketo Measure].

Per inviare i dati dei punti di contatto all&#39;istanza [!DNL Salesforce], l&#39;utente connesso deve avere accesso a [!DNL Marketo Measure] oggetti personalizzati (ad esempio, Buyer Touchpoint e Buyer Attribution Touchpoint) e a [!DNL Salesforce] oggetti standard come lead e contatti.

Crea un profilo [!DNL Marketo Measure] per assicurarti di non riscontrare errori di convalida durante il push dei dati in Salesforce.

Passaggio 1: creare un profilo [!DNL Marketo Measure] specifico

1. Assegna le seguenti autorizzazioni:

* &quot;[!DNL Marketo Measure] set di autorizzazioni amministratore&quot;
   * Il set di autorizzazioni gestite consente a un amministratore di SFDC di creare, leggere, scrivere ed eliminare record da [!DNL Marketo Measure] oggetti.
* &quot;Visualizza e modifica set di autorizzazioni lead convertiti&quot;
   * Questo consente a [!DNL Marketo Measure] di decorare i lead dopo che sono stati convertiti in contatti. Se questo set di autorizzazioni non è abilitato, possono verificarsi significative lacune nel tracciamento dei dati.

>[!NOTE]
>
>Questo profilo può essere un clone di un profilo amministratore di sistema.

Passaggio 2: crea un utente [!DNL Marketo Measure] dedicato in modo da poter tenere traccia dell&#39;impatto di [!DNL Marketo Measure] sull&#39;istanza [!DNL Salesforce]

1. Assegnare il nuovo profilo [!DNL Marketo Measure] a tale utente.

1. Abilita &quot;Utente marketing&quot; come autorizzazione a livello di utente.

* La casella di controllo [!UICONTROL Marketing User] consente all&#39;utente di creare campagne e utilizzare l&#39;Importazione guidata campagne. Se questa opzione non è selezionata, l’utente può solo visualizzare le campagne e la configurazione avanzata della campagna, modificare la cronologia della campagna per un singolo lead o contatto ed eseguire i rapporti sulle campagne. [!DNL Marketo Measure] deve essere in grado di leggere e scrivere nell&#39;oggetto della campagna.

Passaggio 3: escludere questo profilo da tutti i trigger, i flussi di lavoro e i processi

Passaggio 4: accedere all&#39;account [!DNL Marketo Measure] e autorizzare nuovamente la connessione [!DNL Salesforce] con il nuovo utente

1. Visitare il sito Web all&#39;indirizzo apps.bizible.com e accedere con le credenziali [!DNL Salesforce] di produzione del nuovo utente.

1. Selezionare **[!UICONTROL Settings]** nel menu a discesa **[!UICONTROL My Account]**.

1. Selezionare **[!UICONTROL Connections]** nel raggruppamento **[!UICONTROL Integrations]**.

1. Fare clic sull&#39;icona della chiave a destra della connessione [!DNL Salesforce] attualmente connessa e selezionare **Riautorizza con produzione**. Accedere nuovamente con le nuove credenziali utente (se richieste).

>[!MORELIKETHIS]
>
>* [Panoramica delle autorizzazioni di integrazione](/help/api-connections/utilizing-marketo-measures-api-connections/integration-permissions-overview.md){target="_blank"}
>
>* [Installazione di Adobe Admin Console](/help/configuration-and-setup/getting-started-with-marketo-measure/adobe-admin-console-setup.md){target="_blank"}
