---
unique-page-id: 18874580
description: Collegare Marketo Measure a Salesforce - [!DNL Marketo Measure] - Documentazione del prodotto
title: Collegare Marketo Measure a Salesforce
exl-id: 9be8d3fa-1045-4e41-bc2e-5b9d4d3513ae
source-git-commit: 993a326c377b3b6ff48c4e0114b59297f9ca2ca6
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Collegare Marketo Measure a Salesforce {#connect-marketo-measure-to-salesforce}

Questo articolo fornisce una panoramica su come collegare le [!DNL Salesforce] l&#39;account [!DNL Marketo Measure] conto.

## Collegamento [!DNL Marketo Measure] con [!DNL Salesforce] {#connecting-marketo-measure-with-salesforce}

1. Utilizzare un browser in incognito per accedere a [!DNL Marketo Measure].

1. Nella barra dei menu nella parte superiore dello schermo, seleziona **[!UICONTROL My Account]** e fai clic su [!UICONTROL Settings] opzione .

1. Nella colonna delle opzioni di impostazione a sinistra, fai clic su [!UICONTROL Connections] situato sotto [!UICONTROL Integrations] sezione .

   ![](assets/1.png)

1. Nella sezione CRM in Connessioni, fai clic su **[!UICONTROL Set Up New CRM Connection]**.

   ![](assets/2.png)

1. Viene visualizzata una finestra pop-up che ti chiede di selezionare la connessione CRM. Fai clic sul pulsante [!UICONTROL Connect] accanto al pulsante [!DNL Salesforce] logo.

   ![](assets/3.png)

1. Viene visualizzata una finestra pop-up finale, che ti chiede il tuo [!DNL Salesforce] credenziali, sandbox o produzione. Inserisci le tue informazioni e fai clic su **[!UICONTROL Authorize]** per collegare l’account a [!DNL Marketo Measure].

>[!NOTE]
>
>[!DNL Marketo Measure] può essere collegato solo a un [!DNL Salesforce] istanza alla volta.
>
>* A [!DNL Marketo Measure] È possibile collegare un’istanza a un’istanza Sandbox SFDC per testare l’integrazione prima di passare alla connessione all’istanza di produzione SFDC.
>* Se esegui prima il test con una Sandbox SFDC, ti consigliamo vivamente di testarne una che sia una replica esatta dell’istanza di produzione SFDC in termini di campi relativi agli oggetti Lead, Contact, Account, Opportunity, Campaign e Case. Se in produzione sono presenti attivatori APEX attivi che attivano gli aggiornamenti agli oggetti Lead, Contact, Account, Opportunity, Campaign e Case, dovresti provare a attivarli nella sandbox.
>* Una volta terminato il test, aggiornerai il tuo [!DNL Marketo Measure] per puntare alla vostra produzione [!DNL Salesforce] (anziché Sandbox [!DNL Salesforce]). A causa del modo in cui è stata realizzata l’integrazione, una volta [!DNL Marketo Measure] l&#39;account è collegato a Produzione [!DNL Salesforce], non puoi andare &quot;indietro&quot; e connetterti a una sandbox [!DNL Salesforce] org.


