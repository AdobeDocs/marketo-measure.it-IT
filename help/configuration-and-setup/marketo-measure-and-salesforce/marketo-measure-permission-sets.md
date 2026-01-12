---
description: '[!DNL Marketo Measure] set di autorizzazioni - [!DNL Marketo Measure]'
title: '[!DNL Marketo Measure] set di autorizzazioni'
exl-id: 84b7aa24-3934-4584-af05-02e804d00a98
feature: Salesforce
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---


# [!DNL Marketo Measure] set di autorizzazioni {#marketo-measure-permission-sets}

Scopri come accedere e assegnare [!DNL Marketo Measure] set di autorizzazioni in Salesforce.

## [!DNL Marketo Measure] set di autorizzazioni {#marketo-measure-permission-sets-1}

Con il pacchetto Salesforce [!DNL Marketo Measure] sono inclusi tre set di autorizzazioni. Questi set di autorizzazioni forniscono l&#39;accesso a [!DNL Marketo Measure] per amministratori, addetti al marketing e utenti standard.

Per accedere e assegnare i set di autorizzazioni in Salesforce:

1. Fai clic su **[!UICONTROL Setup]**.
1. Nel margine sinistro fare clic su **[!UICONTROL Users]**, quindi su **[!UICONTROL Permission Sets]**.
1. Selezionare il set di autorizzazioni [!DNL Marketo Measure] da assegnare.
1. Fare clic su **[!UICONTROL Manage Assignments]**, quindi su **[!UICONTROL Add Assignments]**.
1. Selezionare gli utenti per il set di autorizzazioni e fare clic su **[!UICONTROL Assign]**.

   ![ 5](assets/1-5.png)

## [!DNL Marketo Measure] set di autorizzazioni spiegati {#marketo-measure-permission-sets-explained}

<table>
 <tbody>
  <tr>
   <td><span><strong>[!DNL Marketo Measure] Amministratore</strong></span></td>
   <td><span>Consente a un amministratore di SFDC di creare, leggere, scrivere ed eliminare record da [!DNL Marketo Measure] oggetti. La licenza con cui [!DNL Marketo Measure] invia i dati a SFDC deve avere questo set di autorizzazioni abilitato. Inoltre, si consiglia che questa licenza abbia la possibilità di modificare i lead convertiti negli scenari in cui il lead viene convertito prima di [!DNL Marketo Measure] applicando i dati al record. In questo modo viene garantita l'accuratezza del reporting tra Salesforce e [!DNL Marketo Measure]. <a href="https://help.salesforce.com/articleView?id=release-notes.rn_sales_leads_view_converted.htm&amp;type=5&amp;release=206&amp;language=en_us">Ulteriori informazioni</a>.</span></td>
  </tr>
  <tr>
   <td><span><strong>[!DNL Marketo Measure] Utente marketing</strong></span></td>
   <td><span>Consente a un utente marketing di leggere e scrivere record da [!DNL Marketo Measure] oggetti. Tutti i membri del team marketing devono avere l'autorizzazione Utente marketing [!DNL Marketo Measure] abilitata. <br></span></td>
  </tr>
  <tr>
   <td><span><strong>[!DNL Marketo Measure] Utente standard</strong></span></td>
   <td><span>Consente a un utente di leggere i record da [!DNL Marketo Measure] oggetti.</span></td>
  </tr>
 </tbody>
</table>

I team di sviluppo vendite in entrata e i responsabili dell&#39;account potrebbero trarre vantaggio dai dati di [!DNL Marketo Measure]. Se questi ruoli desiderano utilizzare i dati [!DNL Marketo Measure] nel reporting, abilitare il set di autorizzazioni utente standard [!DNL Marketo Measure].

>[!NOTE]
>Inoltre, per poter accedere all’oggetto Campaign, l’utente tramite il quale siamo connessi deve avere il profilo &quot;Utente marketing&quot; [!DNL Salesforce] abilitato a livello di utente. Per verificare questa situazione, fare clic su **[!UICONTROL Setup]** > **[!UICONTROL Manage Users]** > **[!UICONTROL Profiles]** > **[!UICONTROL Marketing User]** > **Utenti assegnati**.
