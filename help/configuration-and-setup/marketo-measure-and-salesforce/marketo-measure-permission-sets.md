---
unique-page-id: 18874789
description: "[!DNL Marketo Measure] Set di autorizzazioni - [!DNL Marketo Measure] - Documentazione del prodotto"
title: "[!DNL Marketo Measure] Set di autorizzazioni"
exl-id: 84b7aa24-3934-4584-af05-02e804d00a98
feature: Salesforce
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# [!DNL Marketo Measure] Set di autorizzazioni {#marketo-measure-permission-sets}

Scopri come accedere e assegnare [!DNL Marketo Measure] Set di autorizzazioni in Salesforce.

## [!DNL Marketo Measure] Set di autorizzazioni {#marketo-measure-permission-sets-1}

Tre set di autorizzazioni sono inclusi nel [!DNL Marketo Measure] Pacchetto Salesforce Questi set di autorizzazioni forniscono accesso a [!DNL Marketo Measure] per amministratori, addetti al marketing e utenti standard.

Per accedere e assegnare i set di autorizzazioni in Salesforce:

1. Clic **[!UICONTROL Setup]**.
1. Nel margine sinistro, fai clic su **[!UICONTROL Users]**, quindi **[!UICONTROL Permission Sets]**.
1. Seleziona la [!DNL Marketo Measure] Set di autorizzazioni che desideri assegnare.
1. Clic **[!UICONTROL Manage Assignments]**, quindi **[!UICONTROL Add Assignments]**.
1. Seleziona gli utenti per il set di autorizzazioni e fai clic su **[!UICONTROL Assign]**.

   ![](assets/1-5.png)

## [!DNL Marketo Measure] Spiegazione dei set di autorizzazioni {#marketo-measure-permission-sets-explained}

<table> 
 <tbody> 
  <tr> 
   <td><span><strong>[!DNL Marketo Measure] Amministratore</strong></span></td> 
   <td><span>Consente a un amministratore SFDC di creare, leggere, scrivere ed eliminare record da [!DNL Marketo Measure] oggetti. La licenza in base alla quale [!DNL Marketo Measure] invia i dati a SFDC se questo set di autorizzazioni è abilitato. Inoltre, si consiglia che questa licenza possa modificare i lead convertiti negli scenari in cui il lead viene convertito prima di [!DNL Marketo Measure] applicazione dei dati al record. Questo garantirà la precisione nella generazione dei rapporti tra Salesforce e [!DNL Marketo Measure]. <a href="http://releasenotes.docs.salesforce.com/en-us/spring17/release-notes/rn_sales_leads_view_converted.htm">Fai clic qui per ulteriori informazioni</a>.</span></td> 
  </tr> 
  <tr> 
   <td><span><strong>[!DNL Marketo Measure] Utente marketing</strong></span></td> 
   <td><span>Consente a un utente marketing di leggere e scrivere record da [!DNL Marketo Measure] oggetti. Tutti i membri del team di marketing devono avere [!DNL Marketo Measure] Set di autorizzazioni per gli utenti marketing abilitato. <br></span></td> 
  </tr> 
  <tr> 
   <td><span><strong>[!DNL Marketo Measure] Utente standard</strong></span></td> 
   <td><span>Consente a un utente di leggere i record da [!DNL Marketo Measure] oggetti.</span></td> 
  </tr> 
 </tbody> 
</table>

I team addetti allo sviluppo delle vendite in entrata e gli account executive possono trarre vantaggio da [!DNL Marketo Measure] dati. Se questi ruoli desiderano utilizzare [!DNL Marketo Measure] dati nel reporting, abilita [!DNL Marketo Measure] Set di autorizzazioni utente standard.

>[!NOTE]
>
>Inoltre, l’utente tramite il quale siamo connessi deve avere l’&quot;Utente di marketing&quot; [!DNL Salesforce] Profilo abilitato a livello di utente per l’accesso all’oggetto Campaign. Per verificare questa situazione, fai clic su in **[!UICONTROL Setup]** > **[!UICONTROL Manage Users]** > **[!UICONTROL Profiles]** > **[!UICONTROL Marketing User]** > **Utenti assegnati**.
