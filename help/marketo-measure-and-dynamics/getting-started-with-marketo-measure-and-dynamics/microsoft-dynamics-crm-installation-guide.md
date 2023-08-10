---
unique-page-id: 18874763
description: "[!DNL Microsoft Dynamics] Guida all’installazione di CRM - Marketo Measure - Documentazione del prodotto"
title: "[!DNL Microsoft Dynamics] Guida all'installazione di CRM"
exl-id: bc422c98-60bb-49ea-9bd1-c4149ae628b1
feature: Installation, Microsoft Dynamics
source-git-commit: a2a7657e8377fd5c556d38f6eb815e39d2b8d15e
workflow-type: tm+mt
source-wordcount: '1306'
ht-degree: 0%

---

# [!DNL Microsoft Dynamics] Guida all’installazione di CRM {#microsoft-dynamics-crm-installation-guide}

>[!NOTE]
>
>Potresti vedere le istruzioni che specificano &quot;[!DNL Marketo Measure]&quot; nella nostra documentazione, ma vedi ancora &quot;Bizible&quot; nel tuo CRM. Stiamo lavorando per aggiornarlo e il rebranding verrà riportato nel tuo CRM a breve.

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

## [!DNL Marketo Measure] Autorizzazioni utente {#marketo-measure-user-permissions}

Si consiglia di creare un [!DNL Marketo Measure] Utente in Dynamics per consentire a di esportare e importare dati tramite per evitare problemi con altri utenti nel CRM. Prendi nota del nome utente e della password, nonché dell’URL dell’endpoint, in quanto verranno utilizzati durante la creazione di [!DNL Marketo Measure] account.

## Ruoli di sicurezza {#security-roles}

Se l’organizzazione utilizza i ruoli di sicurezza di Dynamics, assicurati che l’utente connesso o l’utente dedicato [!DNL Marketo Measure] L’utente dispone di autorizzazioni di lettura/scrittura sufficienti per le entità richieste.

I ruoli di sicurezza si trovano qui: **[!UICONTROL Settings]** > **[!UICONTROL Security]** > **[!UICONTROL Security Roles]**.

Per [!DNL Marketo Measure] entità personalizzate, avremo bisogno di autorizzazioni complete su tutte le nostre entità.

>[!NOTE]
>
>Anche gli utenti che chiuderanno le opportunità avranno bisogno di autorizzazioni complete.

![](assets/4.png)

Per le entità standard di Dynamics, consulta [!DNL Marketo Measure] Documento schema Dynamics. Ad alto livello, [!DNL Marketo Measure] è sufficiente leggere in determinate entità per raccogliere i dati appropriati e scrivere nei campi personalizzati che verranno installati con la soluzione gestita. Non verranno creati nuovi record standard e non verranno aggiornati campi standard.

## Includi punti di contatto nei layout di pagina: {#include-touchpoints-on-page-layouts}

1. Per ogni Entità, passa all’Editor di moduli. Puoi trovarlo in **[!UICONTROL Settings]** > **[!UICONTROL Customizations]** > **[!UICONTROL Customize the System]** > `[Entity]` > **[!UICONTROL Forms]**. Oppure è possibile trovarlo nelle impostazioni mentre si sta visualizzando un record.

   * Le entità da configurare: account, opportunità, contatto, lead e campagna.

   * Per configurare le campagne, devi attivare l’opzione &quot;Sincronizzazione campagna&quot; in **[!UICONTROL CRM]** > **[!UICONTROL Campaigns]**.

   ![](assets/5.png)

1. Layout di pagina: per prima cosa aggiungi &quot;[!UICONTROL One Column]&quot; riquadro nella sezione in cui desideri che i punti di contatto siano attivi. All’interno della nuova colonna, sarà necessaria una griglia secondaria aggiunta a ogni modulo all’interno delle entità Account, Opportunità, Contatto e Lead.

   ![](assets/6.png)

   ![](assets/7.png)

