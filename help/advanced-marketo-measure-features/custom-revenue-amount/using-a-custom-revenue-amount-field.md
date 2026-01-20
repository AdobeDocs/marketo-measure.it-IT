---
unique-page-id: 18874793
description: Utilizzo di un campo personalizzato per l'importo dei ricavi - [!DNL Marketo Measure]
title: Utilizzo di un campo personalizzato per l'importo dei ricavi
exl-id: 517ea4f9-aa83-48d0-8ce7-003f4a907430
feature: Custom Revenue Amount
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 0%

---

# Utilizzo di un campo personalizzato per l&#39;importo dei ricavi {#using-a-custom-revenue-amount-field}

Per impostazione predefinita, i punti di contatto di attribuzione buyer richiameranno l’importo dell’opportunità da uno dei due campi seguenti:

* Importo (predefinito SFDC)
* [!DNL Marketo Measure] importo opportunità (personalizzato)

Se utilizzi un campo Importo personalizzato nelle opportunità, sarà necessario configurare un flusso di lavoro per calcolare i ricavi di Buyer Touchpoint. Questa operazione richiede una conoscenza più avanzata di [!DNL Salesforce], pertanto potrebbe richiedere l&#39;assistenza dell&#39;amministratore di SFDC.

A partire da, avremo bisogno delle seguenti informazioni:

* Nome API del campo Importo

Da qui inizieremo a creare il flusso di lavoro.

## Creazione del flusso di lavoro in Salesforce Lightning {#create-the-workflow-in-salesforce-lightning}

