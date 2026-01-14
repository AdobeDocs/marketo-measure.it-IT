---
description: OAuth con [!DNL Azure Active Directory] per le linee guida di Dynamics CRM per gli utenti di Marketo Measure
title: OAuth con  [!DNL Azure Active Directory]  per Dynamics CRM
exl-id: 0a2f6b29-541d-4965-a460-e6f19b934edb
feature: Microsoft Dynamics
hidefromtoc: true
source-git-commit: 0299ef68139df574bd1571a749baf1380a84319b
workflow-type: tm+mt
source-wordcount: '766'
ht-degree: 0%

---

# OAuth con [!DNL Azure Active Directory] per Dynamics CRM {#oauth-with-azure-active-directory-for-dynamics-crm}

## Chi è interessato {#who-s-affected}

Questa configurazione è per i nuovi clienti [!DNL Marketo Measure] che utilizzano Dynamics CRM con un account [!DNL Azure Active Directory] (AAD) o per i clienti che desiderano migrare dal nome utente e password legacy a [!DNL Azure Active Directory] con OAuth.

>[!NOTE]
>
>Per entrambi questi scenari, AAD è configurato qui per facilitare la connessione dell&#39;istanza Dynamics in [!DNL Marketo Measure] come provider di dati.

## Configura nuova applicazione {#set-up-new-application}

