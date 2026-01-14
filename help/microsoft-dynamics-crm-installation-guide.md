---
description: Guida dettagliata per installare e configurare il pacchetto Marketo Measure in Microsoft Dynamics CRM
title: Guida all'installazione di [!DNL Microsoft Dynamics] CRM
exl-id: bc422c98-60bb-49ea-9bd1-c4149ae628b1
feature: Installation, Microsoft Dynamics
hidefromtoc: true
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 0%

---

# Guida all&#39;installazione di [!DNL Microsoft Dynamics] CRM {#microsoft-dynamics-crm-installation-guide}

>[!NOTE]
>
>Potresti vedere le istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella documentazione, ma vedere ancora &quot;Bizible&quot; nel tuo CRM. Stiamo lavorando per aggiornarlo e il rebranding verrà riportato nel tuo CRM a breve.

## Versioni supportate {#supported-versions}

[!DNL Marketo Measure] supporta le seguenti [!DNL Microsoft Dynamics CRM] versioni:

* [!DNL Microsoft Dynamics 2016] (online e on-premise)
* [!DNL Microsoft Dynamics 365] (online e on-premise)

Per la connessione e l&#39;autenticazione, [!DNL Marketo Measure] supporta le seguenti versioni di Active Directory Federated Services (ADFS):

* ADFS 4.0 - [!DNL Windows Server 2016]
* ADFS 5.0 - [!DNL Windows Server 2019]

## Installare la soluzione gestita {#install-the-managed-solution}

[Scarica e installa](assets/marketo-measure-dynamics-extension.zip) il file zip all&#39;interno di Dynamics CRM.

**[!UICONTROL Settings]** > **[!UICONTROL Customizations]** > **[!UICONTROL Solutions]** > **[!UICONTROL Import]** (pulsante) > **[!UICONTROL Choose File]**.

>[!NOTE]
>
>Le due schermate seguenti possono variare leggermente rispetto all’immagine precedente, in quanto sono state acquisite durante l’aggiornamento di una soluzione.

## Creazione di un utente [!DNL Marketo Measure] {#creating-a-marketo-measure-user}

È consigliabile creare un utente Marketo Measure dedicato come &quot;utente applicazione&quot; all’interno di Dynamics per esportare e importare dati tramite per evitare problemi con altri utenti nel CRM. Prendere nota del nome utente e della password, nonché dell&#39;URL dell&#39;endpoint, utilizzati durante la creazione dell&#39;account [!DNL Marketo Measure].

## Ruoli di sicurezza {#security-roles}

Se l&#39;organizzazione utilizza i ruoli di Dynamics Security, verificare che l&#39;utente connesso o l&#39;utente [!DNL Marketo Measure] dedicato disponga di autorizzazioni di lettura/scrittura sufficienti per le entità richieste.

I ruoli di sicurezza si trovano qui: **[!UICONTROL Settings]** > **[!UICONTROL Security]** > **[!UICONTROL Security Roles]**.

Per le entità personalizzate [!DNL Marketo Measure], sono necessarie autorizzazioni complete per tutte le entità.

Sono necessarie anche le autorizzazioni &quot;Crea&quot; per la campagna, oltre alle autorizzazioni di lettura/scrittura per le entità standard.

>[!NOTE]
>
>Anche gli utenti che chiudono le opportunità devono disporre dell’autorizzazione completa.

Per le entità standard di Dynamics, fare riferimento al documento dello schema di Dynamics [!DNL Marketo Measure]. A un livello avanzato, [!DNL Marketo Measure] legge alcune entità per raccogliere i dati appropriati e scrivere nei campi personalizzati installati con la soluzione gestita. I record standard non vengono creati e i campi standard non vengono aggiornati.

## Includi punti di contatto nei layout di pagina: {#include-touchpoints-on-page-layouts}

1. Per ogni Entità, passa all’Editor di moduli. Puoi trovarlo in **[!UICONTROL Settings]** > **[!UICONTROL Customizations]** > **[!UICONTROL Customize the System]** > `[Entity]` > **[!UICONTROL Forms]**. Oppure è possibile trovarlo nelle impostazioni mentre si visualizza un record.

   * Le entità da configurare: account, opportunità, contatto, lead e campagna.

   * Per configurare le campagne, è necessario attivare l&#39;opzione &quot;Sincronizzazione campagne&quot; in **[!UICONTROL CRM]** > **[!UICONTROL Campaigns]**.

1. Layout di pagina: aggiungi prima una sezione &quot;[!UICONTROL One Column]&quot; nella sezione in cui desideri che i punti di contatto siano attivi. All’interno della nuova colonna, è necessaria una griglia secondaria aggiunta a ogni modulo delle entità Account, Opportunità, Contatto e Lead.

1. Selezionare l&#39;oggetto (Punti di contatto di attribuzione buyer o Punti di contatto buyer) di cui eseguire il rendering nella griglia secondaria, a seconda della relazione oggetto. È possibile modificare le colonne visualizzate facendo clic sul pulsante Modifica. Il layout predefinito è impostato dalla soluzione gestita.

   Subgrid Buyer Attribution Touchpoint: account, opportunità e contatti
Griglia secondaria Buyer Touchpoint - Lead e contatti

1. Dopo aver completato l’aggiornamento del modulo, pubblica e salva le modifiche.

## Considerazioni relative allo schema {#schema-related-considerations}

### Entrate