I seguenti passaggi sono per gli utenti di Salesforce Lightning. Se utilizzi ancora Salesforce Classic, i passaggi [sono elencati di seguito](#create-the-workflow-in-salesforce-classic).

1. Da Configurazione, digitare &quot;Flussi&quot; nella casella Ricerca rapida e selezionare **[!UICONTROL Flows]** per avviare Flow Builder. Nel pannello di destra fare clic sul pulsante **[!UICONTROL New Flow]**.

   ![](assets/using-a-custom-revenue-amount-field-1.png)

1. Seleziona **[!UICONTROL Record-Triggered Flow]** e fai clic su **[!UICONTROL Create]** in basso a destra.

   ![](assets/using-a-custom-revenue-amount-field-2.png)

1. Nella finestra Configura avvio, selezionare l&#39;oggetto Opportunità. Dalla sezione [!UICONTROL Configure Trigger], selezionare **[!UICONTROL A record is created or updated]**.

   ![](assets/using-a-custom-revenue-amount-field-3.png)

1. Nella sezione Imposta condizioni di ingresso selezionare [!UICONTROL Condition Requirements] in **[!UICONTROL Custom Condition Logic Is Met]**.
   * Dal campo di ricerca, selezionare il campo Importo personalizzato.
   * Impostare l&#39;operatore come **Is Null** e il valore come **[!UICONTROL False]**.
   * Impostare i criteri di valutazione su **[!UICONTROL Every time a record is updated and meets the condition requirements]**.

   ![](assets/using-a-custom-revenue-amount-field-4.png)

1. Nella sezione &quot;Ottimizzare il flusso per&quot;, selezionare **[!UICONTROL Fast Field Updates]**. Fai clic su **[!UICONTROL Done]** in basso a destra.

   ![](assets/using-a-custom-revenue-amount-field-5.png)

1. Per aggiungere l&#39;elemento, fare clic sull&#39;icona + e selezionare **[!UICONTROL Update Triggering Record]**.

   ![](assets/using-a-custom-revenue-amount-field-6.png)

1. Nella finestra Nuovo record aggiornamento, inserire quanto segue:

   * Immetti un’etichetta: il nome API viene generato automaticamente
   * In &quot;Come trovare i record da aggiornare e impostare i relativi valori&quot;, selezionare **[!UICONTROL Use the opportunity record that triggered the flow]**.
   * Nella sezione &quot;[!UICONTROL Set Filter Conditions]&quot; selezionare **[!UICONTROL Always Update Record]** come requisito condizione per aggiornare il record.
   * Nel campo &quot;[!UICONTROL Set Field Values for the Campaign Record],&quot; da, selezionare l&#39;importo opportunità Marketo Measure (**bizible2__Bizible_Opportunity_Amount__c**) e il valore da. Selezionare quindi il campo Importo personalizzato.
   * Fai clic su **[!UICONTROL Done]**.

   ![](assets/using-a-custom-revenue-amount-field-7.png)

1. Fare clic su **[!UICONTROL Save]**. Viene visualizzata una finestra a comparsa. Digita &quot;Etichetta flusso&quot; nella finestra Salva il flusso (il Nome API del flusso verrà generato automaticamente). Fare di nuovo clic su **[!UICONTROL Save]**.

   ![](assets/using-a-custom-revenue-amount-field-8.png)

1. Fare clic sul pulsante **[!UICONTROL Activate]** per attivare il flusso.

   ![](assets/using-a-custom-revenue-amount-field-9.png)

## Creare il flusso di lavoro in Salesforce Classic {#create-the-workflow-in-salesforce-classic}

I passaggi seguenti sono per gli utenti di Salesforce Classic. Se hai effettuato il passaggio a Salesforce Lightning, questi passaggi [si trovano sopra](#create-the-workflow-in-salesforce-lightning).

1. Passa a **[!UICONTROL Setup]** > **[!UICONTROL Create]** > **[!UICONTROL Workflow & Approvals]** > **[!UICONTROL Workflow Rules]**.

   ![](assets/using-a-custom-revenue-amount-field-10.png)

1. Selezionare **[!UICONTROL New Rule]**, impostare l&#39;oggetto come &quot;Opportunità&quot; e fare clic su **[!UICONTROL Next]**.

   ![](assets/using-a-custom-revenue-amount-field-11.png)

   ![](assets/using-a-custom-revenue-amount-field-12.png)

1. Configura il flusso di lavoro. Impostare il nome della regola come &quot;Aggiorna importo opportunità [!DNL Marketo Measure]&quot;. Imposta il criterio di valutazione su &quot;Creato e ogni volta che viene modificato&quot;. Per i criteri delle regole, selezionare il campo Importo personalizzato, selezionare l&#39;operatore [!UICONTROL as "Not Equal To"] e lasciare vuoto il campo &quot;Valore&quot;.

   ![](assets/using-a-custom-revenue-amount-field-13.png)

1. Aggiungi un’azione del flusso di lavoro. Imposta questo elenco a discesa su &quot;[!UICONTROL New Field Update]&quot;.
   ![](assets/using-a-custom-revenue-amount-field-14.png)

1. Qui compilerai le informazioni del campo. Nel campo &quot;Nome&quot;, si consiglia di utilizzare questa denominazione: &quot;[!DNL Marketo Measure] Importo Opp.&quot; Il &quot;Nome univoco&quot; verrà compilato automaticamente in base al campo &quot;Nome&quot;. Nell&#39;elenco a discesa &quot;Campo da aggiornare&quot; selezionare &quot;[!DNL Marketo Measure] importo opportunità.&quot; Dopo aver selezionato il campo, seleziona la casella &quot;Re-Evaulate Workflow Rules after Field Change&quot; (Valuta nuovamente regole flusso di lavoro dopo la modifica del campo). In &quot;Specifica nuovo valore campo&quot;, selezionare &quot;Utilizza una formula per impostare il nuovo valore&quot;. Nella casella vuota, rilascia il nome API del campo Importo personalizzato. Fai clic su **[!UICONTROL Save]**.

   ![](assets/using-a-custom-revenue-amount-field-15.png)

1. verrai riportato a una pagina rollup per il flusso di lavoro, assicurati di &quot;Attivare&quot; e non dimenticare di continuare. Per attivare, fare clic su **[!UICONTROL Edit]** accanto al nuovo flusso di lavoro e quindi su **[!UICONTROL Activate]**.

   Dopo aver completato questi passaggi, le opportunità dovranno essere aggiornate per attivare il flusso di lavoro in modo che abbia il nuovo valore dal campo [!UICONTROL custom opportunity].

   Questo può essere ottenuto eseguendo le opportunità tramite Data Loader in SFDC. Trova dettagli sull&#39;utilizzo di Data Loader in [questo articolo](/help/advanced-marketo-measure-features/custom-revenue-amount/using-data-loader-to-update-marketo-measure-custom-amount-field.md){target="_blank"}.

In caso di domande, contatta il team degli account Adobe (il tuo Account Manager) o il [[!DNL Marketo] supporto](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