1. Accedi al [portale di Azure](https://portal.azure.com/#home).

1. Scegliere il tenant di Azure AD facendo clic sull&#39;account nell&#39;angolo superiore destro della pagina, quindi fare clic sulla navigazione Switch Directory e selezionare il tenant appropriato. Ignorare questo passaggio se si dispone di un solo tenant Azure AD nell&#39;account o se è già stato selezionato il tenant Azure AD appropriato.

   ![](assets/bizible-taxonomy-1.png)

1. Cerca &quot;[!DNL Azure Active Directory]&quot; nella barra di ricerca e fai clic sul nome per aprire.

   ![](assets/creating-2e-1.png)

1. Fare clic su **[!UICONTROL App Registrations]** nel menu a sinistra.

   ![](assets/getting-dynamics-1.png)

1. Fai clic su **[!UICONTROL New Registration]** in alto.

   ![](assets/getting-dynamics-10.png)

1. Seguire le istruzioni e creare un&#39;applicazione. Non importa se si tratta di un&#39;applicazione Web o di un client pubblico (mobile e desktop), ma se desideri esempi specifici per applicazioni Web o applicazioni client pubbliche, vedi [quickstarts](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-overview).\
   a. Nome è il nome dell&#39;applicazione e descrive l&#39;applicazione agli utenti finali.\
   b. In Tipi di conto supportati, selezionare Account in qualsiasi directory organizzativa e account Microsoft personali.\
   c. Fornisci l’URI di reindirizzamento. Per le applicazioni web, questo è l’URL di base dell’app a cui gli utenti possono accedere. Ad esempio, `http://localhost:12345`. Per i client pubblici (mobili e desktop), Azure AD lo utilizza per restituire le risposte token. Immettere un valore specifico per l&#39;applicazione. Ad esempio, `http://MyFirstAADApp`.

1. Dopo aver completato la registrazione, Azure AD assegna all&#39;applicazione un identificatore client univoco (ID applicazione). Questo valore è necessario nella sezione successiva, quindi copialo dalla pagina dell’applicazione.

1. Per trovare l&#39;applicazione nel portale di Azure, fare clic su **[!UICONTROL App Registrations]**, quindi su **[!UICONTROL All Applications]**. Apri la nuova applicazione creata

1. Fare clic su **[!UICONTROL Authentication]** nel menu a sinistra.

   ![](assets/getting-dynamics-11.png)

1. Aggiungere gli URL di reindirizzamento [!DNL Marketo Measure]: `https://apps.bizible.com/OAuth2` e `https://apps.bizible.com/OAuth2?identityOnly=true` all&#39;elenco degli URL di reindirizzamento.

   ![](assets/getting-dynamics-2.png)

1. Passa alla scheda Autorizzazioni API e accertati che all’applicazione siano assegnate le autorizzazioni corrette.

   ![](assets/getting-dynamics-3.png)

1. Da qui immettere &quot;[!UICONTROL enterprise]&quot; nella casella di ricerca e fare clic su **[!UICONTROL Enterprise Applications]**.

   ![](assets/getting-dynamics-4.png)

1. Di nuovo, individua e apri la nuova applicazione dall’elenco delle applicazioni.

1. Nella scheda Autorizzazioni fare clic su **[!UICONTROL Grant Admin Consent for (instance name)]**.

   ![](assets/getting-dynamics-5.png)

1. Fai clic su **[!UICONTROL Accept]**.

   ![](assets/getting-dynamics-6.png)

1. Dalla scheda &quot;[!UICONTROL Users and Groups]&quot;, assicurarsi che &quot;Utenti e gruppi&quot; validi siano assegnati all&#39;applicazione.

   ![](assets/getting-dynamics-7.png)

## Creazione di un utente dell&#39;applicazione {#creating-an-application-user}

Al termine della registrazione dell’applicazione, è possibile creare un utente dell’applicazione.

1. Passare all&#39;ambiente Common Data Service (`https://[org].crm.dynamics.com`).

1. Passa a **[!UICONTROL Settings]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.

1. Scegliere **[!UICONTROL Application Users]** nel filtro di visualizzazione.

1. Selezionare **[!UICONTROL + New]**.

1. Nel modulo Utente applicazione immettere le informazioni richieste.

   >[!NOTE]
   >
   >* Le informazioni sul nome utente non devono corrispondere a un utente esistente in [!DNL Azure Active Directory].
   >
   >* Nel campo ID applicazione immettere l&#39;ID applicazione dell&#39;app registrata in precedenza in Azure AD.

1. Se la configurazione è corretta, dopo aver selezionato **[!UICONTROL Save]**, i campi **[!UICONTROL Application ID URI]** e **[!UICONTROL Azure AD Object Id]** verranno compilati automaticamente con i valori corretti.

1. Prima di uscire dal modulo utente, scegliere **[!UICONTROL Manage Roles]** e assegnare un ruolo di sicurezza all&#39;utente dell&#39;applicazione in modo che possa accedere ai dati dell&#39;organizzazione desiderati.

## Connessione dell’istanza Dynamics tramite OAuth {#connecting-your-dynamics-instance-via-oAuth}

1. Quando configuri la tua connessione Dynamics per la prima volta, segui i passaggi 1-5 della sezione &quot;CRM come provider di dati&quot; in [questo articolo](/help/marketo-measure-and-dynamics/microsoft-dynamics-crm-installation-guide.md).

1. Quando viene richiesto di immettere le credenziali OAuth, compila l’ID client, il segreto client e l’URI dell’ID applicazione impostati nella sezione precedente.

a. L’ID client è l’ID del passaggio #7 nella sezione precedente. Se non l&#39;hai annotato, l&#39;ID applicazione viene visualizzato nelle Impostazioni della registrazione dell&#39;app.

b. Segreto client è il segreto dell’applicazione creato nel portale di Azure per l’applicazione in Certificati e segreti.

![](assets/getting-dynamics-8.png)

c. L’URI dell’ID applicazione è l’URL dell’API web di destinazione (risorsa protetta). Per trovare l&#39;URL dell&#39;ID app, nel portale di Azure fare clic su [!DNL Azure Active Directory], fare clic su Registrazioni applicazioni, aprire la pagina Impostazioni dell&#39;applicazione, quindi fare clic su Proprietà. Potrebbe anche essere una risorsa esterna come `https://graph.microsoft.com`. Questo è normalmente l’URL dell’istanza Dynamics.

1. Dopo aver fatto clic su **[!UICONTROL Submit]**, ti verrà richiesto di accedere con [!DNL Azure Active Directory]. Quando l&#39;autenticazione ha esito positivo, l&#39;account Dynamics è connesso come provider di dati in [!DNL Marketo Measure].

## Nuova autenticazione dell’account Dynamics {#re-authenticating-your-dynamics-account}

1. Quando ti trovi nell&#39;applicazione [!DNL Marketo Measure], passa a **[!UICONTROL My Settings]** > **[!UICONTROL Settings]** > **[!UICONTROL Connections]**.

1. Fai clic sull’icona della chiave nella sezione CRM accanto alla connessione Dynamics.

1. Quando si fa clic sulla chiave, viene visualizzato un pop-up in cui viene richiesto di immettere l&#39;ID client, il segreto client e l&#39;URI dell&#39;ID applicazione, in modo analogo al flusso di iscrizione.

   ![](assets/getting-dynamics-9.png)

1. Dopo aver fatto clic su **[!UICONTROL Submit]**, ti verrà richiesto di accedere con [!DNL Azure Active Directory]. Quando l&#39;autenticazione ha esito positivo, l&#39;account Dynamics viene nuovamente autorizzato entro [!DNL Marketo Measure].