[!DNL Marketo Measure] punta al campo Reddito effettivo standard per impostazione predefinita. Se non lo utilizzi, spiega come generare rapporti sui ricavi al Solutions Engineer o al Success Manager, in quanto sarà necessario un flusso di lavoro personalizzato.

### Data di chiusura

[!DNL Marketo Measure] punta al campo Data di chiusura effettiva preconfigurato. Se non lo utilizzi o se utilizzi anche il campo Data di chiusura prevista, spiega il processo al tuo Solutions Engineer o Success Manager. Per tenere conto di entrambi i campi potrebbe essere necessario un flusso di lavoro personalizzato.

## Configurazione delle connessioni e dei provider di dati {#configuring-your-connections-and-data-providers}

Dopo aver effettuato l&#39;accesso all&#39;applicazione [!DNL Marketo Measure] e essere stato configurato come utente in Adobe Admin Console, il passaggio successivo consiste nel configurare le varie connessioni dati.

**CRM come provider di dati**

1. Nel tuo account [!DNL Marketo Measure], fai clic sul menu a discesa **[!UICONTROL My Account]** e seleziona **[!UICONTROL Settings]**.

1. In [!UICONTROL Integrations] nella barra di spostamento a sinistra, fare clic su **[!UICONTROL Connections]**.

1. Fare clic sul pulsante **[!UICONTROL Set Up New CRM Connection]**.

1. Accanto a [!UICONTROL Microsoft Dynamics CRM], fare clic sul pulsante **[!UICONTROL Connect]**.

1. Seleziona [!UICONTROL Credentials] (Mostra origine dati) o [!UICONTROL OAuth] (Blocca selezione).

   >[!NOTE]
   >
   >Per ulteriori informazioni su OAuth, visita [questo articolo](/help/oauth-with-azure-active-directory-for-dynamics-crm.md). In caso di domande sul processo, contattare il rappresentante dell&#39;account [!DNL Marketo Measure].

1. In questo esempio sono state scelte le credenziali. Immettere le credenziali e fare clic su **[!UICONTROL Next]**.

Dopo la connessione, visualizzerai i dettagli della connessione Dynamics nell’elenco Connessioni CRM/MAP.

**Connessioni account annuncio**

Per collegare i tuoi account annuncio con [!DNL Marketo Measure], inizia visitando la scheda [!UICONTROL Connections] nell&#39;applicazione [!DNL Marketo Measure].

1. Segui i passaggi 1 e 2 della precedente sezione _CRM come provider di dati_.

1. Fare clic sul pulsante **[!UICONTROL Set up New CRM Connection]**.

1. Seleziona la piattaforma desiderata.

**[!DNL Marketo Measure]JavaScript**

Affinché [!DNL Marketo Measure] possa tenere traccia delle attività Web, sono disponibili più passaggi per la configurazione.

1. Fai clic sul menu a discesa **[!UICONTROL My Account]** e seleziona **[!UICONTROL Account Configuration]**.

1. Immetti il numero di telefono. Per il sito Web, immettere il dominio principale utilizzato per il monitoraggio di [!DNL Marketo Measure] nel sito Web. Al termine, fai clic su **[!UICONTROL Save]**.

   >[!NOTE]
   >
   >Per aggiungere più domini radice, contattare il rappresentante commerciale [!DNL Marketo Measure].

1. [[!DNL Marketo Measure] JavaScript](/help/marketo-measure-tracking/adding-marketo-measure-script.md) deve quindi essere posizionato sull&#39;intero sito e sulle relative pagine di destinazione. È consigliabile codificare lo script all&#39;interno dell&#39;intestazione delle pagine di destinazione o aggiungere tramite un sistema Tag Management, ad esempio [Google Tag Manager](/help/marketo-measure-tracking/adding-marketo-measure-script-via-google-tag-manager.md).

   >[!NOTE]
   >
   >Per impostazione predefinita, [!DNL Marketo Measure] esporta 200 record per credito API ogni volta che un processo invia dati al CRM. Per la maggior parte dei clienti, questo fornisce il saldo ottimale tra i crediti API utilizzati da [!DNL Marketo Measure] e i requisiti delle risorse CPU nel CRM. Tuttavia, per i clienti con configurazioni di gestione delle relazioni con i clienti complesse, come flussi di lavoro e attivatori, potrebbe essere utile ridurre le dimensioni del batch per migliorare le prestazioni di gestione delle relazioni con i clienti. A questo scopo, [!DNL Marketo Measure] consente ai clienti di configurare la dimensione del batch di esportazione CRM. Questa impostazione è disponibile nella pagina Impostazioni > CRM > Generale dell&#39;applicazione Web [!DNL Marketo Measure] e i clienti possono scegliere tra dimensioni batch di 200 (impostazione predefinita), 100, 50 o 25.
   >
   >Quando modifichi questa impostazione, tieni presente che le dimensioni batch più piccole consumano più crediti API dal CRM. È consigliabile ridurre la dimensione del batch solo se si verifica un timeout di CPU o un carico elevato di CPU nel CRM.

   >[!NOTE]
   >
   >Quando disattivi l’esportazione di dati da Marketo Measure a Dynamics, non vengono rimossi i dati esistenti. Per assistenza sulla rimozione dei dati esistenti, contatta il supporto Dynamics.

   >[!MORELIKETHIS]
   >
   >[Notifiche di errore](/help/configuration-and-setup/error-notifications.md){target="_blank"}
