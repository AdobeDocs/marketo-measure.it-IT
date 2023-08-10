---
unique-page-id: 18874793
description: Utilizzo di un campo personalizzato per l’importo dei ricavi - [!DNL Marketo Measure] - Documentazione del prodotto
title: Utilizzo di un campo personalizzato per l'importo dei ricavi
exl-id: 517ea4f9-aa83-48d0-8ce7-003f4a907430
feature: Custom Revenue Amount
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# Utilizzo di un campo personalizzato per l&#39;importo dei ricavi {#using-a-custom-revenue-amount-field}

Per impostazione predefinita, i punti di contatto di attribuzione buyer richiameranno l’importo dell’opportunità da uno dei due campi seguenti:

* Importo (predefinito SFDC)
* [!DNL Marketo Measure] Importo dell’opportunità (personalizzato)

Se utilizzi un campo Importo personalizzato nelle opportunità, dovremo configurare un flusso di lavoro per calcolare i ricavi del punto di contatto dell’acquirente. Questa operazione richiede una conoscenza più avanzata di [!DNL Salesforce], quindi potrebbe richiedere l&#39;assistenza dell&#39;amministratore SFDC.

A partire da, avremo bisogno delle seguenti informazioni:

* Nome API del campo Importo

Da qui, inizieremo a creare il flusso di lavoro.

1. Accedi a **[!UICONTROL Setup]** > **[!UICONTROL Create]** > **[!UICONTROL Workflow & Approvals]** > **[!UICONTROL Workflow Rules]**.

   ![](assets/1.jpg)

1. Seleziona **[!UICONTROL New Rule]**, impostare l&#39;oggetto come &quot;Opportunità&quot; e fare clic su **[!UICONTROL Next]**.

   ![](assets/2.jpg)

   ![](assets/3.jpg)

1. Configura il flusso di lavoro. Imposta il nome della regola come &quot;Aggiorna&quot; [!DNL Marketo Measure] Importo dell’opportunità.&quot; Imposta il criterio di valutazione su &quot;Creato e ogni volta che viene modificato&quot;. Per Criteri regola, seleziona il campo Importo personalizzato e l’operatore [!UICONTROL as "Not Equal To"] e lasciare vuoto il campo &quot;Valore&quot;.

   ![](assets/4.jpg)

1. Aggiungi un’azione del flusso di lavoro. Imposta questo elenco a discesa su &quot;[!UICONTROL New Field Update].&quot;

   ![](assets/5.jpg)

1. Qui compilerai le informazioni sul campo. Nel campo &quot;Nome&quot;, si consiglia di utilizzare questa denominazione: &quot;[!DNL Marketo Measure] Importo Opp.&quot; Il &quot;Nome univoco&quot; verrà compilato automaticamente in base al campo &quot;Nome&quot;. Nell’elenco a discesa &quot;Campo da aggiornare&quot;, seleziona &quot;[!DNL Marketo Measure] Importo dell’opportunità.&quot; Dopo aver selezionato il campo, seleziona la casella &quot;Re-Evaulate Workflow Rules after Field Change&quot; (Valuta nuovamente regole flusso di lavoro dopo la modifica del campo). In &quot;Specifica nuovo valore campo&quot;, selezionare &quot;Utilizza una formula per impostare il nuovo valore&quot;. Nella casella vuota, rilascia il nome API del campo Importo personalizzato. Clic **[!UICONTROL Save]**.

   ![](assets/6.png)

1. Verrai riportato a una pagina di rollup per il flusso di lavoro, assicurati di &quot;Attivare&quot; e sarai a posto. Per attivare, fai clic su **Modifica** accanto al nuovo flusso di lavoro e quindi fai clic su **Attiva**.

   Dopo aver completato questi passaggi, le opportunità dovranno essere aggiornate per attivare il flusso di lavoro in modo che abbia il nuovo valore da [!UICONTROL custom opportunity] campo.

   A tale scopo, esegui le opportunità tramite Data Loader in SFDC. Scopri come utilizzare Data Loader in [questo articolo](/help/advanced-marketo-measure-features/custom-revenue-amount/using-data-loader-to-update-marketo-measure-custom-amount-field.md).

In caso di domande, contatta il team degli Adobi (il tuo Account Manager) o [[!DNL Marketo] Supporto](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
