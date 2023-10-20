---
description: Utilizzo di un campo personalizzato per l’importo dei ricavi - [!DNL Marketo Measure] - Documentazione del prodotto
title: Utilizzo di un campo personalizzato per l'importo dei ricavi
hide: true
hidefromtoc: true
feature: Custom Revenue Amount
source-git-commit: 2d2fe74998abd853f6592c5e65edfe2ce39d7ce6
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 0%

---

# Utilizzo di un campo personalizzato per l&#39;importo dei ricavi {#using-a-custom-revenue-amount-field}

Per impostazione predefinita, i punti di contatto di attribuzione buyer richiameranno l’importo dell’opportunità da uno dei due campi seguenti:

* Importo (predefinito SFDC)
* [!DNL Marketo Measure] Importo dell’opportunità (personalizzato)

Se utilizzi un campo Importo personalizzato nelle opportunità, dovremo configurare un flusso di lavoro per calcolare i ricavi del punto di contatto dell’acquirente. Questa operazione richiede una conoscenza più avanzata di [!DNL Salesforce], quindi potrebbe richiedere l&#39;assistenza dell&#39;amministratore SFDC.

A partire da, avremo bisogno delle seguenti informazioni:

* Nome API del campo Importo

Da qui inizieremo a creare il flusso di lavoro.

## Creare il flusso di lavoro in Salesforce Lightning {#create-the-workflow-in-salesforce-lightning}

I seguenti passaggi sono per gli utenti di Salesforce Lightning. Se utilizzi ancora Salesforce Classic, questi passaggi [sono elencati di seguito](#create-the-workflow-in-salesforce-classic).

1. In Configurazione, digitare &quot;Flussi&quot; nella casella Ricerca rapida e selezionare **Flussi** per avviare Flow Builder. Dal pannello di destra, fai clic su **Nuovo flusso** pulsante.

   ![](assets/using-a-custom-revenue-amount-field-1.png)

1. Seleziona **Flusso attivato da record** e fai clic su **Crea** in basso a destra.

   ![](assets/using-a-custom-revenue-amount-field-2.png)

1. Nella finestra Configura avvio, selezionare l&#39;oggetto Opportunità. Dalla sezione Configura attivatore, seleziona **Un record viene creato o aggiornato**.

   ![](assets/using-a-custom-revenue-amount-field-3.png)

1. Nella sezione Imposta condizioni di ingresso, in Requisiti condizione, selezionare **La Logica Della Condizione Personalizzata È Soddisfatta**.
   * Dal campo di ricerca, selezionare il campo Importo personalizzato.
   * Imposta l’operatore come **Is Null** e il valore come **Falso**.
   * Imposta i criteri di valutazione su **Ogni volta che un record viene aggiornato e soddisfa i requisiti delle condizioni**.

   ![](assets/using-a-custom-revenue-amount-field-4.png)

1. Nella sezione &quot;Ottimizza il flusso per&quot;, seleziona **Aggiornamenti rapidi dei campi**. Clic **Fine**.

   ![](assets/using-a-custom-revenue-amount-field-5.png)

1. Per aggiungere l’elemento, fai clic sull’icona più (+) e seleziona **Aggiorna record di attivazione**.

   ![](assets/using-a-custom-revenue-amount-field-6.png)

1. Nella finestra Nuovo record aggiornamento, inserire quanto segue:

   * Immetti un’etichetta: il nome API viene generato automaticamente
   * In &quot;Come trovare i record da aggiornare e impostare i relativi valori&quot;, selezionare **Utilizza il record opportunità che ha attivato il flusso**.
   * Nella sezione &quot;Set Filter Conditions&quot; (Imposta condizioni filtro), seleziona **Aggiorna sempre record** come requisito della condizione per aggiornare il record.
   * In &quot;Imposta valori campo per il record della campagna&quot;, in campo, selezionare Importo opportunità Marketo Measure e impostare il campo Importo personalizzato.
   * Clic **Fine**.

   ![](assets/using-a-custom-revenue-amount-field-7.png)

1. Fai clic su **Salva**. Viene visualizzata una finestra a comparsa. Digita &quot;Etichetta flusso&quot; nella finestra Salva il flusso (il Nome API del flusso verrà generato automaticamente). Clic **Salva** di nuovo.

   ![](assets/using-a-custom-revenue-amount-field-8.png)

1. Fai clic su **Attiva** per attivare il flusso.

   ![](assets/using-a-custom-revenue-amount-field-9.png)

## Creare il flusso di lavoro in Salesforce Classic {#create-the-workflow-in-salesforce-classic}

I seguenti passaggi sono per gli utenti di Salesforce Classic. Se hai effettuato il passaggio a Salesforce Lightning, questi passaggi [si trova sopra](#create-the-workflow-in-salesforce-lightning).

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