1. Selezionare l&#39;oggetto (Punti di contatto di attribuzione buyer o Punti di contatto buyer) di cui eseguire il rendering nella griglia secondaria, a seconda della relazione oggetto. Se necessario, modificare le colonne da visualizzare facendo clic sul pulsante Modifica. Un layout predefinito è stato impostato dalla soluzione gestita.

   Subgrid punto di contatto per l&#39;attribuzione dell&#39;acquirente - Account, opportunità e contatto\
   Subgrid punto di contatto acquirente - Lead e contatti

   ![](assets/8.png)

1. Dopo aver completato l’aggiornamento del modulo, pubblica e salva le modifiche.

## Considerazioni relative allo schema {#schema-related-considerations}

**Ricavi**

[!DNL Marketo Measure] punta al campo Reddito effettivo standard per impostazione predefinita. Se non lo utilizzi, spiega come invii i rapporti sui ricavi al tuo Solutions Engineer o Success Manager, in quanto sarà necessario un flusso di lavoro personalizzato.

**Data di chiusura**

[!DNL Marketo Measure] punta al campo Data di chiusura effettiva. Se non lo utilizzi o se utilizzi anche il campo Data di chiusura prevista, spiega il processo al tuo Solutions Engineer o Success Manager. Potrebbe essere necessario un flusso di lavoro personalizzato per tenere conto di entrambi i campi.

## Configurare il Adobe Admin Console e il provider di identità {#set-up-your-adobe-admin-console-and-identity-provider}

Il primo passaggio per utilizzare [!DNL Marketo Measure] : per creare e accedere al Adobe Admin Console con provisioning. Se non hai già ricevuto l’e-mail con le istruzioni di accesso, contatta il tuo [!DNL Marketo Measure] Rappresentante dell’account.

