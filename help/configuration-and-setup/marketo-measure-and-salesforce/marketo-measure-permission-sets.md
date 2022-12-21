---
unique-page-id: 18874789
description: "[!DNL Marketo Measure] Set di autorizzazioni - [!DNL Marketo Measure] - Documentazione del prodotto"
title: "[!DNL Marketo Measure] Set di autorizzazioni"
exl-id: 84b7aa24-3934-4584-af05-02e804d00a98
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# [!DNL Marketo Measure] Set di autorizzazioni {#marketo-measure-permission-sets}

Scopri come accedere e assegnare [!DNL Marketo Measure] Set di autorizzazioni in Salesforce.

## [!DNL Marketo Measure] Set di autorizzazioni {#marketo-measure-permission-sets-1}

Sono inclusi tre set di autorizzazioni con [!DNL Marketo Measure] Pacchetto Salesforce. Questi set di autorizzazioni consentono di accedere a [!DNL Marketo Measure] per amministratori, addetti al marketing e utenti standard.

Per accedere e assegnare set di autorizzazioni in Salesforce:

1. Clic **[!UICONTROL Setup]**.
1. A sinistra, fai clic su **[!UICONTROL Users]**, quindi **[!UICONTROL Permission Sets]**.
1. Seleziona la [!DNL Marketo Measure] Set di autorizzazioni da assegnare.
1. Fai clic su **[!UICONTROL Manage Assignments]**, quindi **[!UICONTROL Add Assignments]**.
1. Seleziona gli utenti per il set di autorizzazioni e fai clic su **[!UICONTROL Assign]**.

   ![](assets/1-5.png)

## [!DNL Marketo Measure] Spiegazione dei set di autorizzazioni {#marketo-measure-permission-sets-explained}

<table> 
 <tbody> 
  <tr> 
   <td><span><strong>[!DNL Marketo Measure] Amministratore</strong></span></td> 
   <td><span>Consente a un amministratore SFDC di creare, leggere, scrivere ed eliminare i record da [!DNL Marketo Measure] oggetti. La licenza in base alla quale [!DNL Marketo Measure] invia i dati a SFDC dovrebbe avere questo set di autorizzazioni abilitato. Inoltre, si consiglia che questa licenza abbia la possibilità di modificare i lead convertiti negli scenari in cui il lead viene convertito prima di [!DNL Marketo Measure] applicazione di dati al record. In questo modo sarà possibile garantire l’accuratezza delle relazioni tra Salesforce e [!DNL Marketo Measure]. <a href="http://releasenotes.docs.salesforce.com/en-us/spring17/release-notes/rn_sales_leads_view_converted.htm">Ulteriori informazioni qui</a>.</span></td> 
  </tr> 
  <tr> 
   <td><span><strong>[!DNL Marketo Measure] Utente marketing</strong></span></td> 
   <td><span>Consente a un utente marketing di leggere e scrivere record da [!DNL Marketo Measure] oggetti. Tutti i membri del team marketing devono avere [!DNL Marketo Measure] Set di autorizzazioni utente marketing abilitato. <br></span></td> 
  </tr> 
  <tr> 
   <td><span><strong>[!DNL Marketo Measure] Utente standard</strong></span></td> 
   <td><span>Consente a un utente di leggere i record da [!DNL Marketo Measure] oggetti.</span></td> 
  </tr> 
 </tbody> 
</table>

I team di sviluppo delle vendite in entrata e i dirigenti di account possono trarre vantaggio da [!DNL Marketo Measure] dati. Se desideri utilizzare questi ruoli [!DNL Marketo Measure] dati nel reporting, abilita [!DNL Marketo Measure] Set di autorizzazioni Utente standard.

>[!NOTE]
>
>Inoltre, l&#39;utente a cui siamo collegati deve avere l&#39;&quot;Utente di marketing&quot; [!DNL Salesforce] Profilo abilitato a livello di utente per consentirci di accedere all’oggetto Campaign. Per verificare questo, fai clic su **[!UICONTROL Setup]** > **[!UICONTROL Manage Users]** > **[!UICONTROL Profiles]** > **[!UICONTROL Marketing User]** > **Utenti assegnati**.
