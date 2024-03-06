---
unique-page-id: 18874763
description: "[!DNL Microsoft Dynamics] Guida all’installazione di CRM - Marketo Measure - Documentazione del prodotto"
title: "[!DNL Microsoft Dynamics] Guida all'installazione di CRM"
exl-id: bc422c98-60bb-49ea-9bd1-c4149ae628b1
feature: Installation, Microsoft Dynamics
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '906'
ht-degree: 0%

---

# [!DNL Microsoft Dynamics] Guida all’installazione di CRM {#microsoft-dynamics-crm-installation-guide}

>[!NOTE]
>
>Potresti vedere le istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella documentazione, ma vedi ancora &quot;Bizible&quot; nel tuo CRM. Stiamo lavorando per aggiornarlo e il rebranding verrà riportato nel tuo CRM a breve.

## Versioni supportate {#supported-versions}

[!DNL Marketo Measure] supporta quanto segue [!DNL Microsoft Dynamics CRM] versioni:

* [!DNL Microsoft Dynamics 2016] (Online e On-Premise)
* [!DNL Microsoft Dynamics 365] (Online e On-Premise)

Per la connessione e l’autenticazione, [!DNL Marketo Measure] supporta le seguenti versioni di Active Directory Federated Services (ADFS):

* ADFS 4.0 - [!DNL Windows Server 2016]
* ADFS 5.0 - [!DNL Windows Server 2019]

## Installare la soluzione gestita {#install-the-managed-solution}

[Scarica e installa](assets/marketo-measure-dynamics-extension.zip) il file zip all’interno di Dynamics CRM.

**[!UICONTROL Settings]** > **[!UICONTROL Customizations]** > **[!UICONTROL Solutions]** > **[!UICONTROL Import]** (pulsante) > **[!UICONTROL Choose File]**.

![](assets/1.png)

>[!NOTE]
>
>Le due schermate seguenti possono variare leggermente rispetto all’immagine precedente, in quanto sono state acquisite durante l’aggiornamento di una soluzione.

![](assets/2.png)

![](assets/3.png)

## Creazione di un [!DNL Marketo Measure] Utente {#creating-a-marketo-measure-user}

È consigliabile creare un utente Marketo Measure dedicato come &quot;utente applicazione&quot; all’interno di Dynamics per esportare e importare dati tramite per evitare problemi con altri utenti nel CRM. Prendi nota del nome utente e della password, nonché dell’URL dell’endpoint, in quanto vengono utilizzati durante la creazione di [!DNL Marketo Measure] account.

## Ruoli di sicurezza {#security-roles}

Se la tua organizzazione utilizza i Ruoli di Dynamics Security, assicurati che l’utente connesso o l’utente dedicato [!DNL Marketo Measure] L’utente dispone di autorizzazioni di lettura/scrittura sufficienti per le entità richieste.

I ruoli di sicurezza si trovano qui: **[!UICONTROL Settings]** > **[!UICONTROL Security]** > **[!UICONTROL Security Roles]**.

Per [!DNL Marketo Measure] entità personalizzate, sono necessarie autorizzazioni complete in tutte le nostre entità.

>[!NOTE]
>
>Anche gli utenti che chiudono le opportunità devono disporre dell’autorizzazione completa.

![](assets/4.png)

Per le entità standard di Dynamics, consulta [!DNL Marketo Measure] Documento schema Dynamics. Ad alto livello, [!DNL Marketo Measure] legge in alcune entità per raccogliere i dati appropriati e scrivere nei campi personalizzati installati con la soluzione gestita. I record standard non vengono creati e i campi standard non vengono aggiornati.

## Includi punti di contatto nei layout di pagina: {#include-touchpoints-on-page-layouts}

1. Per ogni Entità, passa all’Editor di moduli. Puoi trovarlo in **[!UICONTROL Settings]** > **[!UICONTROL Customizations]** > **[!UICONTROL Customize the System]** > `[Entity]` > **[!UICONTROL Forms]**. Oppure è possibile trovarlo nelle impostazioni mentre si visualizza un record.

   * Le entità da configurare: account, opportunità, contatto, lead e campagna.

   * Per configurare le campagne, devi attivare l’opzione &quot;Sincronizzazione campagna&quot; in **[!UICONTROL CRM]** > **[!UICONTROL Campaigns]**.

   ![](assets/5.png)

1. Layout di pagina: per prima cosa aggiungi &quot;[!UICONTROL One Column]&quot; nella sezione in cui desideri che siano attivi i punti di contatto. All’interno della nuova colonna, è necessaria una griglia secondaria aggiunta a ogni modulo delle entità Account, Opportunità, Contatto e Lead.

   ![](assets/6.png)

   ![](assets/7.png)

1. Selezionare l&#39;oggetto (Punti di contatto di attribuzione buyer o Punti di contatto buyer) di cui eseguire il rendering nella griglia secondaria, a seconda della relazione oggetto. È possibile modificare le colonne visualizzate facendo clic sul pulsante Modifica. Il layout predefinito è impostato dalla soluzione gestita.

   Subgrid punto di contatto per l&#39;attribuzione dell&#39;acquirente - Account, opportunità e contatto\
   Subgrid punto di contatto acquirente - Lead e contatti

   ![](assets/8.png)

1. Dopo aver completato l’aggiornamento del modulo, pubblica e salva le modifiche.

## Considerazioni relative allo schema {#schema-related-considerations}

**Ricavi**

[!DNL Marketo Measure] punta al campo Reddito effettivo standard per impostazione predefinita. Se non lo utilizzi, spiega come generare rapporti sui ricavi al Solutions Engineer o al Success Manager, in quanto sarà necessario un flusso di lavoro personalizzato.