Come prodotto all’interno della suite Adobe, [!DNL Marketo Measure] sfrutta tutte le funzionalità di Adobe Admin Console per Identity Management. Altre risorse possono essere [trovato qui](https://helpx.adobe.com/it/enterprise/using/admin-console.html).

È consigliabile esaminare tutte le risorse, le best practice e le opzioni disponibili per [Identity Management](https://helpx.adobe.com/enterprise/using/set-up-identity.html).

Per informazioni e una panoramica sulla configurazione dell’Identity Management in Adobe Admin Console, contatta il tuo [!DNL Marketo Measure] Rappresentante dell’account.

Per facilitare l’autenticazione e l’autorizzazione degli utenti con [!DNL Marketo Measure] istanze, sono necessari i seguenti passaggi all’interno di Adobe Admin Console:

**Configurazione di [!DNL Marketo Measure] Scheda prodotto**

Dopo aver effettuato l&#39;accesso a Adobe Admin Console, verranno visualizzati i [!DNL Marketo Measure] Istanze di prodotto presenti nella sezione Panoramica.

![](assets/microsoft-dynamics-crm-installation-guide-8a.png)

Facendo clic su [!DNL Marketo Measure] La scheda prodotto mostrerà tutte le [!DNL Marketo Measure] istanze. Per impostazione predefinita, ogni [!DNL Marketo Measure] L’istanza ha un proprio profilo con prefisso &quot;[!DNL Marketo Measure]&quot;. Tutti gli amministratori o gli utenti aggiunti a questo o a qualsiasi altro profilo all’interno di questa istanza potranno accedere a [!DNL Marketo Measure].

![](assets/microsoft-dynamics-crm-installation-guide-8b.png)

Non è richiesta alcuna azione per creare un nuovo profilo all’interno del [!DNL Marketo Measure] Istanze del prodotto.

Per iniziare ad aggiungere gli utenti che possono accedere [!DNL Marketo Measure], fare riferimento al [Aggiunta [!DNL Marketo Measure] Amministratori e [!DNL Marketo Measure] Utenti](#adding-marketo-measure-admins-and-marketo-measure-users) sezione successiva.

## Aggiunta [!DNL Marketo Measure] Amministratori e [!DNL Marketo Measure] Utenti {#adding-marketo-measure-admins-and-marketo-measure-users}

Il passaggio successivo consiste nel concedere l&#39;accesso al [!DNL Marketo Measure] mediante l&#39;aggiunta di utenti. Questa operazione può essere eseguita nella directory amministratori e utenti di [!DNL Marketo Measure] scheda prodotto.

| Tipo utente | Descrizione |
|---|---|
| Amministratori | si tratta di amministratori e utenti avanzati [!DNL Marketo Measure] Applicazione con piena capacità di aggiornamento e gestione [!DNL Marketo Measure]opzioni di configurazione specifiche di |
| Utenti | si tratta di utenti standard di [!DNL Marketo Measure] Applicazione con autorizzazioni di sola lettura all&#39;interno del [!DNL Marketo Measure] applicazione |

Quando aggiungi un utente al rispettivo gruppo, visualizzerai il relativo [Tipo di identità elencato](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/set-up-identity.ug.html).

>[!NOTE]
>
>Per essere un [!DNL Marketo Measure] amministratore (in [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}), un utente deve essere aggiunto come Utente _e_ un amministratore in qualsiasi [!DNL Marketo Measure] profilo di prodotto all’interno di [!DNL Marketo Measure] scheda prodotto.

**Accesso a[!DNL Marketo Measure]**

Dopo che un utente è stato aggiunto a un profilo di prodotto, può accedere al suo [!DNL Marketo Measure] istanze scegliendo **Accedi con Adobe ID** opzione a [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}.

![](assets/microsoft-dynamics-crm-installation-guide-15.png)

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
   >Per ulteriori informazioni su OAuth, visita [questo articolo](/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/oauth-with-azure-active-directory-for-dynamics-crm.md). In caso di domande sul processo, contattare il [!DNL Marketo Measure] Rappresentante dell’account.

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

Per ottenere [!DNL Marketo Measure] per tenere traccia delle attività web, sono disponibili diversi passaggi per la configurazione.

1. Fai clic su **[!UICONTROL My Account]** a discesa e selezionare **[!UICONTROL Account Configuration]**.

   ![](assets/microsoft-dynamics-crm-installation-guide-23.png)

1. Immetti il numero di telefono. Per il sito web, immetti il dominio principale che verrà utilizzato per [!DNL Marketo Measure] tracciamento sul sito web. Clic **[!UICONTROL Save]** al termine.

   ![](assets/microsoft-dynamics-crm-installation-guide-24.png)

   >[!NOTE]
   >
   >Per aggiungere più domini radice, contatta il tuo [!DNL Marketo Measure] Rappresentante dell’account.

1. Il [[!DNL Marketo Measure] JavaScript](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script.md) quindi deve essere posizionato sull’intero sito e sulle pagine di destinazione. È consigliabile codificare lo script all’interno della parte superiore delle pagine di destinazione o aggiungerlo tramite un sistema Tag Management, ad esempio [Gestione tag Google](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script-via-google-tag-manager.md).

   >[!NOTE]
   >
   >Per impostazione predefinita, [!DNL Marketo Measure] esporta 200 record per credito API ogni volta che un processo invia dati al CRM. Per la maggior parte dei clienti, questo fornisce l’equilibrio ottimale tra i crediti API utilizzati da [!DNL Marketo Measure] e i requisiti delle risorse CPU nel sistema CRM. Tuttavia, per i clienti con configurazioni di gestione delle relazioni con i clienti complesse, come flussi di lavoro e attivatori, potrebbe essere utile ridurre le dimensioni del batch per migliorare le prestazioni di gestione delle relazioni con i clienti. A tal fine: [!DNL Marketo Measure] consente ai clienti di configurare la dimensione del batch di esportazione del sistema CRM. Questa impostazione è disponibile nella pagina Impostazioni > CRM > Generale in [!DNL Marketo Measure] l’applicazione web e i clienti possono scegliere tra dimensioni batch di 200 (impostazione predefinita), 100, 50 o 25.
   >
   >Quando modifichi questa impostazione, tieni presente che le dimensioni batch più piccole consumeranno più crediti API dal CRM. È consigliabile ridurre la dimensione del batch solo se si verifica un timeout della CPU o un carico della CPU elevato nel CRM.

   >[!NOTE]
   >
   >Se disattivi l’esportazione di dati da Marketo Measure a Dynamics, non verranno rimossi i dati esistenti. Per assistenza sulla rimozione dei dati esistenti, contatta il supporto Dynamics.
