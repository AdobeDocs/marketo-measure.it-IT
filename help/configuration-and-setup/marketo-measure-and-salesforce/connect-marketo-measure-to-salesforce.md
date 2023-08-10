---
unique-page-id: 18874580
description: Collegare Marketo Measure a Salesforce - [!DNL Marketo Measure] - Documentazione del prodotto
title: Connettere Marketo Measure a Salesforce
exl-id: 9be8d3fa-1045-4e41-bc2e-5b9d4d3513ae
feature: Salesforce
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Connettere Marketo Measure a Salesforce {#connect-marketo-measure-to-salesforce}

Questo articolo fornisce una panoramica su come collegare [!DNL Salesforce] account per il tuo [!DNL Marketo Measure] account.

## Connessione [!DNL Marketo Measure] con [!DNL Salesforce] {#connecting-marketo-measure-with-salesforce}

1. Utilizza un browser in incognito per accedere a [!DNL Marketo Measure].

1. Nella barra dei menu nella parte superiore dello schermo, passa a **[!UICONTROL My Account]** e fai clic su [!UICONTROL Settings] opzione.

1. Nella colonna di opzioni di impostazione a sinistra, fare clic su [!UICONTROL Connections] si trova sotto [!UICONTROL Integrations] sezione.

   ![](assets/1.png)

1. Nella sezione CRM in Connessioni, fai clic su **[!UICONTROL Set Up New CRM Connection]**.

   ![](assets/2.png)

1. Verrà visualizzata una finestra popup in cui viene richiesto di selezionare la connessione CRM. Fai clic su [!UICONTROL Connect] accanto al pulsante [!DNL Salesforce] Logo.

   ![](assets/3.png)

1. Viene visualizzata una finestra pop-up finale in cui viene richiesto di [!DNL Salesforce] credenziali, sandbox o produzione. Inserisci le tue informazioni e fai clic su **[!UICONTROL Authorize]** per collegare l&#39;account a [!DNL Marketo Measure].

>[!NOTE]
>
>[!DNL Marketo Measure] può essere connesso a una sola [!DNL Salesforce] alla volta.
>
>* A [!DNL Marketo Measure] L&#39;istanza può essere connessa a un&#39;istanza Sandbox SFDC per testare l&#39;integrazione prima di passare alla connessione all&#39;istanza di produzione SFDC.
>* Se esegui prima il test con una sandbox SFDC, ti consigliamo vivamente di eseguire il test con una che sia una replica esatta dell’istanza di produzione SFDC in termini di campi sugli oggetti Lead, Contatto, Account, Opportunità, Campagna e Caso. Se in produzione sono presenti trigger APEX attivi che attivano gli aggiornamenti per gli oggetti Lead, Contact, Account, Opportunity, Campaign e Case, è necessario provare a renderli attivi nella sandbox.
>* Al termine del test, potrai aggiornare [!DNL Marketo Measure] account per indicare la tua produzione [!DNL Salesforce] (anziché Sandbox [!DNL Salesforce]). A causa del modo in cui è stata costruita l’integrazione, una volta [!DNL Marketo Measure] l&#39;account è connesso alla produzione [!DNL Salesforce], non è possibile tornare indietro e connettersi a una sandbox [!DNL Salesforce] org.