**Data di chiusura**

[!DNL Marketo Measure] punta al campo Data di chiusura effettiva. Se non lo utilizzi o se utilizzi anche il campo Data di chiusura prevista, spiega il processo al tuo Solutions Engineer o Success Manager. Per tenere conto di entrambi i campi potrebbe essere necessario un flusso di lavoro personalizzato.

## Configurazione delle connessioni e dei provider di dati {#configuring-your-connections-and-data-providers}

Dopo aver effettuato l’accesso a [!DNL Marketo Measure] e sono stati impostati come utente in Adobe Admin Console, il passaggio successivo consiste nel configurare le varie connessioni dati.

**CRM come provider di dati**

1. Nel tuo [!DNL Marketo Measure] account, fai clic su **[!UICONTROL My Account]** a discesa e selezionare **[!UICONTROL Settings]**.

   ![](assets/microsoft-dynamics-crm-installation-guide-16.png)

1. Sotto [!UICONTROL Integrations] nella barra di navigazione a sinistra, fai clic su **[!UICONTROL Connections]**.

   ![](assets/microsoft-dynamics-crm-installation-guide-17.png)

1. Fai clic su **[!UICONTROL Set Up New CRM Connection]** pulsante.

   ![](assets/microsoft-dynamics-crm-installation-guide-18.png)

1. Accanto a [!UICONTROL Microsoft Dynamics CRM], fare clic su **[!UICONTROL Connect]** pulsante.

   ![](assets/microsoft-dynamics-crm-installation-guide-19.png)

1. Seleziona [!UICONTROL Credentials] o [!UICONTROL OAuth].

   ![](assets/microsoft-dynamics-crm-installation-guide-20.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni su OAuth, visita [questo articolo](/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/oauth-with-azure-active-directory-for-dynamics-crm.md). In caso di domande sul processo, contatta il [!DNL Marketo Measure] Rappresentante dell’account.

1. In questo esempio sono state scelte le credenziali. Immetti le credenziali e fai clic su **[!UICONTROL Next]**.

Dopo la connessione, visualizzerai i dettagli della connessione Dynamics nell’elenco Connessioni CRM/MAP.

**Connessioni account annuncio**

Per collegare i tuoi account annuncio con [!DNL Marketo Measure], inizia visitando il [!UICONTROL Connections] all&#39;interno del [!DNL Marketo Measure] applicazione.

1. Segui i passaggi 1 e 2 indicati sopra _CRM come provider di dati_ sezione.

1. Fai clic su **[!UICONTROL Set up New CRM Connection]** pulsante.

   ![](assets/microsoft-dynamics-crm-installation-guide-21.png)

1. Seleziona la piattaforma desiderata.

   ![](assets/microsoft-dynamics-crm-installation-guide-22.png)

**[!DNL Marketo Measure]JavaScript**

Per [!DNL Marketo Measure] per tenere traccia delle attività web, sono disponibili diversi passaggi per la configurazione.

1. Fai clic su **[!UICONTROL My Account]** a discesa e selezionare **[!UICONTROL Account Configuration]**.

   ![](assets/microsoft-dynamics-crm-installation-guide-23.png)

1. Immetti il numero di telefono. Per il sito web, immetti il dominio principale utilizzato per [!DNL Marketo Measure] tracciamento sul sito web. Clic **[!UICONTROL Save]** al termine.

   ![](assets/microsoft-dynamics-crm-installation-guide-24.png)

   >[!NOTE]
   >
   >Per aggiungere più domini principali, contatta il tuo [!DNL Marketo Measure] Rappresentante dell’account.

1. Il [[!DNL Marketo Measure] JavaScript](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script.md) quindi deve essere posizionato sull’intero sito e sulle pagine di destinazione. È consigliabile codificare lo script all’interno della parte superiore delle pagine di destinazione o aggiungerlo tramite un sistema Tag Management, ad esempio [Gestione tag Google](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script-via-google-tag-manager.md).

   >[!NOTE]
   >
   >Per impostazione predefinita, [!DNL Marketo Measure] esporta 200 record per credito API ogni volta che un processo invia dati al CRM. Per la maggior parte dei clienti, questo fornisce l’equilibrio ottimale tra i crediti API utilizzati da [!DNL Marketo Measure] e i requisiti delle risorse CPU nel sistema CRM. Tuttavia, per i clienti con configurazioni di gestione delle relazioni con i clienti complesse, come flussi di lavoro e attivatori, potrebbe essere utile ridurre le dimensioni del batch per migliorare le prestazioni di gestione delle relazioni con i clienti. A tal fine: [!DNL Marketo Measure] consente ai clienti di configurare la dimensione del batch di esportazione del sistema CRM. Questa impostazione è disponibile nella pagina Impostazioni > CRM > Generale in [!DNL Marketo Measure] l’applicazione web e i clienti possono scegliere tra dimensioni batch di 200 (impostazione predefinita), 100, 50 o 25.
   >
   >Quando modifichi questa impostazione, tieni presente che le dimensioni batch più piccole consumano più crediti API dal CRM. È consigliabile ridurre la dimensione del batch solo se si verifica un timeout della CPU o un carico della CPU elevato nel CRM.

   >[!NOTE]
   >
   >Quando disattivi l’esportazione di dati da Marketo Measure a Dynamics, non vengono rimossi i dati esistenti. Per assistenza sulla rimozione dei dati esistenti, contatta il supporto Dynamics.

   >[!MORELIKETHIS]
   >
   >[Notifiche di errore](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md){target="_blank"}
