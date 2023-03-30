---
unique-page-id: 18874793
description: Utilizzo di un campo Importo ricavi personalizzato - [!DNL Marketo Measure] - Documentazione del prodotto
title: Utilizzo di un campo Importo ricavi personalizzato
exl-id: 517ea4f9-aa83-48d0-8ce7-003f4a907430
source-git-commit: 51397a02872035fef41d308c1f855bcaecc29c4e
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# Utilizzo di un campo Importo ricavi personalizzato {#using-a-custom-revenue-amount-field}

Per impostazione predefinita, i punti di contatto di attribuzione dell’acquirente estraggono l’importo dell’opportunità da uno dei due campi seguenti:

* Importo (predefinito SFDC)
* [!DNL Marketo Measure] Importo opportunità (personalizzato)

Se utilizzi un campo Importo personalizzato sulle opportunità, sarà necessario configurare un flusso di lavoro per calcolare i ricavi dei punti di contatto dell’acquirente. Questa operazione richiede una conoscenza più avanzata di [!DNL Salesforce], quindi potrebbe richiedere l’assistenza dell’amministratore SFDC.

A partire da questo momento, saranno necessarie le seguenti informazioni:

* Nome API del campo Importo

Da qui inizieremo a creare il flusso di lavoro.

1. Passa a **[!UICONTROL Setup]** > **[!UICONTROL Create]** > **[!UICONTROL Workflow & Approvals]** > **[!UICONTROL Workflow Rules]**.

   ![](assets/1.jpg)

1. Seleziona **[!UICONTROL New Rule]**, imposta l&#39;oggetto come &quot;Opportunity&quot; e fai clic su **[!UICONTROL Next]**.

   ![](assets/2.jpg)

   ![](assets/3.jpg)

1. Configura il flusso di lavoro. Imposta il nome della regola come &quot;Aggiorna [!DNL Marketo Measure] Importo opportunità.&quot; Imposta i criteri di valutazione su &quot;Creato e ogni volta che viene modificato&quot;. Per Criteri regola, seleziona il campo Importo personalizzato e seleziona l&#39;operatore [!UICONTROL as "Not Equal To"] e lasciare vuoto il campo &quot;Valore&quot;.

   ![](assets/4.jpg)

1. Aggiungi un’azione del flusso di lavoro. Imposta questo elenco di selezione su &quot;[!UICONTROL New Field Update].&quot;

   ![](assets/5.jpg)

1. Qui si compilano le informazioni sul campo. Nel campo &quot;Nome&quot;, si consiglia di utilizzare questa denominazione: &quot;[!DNL Marketo Measure] Importo Opp.&quot; Il campo &quot;Nome univoco&quot; verrà compilato automaticamente in base al campo &quot;Nome&quot;. Nella casella di selezione &quot;Campo da aggiornare&quot; selezionare &quot;[!DNL Marketo Measure] Importo opportunità.&quot; Dopo aver selezionato il campo, selezionare la casella &quot;Rielabora regole flusso di lavoro dopo la modifica del campo&quot;. In &quot;Specifica nuovo valore campo&quot;, selezionare &quot;Utilizza una formula per impostare il nuovo valore&quot;. Nella casella vuota, rilascia il nome API del campo Importo personalizzato. Clic **[!UICONTROL Save]**.

   ![](assets/6.png)

1. Verrai riportato a una pagina di rollup per il tuo flusso di lavoro, assicurati di &quot;Attivare&quot; e sarai in grado di farlo. Per attivare, fai clic su **Modifica** accanto al nuovo flusso di lavoro, quindi fai clic su **Attiva**.

   Una volta completati questi passaggi, le opportunità dovranno essere aggiornate per attivare il flusso di lavoro in modo che il nuovo valore dal [!UICONTROL custom opportunity] campo .

   Questo può essere realizzato eseguendo le tue opportunità tramite Data Loader all&#39;interno di SFDC. Per informazioni sull&#39;utilizzo di Data Loader in [articolo](/help/advanced-marketo-measure-features/custom-revenue-amount/using-data-loader-to-update-marketo-measure-custom-amount-field.md).

In caso di domande lungo il percorso, non esitare a contattare il team dell&#39;account Adobe (il tuo Account Manager) o [[!DNL Marketo] Supporto](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
