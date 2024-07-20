---
unique-page-id: 18874580
description: Connetti Marketo Measure a Salesforce - [!DNL Marketo Measure]
title: Connettere Marketo Measure a Salesforce
exl-id: 9be8d3fa-1045-4e41-bc2e-5b9d4d3513ae
feature: Salesforce
source-git-commit: 741ab20845de2f3bcde589291d7446a5b4f877d8
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# Connettere Marketo Measure a Salesforce {#connect-marketo-measure-to-salesforce}

Questo articolo fornisce una panoramica su come collegare l&#39;account [!DNL Salesforce] all&#39;account [!DNL Marketo Measure].

## Connessione di [!DNL Marketo Measure] con [!DNL Salesforce] {#connecting-marketo-measure-with-salesforce}

1. Utilizzare un browser in incognito per accedere a [!DNL Marketo Measure].

1. Nella barra dei menu nella parte superiore dello schermo, passare a **[!UICONTROL My Account]** e fare clic sull&#39;opzione **[!UICONTROL Settings]**.

1. Nella colonna di opzioni di impostazione a sinistra, fare clic su **[!UICONTROL Connections]** che si trova nella sezione [!UICONTROL Integrations].

   ![](assets/connect-marketo-measure-to-salesforce-1.png)

1. Nella sezione CRM in Connessioni fare clic su **[!UICONTROL Set Up New CRM Connection]**.

   ![](assets/connect-marketo-measure-to-salesforce-2.png)

1. Viene visualizzata una finestra popup in cui viene richiesto di selezionare la connessione CRM. Fare clic su **[!UICONTROL Connect]** accanto al logo [!DNL Salesforce].

   ![](assets/connect-marketo-measure-to-salesforce-3.png)

1. Viene visualizzata una finestra popup finale che richiede le credenziali [!DNL Salesforce], la sandbox o la produzione. Immettere le informazioni e fare clic su **[!UICONTROL Authorize]** per connettere l&#39;account a [!DNL Marketo Measure].

>[!NOTE]
>
>[!DNL Marketo Measure] può essere connesso a una sola istanza [!DNL Salesforce] alla volta.
>
>* Un&#39;istanza [!DNL Marketo Measure] può essere connessa a un&#39;istanza Sandbox SFDC per testare l&#39;integrazione prima di passare alla connessione all&#39;istanza di produzione SFDC.
>* Se esegui prima il test con una sandbox SFDC, ti consigliamo vivamente di eseguire il test con una che sia una replica esatta dell’istanza di produzione SFDC in termini di campi sugli oggetti Lead, Contatto, Account, Opportunità, Campagna e Caso. Se in produzione sono presenti trigger APEX attivi che attivano gli aggiornamenti per gli oggetti Lead, Contact, Account, Opportunity, Campaign e Case, è necessario provare a renderli attivi nella sandbox.
>* Al termine del test, aggiorna l&#39;account [!DNL Marketo Measure] in modo che punti alla [!DNL Salesforce] di produzione (anziché alla Sandbox [!DNL Salesforce]). A causa del modo in cui è stata creata l&#39;integrazione, una volta che un account [!DNL Marketo Measure] è connesso alla produzione [!DNL Salesforce], non è possibile tornare indietro e connettersi a un&#39;organizzazione Sandbox [!DNL Salesforce].

## Utilizzo crediti API {#api-credits-usage}

Marketo Measure impiega un&#39;attività di integrazione CRM per interfacciarsi con la Salesforce di un cliente attraverso un utente integrato. Tutti gli scambi di dati tramite questo utente utilizzano i crediti API Salesforce. Puoi allocare una quota di credito a un utente di integrazione, il che consente di regolare chiamate API eccessive. La quota o il limite viene reimpostato ogni 24 ore.

Puoi accedere a questo limite in Marketo Measure tramite: **Il mio account** > **Impostazioni** > **CRM** > **Generale** > **Limite API CRM giornaliero** e puoi configurarlo per i tenant.

![](assets/connect-marketo-measure-to-salesforce-4.png)

### Impostazione di un limite per i crediti API {#setting-a-limit-for-api-credits}

1. Passa a **Il mio account** > **Impostazioni**.

1. In CRM, fare clic su **Generale**. È disponibile l&#39;opzione **Limite API CRM giornaliero**.

1. Fai clic sull’icona Blocca per modificarla.

   ![](assets/connect-marketo-measure-to-salesforce-5.png)

1. Inserisci un limite desiderato uguale o superiore a 100.000. Al termine, fai clic su **Salva**.

   ![](assets/connect-marketo-measure-to-salesforce-6.png)

>[!NOTE]
>
>Per aumentare i crediti API di Salesforce disponibili per la soluzione connessa, contatta l&#39;amministratore Salesforce e fai riferimento a [questo documento Salesforce](https://developer.salesforce.com/docs/atlas.en-us.salesforce_app_limits_cheatsheet.meta/salesforce_app_limits_cheatsheet/salesforce_app_limits_platform_api.htm){target="_blank"}.

>[!MORELIKETHIS]
>
>[Notifiche di errore](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md){target="_blank"}
